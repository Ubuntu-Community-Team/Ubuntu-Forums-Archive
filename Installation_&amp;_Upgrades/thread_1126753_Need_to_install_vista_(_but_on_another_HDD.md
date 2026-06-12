---
title: "Need to install vista :( but on another HDD?"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by Kain000 on 2009-04-15
Hey everyone, 
as you may have guessed form my title, I am (unfourtinally) in need of Vista for gameing.  As much as i dislike microsoft, there is no better tool for gaming.  I've tried my best to utliaze virtualbox now that it supports 3d acceleration of the host's video cards, but couldnt get it to work properly.  

wine is great but will not work for alot of great games.

so my only option seems to be an actual install of Vista.   Currently I have a 400 GB Drive that hosts ubuntu 8.10, and my media, which is rapidly filling up, and as such I would like to aviod adding another partition to that.  (delaying the enivatable tera-byte upgrade...)   

I have a second drive (250Gb) also in the tower for extra storage and backups.  I would like to put vista here, but I dont know wether or not GRUB will parse both drives for OS images.

Idealy for this to work i would boot up and grub would see ubuntu on the 400gb drive and vista on the 250gb drive and allow me to choose.   is this possible, or will it only search the drive it's on (400gb)

is there a way to configure GRUB to search BOTH drives althought it's only on the 400?  (Yes i know that because we use linux, anything is possible and I can make grub do w/e I would like with the proper re-programing, but i would hope to avoid this senario. lol)

thanks in advance, 
Sean

---

### Post by Partyboi2 on 2009-04-15
You should be able to install vista to the hard drive you want to and then after it is installed restore [[COLOR=Blue]grub using a live cd[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by Kain000 on 2009-04-15
> **Partyboi2 said:**
> You should be able to install vista to the hard drive you want to and then after it is installed restore [[COLOR=Blue]grub using a live cd[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351").

thanks for the link, From what I can tell this will return grub to a state of booting before windows takes over, but How do I tell it to search 2 hard drives?

---

### Post by s3a on 2009-04-15
To my knowledge, having grub on one drive will be able to boot an operating system from any drive if you were trying to load grub on two drives or something.

---

### Post by Kain000 on 2009-04-15
alright i will give that a try.  thanks

---

