---
title: "No Xorg with intrepid- Thinkpad T500"
date: 2008-12-23
forum: Hardware
---

### Post by velozoom on 2008-12-23
Vid Card is a Radeon HD 3650

I upgraded to Intrepid this morning after hearing that video and X support for the ATI cards that had been broken was fixed.  It has not, apparently.  

I see the "loading" splash screen but then X fails to start and I am taken to a command line login prompt.  Can't start X.  When I try the message is "No screens found"  xorg.conf looks like it has no config at all.  I tried to create an entry to use the vesa driver and then the fglrx driver but nothing.   When I run #Xorg -configure the screen goes black and the only way out is to reboot.  

Help....?

---

### Post by Databit on 2008-12-24
It's not just you. I just received the exact same hardware T500 with Radeon HD 3650 and I'm having the exact same issue.
I'm about to try the alternate (non graphical) install. Then if it takes me to a prompt after install all load the radeon drivers manually. I'll let you know how it works out

---

### Post by Databit on 2008-12-24
Go into BIOS Setup (hold down f1 at lenovo splash)
Config-> Display
Set graphics from switched to discrete and set auto OS switch to disabled
Then you should be able to boot the live cd

---

### Post by velozoom on 2008-12-25
> **Databit said:**
> Go into BIOS Setup (hold down f1 at lenovo splash)
Config-> Display
Set graphics from switched to discrete and set auto OS switch to disabled
Then you should be able to boot the live cd

wow, thanks!  I'm installing right now.  I'll let you know how it turns out. 

I've never seen that option before....I'll have to look up the diff between discrete and switched modes.....

---

### Post by velozoom on 2008-12-25
YEAH!  That totally worked!  THANKS!  I've been trying to sort this out for weeks by tweaking the OS when it was always in the hardware setings on the board.  Thanks a billion!  

Looked up the terms above, thanks for the knowledge!

---

### Post by Databit on 2008-12-26
np. I picked up the T500 and modified it a touch just because all the hardware seemed to be supported in Ubuntu/Linux. Was quite confused when it wouldn't work.

Did you have any trouble with your wireless? Gave me a touch of trouble but was able to get it worked out

---

### Post by velozoom on 2008-12-30
Once I sorted the video issue and could install 8.10, wireless works flawlessly.  The wireless card wasn't even recognized with 8.04, however.  So in that sense, yes I had some issues. ;) 

I've gotten it to work with A, G, and N networks without a bit of configuration other than basic network set up- SSID and passcode

---

### Post by badbowtie03 on 2009-01-06
I just got a T500 with the 11b/g Wireless LAN Mini PCS Express Adapter III and the driver is provided by Atheros Communications Inc. 

I finally just got Ubuntu installed and I have no idea how to setup the whole wireless thing... I dont think it is. I ran the Terminal thing with some tutorial and i typed in a command and it said it was unrecognized or something.. Anyways can someone please send me in the right direction. Thanks

---

