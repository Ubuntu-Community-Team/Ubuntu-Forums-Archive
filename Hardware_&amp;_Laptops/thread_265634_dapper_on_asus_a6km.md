---
title: "dapper on asus a6km"
date: 2006-09-26
forum: Hardware &amp; Laptops
---

### Post by zes on 2006-09-26
hi, to all

i`ve installed dapper on my new asus a6km turion amd64, dapper (32b), i´m trying to configure all i can, so that´s will be my experience, and yours too.

obviously i had to boot dapper desktop cd from live cd without any usb device connected, after that (very quickly).

.- dappper recognize my xp installation quite good and now have  dual boot with grub.

.- i downloaded automatix and installed nvidia drivers for the graphic chip (geforce go 7300), works fine.... i hope it will be better but... i have 3d.....

.- sound work fine too.
.- i have to configure touchpad, now wors but not scroll and drag functions.

.- i have to add 1280x800 option in all modes of depth in xorg.conf to be able to change resolution, now seems better.

i will write more....

---

### Post by arkangel on 2006-09-26
Hi and welcome 
Althougth  I have another model form asus, try the following for your touchpad
 
in a console type
   $sudo apt-get install qsynaptics

then edit the  xorg :
   $sudo gedit /etc/X11/xorg.conf

in the section "input device"  with this line :  Identifier  "Synaptics Touchpad" add  this option 
    **Option "ShmConfig" "true"**

exit X , ctl+alt+bkpsc : and run 

    $sudo qsynaptics

if everithing goes ok , customize  accordingly

---

### Post by zes on 2006-09-27
yeah!, thanks, i found the way to configure touchpad rewriting xorg.conf, and after i get gsynaptics, now it´s another thing...., i was crazy with mouse arrow, now works fine.


.- next step i think will be install xgl/compiz,.... let me see..
 by

---

