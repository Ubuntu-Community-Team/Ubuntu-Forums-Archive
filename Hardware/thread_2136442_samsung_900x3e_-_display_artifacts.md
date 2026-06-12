---
title: "samsung 900x3e - display artifacts"
date: 2013-04-17
forum: Hardware
---

### Post by krist0ph on 2013-04-17
Hi,

I recently bought the samsung 900x3e ultrabook and installed ubuntu. Most things work fine, however, the screen shows artifacts (horizontal lines appearing over the screen - [see screenshot]("https://launchpadlibrarian.net/137577559/problem.jpg")).

Is anyone else using the 900x3e with linux? Would be interesting to know if it is a hardware or software issue.

Windows 8 runs fine if I turn the laptop on and start it directly. If I boot linux and then reboot to windows,  some rest of the artifacts is also visible in windows.

---

### Post by antymat on 2013-04-24
Try switching off the acceleration (there will be no artefacts, but also no Compiz...): add ```
nomodeset forcevesa
``` to your kernel booting options (i.e. press TAB in Grub booting page).[br]1[/br][br]1[/br]The same happens in Fedora and System Rescue CD.

---

### Post by murmlos on 2013-04-28
I am having the same problem, running Arch Linux and using:
linux-3.8.10-1
xf86-video-intel 2.21.6-1

Forcing vesa didn't help me 

Samsung 900x3e

EDIT: Forcing Vesa does help!

---

### Post by hayo.hase on 2013-09-24
I had this problem with ubuntu 13.04 too, but it disappeared with ubuntu 13.10.

---

