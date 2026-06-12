---
title: "Can't install on Dell Inspiron 9300"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by jmvbxx on 2006-02-03
I can boot the iso DVD and I get to the main menu where I can choose install, server or ENTER.

No matter which I choose, the installation starts for a very short while and then all of the sudden stops and leave the screen blank w nothing running, not the HD or the DVD drive.

I have to manually force a reboot to get the computer to run again.

Any help is appreciated!

---

### Post by Scotland on 2006-02-03
[QUOTE=jmvbxx]I can boot the iso DVD and I get to the main menu where I can choose install, server or ENTER.

No matter which I choose, the installation starts for a very short while and then all of the sudden stops and leave the screen blank w nothing running, not the HD or the DVD drive.

I have to manually force a reboot to get the computer to run again.

Any help is appreciated![/QUOTE]


I had a problem today installing on my new inspiron 9400. Let me select language etc then said it could not mount my cd :(

Turns out, burned a new cd at slower speed and that was the problem. Well, the start of my problems - Keyboard hangs immediately after login display using the 686-SMP kernel :(

Try reburning

Dougie.

---

### Post by pax on 2006-02-03
I went crazy trying to understand why I couldn't install ubuntu on my new inspiron 9300. It's funny, but It helps to read the screen some time ;-)

Reboot, press F2, now you are in BIOS, go down to boot order option, and use the 'U' key to move the CD/DVD drive up to the first line. Save and exit.

When you get to ubuntu install screen, press F2 (i believe) read the screen, at the bottom it will explain that installation with some notebooks require an extra command to invoke. Type that command and proceed to the best OS I used on a notebook, Ubuntu.

Good luck.

---

### Post by Zach1188 on 2006-02-06
I have the same problem on my Inspiron 9300. Pax, should I press F2 on the main screen that prompts you to press Enter/Sever or when it begins to list files?

---

### Post by ewjmulder on 2006-02-06
Hi guys, I've installed Ubuntu successfully on my inspiron 9400 yesterday. You should type 'linux vga=771' on the prompt (is explained in the 'F5 menu' on Install CD boot).

Good luck!

Erik
- The Netherlands

---

### Post by newuser111 on 2006-02-06
try booting with linux acpi=off

---

