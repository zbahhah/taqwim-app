# Offline world map: the data and its codes

Source: Natural Earth 5.1.2 (naturalearthdata.com), public domain, checked 2026-11-03.

These files were made by `tools/make-offline-map.py` from these inputs:

- `ne_50m_land.geojson` — SHA-256 `e874b27a51d146452be360cafb3cc50c86001074a67d534113e6534682f9826b`
- `ne_50m_lakes.geojson` — SHA-256 `d350b75978b26fe839b797c2c529b2fb8f47fb3983c03f4964e36d5df9378a52`
- `ne_50m_admin_0_boundary_lines_land.geojson` — SHA-256 `2faac4f6b34386f3d21b6e018cf151f241f00e5c936d44dd17d7d9bfb147fa48`
- `ne_50m_admin_0_countries.geojson` — SHA-256 `3e458fc036ad0a66411f2c1e6cac49c5d7bfb81cb1123bc513b22511a2b7fdeb`
- `ne_10m_populated_places.geojson` — SHA-256 `9b8e3de09048ef00dfc70357dbb9fa324493f214b5e0ae4daf1aa79a8d10116b`

- `land.json`, `lakes.json`: geometries only, no properties.
- `borders.json`: each line has `c`, its class, and `v`, the class of
  every point-of-view column that holds one.
- `labels.json`: the country label points first, then the cities;
  `k` is `c` for a country and `p` for a city, `z` the zoom it shows
  from, `r` a city's rank, `v` a country's point-of-view classes.

## Class codes

Boundary lines (`c`, and the values of `v`):

| Natural Earth | Code |
|---|---|
| International boundary (verify) | `i` |
| Disputed (please verify) | `d` |
| Line of control (please verify) | `l` |
| Indefinite (please verify) | `n` |
| Indeterminant frontier | `f` |
| Claim boundary | `k` |
| Map unit boundary | `m` |
| Admin-1 boundary | `a` |
| Unrecognized | `u` |

Country label points (the values of `v`):

| Natural Earth | Code |
|---|---|
| Admin-0 country | `c` |
| Admin-0 dependency | `p` |
| Admin-0 breakaway and disputed | `b` |
| Admin-1 states provinces | `s` |
| Admin-1 region | `r` |
| Unrecognized | `u` |

The keys of `v` are Natural Earth's own file codes: `iso`, `tlc`, `usa`, `fra`, `rus`, `esp`, `chn`, `twn`, `ind`, `nep`, `pak`, `deu`, `gbr`, `bra`, `isr`, `pse`, `sau`, `egy`, `mar`, `prt`, `arg`, `jpn`, `kor`, `vnm`, `tur`, `idn`, `pol`, `grc`, `ita`, `nld`, `swe`, `bdg`, `ukr`.

## Name overrides

| Natural Earth NAME | en | ar |
|---|---|---|
| Jerusalem | Al-Quds | keep |
| Makkah | Makkah | keep |
| Medina | Madinah | keep |

## Which point of view the app draws

Borders and country names follow one point of view: the saved
`border_view` setting, otherwise `sau` (Saudi Arabia's).
