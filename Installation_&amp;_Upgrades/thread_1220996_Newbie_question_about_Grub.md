---
title: "Newbie question about Grub"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by astralpilot on 2009-07-23
This is my first post as i'm new to Linux, but so far I can't get Grub to work properly. My system Runs Windows XP pro on a IDE drive and I have a second drive a SATA which i hope to install Ubuntu. 
 
When installing and configuring GRUB I have tried all boot install options but they don't allow it to work properly. Either it boots stright to XP with no dual boot screen or boot screen that looks good but only allows Ubuntu to load when trying to boot to XP it shows a Error 13.
 
I have tried to find out solutions but have come to the conclusion it must be the IDE SATA problem
 
Any ideas
 
Thanks

---

### Post by louieb on 2009-07-23
Think you have it right when you said IDE/SATA problem. Grub installer get confused and gets it right about half the time. 

Guess you have BIOS menu that lets you choose which drive to boot 1st. 

Boot to Ubuntu - need the content of file /boot/grub menu.lst. 

Press alt+f2 (run dialog)  and enter

```
gedit /boot/grub/menu.lst
```

paste the content in your next post. (use code tags). 

Note you won't be able to save the file using the above (safer that way). Will go over that after suggesting what change need to be made.

---

### Post by astralpilot on 2009-07-31
Thanks for the info I'll give it a go and report back.
 
Sorry for the delay lost Bband connection and only just managed to reconnect

---

