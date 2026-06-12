---
title: "Keyboard Backlight Not Working - Sony SVT15115CXS (18.04)"
date: 2018-08-24
forum: Hardware
---

### Post by azb8496 on 2018-08-24
[COLOR=#242729][FONT=Arial]The keyboard backlight on this laptop is not working.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]lsmod shows the "sony-laptop" module. When I get modinfo for sony-laptop, I see a parameter for kbd_backlight (0=Disable, 1=Automatic, 2=Always).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've tried "sudo modprobe -v sony-laptop kbd_backlight=1" (and also "=2"), which I saw as an answer somewhere else, but that did not work.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Note, the backlight works during boot, but turns off once Ubuntu loads.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I would forever be grateful to someone shedding some light on this predicament; I'm in the dark at the moment.[/FONT][/COLOR]

---

