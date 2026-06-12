---
title: "How to install Squeezebox Server?"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by Cams on 2009-11-11
I decided to upgrade my ClarkConnect server that I used for my Squeezeboxes. I'd been using it for 3 or 4 years. I tried the upgrade and it broke so I decided to start again and though, since I'm starting again, I'll try Ubuntu server. I have Ubuntu desktop on a laptop and like it. 

I just installed Karmic Koala server 32-bit and am now looking at a flashing cursor: username@ubuntu:$

How do I install SlimServer or Squeezecenter or Squeezebox Server as it's now known on this computer and how do I create the directory to hold all my FLAC files and make it visible from my Windows PC? I just need to know the commands to type. I have three HDDs in the computer. I did have three 250GB drives, but swapped the boot drive for a 400GB drive (part of the reason why the ClarkConnect upgrade didn't work was that I'd run out of disk space). I did the guided install with LVM. 

Thanks
Cams

---

### Post by Cams on 2009-11-11
Aha, I found something with Google and it worked! This is with Ubuntu server 9.10. 

[http://havetheknowhow.com/Install-the-software/Install-Squeezebox-server.html](http://havetheknowhow.com/Install-the-software/Install-Squeezebox-server.html)

Installing main stable didn't work. Something to do with MySQL 5.1. So I tried testing main instead and that worked. 

I'm desperately needing help with getting my music files onto the system though. As I said, I have three HDDs and I used the guided install with LVM. The Squeezecenter install is asking me where my music is stored and I can see that I have a directory called /home/$usnername$ and one called /media/ (amongst others). I would like to have as much disk space as possible for my music files (there is about 600GB to add). How do I create the diskspace using my HDDs and make it so that I can copy the files from my Windows computer (Windows 7) to the Ubuntu one?

Thanks... getting there slowly!

PS. I've added an attachment that shows the directories that were created but I don't know how to see the disks and disk space, etc.

---

