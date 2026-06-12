---
title: "LIVE-CD Passwort Ubuntu 2D"
date: 2012-04-12
forum: Hardware
---

### Post by MaRittaba on 2012-04-12
Hej,

I was going to test the actual version 11.10 via LIVE-CD on my Notebook.

It's a HP notebook with an external monitor. I don't want to mirror but an extended desktop.

Problem is, extended desktop in max. resoluton no possible due resolution restrictions in none 2d-mode.

But how can I switch in Ubuntu 2D-mode - without password? 

Where can I find the password?


Best regards
Martin

COMPUTER:
[FONT=Courier New]Modell......: HP/Compaq nx6325 
CPU.........: AMD Turion 64 X2 Mobile TL-60
OS..........: Windows XP Prof. SP3
Graphic.....: ATI Radion XPress 1150
Monitor.....: SXGA+ (1400x1050)  
Ext. Monitor: WUXGA (1920x1200)[/FONT]

---

### Post by ajgreeny on 2012-04-12
On a live CD the username is **ubuntu** and the password is left blank, just hit enter without typing anything.

---

### Post by MaRittaba on 2012-04-13
> **ajgreeny said:**
> On a live CD the username is **ubuntu** and the password is left blank, just hit enter without typing anything.

Yes, I did so but with no afford. Same as before.
Did the system really switch in 2D-mode?
Can I check this in some way?

Error when trying to choose 1920x1200 and 1400x1050 for the displays:

"The selected configuration für displays could not be applied.
Requested size (3320,1200) exceeds 3D hardware limit (2048,2048).
You must either rearrange the displays sp that they fit within a (20,48,2048) 
square or select the Ubuntu 2D session at login."

---------

Directly after booting and loading when I try to optimize the displays the following message apears:
"Restricted drivers available
In order to use your system hardware more efficiently you could use 
drivers or so that is not free software."

May this is the problem, it is to designed to fail.

Where can I get this software and what does it cost?

---

### Post by ajgreeny on 2012-04-13
The restricted drivers cost nothing and are made available by the card makers. Go to **Additional drivers** from the dash (I think; I don't use 11.10 unity) and choose the most recent driver offered, then logout and login again, or reboot if the new login does not work.

---

### Post by MaRittaba on 2012-04-13
> **ajgreeny said:**
> The restricted drivers cost nothing and are made available by the card makers. Go to **Additional drivers** from the dash (I think; I don't use 11.10 unity) and choose the most recent driver offered, then logout and login again, or reboot if the new login does not work.

Is this possible with Live-CD or do I have to install the system?

---

### Post by ajgreeny on 2012-04-13
Sorry, I forgot this is a live system.

You could possibly install the drivers, but even if you do, they will disappear when you reboot the live system, and if they don't work with a simple logout and login, they wil not work at all.

---

