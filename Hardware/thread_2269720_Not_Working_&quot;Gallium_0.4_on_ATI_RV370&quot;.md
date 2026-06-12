---
title: "Not Working &quot;Gallium 0.4 on ATI RV370&quot;"
date: 2015-03-17
forum: Hardware
---

### Post by guilhermebidarra on 2015-03-17
Hi Everyone!

After installing ubuntu on my pc, I noticed that the resolution was incorrect, moreover, after using xrand when restarted the computer, back to what it was before (using xrand solved it, but when restarted, it always go back to the wrong resolution).
 I also noticed that the games did not have the same performance as when played in windows XP (for example: Minecraft).
 I tried to install the drives Gallium 0.4 on ATI RV370 (fglrx drives) and when restarted the computer, did not open the Unity and the resolution turned to 800x600 instead of 1024x768.

 What is the problem? Are the corrupted drivers or is the hardware?

 (Sorry for my english: D)

---

### Post by Vladlenin5000 on 2015-03-17
"Gallium" means you're using the open source drivers, not the proprietary ones (fglrx) you really need for better performance. And "Gallium" requires no installation: It's activated by default and it's called Radeon...
According to this - [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) - it should work fine for your hardware. Unfortunately, ATI/AMD no longer supports your hardware with proprietary drivers therefore whatever place you're in right now is where you're going to be, Radeon (open source) is currently the only driver that works for Ubuntu and that old graphics.

---

### Post by mastablasta on 2015-03-18
> **Vladlenin5000 said:**
> whatever place you're in right now is where you're going to be, Radeon (open source) is currently the only driver that works for Ubuntu and that old graphics.

that's true but there are many opensource driver versions (development ones for example). you could also perhaps do some tweaks.  but in the end opensource drivers are a hit or miss. sometimes they work really well, other times not so much. and occasionally they even cause full system crashes. so much for opensource, but then again AMD didn't fully open itself yet. but they are going that road. they are helping develop the opensource drivers.

edit : if you really tried to install fglrx make sure you now remove them. and try to tweak opensource drivers propperly.

---

### Post by Yellow Pasque on 2015-03-18
[https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently](https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently)

---

