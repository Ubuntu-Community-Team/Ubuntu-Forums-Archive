---
title: "Wubi install fails. &quot;Initramfs&quot;?"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by Midnitewolf on 2009-02-26
Not to flame linux, but i gotta say, my friend tells me to go to ubuntu for a more stable easy OS, and instead i spend almost 4 days of hair-pulling outrageous frustration.

The livecd wont install, the program wont list my partitions, even with full formats, even with partition management programs, etc etc, my first thread is here: [http://ubuntuforums.org/showthread.php?t=1081224](http://ubuntuforums.org/showthread.php?t=1081224)

Anyway i was recommended to download and use Wubi instead as a safer and easier alternative, so i downloaded it straight from the site, ran the installation, it said it was complete and asked me to reboot.. so i reboot, i select Ubuntu from the OS selection screen, and now im stuck

My screen is black with some kind of DOS-ish prompt, it says: Busybox v1.10.2 shell  (initramfs)

AND NOTHING ELSE. What am i supposed to do now? All i want.. is to run this OS, run some programs on it, and get back to my life.

---

### Post by avtolle on 2009-02-26
From looking at the Wubi guide, here are my thoughts and recommendations: a common reason for being dropped into the intramfs box when rebooting from a Wubi installation is that the HDD is badly fragmented; uninstall Ubuntu, defrag the drrive, and then reinstall. Another reason for the error is the "hard powerdown" of the computer, i.e., pressing the power button to shutdown. Again, if this is a possibility, uninstall Ubuntu; run chkdsk -r within Windows; reinstall using Wubi.

Other things you might look at: if you used the iso you had previously downloaded and burned to cd, did you check the md5sum of the iso after its download before burning it to the cd or before using Wubi to install from it? With reference to your problems with the Live CD you tried, did you burn it as an image at low speed and do a cd verification check at the initial menu when first booting from it? 

Assuming you are able to boot from the Live CD and get to the desktop, have you done as requested in the responses to your original thread and opened a terminal (Applications>Accessories>Terminal) and at the command prompt done```
fdisk -l
```and pasted the results so others might take a look at how your partitions are reported (this is a safe command to run). Good luck.

---

### Post by OneShirtChris on 2009-02-26
Also to clarify, the LiveCD can be use to do a Ubuntu Wubi install from within Windows itself. Try getting a new CD Image and just using that CD to install Wubi Ubuntu.

---

### Post by Midnitewolf on 2009-02-26
alrighty, heres where im at.

I ran all those cd integrity checks, came off good, and i redownloaded the desktop cd image, then re-checked its integrity again, and it came up good.

I tried installing wubi, when it booted back up, i got the same black screen with the (initramfs) command-prompt thingy...

i read in another forum that if i changed the menu.lst file, it would fix this... yet i have nothing inside my grub folder. Its totally empty.

I dont know where to go from here

---

### Post by Midnitewolf on 2009-02-26
Oh, and one more thing, even tho i made sure to run the uninstall of wubi from my control panel (add/remove programs), when i boot up the pc, i have like 5 entries of wubi.. one for each attempted install

---

### Post by avtolle on 2009-02-26
I'd delete all but one instance of wubi. When you removed Ubuntu from Add/Remove under Windows, that did not delete Wubi.exe, IIRC. 

Changing the menu.list file doesn't, to my knowledge, have any effect on your being dropped into busy box (intrafms). 

Did you run chkdsk -r from windows?

---

