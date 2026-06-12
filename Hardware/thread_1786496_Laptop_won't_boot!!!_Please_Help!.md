---
title: "Laptop won't boot!!! Please Help!"
date: 2011-06-19
forum: Hardware
---

### Post by egfrank81 on 2011-06-19
I have a laptop running ubuntu 11.04 and Windows 7. I've had this set up since 11.04 release and have had no problems. I recently purchased a new hard drive for my laptop, I removed my old and and installed the new. When  I turned on my laptop, the hp load screen appeared and after that...a blank screen.

I restarted my laptop and loaded bios, I was able to access bios, but as soon as i exited I saw a blank screen once again. I then thought there may be some problems due to Grub, so i reinstalled my old hard drive and I'm having the same problems.

I tried to reset my bios CMOS battery and still the same problem. I can access bios but nothing else. the computer won't boot from hard drive/cd-rom/usb. I ran diagnostics through bios and every thing checked out okay.

Any ideas?

---

### Post by ajgreeny on 2011-06-19
When you put the new drive in and took out the old one, what was on the new drive?  It sounds as if it is a blank/empty drive.  Did you install the OS onto it before fitting it, or did you have both and then clone the OS from old to new?

When you loaded the BIOS what did you do when you were there?  Perhaps you need to check that there are any disks detected, then if you have two disks, make sure they are set in the correct boot-priority order.

---

### Post by egfrank81 on 2011-06-19
Thanks for the response, the new drive I attempted to install was clean /blank. I was unable to install anything because I received the blank screen after the HP /BIOS boot screen.

There are no beeps on start-up.

---

### Post by egfrank81 on 2011-06-19
Oh, and I'm booting with a single drive set to master

---

### Post by ajgreeny on 2011-06-19
Are you sure you have it set to boot from your CD or USB first in the boot priority list?  It still sounds to me as if you are trying to boot to the empty drive, which of course will do exactly as you describe.

There may be a function key you need to press (F2, F12 perhaps) as you power-on in order to choose your boot device, but you will need to find that from the machines instruction manual, or whatever you have for it.

---

### Post by egfrank81 on 2011-06-19
Thanks again, but I changed boot first settings. I'm now trying to boot from my original hard drive that contains both Ubuntu and win 7.

Both drives work when I install them on my wife's laptop.

---

