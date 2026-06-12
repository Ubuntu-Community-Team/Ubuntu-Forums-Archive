---
title: "touchpad does not work :("
date: 2010-01-26
forum: Hardware
---

### Post by Greensystemsgo on 2010-01-26
howdy ubuntu. recieved a laptop as a gift, ran xp ok i suppose, but this machine will NEVER game so i stuck ubuntu on it.

specs are amd xp 2200+ = 1.8ghz
256mb ram (built into board), i added an addition 256 totaling 512mb
via 32mb shared graphics

usb mouse works fine oob
onboard keyboard works fine oob
everything else works fine, just the mouse :(

MEDION MAM2010

---

### Post by quixote on 2010-01-28
touchpads usually use a synaptics driver in the /etc/X11/xorg.conf file. but maybe your setup needs something special.  If you can find the manufacturer/vendor and any other specifics for your touchpad, then I'd suggest searching for 

vendorname model xorg.conf

and see if anyone has some exact info on the lines you want in your xorg.conf.

---

