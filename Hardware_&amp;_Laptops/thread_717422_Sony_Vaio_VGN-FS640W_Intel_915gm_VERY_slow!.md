---
title: "Sony Vaio VGN-FS640/W Intel 915gm VERY slow!"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by xxguitardud3 on 2008-03-07
My sony vaio is dual booting windows and ubuntu.  I wanted to use beryl on ubuntu but, its just way too slow.  My Intel 915gm has 128 mb of shared video memory, yet my little brothers old gateway laptop with an intel 2 (somthing like that lolz) that has a maximum of 8mb of video memory is alot faster.  I am using the i810 driver.

---

### Post by xxguitardud3 on 2008-03-07
bump!

---

### Post by c0r on 2008-03-24
tweaking your xorg.conf will help performance issues:

add this to your "Device" section:

Option      	"AccelMethod"   	"exa"
Option       	"MigrationHeuristic" 	"greedy"

and this to your "Module" section:

Section "Module"
    Load  "dbe"
    Load  "dri"
    Load  "extmod"
    Load  "glx"
    Load  "bitmap" # bitmap-fonts
    Load  "freetype"
    Load  "record"
    Load  "synaptics"
EndSection

also add following to the end of the xorf.conf file:

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option	"Composite" "true"
EndSection
   

These tweaks greatly improved my compiz-fusion i915chipset (i810 driver) setup.

:KS

---

### Post by xxguitardud3 on 2008-04-25
sorry i havent responded in a while, but now i have ubuntu hardy! how would i enter all that into my xorg since they changed the way u edit it?:confused:

---

