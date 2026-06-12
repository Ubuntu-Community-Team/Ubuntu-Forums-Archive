---
title: "Acer Aspire One D250 Boot Failure"
date: 2010-02-09
forum: Hardware
---

### Post by 00b00nt00 on 2010-02-09
Some comments have been made on other threads about this issue, so this is my attempt to unify them.

The model in question is the Acer Aspire One D250 (KAV 60). Basic specs:

1.66GHz N280 CPU
2GB RAM
160GB HDD
Gigabit Ethernet
Bluetooth
b/g wireless
1024 * 600 10.1" LCD
BIOS v1.26

Outline

The computer will boot UNR from either a Live CD or Live USB, no problems. After installation, the computer asks to be rebooted to discontinue the live session, as per usual. However, on re-boot, the computer freezes shortly after the POST, with only a flashing cursor visible.

The computer will occasionally boot after unplugging everything, and once running Ubuntu is fine.

Any suggestions?

---

### Post by josarn on 2010-02-10
I had a similar problem in an Acer Aspire One A150. Made a clean install of ubuntu 9.10 and when I rebooted the netbook behaved as described. Googled about it and flashing the BIOS was the one thing left to try. Followed these steps:

[http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html](http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html)

An the problem was solved...

---

### Post by josarn on 2010-02-10
I forgot to mention that flashing the bios shouldn't be done for fun because if something goes wrong it really goes wrong...

---

### Post by 00b00nt00 on 2010-02-13
Thanks for the reply.

I've already flashed the latest BIOS using FreeDOS, luckily, the computer was never a 'brick' (Windows 7 boots fine), so I'm not going to try such drastic measures.

The computer seems to have settled down over a few boots, which makes me think it is a software rather than hardware issue.

---

### Post by josarn on 2010-02-14
Sorry, I misunderstood. Mine was a nice looking "brick"!

---

### Post by kashuk on 2010-05-15
Hi, I just did a fresh install in my AONE D250 and after finished, it asked for rebbot and then ... nothing :( only the flashing cursor.

I'm thinking on install karmic netbook-remix an after that try with a complete upgrade, any other idea ?

Update:

I just removed the battery and my AONE booted ok, now Im trying  to do a complete update. Wish me luck

Update2:

The problem is still present but I've noticed that if i want a successful boot i have to unplug the battery and A/C power for a while before trying.

---

