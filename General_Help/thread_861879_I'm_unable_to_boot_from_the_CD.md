---
title: "I'm unable to boot from the CD"
date: 2008-07-17
forum: General Help
---

### Post by Faethin on 2008-07-17
I'm trying to install Ubuntu on my new computer (bion, intel core2 duo, 1.83Ghz, 2Gb RAM, 106Gb Disk). When I start the computer with the Ubuntu CD it displays the installation menu. After selecting the "Install Ubuntu" option, the computer seems to begin reading the CD and all. But when the Ubuntu logo appears every process seems to shut down, including reading the disc. The computers simply stops, as if it were frozen.

I tried selecting other options from the menu after resetting the computer, such as "Testing the CD" or taking a look at Ubuntu without installing it and the same thing happens: the logo appears and nothing happens.

A little help please? I'd appreciate it enormously.

---

### Post by iaculallad on 2008-07-17
A bad ISO burn? Try reading [Ubuntu Community's ISO burning page]("https://wiki.ubuntu.com/BurningIsoHowto").

And try to burn the ISO file using lower speed burn (2x).

---

### Post by Faethin on 2008-07-17
The thing is, I tried with the original Ubuntu CD with which I installed Ubuntu on this computer. When it didn't work (showing me the same troubles I described above) I downloaded another image (since I had deleted the first). So that's two different discs I've tried with, one of which definitely works. Do you still think I should re-burn the disc?

---

### Post by iaculallad on 2008-07-17
No need to re-burn the ISO.
What mobo are you using? SATA or PATA?

---

### Post by Faethin on 2008-07-17
I'm sorry. I'm a newbie. I don't know what SATA or PATA means.

---

### Post by iaculallad on 2008-07-17
> **Faethin said:**
> I'm sorry. I'm a newbie. I don't know what SATA or PATA means.

I mean you're hard drive, is it serial or parallel? And what motherboard are you using?

---

### Post by jarrhed on 2008-07-17
It's most likely to things:
1. You have a bad burner
Before you try to boot to it check if the cd is coming up with all the files and such in My Computer (Assuming your in Windows) or just check if it mounts with all the files
2. Your not booting to disc
Make sure your booting from the cdrom drive. Most motherboards have a option to boot from other media at bios. Generally its either F11, F12 or F10 or ESC but it changes with every motherboard. If that doesnt work go to bios (Generally push ESC or Delete at bios) and change the boot order to cdrom hardrive floppy etc

Try those

---

### Post by Faethin on 2008-07-17
Thank you for your quick responses.

I did manage to get to Live CD by changing some parameter according to [https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters). However, at step four, when partitioning the drives... no drives appear.

>_<

At least I got to Live CD, huh.

---

