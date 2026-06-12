---
title: "I brokes it.  Screen shuts off before I can login."
date: 2010-02-03
forum: Hardware
---

### Post by Eirinjas on 2010-02-03
Okay, I was sick of the problems I have with the ATI Radeon 9800 XT in Ubuntu.  Some stuff works, some doesn't, but performance is crap even when it does.  Supposed to be a 256 meg card, but it's not using even half of it.

 So, I know how Nvidia cards are supposed to have better performance and I have an old Geforce 4000 MX.  So, I popped that in and tried that out.  It worked, but the framerate was unbearable.  I play some 3D games and it was doing half of what the ATI was doing in the FPS department.

 So, I switched back to the 9800 XT.  Had to undo the Nvidia stuff and reinstall the old open source driver, but it was working.  Still not content to leave well enough alone, I decided to edit the XORG.CONF file.  I added 3 lines to it, saved it, and now the monitor blanks and shuts off during boot up and I can't get into Ubuntu.  I know what I have to undo, but I can't undo.  I can't edit XORG.CONF from the LIVECD, and I tried recovery mode and that didn't help.  Now I notice that it's loading a module or something for the Nvidia card, even though it's no longer installed.

Any help would be very much appreciated.  Thanks!

---

### Post by mgichoga on 2010-02-03
If you can get in with the live CD, xorg normally makes backups of configs before it changes them. in the Directory /etc/X11/, there will be some xorg.conf.<timestamp>. You could try overwriting the current one if you know you had a working copy at one time. Make a backup, preferably of the whole directory of course.

---

### Post by Eirinjas on 2010-02-03
Won't let me.  Complains I don't have permission.  This sucks.

---

### Post by mgichoga on 2010-02-03
Are you sure you trying to copy it to the hard drive rather than the live cd environment? If you go to the places menu, there should be your hard drive. Normally you should be able to copy to it. If not I would guess its because you need to sudo so you can copy. 

go to Applications > Accessories > Terminal

once in terminal type in 'gksudo nautilus'  (without quotes)

Try navigate to your hard drive again and copy those files again.
Hope this helps.

---

