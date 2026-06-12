---
title: "can't get simple usb music player to work-not authorized"
date: 2014-03-04
forum: Hardware
---

### Post by rolypolycat2 on 2014-03-04
I have a basic mp3 player that loaded up just like any other usb item, but now, when I try to load any music, I get this error message:not authorized to perform operation. It's an RCA Lyra, and it shows up in the side of pcmanfm, but I can't do anything with it when I click on it. And going to root in pcmanfm doesn't help; for some reason, it vanishes from the menu. I checked mount all media in pcmanfm, and I've tried to find an option in the settings panel, but no luck. Can anyone tell me why my computer seems to think I shouldn't use my mp3 player? (my music isn't that bad, honest!)

I'm using enlightenment 17  on a minimal install. Before, I ran bodhilinux; the player worked fine under bodhi. I tried using the ls -l command on /media, and got this:

michelle@the-cathouse:/media$ ls -l
total 8
lrwxrwxrwx 1 root root 6 Jan 11 22:03 cdrom -> cdrom0
drwxrwxrwx 2 root root 4096 Feb 27 17:13 cdrom0
drwxrwxrwx 2 root root 4096 Feb 27 17:10 cdrom1
michelle@the-cathouse:/media$

This is what I got the first time. I went in pcmanfm under root permissions, changed the owner to michelle, and this is what I get running the command again.
michelle@the-cathouse:/media$ ls -l
total 8
lrwxrwxrwx 1 michelle michelle 6 Jan 11 22:03 cdrom -> cdrom0
drwxrwxrwx 2 michelle michelle 4096 Feb 27 17:13 cdrom0
drwxrwxrwx 2 michelle michelle 4096 Feb 27 17:10 cdrom1
michelle@the-cathouse:/media$

Even though it's changed permissions, it still won't let me access it. Using pcman under root, I can access the player, but only by going to media, and clicking on cdrom (which is interesting, since it's not a cdrom). However, it shows files which aren't on it, but were there just before the ones on the device now-(that I'm trying to erase).

When I try mounting the cdrom, I get this:michelle@the-cathouse:/media$ mount /media/cdrom
mount: block device /dev/sr1 is write-protected, mounting read-only
mount: no medium found on /dev/sr1
michelle@the-cathouse:/media$

I also see that it just says: USB connected, on the player screen itself. When Im accessing it from pcmanfm root, I can delete the files (the old ones), and add new, but it doesn't show the files that replaced the original files, and which shouldn't be there anyway. The present, and last files to be added, was an audio mp3 book; the files I want to replace that with are mp3 music files that were there before I took them off for the book. It doesn't seem to do anything, even though all the right message windows come up saying the operations are being carried out. And I can't unmount it through my account, and I can only reach the player on root through /media/cdrom.

I've never seen the player do this before, even under several distros, or earlier versions of ubuntu. I hope this information helps.

rolypolycat

---

