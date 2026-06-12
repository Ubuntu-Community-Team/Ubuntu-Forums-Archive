---
title: "Ubuntu infinite reboot loop and Samba"
date: 2009-09-03
forum: Hardware
---

### Post by mattgyver83 on 2009-09-03
Hi, to my knowledge I didnt do anything different then i normally do.
I was transfering some files over to my server from another box, suddenly the computer restarted.  I noticed that the splash screen got about 3/4 loaded and then it restarted again.  I let it do this several times and the same thing happend.

I removed the "quiet splash" string from grub and watched as it loaded.  Everytime like clockwork it will ge tto the "Starting Samba Daemons" and then my computer will reboot.

If i run the machine in recovery mode the system boots, however running in recovery, the selecting the option to continue normal boot fails as well.

This is quite puzzling, and of course by my luck happens as soon as I finally get my server operational.

Any help on this would be greatly appreciated.

thanks.

---

### Post by arcull on 2009-09-03
Did you try to reinstal samba deamon?

---

### Post by mattgyver83 on 2009-09-05
yes i did, that didnt seem to fix anything.

I ran rcconf and removed samba from starting upon boot.  That seems to allow me to get the machine started up.. and for some reason, still automounts my SMB share per my /etc/fstab.

I wouldnt exactly call this a fix however.

anyone?

---

