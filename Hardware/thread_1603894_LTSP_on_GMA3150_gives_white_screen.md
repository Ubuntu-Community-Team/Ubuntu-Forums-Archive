---
title: "LTSP on GMA3150 gives white screen"
date: 2010-10-23
forum: Hardware
---

### Post by steamboatsailor on 2010-10-23
Hi, I got a new Zotac mini-pc with an Intel Atom D510 and an GMA3150 (Intel N10). The computer is planned to run ltsp from an 10.04 server.
I got the computer booting and can see the Ubuntu splash. Then instead of the LDM-login screen the monitor turns white and i have an mouse-pointer but nothing more (It's an working X with nothing on..). 
As i have put in ssh-server in the image i can login and it's seams ok. But I have no LDM-screen.
I have other computers running ltsp from the same server without problem, so the ltsp-server seams to be correct installed.

Someone that can have any hints to search..?

/SteamboatSailor

---

### Post by steamboatsailor on 2010-10-29
Ok, answering my self then... I completed my lts.conf with the following:

[FONT=Courier New][MAC-address]
XRANDR_OUTPUT_01 = VGA1
XRANDR_MODE_01 = 1024x768
XRANDR_RATE_01 = 60
X_HORZSYNC = "30-100"
X_VERTREFRESH = "55-75"[/FONT]


Then I got my ldm login screen. The reolution was terrible but that&#347; easy to fix with Xrand. In my case ```
 xrandr --output vga1 --mode 1280x1024
``` did it.

---

