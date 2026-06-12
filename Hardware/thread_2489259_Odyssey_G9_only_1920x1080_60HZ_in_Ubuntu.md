---
title: "Odyssey G9 only 1920x1080 60HZ in Ubuntu"
date: 2023-07-24
forum: Hardware
---

### Post by gst-grid-tech on 2023-07-24
[FONT=inherit]Hi,[/FONT]
[FONT=inherit]
[/FONT]
[FONT=inherit]just got an Odyssey G9, (  lc49g97tssnxdc  ) I use with my personal, Windows 11 and Work Windows 10 an resolution is great. However, on my personal Lenovo laptop, that i have docked, connected via Display port cable seems to max at 1920x1080 60HZ in Ubuntu.[/FONT]
[FONT=inherit]
[/FONT]
[FONT=inherit]I am NOT  very  Ubuntu/Linux/Unix  proficient..

However, my limited understanding is, 
if the Hardware supports it, you should be able to do it.


[/FONT]
[FONT=inherit]specs are[/FONT]
[FONT=inherit]
Samsung Odyssey G9, lc49g97tssnxdc,  display port to display port[/FONT]
[FONT=inherit]Lenovo ThinkPad T450s[/FONT]
[FONT=inherit]Mesa Intel® HD Graphics 5500 (BDW GT2)[/FONT]
[FONT=inherit]Ubuntu 22.04.2 LTS  64 bit[/FONT]
[FONT=inherit]GNome v 42.9[/FONT]
[FONT=inherit]Wayland  / x11[/FONT]
[FONT=inherit]Think Pad Pro Dock type 40A1[/FONT]
[FONT=inherit]
[/FONT]
[FONT=inherit]
[/FONT]
[FONT=inherit]My Wife has her OWN Lenovo ThinkPad T450s, but with Windows 11 and in the same Think Pad Pro Dock type 40A1, she is able to get [/FONT]
[FONT=inherit]3840 x 1080 119.97Hz, so some how i need to find the way to increase the resolution on my Lenovo ThinkPad T450s, 
running Ubuntu 22 since the hardware clearly supports at least 3840 x 1080 119.97Hz.

[/FONT]
[FONT=inherit]
[/FONT]
[FONT=inherit]Any help or suggestions would be greatly appreciated


[/FONT]
[FONT=inherit]
[/FONT]

---

### Post by gst-grid-tech on 2023-07-28
Thank you Chat GPT for helping my with the solution

xrandr --newmode "3840x1080_60.00"  419.25  3840 4168 4840 5600  1080 1083 1093 1111 -hsync +vsync
xrandr --addmode DP-2-2 3840x1080_60.00
xrandr --output DP-2-2 --mode 3840x1080_60.00

---

