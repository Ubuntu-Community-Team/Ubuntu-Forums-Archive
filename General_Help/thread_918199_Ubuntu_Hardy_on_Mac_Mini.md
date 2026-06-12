---
title: "Ubuntu Hardy on Mac Mini"
date: 2008-09-12
forum: General Help
---

### Post by rugbert on 2008-09-12
I followed this guide:
[https://help.ubuntu.com/community/Mac_mini](https://help.ubuntu.com/community/Mac_mini)
but it only works with 7.04

8.04 installs fine but upon reboot it doesnt give me the option for booting to "windows". I hold alt, and boot loader comes up but the only option I get is Mac. 

I REALLY need to get 8.04 working so I can 
do this:
[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/) 

and trick my mac fanboy boss and and some of my coworkers into using linux!

---

### Post by rugbert on 2008-09-22
BUMP!

I found and followed this guide:
[http://blog.costan.us/2008/04/ubuntu-804-on-mac-mini.html](http://blog.costan.us/2008/04/ubuntu-804-on-mac-mini.html)

but im st ill having problems. I can get up to step 9 where it instructs me to:
> 
9# On the last install screen, click Advanced, and replace (hd0) with (hd0,2). This is necessary so that Grub installs in the right place.
10# Upon rebooting, go to EFI Console in rEFIt. It will offer to update the MBR to reflect the EFI partition table. Accept. Then the Mini will reboot again.


When I go to manually partition for ubuntu it shows 3 partitions and three free spaces between them. so Ubuntu would be installed on sda3. Im not sure if the grub should be installed there or what. 

Is this guide telling me that it should be placed on the root partition of ubuntu or somewhere else? Because Ive tried putting it on sda3 (there was no hd0,2 option) but when I try to boot to the ubuntu partition it says something like "no bootable device found". Then again, going into the EFI console doesnt magically update the MBR for me tho....

---

### Post by rugbert on 2008-09-27
bump.... :\

---

