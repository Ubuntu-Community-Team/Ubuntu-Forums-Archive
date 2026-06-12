---
title: "UNR Karmic on a friend's Eee 701 2G"
date: 2009-12-30
forum: Hardware
---

### Post by Alejandro Nova on 2009-12-30
Greetings, and glad to be back in this forum.

This time, I'm happy because I'm killing for good a bloated and unresponsive Windows XP install, replacing it with a 100% free Ubuntu Netbook Remix. But I wasn't so happy when I was installing it. The problem? An original 701 with 2 GB.

I had to resort to the slower solution of mounting /usr in a 4 GB SD card. But, before that, I tried the super tip here: [http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/](http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/) . A UNR liposuction would give me 400 MB free in the Eee's 2 GB flash device with everything installed, but Karmic's bootsystem conspired against it. 

1. I tried to mix squashfs and unionfs as adviced. Obviously, it failed, because Karmic features no unionfs.

2. But when I tried again with aufs, I crashed onto the wall of mountall. I didn't know how to disable the default behaviour of mountall, and force the thing to stop trying to mount all devices at once and mount them in /etc/fstab order. Even now, sometimes mountall shows me an irrelevant message "I can't mount /usr" that fades away when the thing mounts /usr.

Guys, maybe I'm trying to do miracles with a 2 gig computer, but Linux can do these sorts of miracles (I'd never think about compressing the whole system in Windows, and their compression scheme is a joke). How can I override the behaviour of mountall and install a squashfs/unionfs scheme that works, on Karmic?

BTW, this one is for a friend of my girlfriend. She doesn't know anything about computers, and I thought Ubuntu would be perfect for her. Every geeky message in my boot process is a deterrent for her to use and enjoy Ubuntu Linux.

---

### Post by Geistanon on 2010-01-23
Could always downgrade and use old kernel/distro (to fit the guide).

---

