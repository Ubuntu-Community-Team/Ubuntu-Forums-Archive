---
title: "problems with 2 usb drives"
date: 2006-04-28
forum: Hardware &amp; Laptops
---

### Post by barrett on 2006-04-28
I am still something of a beginner, help is deeply appreciated.

I have an external hard drive and an mp3 player both of which have usb connections. My installation of Breezy mounts the hard drive automatically as /media/usbdisk. The hard drive has all my documents and my desktop. The problem is that if the hard drive is plugged in first when the mp3 player is plugged in second all of the connections to the hard drive are lost. Any documents that are open cannot be saved. Bookmarks stop working. etc. 

Any ideas what is wrong or what can be done? 

thanks, barrett

---

### Post by Gannin on 2006-04-29
I would first try to isolate the problem.  Download a live CD of a different distribution, like Mandriva One or PCLinuxOS, and then plug in your USB devices in the same way and see if they have the same problems.

---

### Post by barrett on 2006-04-30
Thanks for this suggestion. The computer in question is in my office and I am home for a couple of days. I am a little resistant to trying another distro. I tried Mandriva on this machine before and had some other problems. Ubuntu solved those and I have spent a few months tweaking to get things the way I like. I would be a little sad to lose that. I think perhaps when I get back I'll try to track where and how the mp3 player is mounted and research whether or not there is any way to exempt the external hard drive from the automatic mounting process. But if that turns out to be beating my head against the wall, new distributions are always entertaining. barrett

---

### Post by Gannin on 2006-04-30
That's why I suggested trying a live CD distribution.  It runs completely off the CD without installing anything and without touching your files.

---

### Post by barrett on 2006-04-30
a little slow on the uptake on this side, but pclinuxos is downloading now. I'll be back in my office on Tuesday and will boot from the CD and see what happens.

For what it's worth, on my home PC -- which has Mandriva 2006 64 -- I put a line in fstab that usually causes the external hard drive to be mounted at a point of my choosing. When I plug in the mp3 player, Mandriva mounts it automatically and the external hard drive is not affected. I tried putting a similar line in the fstab file on the Ubuntu installation in my office, but Ubuntu still mounted the hard drive to a point of its choosing. 

barrett

---

### Post by Gannin on 2006-05-01
I know one difference between the two is that Mandriva mounts everything under /mnt, where as Ubuntu, as you already pointed out, mounts everything under /media.

---

