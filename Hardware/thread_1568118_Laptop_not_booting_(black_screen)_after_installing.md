---
title: "Laptop not booting (black screen) after installing windows"
date: 2010-09-04
forum: Hardware
---

### Post by imakbari on 2010-09-04
Hi,
I've got a really strange problem with my laptop.
Since I installed windows (Ubuntu > Ubuntu + Windows7) my computer is having troubles in booting up.
In fact it doesn't even show up the boot screen. it just turns on the screen backlight and the CPU fan starts. And also USB charging works. 
But that doesn't happen all the time. If I wait like 5 minutes that would be gone specially if I remove the battery.
I really don't know what to do.


Any help is appreciated.
Thanks in advance.

---

### Post by quixote on 2010-09-05
Windows always writes its own bootloader, and that one doesn't see any other OSes except its own.  Which makes your situation odd: your computer should be booting into Windows and it should look like you've lost ubuntu.  (You haven't, but the Windows bootloader wouldn't see it.)

Fixing this involves reinstalling grub, which isn't very difficult.  A few questions first:

--Does a grub choice of operating systems come up and then go to the blank screen?  Or is it straight to the blank screen?

--Can you boot with a liveCD?

--Which partitions do you have on your boot drive, and which OS is where?  How many other drives + their partitions, if any, do you have on the system?

---

### Post by anubhavrocks on 2010-09-05
This might be helpful:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by imakbari on 2010-09-09
Sorry for the delay and tnx a lot for your attention. It was really easy. I just had 2 update my computer BIOS. It works like a charm now. (By the way i had to go and change SATA Controller mode from AHCI to Compatibility, otherwise it wouldn't run OS)

---

