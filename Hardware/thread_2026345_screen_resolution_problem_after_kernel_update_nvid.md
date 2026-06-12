---
title: "screen resolution problem after kernel update nvidia"
date: 2012-07-14
forum: Hardware
---

### Post by vbdanl on 2012-07-14
hi.  i have a hp with nvidia geforce 6150 LE card.
not sure, but i think i had a problem with the screen resolution when i upgraded from 10.04 to 12.04.  don't remember what i did to get it to work, but my guess is installed some driver.

if i boot into 3.2.0.25 kernel, the screen resolution is good (1280x1024).
just installed updates to 3.2.0-26 kernel, and now screen resolution is something like 480x600 or something very big.. some screens i cant get to some of the buttons because there is no way of navigating..
when i go into additional drivers on the -25 kernel, it does not appear i am using any of the drivers it shows.

i don't want to mess something up in in -26 kernel that makes the older kernels quit working (not sure if that would happen or not, but thought i should just ask for help rather than just diving in)..

is there a config file or something i could look at in the older kernel that would tell me what i need to install in the newer kernel ?
both -25 and -26 kernels show "laptop" as the monitor in "displays", but this is a desktop with a old 17" proview monitor (not a laptop)..
thanks kindly for any help..

---

### Post by vbdanl on 2012-07-15
i figured out how to fix it after doing some more googling..
i ran these commands, then rebooted.. screen resolution is good now.
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

maybe i will have to do this after each kernel upgrade ?  not sure..

---

### Post by typhoon_tip on 2012-07-15
You should be OK now !

---

