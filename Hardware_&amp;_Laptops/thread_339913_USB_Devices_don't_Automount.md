---
title: "USB Devices don't Automount"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by klittzzer on 2007-01-16
I am totally stumped.

Neither Ubuntu or Kubuntu Edgy automount any USB device I plug in. If I plug in my USB mp3 player or flash drive (mp3 player is 2gib Logik and flash is Dell 64mb) before I boot, both Gnome and KDE pick them up, but not before a long wait during which my processor is running at 100%. Both OS s do not run properly if anything is plugged in via a USB port.

Is this normal?

I have trawled through the posts regarding this problem yet cannot find a solution. I must say that my Hard Drive (hda1 I did a full install of Ubuntu Edgy 2.6.17-10) is not picked up either. Nothing is present in /mnt/ and the /media/ folder only shows my CD rom drive when I open it.

I really could do with some help so please at least have a look at this post.

Peace

klittzzer

---

### Post by Richard Kut on 2007-01-16
Hi klittzzer! It is gnome-volume-manager that is responsible for auto-mounting usb devices when they are plugged in. Ensure that this is running in your environment prior to plugging in a usb device.

I also found this while googling:

[http://gentoo-wiki.com/HOWTO_gnome-volume-manager](http://gentoo-wiki.com/HOWTO_gnome-volume-manager)

Of course, be sure to do:

sudo apt-get update

before going any further, because by looking at your kernel version I think it is time for an update. The update may fix whatever is missing or broken.

Good luck!

---

### Post by klittzzer on 2007-01-16
Thanks for your reply. Nothing seems to work though. I have updated and have had gnome-volume manager all of the time. I really don't know why this problem persists. When I plug the player in before I boot the computer it is recognised. I have right clicked the desktop icon and checked the mount automatically box under mounting in properties but it still doesn't load. It shows up fine in fstab but when I plug anything in via USB while the computer is running it won't get detected. 

Surely this can be sorted out? Windows used to recognise USB devices instantly. Is there a distro which is compatibe with USB devices cos it looks as though Ubuntu and Kubuntu can't handle mp3 players or flash drives.

Nice one

Any replies?

---

### Post by discord on 2007-01-16
so ubunut normally automounts usb devices fine. you have been vague about your hardware.

---

### Post by Pobega on 2007-01-16
Sure it doesn't automount them, but are you able to mount the devices using the mount/umount commands? You'd better make sure it's not a hardware problem before assuming it's a software problem.

And what do you mean by >  my /media folder only shows my cdrom drive when i open itA bit more specification would sure help us solve your problems.

---

### Post by klittzzer on 2007-01-17
Ok. Thanks again for your time. I am in UK, hence time taken to reply. 
I will get all the info you need if you reckon it can be solved.

I will be able to spend a bit of time gathering the data after 5pm UK time.

Let me know the hardware details and I will do my best.

To elaborate on the hard drive issue- Gnome now recognises my file system again and lodges a file 'filesystem' in the 'computer folder'. KDE, however, does not.

Again, my mp3 player (Logik 2gib) loads if I plug it in any USB port before boot yet won't load if I try to 'hot plug' it while Gnome or KDE are running???

Strange eh

I will be back at time above to discuss further if you al can be kind enough to help me

Big thanks

klittzzer

---

