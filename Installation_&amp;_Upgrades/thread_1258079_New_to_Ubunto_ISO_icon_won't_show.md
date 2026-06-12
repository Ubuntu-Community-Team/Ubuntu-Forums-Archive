---
title: "New to Ubunto: ISO icon won't show"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by corster on 2009-09-04
I burnt the disk without ISO icon and it goes to the setup information and I reboot it, but nothing happens; it just boots up Vista's way. So, I have come to the conclusion that I need the ISO icon to do so. Why doesn't the ISO icon show? It would be much appreciated if someone can assist me.

---

### Post by TetonsGulf on 2009-09-04
If it is a valid disc you should be able to access it from within Windows. If you can't, I'm guessing there was an error with the download or the burning process. 

I would try to burn the .iso with a program like [ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm") though. I'm guessing the problem is with the burn. Last I knew, Win didn't burn .iso's out of the box.

If you **can** access it, it's possible your BIOS boot priority is set to boot from the HD before the DVD/CD rom. If you don't want to install via Wubi, you can change those settings and install from there.

---

### Post by ronparent on 2009-09-04
+1

It looks like you have burnt the .iso image file to the cd - the whole disk is one .iso file and cannot be booted. Consequently the cd is not recognized as a bootable drive (even if the cd is first in boot order). A program like ISO Recorder will take the .iso image and burn it to the cd as all the individual files, including the MBR, to enable it to boot and function as the install disk or live cd. I know all of this can be confusing to a new user, but hang in there and you will get a grip on it.

---

