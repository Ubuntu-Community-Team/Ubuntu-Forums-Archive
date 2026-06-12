---
title: "dual Ubuntu boot - grub menu.lst outdated"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2009-07-23
I have a dual boot machine (with no Windows at all). I am dual booting between Ubuntu versions 8.04.3 and 9.04.

I installed 8.04.2 initially into the empty machine, and later installed 9.04 in a separate partition. The grub menu in the 9.04 installation correctly picked up the existence of 8.04.2 at the time, and because the 9.04 was the most recent install, the mbr uses the 9.04 file menu.lst

If it makes any difference, I note that I use 8.04.x a lot - as my main version, and I had soon edited the 9.04 menu.lst so that the default was to run 8.04.2

(and in greater detail I actually installed 8.10 also before 9.04, but of course 9.04 installation  with its grub picked up everything at the time)

I have however noticed that when I update my 8.04.2 any kernel updates are correctly put into the menu.lst file of the 8.04.2 which file of course is not being used, but these do not get mentioned in the active menu.lst in 9.04

This is most obvious just now because the 8.04.2 is now updated to 8.04.3 and when I see the grub menu at machine startup it is the 8.04.2 being shown from the menu of 9.04.

I have now manually edited the menu.lst in 9.04 to include the latest lines for 8.04.3, and it seems to work ok. 

However, I wondered if there was a more elegant way of handling all this?

It is quite usual for me to use an LTS version but also to install and sometimes run, later versions in partitions.

From what I can see, the app grub-update only looks in the current partition, and to solve my apparent problem it would need to look in all other partitions, I am not sure it does this (?)

comments most welcomed, tia

---

### Post by cariboo on 2009-07-23
You can use the configfile directive to boot using 8.04.2's /boot/grub/menu.lst, instead of the 8.04 entries use something like this:

```
root (hd0,0) 
configfile /boot/grub/menu.lst
```

you have to change the (hd0,0) to the partition that 8.04 is on.

---

