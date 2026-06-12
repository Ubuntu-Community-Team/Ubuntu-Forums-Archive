---
title: "Acer Aspire 2023 WLMi: Can't start installation!"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by ClairV on 2005-05-11
Hello there,

I just downloaded version 5.04 of Ubuntu, burnt it into a CDR and boot from it. The very first screen I'm supposed to see ([http://shots.osdir.com/slideshows/305/1.gif](http://shots.osdir.com/slideshows/305/1.gif)) looks corrupted. I see half of the graphic/logo, but the text looks OK. If I press ENTER to install, the screen goes black after a while and nothing seems to work (apart from CTRL+ALT+DEL..).

I've searched the forum and found out that other persons had no problem installing Ubuntu on an Aspire 2023, so I wonder what is my case. Is there anything I can do when the screen goes black to see a log or something? I know it's not a CDR (media) issue, as I tried it on my desktop and worked fine  :roll:

edit: it worked, by using the
linux debian-installer/framebuffer=false
option. However, after installation completed, ubuntu kind of messed up my partitions and I received a "boot record corrupted" (or something) error message. I had to use a Windows98 boot disk to run fdisk and reset the active partition to my NTFS one to be able to boot into windows again  :| I'll try reinstalling ubuntu now and see what happens.

edit2: worked  :smile:

---

