---
title: "New screen resolution is not applied"
date: 2020-05-08
forum: Hardware
---

### Post by Elmi77 on 2020-05-08
Hi,

after connecting a new display to my computer, the screen resolution does not fit any more (as it still has a VGA-connector, it is not detected automatically). So this is not a problem, I added the configuration for the new resolution of 1368x768 via calls

[FONT=inherit]xrandr --newmode
[/FONT]
[FONT=inherit]xrandr --addmode
[/FONT]
[FONT=inherit]xrandr --output 

and placed this in the LightDM configuration so that it survives the next reboot. But my problem with this: When I open the display settings in XFCE, the new resolution appears there, but when I select it and then try to apply it, nothing happens, it stays at the old configuration of 1024x768 px.

So...any idea what could be wrong here?

Thanks!


[/FONT]

---

