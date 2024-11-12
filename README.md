# Modus themes for WezTerm

This repo contains the Modus themes made by Protesialos (aka "prot") for wezterm.
As the existing themes dont work correctly with emacs in terminal and also partially 
do not use the correct colors i decided to make an own spin.

## Usaged
Simply clone the repo into your ~/.config/wezterm and set the desired theme in your config.lua

### Auto (Dark/Light)
If you want automatically switch wezterm depending on the system appearance you can use the 
following in your config.lua:

``` lua
function scheme_for_appearance(appearance)
    if appearance:find 'Dark' then
        return 'modus-vivendi'
    else
        return 'modus-operandi'
    end
end

wezterm.on('window-config-reloaded',
           function(window, pane)
               local overrides = window:get_config_overrides() or {}
               local appearance = window:get_appearance()
               local scheme = scheme_for_appearance(appearance)
               local colors = wezterm.get_builtin_color_schemes()[scheme]
               if overrides.color_scheme ~= scheme then
                   overrides.color_scheme = scheme
                   window:set_config_overrides(overrides)
               end
           end)
```

## Kudos
Protesialos for the modus themes - https://protesilaos.com/emacs/modus-themes-colors

## Alternatives
anhsirk0 port - https://github.com/anhsirk0/wezterm-themes
Gogh themes - https://github.com/Gogh-Co/Gogh
