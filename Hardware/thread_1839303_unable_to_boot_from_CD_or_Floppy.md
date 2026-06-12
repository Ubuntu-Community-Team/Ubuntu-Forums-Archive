---
title: "unable to boot from CD or Floppy?"
date: 2011-09-05
forum: Hardware
---

### Post by dun270 on 2011-09-05
If above applies to you-
Somehow my WinXP doesn't allow enough time for MBR to read/load a boot CD or Floppy-
So-download 'BCDL', copy it onto a floppy with rawrite, or rawrite for windows, or dd in linux, then put it into your floppy drive. There is also a BCDL image available for burning onto a CD if you don't have a floppy drive.
Then put your favorite linux install.iso CD image into the CD drive.
Power off computer.
Turn your computer on it's side with display open so you can read it.
Take off your hard drive bay cover, and slide hard drive back and away from connector, but keep it in the bay, and ready to slide back into connector.
Power on computer.
The BCDL flopping will boot to "Press any key to continue", while at same time, the CD drive will begin to load the cd(cd drive light flickers)
As soon as cd drive light goes out(cd is loaded), slide hard drive back into connector, gently lay PC flat on your desk, press "enter"
The computer will now boot the CD image. Continue with install. Remove the floppy, after CD is booting.
Good Luck

---

