# @wornpage/command-surfaces

Compact Svelte 5 command toolbars and keyboard shortcut hints. The package is
source-delivered so consuming applications compile it with their own theme
tokens and Content Security Policy.

## Install

```sh
bun add @wornpage/command-surfaces
```

## Usage

```svelte
<script>
  import { Kbd, Toolbar } from '@wornpage/command-surfaces';
</script>

<Toolbar label="Document actions">
  <button type="button">Save</button>
  <Kbd keys={['Ctrl', 'S']} />
</Toolbar>

<Toolbar label="Filters" variant="chips">
  <button type="button">Open</button>
  <button type="button">Blocked</button>
</Toolbar>
```

## Toolbar

Toolbar groups related controls without replacing their native keyboard
behavior. It uses `role="group"`, not `role="toolbar"`, so children remain in
the normal Tab sequence. The default layout wraps controls; `variant="chips"`
uses responsive grid tracks. Both variants contain their children without
clipping focus rings or content.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `label` | `string` | `Toolbar` | Accessible group name |
| `variant` | `default \| chips` | `default` | Wrapping layout |

Slot: `children` (required controls).

## Kbd

Kbd renders one or more native `<kbd>` elements. Chord separators are based on
position, so repeated labels remain correct. Long labels wrap inside their
parent instead of widening the document.

| Prop | Type | Description |
|------|------|-------------|
| `keys` | `string[]` | Key labels in display order |

Slot: `children` (optional label before the keys).

## Theme tokens

The components use the existing Wornpage `--cockpit-*` tokens when available.
Toolbar-specific values can be overridden with `--worn-toolbar-background`,
`--worn-toolbar-border`, `--worn-toolbar-radius`, `--worn-toolbar-shadow`,
`--worn-toolbar-padding`, and `--worn-toolbar-gap`.
