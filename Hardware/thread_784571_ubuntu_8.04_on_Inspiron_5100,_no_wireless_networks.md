---
title: "ubuntu 8.04 on Inspiron 5100, no wireless networks detected.  Need *quick* help pls!"
date: 2008-05-06
forum: Hardware
---

### Post by moron_needshelpFast on 2008-05-06
I'm turning to this forum for some (hopefully) really fast help.  I'm in a pickle, and have only about 30 min to find a solution.

1) Installed ubuntu 8.04 on a Dell Inspiron 5100, a fresh install (no dual booting, etc)

2) Install went smoothly, OS boots just fine.  

3) I cannot detect any wireless networks. I know for a fact there is a wireless network, but I can't see how to connect to it.  

4) The little network connection icon in the upper right corner has an exclamation point.  I've right-clicked and enabled wireless, but nothing else has happened.

Do I need to install drivers?  I'm absolutely lost - I needed to set this up to test with at a conference, but my boss needs it in about 30 min.  Otherwise, he'll have to grab a windows laptop.  (BOO!)

I'm a linux newbie, so any plain english help is much appreciated!

---

### Post by moron_needshelpFast on 2008-05-06
Guess he'll be going with a Windows laptop this time.

If anyone has a fix for this, I'd love to read it for future reference.

---

### Post by knix on 2008-05-06
for future reference:
I just did this on a Vostro 1500
Yes, you do need to install drivers.
No, do not use the ones ubuntu tries to use.

Install:ndiswrapper-common, ndiswrapper-utils, and ndisgtk (can be gotten from packages.ubuntu.com). network drivers (or something like that).
Get the windows drivers (from Dell CD or website)
Extract drivers (its an .exe archive, just open with archive manager)
Open ndisgtk (sytem >Administration >Windows
find th bcmwl5.inf file (or other .inf file if not Broadcom based)
Click OK
Create a script (i keep mine on the desktop and run it at each boot. I call it network.sh)
      in gedit (text editor)
            sudo modprobe -r b43
            sudo modprobe -r b44
            sudo modprobe -r ssb
            sudo modprobe -r ndiswrapper
            sudo modprobe ndiswrapper
            sudo modprobe b44
            sudo modprobe ssb

Save as (name).sh
Right click on script.
go to propeties
go to permissions
mark "allow executing file as program"

Then you may want to reboot.

double click the file.
click run in terminal
give terminal root password.
click network monitor, then click outside it (this wakes it up). It should start working pretty quickly)

---

### Post by Fordkiller on 2008-05-09
Im running 8.04 on my dell 5100 with wireless just fine you need to install drivers on it and it will work fine

---

### Post by kris1351 on 2008-06-02
Thanks for the fix, that is much easier than previous versions. I added the modprobe statements to the /etc/rc.local file so they just run automatically at boot. Works well so far.

---

