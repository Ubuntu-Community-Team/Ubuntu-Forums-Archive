---
title: "karmic install - help w/ manual partition &amp; adv./grub install"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by brookie on 2009-10-30
hi all, 

i took the plunge after trying out a newly burned live cd and am trying to install karmic on my inspiron 600m. 

after install it will not reboot so i want to re-install. here is the error i get after re-boot. 

error: no such devices 41230862-63cc-400-8300-e4b175c00691, press any key to continue

no luck with any key, same error repeate.  if i hard power off, and hit esc, the grub menu list will come up and if i select the current kernel or recovery mode i will get the error again. 

so...i thought i'd try another install selecting manual partition. 

/dev/sda1/ formatted as ext4 with mount point at /
/dev/sda5/ as swap

when i get to the last page and click on the advanced button i have the options to put grub on: 
(hd0) or /dev/sda or /dev/sda1

i'm assuming that the initial install didn't put grub on hd0 by default and the system won't reboot because it can't see grub. 

so, i want to try the advanced button but where should i put the bootloader? or is there another way to try and fix this install? 

thanks in advance, any help would be appreciated, 
brook

ps re-installed with grub on /dev/sda no go, same issue

tried c from the grum meu and got some more info: GNU grub version 1.97`beta4 which does not sound rght

---

### Post by brookie on 2009-10-31
burned a new disk and the install went smooth.

---

