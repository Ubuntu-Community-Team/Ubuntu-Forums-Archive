---
title: "Screen panel to big"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by sammydeprez on 2009-05-25
[IMG]http://ubuntuforums.org/images/misc/menu_open.gif[/IMG]I wanted to install the new Ubuntu for netbooks on my HP Mini.
When i select to install or i choose for live without install.

The screen panel is to big for my screen :( So I can't see a lot of things on the right side of the screen and the bottom.

Is their a solution for this?

Thanks guys!!:D

---

### Post by peakshysteria on 2009-05-25
Tell us a bit more about your mini and which OS version you are running and how you installed it. The regular Jaunty Jackalope works like a charm on our HP 2133 Mini-Note.

---

### Post by sammydeprez on 2009-05-25
Its just a normal HP MINI 2133
but i extended the memory to 2gb

Os at the moment is windows xp professional.
But am using a flashdisk to boot from to install the newest ubuntu.

the strange thing is, the first time i booted form the live usb disk :) it was perfect no problems. But no i can't get it right anymore. panel size is to big...

---

### Post by sammydeprez on 2009-05-27
nobody a solution :(
i really want to install the new ubuntu on my system.. but can't see my whole screen :(:(

---

### Post by peakshysteria on 2009-05-28
> **sammydeprez said:**
> Its just a normal HP MINI 2133
but i extended the memory to 2gb

Os at the moment is windows xp professional.
But am using a flashdisk to boot from to install the newest ubuntu.

the strange thing is, the first time i booted form the live usb disk :) it was perfect no problems. But no i can't get it right anymore. panel size is to big...

You say you only booted from the flashdrive. This means you haven't installed Ubuntu as far as I can tell? It sounds like you just have tried the live version without installing it!?

I have no experience in using a Flashdrive to install from. Our install was made from an external (usb) DVD-rom. We just rebooted after inserting the disc. Then went on with the install.

Have you looked at: 

[Linux on the HP 2133 Mini-Note]("http://hp2133linux.blogspot.com/2009/03/installing-ubuntu-904-beta.html")
This also talks about a resolution problem a bit like the one you mention. It might work for you to follow the howto here. We did not encounter these problem on our mini.

or the older:

[Installing from a USB/SD Flash Drive]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133#Installing%20from%20a%20USB/SD%20Flash%20Drive")

---

### Post by sammydeprez on 2009-05-29
Solution found on the website you have me.
> There is a strange bug that occurs after the previous step and when you reboot you will notice that the resolution gets it wrong. This can easily be solved by adding one line in the xorg.conf file. Press "Alt+F2" and type "gksu gedit /etc/X11/xorg.conf", hit "Run" and enter your password when asked.

Look for
[INDENT]Section "Device"
   Identifier    "Configured Video Device"
EndSection[/INDENT]and add this line
[INDENT]Section "Device"
   Identifier    "Configured Video Device"
   [COLOR=#FF0000]Option    "PanelSize"    "1024x600"[/COLOR]
EndSection[/INDENT]Press "Save", close window and fixed.

Reboot and enjoy Ubuntu 9.04. 

---

### Post by peakshysteria on 2009-05-29
Nice. Mark thread as solved if this solved your problem.

---

