---
title: "voodoo3 only displaying at 640x480"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by iggy on 2005-04-19
hi guys, complete linux noob here, so please be gentle :)

just installed 5.04, everything went fine but i cant change the resolution from 640x480 or the refresh rate from 60hz.

i have tried changing from system/screen resolution, but the drop down menus only offer me the previous choices :(

i am running a voodoo3 3000 with a stock install of ubuntu 5.04.

ive had a look at the driver manager ,but it doesnt seem to allow me to change the display driver, and im feeling a bit stuck now. any help would be muchly appreciated, thanks,

stoo.

---

### Post by wondering_jew on 2005-04-20
hmmm one thing that might work for you is to reconfigure your xserver... I use an nvidia card but had the same problem with screen res. Im not sure if you have to be in a console to do it but i always was when I did it at any rate from a console or terminal type

sudo dpkg-reconfigure xserver-xorg

this will bring up a menu driven utility- for the most part you should leave everything as is and not mess with the other settings, but it will allow you to select display resolutions you can use- when you are done restart x and you should be able to select the screen resolutions you added in preferences- if this doesnt work spend some time searching the forums, theres probably some other solutions floating around.

---

