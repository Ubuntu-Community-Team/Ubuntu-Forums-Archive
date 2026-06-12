---
title: "Mobile Intel Graphics 945gm on 7.04 -- feisty"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by resnasty on 2007-07-09
My highest resolution is 1280x800, when i should be able to get 1440x900
.
.
Ive noticed plenty of posts on this.. but they all seem really old, generally talking about dapper or edgy... I'm wondering if there is anything up to date on this in regards to feisty...
.
.
sorry if this is a true double post.. im just having a hell of time trying to find the answer

---

### Post by Gabn on 2007-07-10
have you tried using the 915resolution hack [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

and/or installing the newer driver sudo apt-get install xserver-xorg-video-intel

---

### Post by resnasty on 2007-07-10
I have not... mainly due to the fact im getting lost in the forums... some state that you do not need to use this package... and some do... 

it also seems the linux world moves very fast.. so when i see dates on certain forums im worried i could be going down the wrong road.. and maybe there is something newer around the corner :)
.
.
I already tried to run the update for intel... and that didnt seem to do it... so i guess ill give this 915 a try then

---

### Post by resnasty on 2007-07-10
also... how much ram should i allocate.... i have 2gb in this laptop... and i understand that the 945 has hardly any of itself.. and utilizes ram from the system... 

i just do not know what a good value would be

---

### Post by BoyOfDestiny on 2007-07-10
> **resnasty said:**
> I have not... mainly due to the fact im getting lost in the forums... some state that you do not need to use this package... and some do... 

it also seems the linux world moves very fast.. so when i see dates on certain forums im worried i could be going down the wrong road.. and maybe there is something newer around the corner :)
.
.
I already tried to run the update for intel... and that didnt seem to do it... so i guess ill give this 915 a try then

Ok I have the same chipset as you. :) Yes you need to install 915resolution. As for not having to do it anymore, the answer is yes with Ubuntu Gutsy (still alpha, so I'd stay away from it unless you like living on the edge ;) ). It uses the new Intel driver not the i810 that feisty has.

---

### Post by resnasty on 2007-07-10
Well.. after all of this... i decided to look at the specs of this laptop "lenovo z61t 14.1 " and it said the highest res was 1280x800... which i had by default...

BLAH!!! everything was ok from the get go?....
I just read everywhere that people were getting 1440x900 res... and i assumed i should as well...
.
.
i feel like a tard

---

### Post by dabl on 2007-07-10
When you installed the xserver-xorg-video-intel driver, did you then change the driver in /etc/X11/xorg.conf to "intel" and restart the X server?

---

