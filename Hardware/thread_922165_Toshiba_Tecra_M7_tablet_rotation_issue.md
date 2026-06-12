---
title: "Toshiba Tecra M7 tablet rotation issue"
date: 2008-09-17
forum: Hardware
---

### Post by minime80 on 2008-09-17
Okay, I'm using the rotate.sh script from [this page.]("http://ubuntuforums.org/showthread.php?t=489808&highlight=tecra+m7+rotate&page=7") 

I can manually rotate it fine, so I know the display and everything is working, and I know the rotate.sh script is working because when I resume from suspend the screen is briefly flipped (which is fine). My issue is that when I flip the screen around and fold it down, it doesn't rotate!

I've gone through the script and found that the cause of this is that the lid state is not changing to "closed" in this configuration. I checked the bios and didn't find anything that looked very helpful.

Anybody have any clue what might cause this, because it seems like it works for most of the others in that thread.

**EDIT:** I ran an acpi_listen and rotating down doesn't even throw an event until you lift it back up. My guess is that one of Toshiba's BIOS updates changed this behavior and the people in the previous thread were running older BIOSes (I'm on v3.30).

If I have some time to kill this weekend I may try my hand at writing a small acpi event handler for pressing the screen rotation button below the LCD. \\:D/

---

### Post by minime80 on 2008-09-17
Alright, who's gonna start working on a driver for our accelerometers so we can do [this]("http://www.krizka.net/2008/02/13/thinkpad-x61-tablet-automatic-screen-rotation-under-linux/")? :popcorn:

---

### Post by nightalon on 2009-02-10
This is slightly unrelated, but has anyone had an issue on the models with the G72M/Nvidia Quadro NVS 110M where the whole screen shifts left, then right, within the span of a millisecond?

I discovered that it occurs when PowerMizer is shifting from one state to another.  With my bum motherboard (which was recently replaced) this issue also happened in Windows Vista, but not MacOS.  I doubt MacOS utilizes PowerMizer.

I am using the latest 178.xxx NVidia binary drivers.

If someone has a good idea of where else to post this, I'm all ears!

---

