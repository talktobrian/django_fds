---
name: brian-styleguide
description: BRIAN / Bzu Tech design system (Figma Styleguide_BRIAN) — tokens, typography and every component (buttons, inputs, alerts, nav bar, side bar, prompt bar, cards, carousel...) with exact colors, borders, radii, paddings and variant states. Load before writing or reviewing ANY HTML/CSS in django_fds (templates or forum/static/css/style.css).
---

# BRIAN Styleguide

Source of truth: Figma `Styleguide_BRIAN` (fileKey `tPPZ8qOO7H3Thdrg9Hxare`).
Pages are built from the prototype in `Arquivo_BRIAN` (fileKey `kq127n5AgBO9vSoTrWNK9p`, page "Protótipo final" `34:3736`).
Light mode only — there is no dark mode (the `*-dark` tokens in Figma are unused; never add a dark theme).

## Rules
1. Use only the tokens below (CSS custom properties in `forum/static/css/style.css`). No off-palette hex, no other fonts.
2. Prefer **semantic** tokens (`Surface/…`, `Border/…`, `Text/…`, `Icon/…`) over raw palette steps.
3. Figma strokes: check `strokeAlign` per component (see each section). OUTSIDE stroke ⇒ CSS box grows by 2× stroke and radius grows by the stroke; CENTER ⇒ half. Figma caps each radius at min(w,h)/2, CSS doesn't — clamp yourself.
4. When a section below is not enough, inspect the Figma node (ids are listed per component) with a read-only `use_figma` call before guessing.

## 1. Foundations

### 1.1 Palette (collection "Brand")
| step | Blue (Information) | Red (Error) | Green (Success) | Orange (Primary/Warning) | Purple (Secondary) | Grey (Neutral) |
|---|---|---|---|---|---|---|
| 900 | #010117 | #0c0001 | #000501 | #0a0100 | #060206 | #0b0b0b |
| 775 | #090066 | #40000b | #002603 | #3b0a00 | #2b142e | #1e1e1e |
| 625 | #1900bb | #79011d | #004d0c | #9e2702 | #542c5a | #3e3e3e |
| 500 | **#2827ff** | **#ba0131** | **#027919** | #d34416 | **#894c92** | **#636363** |
| 375 | #597ffe | #ff274e | #01a825 | **#ff5826** | #b768c3 | #8a8a8a |
| 225 | #92afff | #ff8c8e | #00e436 | #ff8f71 | #d39cdb | #b2b2b2 |
| 100 | #d2defb | #fbd3d2 | #8efc90 | #fbd4c9 | #ead6ed | #dedede |
| 50  | #e9eefb | #fbeae9 | #d2fcd1 | #fbeae5 | #f4ebf5 | #eeeeee |

Bold = the "-default" step of that ramp. Foundation: black #000000, white #ffffff.
CSS names: `--blue-500`, `--orange-375`, `--grey-50`, `--black`, `--white` …

### 1.2 Alias roles (collection "Alias")
Primary = Orange · Secondary = Purple · Error = Red · Success = Green · Warning = Orange · Information = Blue · Neutral = Grey (same step numbers).

### 1.3 Semantic tokens (collection "Mapped", mode Light) — USE THESE
**Surface**
| token | → | hex |
|---|---|---|
| page | White | #ffffff |
| default | Primary/50 | #fbeae5 |
| default-secondary | White | #ffffff |
| default-secondary-action | Secondary/50 | #f4ebf5 |
| action | Primary/500 | #d34416 |
| action-secondary | Secondary/500 | #894c92 |
| action-hover | Primary/900 | #0a0100 |
| action-secondary-hover | Secondary/900 | #060206 |
| action-hover-alt | Primary/50 | #fbeae5 |
| action-secondary-hover-alt | Secondary/50 | #f4ebf5 |
| success / error / warning / information | */50 | #d2fcd1 / #fbeae9 / #fbeae5 / #e9eefb |
| information-dark | Information/625 | #1900bb |
| disabled | Neutral/100 | #dedede |
| dark | Neutral/775 | #1e1e1e |
| dark-hover | Neutral/625 | #3e3e3e |
| page-dark | Neutral/900 | #0b0b0b |

**Border**
| token | → | hex |
|---|---|---|
| default | Primary/100 | #fbd4c9 |
| default-dark | Neutral/900 | #0b0b0b |
| action | Primary/500 | #d34416 |
| action-secondary | Secondary/500 | #894c92 |
| action-hover | Primary/900 | #0a0100 |
| action-secondary-hover | Secondary/900 | #060206 |
| action-hover-alt | Primary/625 | #9e2702 |
| action-secondary-hover-alt | Secondary/625 | #542c5a |
| success | Success/500 | #027919 |
| error | Error/500 | #ba0131 |
| warning | Warning/375 | #ff5826 |
| information | Information/500 | #2827ff |
| disabled | Neutral/500 | #636363 |
| focus | Primary/500 | #d34416 |
| dark / dark-hover | Neutral/775 / 625 | #1e1e1e / #3e3e3e |

**Text**
| token | → | hex |
|---|---|---|
| heading | Grey/900 | #0b0b0b |
| body | Grey/775 | #1e1e1e |
| caption | Grey/625 | #3e3e3e |
| placeholder | Grey/375 | #8a8a8a |
| on-action / on-action-hover | White | #ffffff |
| action | Primary/500 | #d34416 |
| action-secondary | Secondary/500 | #894c92 |
| action-hover | Primary/900 | #0a0100 |
| action-secondary-hover | Secondary/900 | #060206 |
| action-hover-alt | Primary/625 | #9e2702 |
| action-secondary-hover-alt | Secondary/625 | #542c5a |
| success / error / warning | */625 | #004d0c / #79011d / #9e2702 |
| information | Information/500 | #2827ff |
| disabled | Grey/500 | #636363 |

**Icon**: default Grey/775 #1e1e1e · placeholder Grey/500 #636363 · on-action White · action Primary/500 · action-secondary Secondary/500 · action-hover Primary/900 · action-hover-alt Primary/625 · success Success/625 · **error Error/500 #ba0131** · warning Warning/625 · information Information/500 · disabled Grey/500.

### 1.4 Typography (text styles + "Responsive" collection, Desktop | Mobile)
| style | family / weight | Desktop size/line | Mobile size/line | notes |
|---|---|---|---|---|
| H1 | Momo Trust Display Regular | 60/72 | 48/56 | |
| H2 | Momo Trust Display Regular | 48/56 | 40/48 | |
| H3 | Carlito Bold | 40/48 | 32/40 | |
| H4 | Carlito Bold | 32/40 | 28/32 | |
| H5 | Carlito Bold | 24/28 | 24/28 | |
| H6 | Carlito Bold | 20/24 | 20/24 | UPPERCASE |
| Body/lg | Momo Trust Sans Regular | 20/24 | same | |
| Body/md | Momo Trust Sans Regular | 16/20 | same | default body |
| Body/sm | Momo Trust Sans Regular | 12/16 | same | |
| Caption | Geist Mono Regular | 12/16 | same | only monospace allowed |
| Button | Momo Trust Display Regular | style says 20/auto; components use 16/20 (see Button) | | |

Letter-spacing 0 everywhere. Paragraph spacing = font size.
Font-family tokens: Heading 1-2 → Momo Trust Display; Heading 3-6 → Carlito; Body → Momo Trust Sans; Caption → Geist Mono.

### 1.5 Scale, border width, radius
- Spacing scale (Brand/Scale): 0, 1, 2, 4, 8, 12, 16, 20, 24, 32 px (names 0,25,50,100…700).
- Border width: none 0 · sm 1 · md 2 · lg 4.
- Border radius: none 0 · sm 1 · md 2 · lg 4 · xl 8. (Components may use literal values — see each.)

### 1.6 Icons
Icon instances are 24×24 (library page "styleguide" holds `Message`, `Info` under "UI" etc.). Color always comes from the `Icon/*` token of the host state — use `currentColor` in SVG and set `color` on the parent.

### 1.7 Shared focus ring (Button, Field, …)
Figma draws a separate `focus` rectangle: x/y = −3 from the component frame, `stroke 2px OUTSIDE`, radius 2, color `Border/focus` #d34416 (Field in error: `Border/error` #ba0131).
Because the component itself has a 1px OUTSIDE stroke, that is: **2px gap after the visible border, then a 2px ring**.
CSS: `outline: 2px solid var(--border-focus); outline-offset: 2px;` (on `:focus-visible`).

## 2. Components (Figma pages in file order)

### 2.1 Label — page `672:1341`
Variants `Status = default | required`. Props: Label text, `icon` (bool, default on, swap default `Info`), `label` (bool).
- Row: horizontal, gap 8, align center, no padding. Height 24 (20 if icon off).
- Text: Body/md 16/20, `Text/body` #1e1e1e.
- Icon: `Info` 24×24, `Icon/action` #d34416 (orange info icon after the text).
- `required`: adds a red asterisk vector 7×6 after the icon, `Icon/error` #ba0131.

### 2.2 Field (the bare text box) — page `725:250`
Variants `Status = default | hover | focus | disabled` × `Type = default (empty/placeholder) | filled | error`.
Props: Label text, `icon-left` (bool, default `Message` = mail icon), `icon-right` (bool, default `Info`).
- Size 379×40 frame + **1px OUTSIDE stroke** ⇒ visible 381×42, visible radius 5 (frame r=4). In CSS: `border:1px; border-radius:5px; height:42px` (box-sizing border-box) or `height:40px` + `content-box`.
- Layout: horizontal, gap 12, padding 0 8, align center. Icons 24×24. Text Body/md 16/20.

| Status / Type | bg | border | text | icons |
|---|---|---|---|---|
| default / default | Surface/default-secondary #fff | Border/default #fbd4c9 | Text/placeholder #8a8a8a | Icon/placeholder #636363 |
| default / filled | #fff | #fbd4c9 | Text/body #1e1e1e | #636363 |
| default / error | #fff | Border/error #ba0131 | Text/error #79011d | Icon/error #ba0131 |
| hover / default & filled | Surface/action-hover-alt #fbeae5 | Border/action-hover-alt #9e2702 | Text/action-hover-alt #9e2702 | Icon/action-hover-alt #9e2702 |
| hover / error | Surface/error #fbeae9 | #ba0131 | #79011d | #ba0131 |
| focus / default | #fff | #fbd4c9 | #8a8a8a | #636363 | + focus ring #d34416 |
| focus / filled | #fff | #fbd4c9 | #1e1e1e | #636363 | + focus ring #d34416 |
| focus / error | Surface/error #fbeae9 | #ba0131 | #79011d | #ba0131 | + focus ring **#ba0131** |
| disabled / any | Surface/disabled #dedede | Border/disabled #636363 | Text/disabled #636363 | Icon/disabled #636363 |

Note: on focus the field border stays `Border/default` (it does NOT turn orange) — the separate ring signals focus.

### 2.3 Input (Label + Field + Hint) — page `726:516`
Variants `Status = default | filled | error` × `Type = default | email`. Props: `Hint copy` (bool + text).
- Vertical stack: Label → (gap **12**) → [Field → (gap **4**) → Hint]. Width 379.
- Label: `default`/`filled` use Label/default, `error` uses Label/required (red asterisk).
- Hint (Body/md 16/20): default `Text/body` #1e1e1e · filled `Text/success` #004d0c · error `Text/error` #79011d.
- Field mapping: default→Field default/default, filled→Field default/filled, error→Field default/error.
- `Type=email` = same structure; the left icon is the `Message` (envelope) icon. `Type=default` shows the label info icon; filled/error variants hide it.

### 2.4 Button — page `672:918`
Variants `Status = default | hover | focus | disabled` × `Type = default | outline | outline-secondary | transparent`.
Props: Label text (default "Button"), `icon-left` / `icon-right` (bools, default on, 24×24 swap, default `Message`).
- Frame 158×48 (hug) + **1px OUTSIDE stroke** ⇒ visible height 50, visible radius **3** (frame r=2).
- Layout: horizontal, gap 8, padding 12 all sides, centered.
- Label text: style **Button = Momo Trust Display Regular 20px, line-height auto** (renders 26px tall). No uppercase.
- CSS skeleton: `display:inline-flex;align-items:center;justify-content:center;gap:8px;padding:12px;border:1px solid;border-radius:3px;font:400 20px/normal var(--font-display);`

| Status / Type | bg | border | text & icon |
|---|---|---|---|
| default / default | Surface/action #d34416 | Border/action #d34416 | Text/on-action #fff |
| default / outline | Surface/default-secondary #fff | Border/action #d34416 | Text/action #d34416 |
| default / outline-secondary | #fff | Border/action-secondary #894c92 | Text/action-secondary #894c92 |
| default / transparent | none | none | Text/action #d34416 |
| hover / default | Surface/action-hover #0a0100 | Border/action-hover #0a0100 | #fff |
| hover / outline | Surface/action-hover-alt #fbeae5 | #d34416 (unchanged) | #d34416 |
| hover / outline-secondary | Surface/action-secondary-hover-alt #f4ebf5 | #894c92 (unchanged) | #894c92 |
| hover / transparent | none (no visual change) | none | #d34416 |
| focus / any | same as default of that type | same | same | + focus ring §1.7 (always orange #d34416, even outline-secondary) |
| disabled / any type (incl. transparent) | Surface/disabled #dedede | Border/disabled #636363 | Text/disabled #636363 |

### 2.5 Button icon (icon-only square) — page `672:1232`
Variants `Status = default | hover | focus | disabled` × `Type = default | outline | transparent`. Prop: `icon` swap (default `Message`).
- 40×40 frame + 1px OUTSIDE stroke ⇒ visible 42×42, radius 3. Padding 8, icon 24×24 centered.
- Colors identical to Button (§2.4) for `default` and `outline`, **except transparent**:
  - transparent default/focus: icon `Icon/placeholder` #636363 (grey), no bg/border.
  - transparent hover: icon turns `Icon/action` #d34416, still no bg.
- Focus ring §1.7 (rect at −3, 2px). Disabled = #dedede bg, #636363 border+icon (all types).
- Always give it an `aria-label`.

### 2.6 BRIAN icon (chat launcher) — page `760:423`
Variants `Status = default | hover`.
- default: 32×32 circle outline, stroke **2px INSIDE** `Icon/action` #d34416, no fill; a small 13×13 glyph (fill+stroke #d34416) inside.
- hover: expands to a **124×32 pill** (same 2px #d34416 outline) revealing the text "BRIAN" in `Text/action-hover-alt` #9e2702 next to the glyph.
- CSS: `border:2px solid var(--orange-500); border-radius:999px; height:32px;` animate width 32→124 on hover, text fades in.
- `brian-logo` (24×36): the mascot logo — multi-gradient vector, export as SVG, never redraw with CSS.

### 2.7 Link — page `726:840`
Variants `Status = default | hover | focus | disabled` (Figma names some "focu"/"Status4" = focus/disabled) × `Type = default | info | error | success | warning`.
Props: Label, `icon-left`/`icon-right` (bools, 24×24 swap).
- Row gap **12**, no padding, height 24. Text Body/md 16/20 **UNDERLINE** always.

| Type | default (text+icon) | hover |
|---|---|---|
| default | Text/action #d34416 | Text/action-hover-alt #9e2702 |
| info | Text/on-action #fff (for use on solid blue banner) | Text/information #2827ff |
| error | #fff | text Text/error #79011d, icon Icon/error #ba0131 |
| success | #fff | Text/success #004d0c |
| warning | #fff | Text/warning #9e2702 |

- focus: same colors as default + ring: rect at −2 (link has no border) ⇒ `outline:2px solid #d34416; outline-offset:2px`.
- disabled: bg `Surface/disabled` #dedede, radius 2, text+icon #636363.
- Inside tinted alerts (§ Alerts) links use the alert's text color — see Alerts.

### 2.8 Text Area — page `782:685`
Composite `Text Area` (vertical, gap 12): Label → Hint (Body/md, `Text/caption` #3e3e3e, ABOVE the box) → box → "Character count" (Body/md, #3e3e3e, below).
Box `.textarea-item` variants `Status = default | hover | focus | disabled` × `Type = default | filled`:
- 579×263, **1px INSIDE stroke** (unlike Field!) ⇒ CSS `border:1px; border-radius:2px;` exact size. Padding 8, text top-left Body/md.

| Status | bg | border | text |
|---|---|---|---|
| default | #fff | Border/default #fbd4c9 | placeholder #8a8a8a / filled #1e1e1e |
| hover | Surface/action-hover-alt #fbeae5 | **Border/action #d34416** | Text/action-hover-alt #9e2702 |
| focus | #fff | #fbd4c9 | as default | + ring at −2 ⇒ `outline:2px solid #d34416; outline-offset:2px` |
| disabled | #dedede | #636363 | #636363 |
No error variant exists — if needed reuse Field error colors.

### 2.9 Side Bar (BRIAN chat history) — page `883:76`
This is the ONLY dark surface family; it uses the `*-dark` semantic tokens (still light-mode site, just a dark panel).

**`side-bar`** variants `Status = default | condensed`, prop `info-card` (bool):
- default: 352 wide, bg `Surface/page-dark` #0b0b0b, radius **8**, vertical, gap **24**, padding **24**.
  Children in order: header row → "Fazer Quiz" Button (default type, full width 304) → `.info-card` → `.conversas` list.
- condensed: **72 wide**, same bg/radius/padding; only the header icon (Chat) is visible.

**Header row `.sidebar-item`**: horizontal gap 12, align center — `Chat` icon 24 · title "Histórico" · `curtain_right_expand_left` icon 24 (collapse toggle) at the right.
- In the side bar instance: title **Carlito Bold 24/28 (H5)**, `Text/heading-dark` #dedede; icons `Icon/on-action` #ffffff.
- (Component default: Body/lg 20/24 #b2b2b2, icons #b2b2b2 — the side bar overrides it.)

**`.info-card`** (login nudge): bg `Surface/information-dark` #1900bb, border `Border/information` #2827ff **1px OUTSIDE**, radius 4 (visible 5), vertical gap 12, padding 12.
- `Info` icon 24 white → text Body/md 16/20 #fff ("Entre na sua conta para salvar histórico.") → gap 4 → Link Type=info "Fazer login" (white, underlined).

**`.conversas`** list: vertical gap 10. `.newconversation-item` first, optional hint (Body/md, `Text/caption-dark` #8a8a8a), then `.conversation-item`s, all full width.

**`.newconversation-item`** ("Nova Conversa" + `Add_round` icon 24): padding 14/10, gap 12, radius 4 + 1px OUTSIDE stroke, text Body/md `Text/body-dark` #b2b2b2, icon `Icon/default-dark` #b2b2b2.
| Status | bg | border |
|---|---|---|
| default | Surface/dark-hover #3e3e3e | Border/dark-hover #3e3e3e |
| hover | Surface/dark #1e1e1e | #3e3e3e |
| focus | #3e3e3e | #3e3e3e + ring rect at −2 (⇒ `outline:2px solid #d34416; outline-offset:1px`) |
| disabled | #dedede | #636363, text/icon #636363 |

**`.conversation-item`** (one history entry): padding 14/10, gap 10, radius 4 + 1px OUTSIDE stroke, text Body/md #b2b2b2, height 48 (visible 50).
| Status | bg / border |
|---|---|
| default | Surface/dark #1e1e1e / Border/dark #1e1e1e |
| hover | Surface/dark-hover #3e3e3e / #3e3e3e |
| focus | #1e1e1e + orange ring (as above) |
| disabled | #dedede / #636363, text #636363 |

### 2.10 Prompt Bar — page `896:674`
**`Prompt Bar`**: bg `Surface/page-dark` #0b0b0b, vertical gap 12, padding 24, items centered. Contains `.input-item` (full width) + `.smalltext-info` (centered).
**`.input-item`** (chat input): bg #fff, border `Border/default` #fbd4c9 **1px OUTSIDE**, radius 4 (visible 5), height 48 (visible 50), horizontal gap 12, padding **4 5**, align center.
- Left: Button icon `transparent` (grey #636363 icon — e.g. attach). Middle: placeholder "Pergunte ao BRIAN..." Body/md `Text/placeholder` #8a8a8a, flex 1. Right: Button icon `default` (orange #d34416 bg, white send icon).
- Reuse Field hover/focus/disabled colors for its states (no separate variants in Figma).
**`.smalltext-info`**: Body/sm 12/16 `Text/body` #1e1e1e (disclaimer under the bar; on the dark bar use `Text/body-dark` #b2b2b2 for contrast).

### 2.11 Card (modal / BRIAN login nudge) — page `896:767`
**`Card`** (prop `logo` bool): bg #fff, radius **8**, NO border, NO shadow, vertical gap 12, padding **51 top / 24 sides / 24 bottom**, width 340.
- Close button: Button icon `transparent` 40×40, **absolutely positioned** top-right (frame at 24,24, right-aligned) — X icon grey #636363, orange on hover.
- `brian-logo` 24×36 centered → `.card-info-item` → button row.
- **`.card-info-item`**: vertical gap 4 — title **H5 Carlito Bold 24/28** `Text/heading` #0b0b0b; hint **Body/sm 12/16** `Text/caption` #3e3e3e.
- Button row: horizontal gap 12, two equal buttons (140 each): primary `default` + `outline`.

### 2.12 Forms (login / signup card) — page `896:971`
**`Forms`**: bg #fff, radius **8**, no border/shadow, vertical gap **24**, padding **24**, width 323 (content 275).
Order: `.card-info-item` (title "Entrar" H5 + Body/sm caption) → Input ("Usuário:") → Input ("Senha:") → full-width Button default ("Entrar") → `.account-item`.
- Inputs here: Label without the info icon (label 20 tall), hint hidden ⇒ Input height 72 (20 + 12 + 40).
- **`.account-item`**: horizontal gap 4 — "Não possui conta?" Body/md `Text/caption` #3e3e3e + Link default "Criar conta." (orange, underlined, no icons).
- Error/filled states: use Input status variants (§2.3). Page background behind the form: `Surface/default` #fbeae5 (orange-50) — see prototype.

### 2.13 Balloon (user chat bubble) — page `902:807`
- bg `Surface/default` #fbeae5 (orange-50), **no border**, padding 12, hug width.
- Radius **24 24 24 0** (TL TR BR BL) — square bottom-left corner = the "tail". CSS `border-radius:24px 24px 24px 0;`
- Text Body/md 16/20 `Text/body` #1e1e1e. Prop: Text.
- BRIAN replies in the prototype are plain text (no bubble) — check the BRIAN chat frames before styling bot messages.

### 2.14 Profile (team member card) — page `902:813`
- 252×92, bg `Surface/default` #fbeae5, border `Border/default` #fbd4c9 **1px OUTSIDE**, radius **48 48 48 0** (pill with square bottom-left) ⇒ CSS radius `49px 49px 49px 0` + 1px border.
- Vertical, padding 16, content aligned to bottom (`justify-content:flex-end`), centered horizontally, gap 0.
- Lines: course tag **Caption Geist Mono 12/16** `Text/action` #d34416 (booleans `design` / `ciencias da computação` — show one: "Design" or "Ciências da Computação") → name **Momo Trust Display 20 (Button style)** `Text/body` #1e1e1e → email **Body/sm 12/16** `Text/caption` #3e3e3e.

### 2.15 Nav Items — page `902:836`
**`.navlink-item`** variants `Status = default | hover | focus | disabled` × `Type = default | active`:
- Text **H6 Carlito Bold 20/24 UPPERCASE**, no underline, no padding.
| Status | default type | active type (current page) |
|---|---|---|
| default | Text/body #1e1e1e | Text/action #d34416 |
| hover | Text/action #d34416 | Text/action-hover-alt #9e2702 |
| focus | same as default + ring at −2 (`outline:2px solid #d34416; outline-offset:2px`) | same |
| disabled | Text/disabled #636363 | — |

**`.login-item`** ("ENTRAR"): `Sign_in_squre` icon 24 + text H6 uppercase, gap **10**.
default #d34416 (icon+text) · hover #9e2702 · focus = default + ring at −2 · disabled #636363.

### 2.16 Nav Bar — page `902:904`
- 1440×56, bg `Surface/page` #fff, **no border, no shadow**. Horizontal space-between, padding **8 20**, align center.
- Left: `Logo` 131×40 (mascot + "Bzu" wordmark; brand art uses #f25c27 / #2c2c2c — keep as exported SVG, don't recolor to tokens).
- Right group (space-between, ~970 wide): Nav-links (3 `.navlink-item`, gap **64**: INÍCIO / SOBRE A BZU / FALE CONOSCO) · `.login-item` ENTRAR · `brian-icon` shown in its **hover/pill state** (124×32 with "BRIAN").
- Logged-in state and mobile menu are not designed in the styleguide — check the prototype frames.

### 2.17 Footer Items — page `902:1026`
**`footer-link`** variants `Status = default | hover | focus | disabled` × `type = default | active`. Lives on the black footer.
- Text Body/md 16/20, sentence case, no underline.
| Status | default type | active type |
|---|---|---|
| default | Text/body-dark #b2b2b2 | Text/action #d34416 |
| hover | Text/action #d34416 | Text/action-hover-alt #9e2702 |
| focus | as default + ring at −2 (`outline:2px solid #d34416; outline-offset:2px`) | same |
| disabled | #636363 | — |
Footer column headings (NAVEGAÇÃO / SUPORTE / PRODUTO) come from the prototype — H6 style (Carlito Bold 20/24 uppercase).

### 2.18 Alerts — page `902:1065`
**`Alert`** variants `Type = default | error | information | success | warning`. Prop: Message.
- 257 wide (fluid), padding **12**, vertical gap **4**, radius **8**, border **1px OUTSIDE** (visible radius 9).
- Content: Message Body/md → Link (underlined, **same color as the message**, no icons).
- **Bottom accent line**: absolute, inset 12px left/right, at the bottom edge, **2px** thick, colored like the border (default uses #9e2702). CSS: `::after{content:"";position:absolute;left:12px;right:12px;bottom:1px;height:2px;background:…}` (verify position with a screenshot if it reads as a progress/timer bar).

| Type | bg | border | text & link | accent line |
|---|---|---|---|---|
| default | Surface/default #fbeae5 | Border/default #fbd4c9 | Text/body #1e1e1e, link #d34416 | Border/action-hover-alt #9e2702 |
| error | Surface/error #fbeae9 | Border/error #ba0131 | Text/error #79011d | #ba0131 |
| information | Surface/information #e9eefb | Border/information #2827ff | Text/information #2827ff | #2827ff |
| success | Surface/success #d2fcd1 | Border/success #027919 | Text/success #004d0c | #027919 |
| warning | Surface/warning #fbeae5 | Border/warning #ff5826 | Text/warning #9e2702 | #ff5826 |

**`.info-card`** (solid info banner, also used in Side Bar §2.9): bg #1900bb, border #2827ff 1px OUTSIDE, radius 4, padding 12, gap 12; white Info icon → `.text-info` (Body/md #fff) → gap 4 → Link Type=info (white underlined; hover #2827ff).
**`.text-info`**: plain Body/md `Text/body` #1e1e1e text block (white when inside info-card).

### 2.19 Case Cards — page `957:62`
Variants `Status = default | hover`. Props: Card-Content (bool), Card-text (title), Case-study (body).
- 424×308, **image fill (cover)**, border `Border/default` #fbd4c9 **1px OUTSIDE**, radius **8** (visible 9).
- default: image only.
- hover: full-size overlay `Surface/page-dark` #0b0b0b at **80% opacity**, same radius 8, padding **24**, vertical gap **12**:
  title **H4 Carlito Bold 32/40** + body **Body/md 16/20**, both `Text/heading-dark` #dedede.
- CSS: overlay `position:absolute; inset:0; background:rgb(11 11 11 / .8); opacity:0 → 1 on :hover / :focus-within`.

### 2.20 Carousel — page `988:517`
**`Carousel`**: horizontal, gap **12**, align center: left arrow · progress bar · right arrow.
**`.carousel-item`** (arrow button) variants `Status = default | hover | focus | disabled` × `Type = left | right`:
- 40×40 circle (radius 999) + **1px OUTSIDE** border ⇒ visible 42×42. Padding 8, icon `Expand_left`/`Expand_right` 24×24.
| Status | bg | border | icon |
|---|---|---|---|
| default | #fff | Border/action #d34416 | Icon/action #d34416 |
| hover | Surface/action-hover-alt #fbeae5 | #d34416 | #d34416 |
| focus | #fff | #d34416 | #d34416 + circular ring at −3 (`outline:2px solid #d34416; outline-offset:2px; border-radius:50%`) |
| disabled | #dedede | #636363 | #636363 |
**`.carousel bar`** (scroll indicator): track height **8**, radius 999, bg `Surface/default` #fbeae5, clips; thumb absolutely positioned, height 8, radius 999, bg `Surface/action` #d34416. Thumb width ≈ visible fraction (e.g. 75 of 168); left offset = scroll progress.

## 3. Page patterns (prototype `Arquivo_BRIAN` → "Protótipo final" `34:3736`)
Frame → template map: inicio `34:4133` → index.html · sobre a bzu `126:3440` → sobre_empresa.html · fale conosco `34:4222` → sobre_nos.html · login/signup section `123:2807` (default/error/filled frames) · BRIAN chat section `123:3439` (no-login, login-nohistory, login-history, collapsed-bar, alert frames). quiz.html has no frame — it is composed from styleguide components.
- Decorative blobs are square VECTORs with corner radius 402 on 3 vertices: rotation 0 ⇒ square corner bottom-left (`50% 50% 50% 0`); rotation −180 ⇒ square corner bottom-right (`50% 50% 0 50%`) — verified against Figma renders. Anchor each blob to its own section; sections must not set z-index so blobs can sit above the dark band.

- Canvas 1440 wide, page bg `Surface/page` #fff. Content column **868** centered (side padding 20 at the edges).
- NavBar (§2.16) on top of every page.
- **Hero**: padding 100 top/bottom, H1 (60/72 Momo Trust Display) centered over an 868-wide media block (chat preview video/image).
- **Dark section** (e.g. "Seu serviço em um chat com IA"): bg `Surface/page-dark` #0b0b0b, **radius 8**, padding **200 / 20**, gap 72. Uses orange blobs: `Surface/action` #d34416 shapes with large asymmetric radii (e.g. `160 402 402 0`, `402 402 0 402`) — clamp radii to half the side (Figma clamps, CSS scales).
- **CTA section**: padding 200/20, gap 48; H3 (Carlito Bold 40/48, `Text/heading`) + Body/md `Text/caption` #3e3e3e, gap 8; button row gap **20**: outline "Sobre a Bzu Tech" + default "Fale com BRIAN".
- **Footer**: bg #0b0b0b, radius **8 8 0 0**, padding **50 / 20**, gap 83.
  - Logo + tagline "Chatbots com IA" (Body/sm, #8a8a8a).
  - Columns NAVEGAÇÃO / SUPORTE / PRODUTO: heading **H6** (Carlito Bold 20/24 uppercase) `Text/heading-dark` #dedede; column gap 24 between heading and list; links (`footer-link` §2.17) stacked with gap **32**.
  - Copyright "© 2026 BRIAN | Todos os direitos reservados." Body/md `Text/caption-dark` #8a8a8a.
- **Login/Signup**: section padding 100/20, `Forms` card (§2.12) centered; decorative orange-50 blobs behind.
- **BRIAN chat**: Side Bar (§2.9) left, Balloon (§2.13) for user messages, Prompt Bar (§2.10) bottom, Card (§2.11) as the login nudge, Alerts (§2.18) for the alert frames.

## 4. CSS implementation notes (drifts fixed 2026-11-25)
- `style.css` now defines the full semantic layer: `--surface-*`, `--border-*`, `--text-*`, `--icon-*` (names = Figma Mapped tokens, kebab-case). Use these in new CSS.
- `--text-heading` = #0b0b0b, `--text-subtitle` = #3e3e3e, `--text-primary`/`--text-color` = Text/body #1e1e1e, `--border-color` = Border/default #fbd4c9.
- `--fs-button: 20px; --lh-button: normal`. `--radius-button: 3px` (visible), `--radius-field: 5px` (visible).
- Responsive type follows Figma Mobile mode at ≤1024px (H1 48/56, H2 40/48, H3 32/40, H4 28/32); ≤640px only reduces section padding.
- Legacy `.btn-primary` / `.btn-secondary` = Button default / outline (1px border, 400 weight, hover #0a0100 / #fbeae5, focus ring, disabled). `.form-control` and `.campo__input`: focus keeps the border and shows the 2px ring.
- Still off-spec, not yet migrated: `--shadow-sm/--shadow-md` (rgba(26,0,32)) — the styleguide has no shadows; avoid using them on new components.

## 5. Checklist before finishing any UI change
- [ ] Every color is a token from §1 (semantic first). No dark-mode code.
- [ ] Fonts only: Momo Trust Display, Carlito, Momo Trust Sans, Geist Mono — with the right style per §1.4.
- [ ] Border width/alignment per component (OUTSIDE ⇒ add to size & radius; Text Area is INSIDE).
- [ ] All states implemented: hover, `:focus-visible` ring (2px #d34416, offset per component), disabled (#dedede / #636363).
- [ ] Icons 24×24, `currentColor`, colored by the state's `Icon/*` token.
- [ ] Compare against the prototype frame (screenshot) when building a page.

