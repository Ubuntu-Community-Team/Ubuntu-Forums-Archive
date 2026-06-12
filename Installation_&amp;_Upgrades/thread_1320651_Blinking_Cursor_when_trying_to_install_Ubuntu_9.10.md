---
title: "Blinking Cursor when trying to install Ubuntu 9.10"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by Scuddlefish on 2009-11-09
Hello all,

Whenever I select to install Ubuntu or run live without making changes to my computer, the screen only turns black with a white blinking cursor. I've seen other threads about video problems, but not exactly with this symptom.
Assuming it was the video card, I used a video card from another computer I knew that the installer worked on, but that time only a blank black screen showed, not even the cursor. Some of my computer specs are listed below.

Dell Optiplex 960
Video: ATI Radeon HD 3470 

Please let me know if I can give you any more information.
Thank you to anyone who helps :).

---

### Post by Scuddlefish on 2009-11-09
bump

I've looked through all of the recent threads and couldn't find anything relevant. Any help would be appreciated.

---

### Post by wallaroo on 2009-11-10
Give this a try ..
[http://ubuntuforums.org/showthread.php?t=1318701](http://ubuntuforums.org/showthread.php?t=1318701)

---

### Post by macdingo on 2009-11-10
You are not alone.
After reading your post I think it is something to do with the 960 architecture.
I have been fighting a 960 for a couple of days now.
I can force it to install by using safe graphics mode and . . . (AHCI off or something) but after it reboots I am stuck as you describe with a blinking cursor.

I found a thread where it was a conflict with a Haupage (at one point I had an old 350 in during install) but a clean install with it out made no difference.

Video setting in BIOS does not fix it.
I have tried with onboard video and with a GeForce 8400 GS but no joy.

I know my disc is good because it has installed successfully on a Dell Dimension 9150.

I was using to 960 to see what 9.10 was like and how easily I could do a clean install and upgrade.

I think 9.10 is worth the effort but I do not really need to run it on the 960 so I have just installed 9.10 on another drive in my Dimension. Since that is the case and since I am tired of fighting it I am just going to have to wait until someone smarter than me (with a Dell 960) solves it.

Good luck!

---

### Post by Scuddlefish on 2009-11-10
Well my problem was different from the link mentioned above. I could choose the language, but after selecting to install or try with no changes, only a blinking cursor would appear. When I tried the vga settings, instead of a blinking cursor, a blank screen appeared.

Thank you for your post macdingo. I tried turning acpi off under the F6 options and that allows me to successfully go into live mode and into the installer, though I haven't tried installing yet, as I fear your described symptom. This is my office computer, and I would like to be fairly confident that the install would go fine.

While in live mode, I did see the ATI fglrx driver to install.
If I installed that driver after installing the OS, how likely is it that things would work smoothly?
 
Any other suggestions would be highly appreciated! :)

---

### Post by Scuddlefish on 2009-11-11
bump

So from seeing other posts, just because I can see the installation by the procedure listed above, I will still most likely just get the blinking cursor upon reboot?

---

