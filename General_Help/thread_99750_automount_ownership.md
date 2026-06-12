---
title: "automount ownership"
date: 2005-12-06
forum: General Help
---

### Post by arvelius on 2005-12-06
I have an ubuntu 5.10 system with two physical users, me that is the user who made the installation and is the user that can sudo and my wife that has a normal user that can't. My problem is that I always get the ownership of automounted units. Normally both users are logged in with each one xsession and if my wife plugs in her digital camera to the USB it directly automounts with my ownership and she can not read the contents on the card, but has to switch to my user. For CD:s she got the reading permissions but can't umount it.

In fstab there is nothing about the usb, I have hal installed and realise from reading in these forums that hal handles this without entering to the fstab but I can't figure out how to configure this so that the active user can read and unmount the attached units. Is there a tutorial out there somewhere?

---

### Post by aysiu on 2005-12-06
Try going to System > Administration > Users and Groups, double-clicking your wife's name and enabling her access to external drives.

---

### Post by mcduck on 2005-12-07
No, that won't help. I have the same problem and I tried that but the normal user still can't eject disks. I suppose 'access to external drives' means read access only.

I had to turn autoplay of CD's and DVD's off from my user account because if both users were logged in, the movie would start playing for both. And two VLC's playing one disk at the same time for two users just doesn't work ;) But I don't want to turn my automounting off too, I really like that feature.

Now if HAL would mount disks and give ownership to the active user, the one who's using display and keyboard/mouse when usb-drive is inserted...

---

### Post by arvelius on 2005-12-07
Thanks for the suggestion aysiu, I tried to let her all rights including "Executing system administration tasks" which i guess is to let her also sudo (I don't have her password so can't try). However nothing seems to change, I've logged her in and out several times and she can still not read from the USB connected camera or unmount any external systems.

I fully agree with mcduck the most useful behaivour would be if automount only occurred for the user using the screen and keyboard.

---

### Post by aysiu on 2005-12-07
I guess your next best bet would be to find out if the USB camera always is at the same /dev (say, /dev/sda1, for example). If so, you could create an /etc/fstab entry for it to automount with read/write privileges for everybody.

---

### Post by arvelius on 2005-12-07
Yes, thats the old way I'v used for my debian systems all times. I was just happy to see this automount feature as we have several cameras, scanner, card readers, USB sticks etc so that it is actually rather often something else already mounted and there is a need to count whats on the line and figure out which device I need to mount. I found this automount feature quite useful for my purposes until my wife complained that she could not even mount manually as the camera directly get automounted.

---

### Post by dcstar on 2005-12-09
[QUOTE=arvelius]I have an ubuntu 5.10 system with two physical users, me that is the user who made the installation and is the user that can sudo and my wife that has a normal user that can't. My problem is that I always get the ownership of automounted units. Normally both users are logged in with each one xsession and if my wife plugs in her digital camera to the USB it directly automounts with my ownership and she can not read the contents on the card, but has to switch to my user. For CD:s she got the reading permissions but can't umount it.
.......[/QUOTE]
I assume your user account is part of the "Root" group, go into System-Administration-Users and Groups and put the other account into the Root group, and also check the properties of that user account match yours.

There is are various "User Privileges" that may apply to your issue.

---

### Post by jerrykenny on 2005-12-09
Also in your fstab entries for the DVD & cdrom drives, change

user

to 


users

---

### Post by arvelius on 2005-12-10
Thanks a lot, I changed the cdrom entry in fstab to users and that really made the trick. Aboute the usb on the other hand neither of the two users belong to the root group, actually we belong to the same groups (exept the personal groups), it anyways works for me. Is it secure to add a normal user to the root group?

---

### Post by pelle.k on 2006-01-20
I guess it's been a while since this post was written, but i like to see threads resolved, to make it easier on the nuubs :)

So add your wifey to the plugdev group to let her browse the usb stick!
BUT... make sure plugdev group REALLY gets added by going in to control center -> users & groups ONE MORE TIME. KDE seems to be a little bit buggy in that area sometimes...

---

