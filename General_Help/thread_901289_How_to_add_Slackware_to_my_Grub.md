---
title: "How to add Slackware to my Grub"
date: 2008-08-26
forum: General Help
---

### Post by kikkertje on 2008-08-26
Hi,

I just installed Slackware to /dev/sda7,
and i thought it would add automatically to my Grub list, but it did not.
So I checked into menu.lst, but i don't know what to add at the bottom of the list.

Could someone explain me how to do it? 

thanks in advance!!

K

---

### Post by eggdeng on 2008-08-26
```
#Added by kikkertje
title           Slackware
root            (hd0,6)
chainloader      +1
```
should do it.

---

### Post by phidia on 2008-08-26
When you installed slack did you also install a bootloader?
I think the simple way to do this is to run grub-install > sudo grub-install that should find your slackware install and add it to menu.lst automatically.

You could edit menu.lst but I think re-installing grub is easier. If you do want to edit anyway check out [this site]("http://humanreadable.nfshost.com/sdeg/grub.htm") for a menu.lst example (you will have to plug in your specific parameters).

---

### Post by phidia on 2008-08-26
> **eggdeng said:**
> ```
#Added by kikkertje
title           Slackware
root            (hd0,6)
chainloader      +1
```
should do it.

That will not do it unless kikkertje installed a bootloader and slackware doesn't come stock with grub it uses lilo.

---

### Post by caljohnsmith on 2008-08-26
> **kikkertje said:**
> Hi,

I just installed Slackware to /dev/sda7,
and i thought it would add automatically to my Grub list, but it did not.
So I checked into menu.lst, but i don't know what to add at the bottom of the list.

Could someone explain me how to do it? 

thanks in advance!!

K
Probably the easiest solution is when you install Slackware, have it install its bootloader (Grub/LILO) *to the boot sector of its own partition*, and not the master boot record (MBR). For Grub, you would specify installing it to (hd0,6) or your Slackware partition, instead of (hd0) which is the MBR of the HDD. If you can do that, you can use eggdeng's method to boot Slackware by adding that entry he gave into your Ubuntu /boot/grub/menu.lst. Alternatively, if you can at least get Slackware to generate its own menu.lst/grub.conf (and whatever LILO uses), you can boot it with:
```
title           Slackware
root            (hd0,6)
configfile      [COLOR="Blue"]/boot/grub/menu.lst[/COLOR]
```
Where you need to of course give the correct path to menu.lst or whatever Slackware uses. If you need more details let me know. :)

---

### Post by eggdeng on 2008-08-26
@phidia
> That will not do it unless kikkertje installed a bootloader and slackware doesn't come stock with grub it uses lilo.
I understand the OP already has an Ubuntu install, has installed Slackware to another partition and wants to configure his (Ubuntu) Grub bootloader to be able to boot to either partition. Why else would he talk about editing his menu.lst? :wink:

---

