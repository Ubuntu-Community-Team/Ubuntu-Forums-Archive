---
title: "accountat softaware(1C) print problem"
date: 2015-01-15
forum: Hardware
---

### Post by ilyamaltian on 2015-01-15
[COLOR=#000099][FONT=Andale Mono]Install 1c 8.3 on ubuntu and its impossible to print, it prints only vectors -tables and image borders, lines, cirles [/FONT][/COLOR]
[FONT=Andale Mono][COLOR=#000099]Try run use LD_DEBUG=libs
get this error:[/COLOR][/FONT]
[COLOR=#000099][FONT=Andale Mono]/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0//2.10.0/loaders/libpixbufloader-svg.so: error: symbol lookup error: undefined symbol: g_module_check_init (fatal) 2288:    /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0//2.10.0/loaders/libpixbufloader-svg.so: error: symbol lookup error: undefined symbol: g_module_unload (fatal) [/FONT][/COLOR]

---

