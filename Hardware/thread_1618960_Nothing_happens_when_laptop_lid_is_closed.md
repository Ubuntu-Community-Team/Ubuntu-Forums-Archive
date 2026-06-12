---
title: "Nothing happens when laptop lid is closed"
date: 2010-11-11
forum: Hardware
---

### Post by dhiman33 on 2010-11-11
:guitar:I've an hp520 laptop and it does NOTHING when I close it's lid. In windows closing the lid causes the laptop to go to sleep. If I change the settings in power management, nothing happens. Is there some way to solve the problem?:(

---

### Post by cr0m on 2010-11-11
I don't have this laptop, however, the video card you have is the Intel GMA 950, which may have some issues.

This post has a good suggestion: make sure you're using the correct driver.
[http://ubuntuforums.org/showpost.php?p=9243418&postcount=3](http://ubuntuforums.org/showpost.php?p=9243418&postcount=3)

HTH.

---

### Post by dhiman33 on 2010-11-12
:(There's no xserver-video-intel in the rep. Though it has something called xserver-xorg-video-intel; and it's already installed. Are u sure my chipset is gma 950? in windows device manager it says my chipset's name is "mobile intel 945gm express chipset".:guitar:

---

### Post by cr0m on 2010-11-12
I'm not sure that you have GMA950, that's just what I was able to ascertain from Google. Your device manager is likely correct.

FWIW, I believe xserver-xorg-video-intel is the correct package.

I am not able to offer you a lot of hard information, but I have the GMA500, and there are serious problems with the drivers--including the sleep/hibernate functions.

One thing that you might try are one of the tweaks mentioned on this page:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Tweaks](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Tweaks)

(the 99video one and installing uswsusp.)

The 99video one did nothing for me. Installing uswsusp enabled me to put my laptop to suspend using the command line. Not optimal, but at least I can suspend... kind of important for a laptop.

---

### Post by Yellow Pasque on 2010-11-12
The GMA950 is the codename for the GPU part of several different 945(g) intel chipsets.

> I am not able to offer you a lot of hard information, but I have the GMA500, and there are serious problems with the drivers--including the sleep/hibernate functions. One thing that you might try are one of the tweaks mentioned on this page:
[https://wiki.ubuntu.com/HardwareSupp...Poulsbo#Tweaks](https://wiki.ubuntu.com/HardwareSupp...Poulsbo#Tweaks)

Poulsbo/GMA500 is a completely different chipset made by PowerVR and licensed by Intel. Apples and oranges..

Anyway, if the laptop suspends/resumes normally, and just has issues with the lid, I would suggest closing and opening the lid and checking logs (like dmesg and/or /var/log/acpid.log if you have it) to see if there's an ACPI problem.

---

### Post by cr0m on 2010-11-13
Thanks for clearing up my misinformation, Temujin. Sorry for giving you bad info dhimman.

---

### Post by dhiman33 on 2010-11-13
:confused:Ya my laptop can suspend normally fom the shut down menu, just closing the lid doesn't work. Ok where can I find these logs?/How to  generate them?

---

### Post by dhiman33 on 2010-11-16
Why someone doesn't answer?!!:confused:

---

### Post by dhiman33 on 2010-11-25
Hello......:confused:

---

### Post by odyssey41 on 2010-11-25
Same thing happens with my laptop (Sony Vaio) with SD card mounted. If no SD card is mounted Suspend will work perfectly when lid is closed.

---

### Post by themadhatter0 on 2011-03-02
Same problem on a Dell Precision M4400 with NVIDIA Quadro FX 770M.

---

