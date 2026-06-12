---
title: "PALM M130 Driving me batty"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by dgrafix on 2006-06-22
](*,) 

I want to get jpilot to work properly, i dont care about (and have given up on) gpilot and evo.

I get 1 sync (if im lucky) per system boot. This is on /dev/ttyUSB0 otherwise i get:

****************************************
 Syncing on device /dev/ttyUSB0
 Press the HotSync button now
****************************************
pi_bind error: /dev/ttyUSB0 No such device
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished


Interesting thing is, after a sync if i try a lsdev -v the terminal just sits there and needs to be Xed to get rid of it (CTRL c no good).

Whats also weird is in this state, when i do a restart, i get a login prompt come up with login TTY1. This only happens when my palm port locks up.

I notice some are using /ttyUSB1 but i get no joy on this at all. nor on the default /dev/pilot (which has never worked)
I dont really understand the way usb works (except you are supposed to plug it in and have it work)

Why is palm interfacing such a big problem in ubuntu, when windows and mac have no problems whatsoever?

I had jpilot working for a bit in Breezy but had to unplug all other devices first (not cool) in dapper though no joy at all.

---

### Post by lkagan on 2006-06-22
Unfortunately, I don't have any advice for you.  I can only share with you what works for me.  I have a treo 650 and have had lots of problems getting evolution and gpilot to work correctly.  

But now I have it working somewhat reliably in dapper.  I first make sure that there is no pilot applet in the taskbar.  I then make sure all gpilotd is killed.  I then run gpilotd as the regular user via command line.  I then press the sync button on my palm and it usually works just fine.

I wish you the best of luck.  I know how irritating this can be.

Larry

---

