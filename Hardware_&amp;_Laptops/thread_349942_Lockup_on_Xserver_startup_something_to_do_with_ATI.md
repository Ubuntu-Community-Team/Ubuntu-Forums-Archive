---
title: "Lockup on Xserver startup something to do with ATI"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by Rocket on 2007-01-30
On most boots from cold my box locks, sometimes it does boot normally, not often though. It locks after the Ubuntu screen with the progress bar but before the user/password screen. 
I can get it to start if I do the following with the power off, swap the link over on the video card (I have no idea what this link does, ATI documentation doesn't mention it) or remove and reinsert the video card. 
I am using the FLGRX 8.33.6 driver from the ATI website, it also happens with the Ubuntu ATI driver.
My box hardware is:
Dapper only
Sempron 3300+
Asus K8VSE M/B
160Gig seagate ide 
400 w power supply
256 Mb Radeon Sapphire 9550 AGP video
1 gig ram

I tried swapping the video card with one I have in an XP box (radeon 9220 125 Mb), Both the Dapper box and the XP box then boot ok. 
Any ideas would be helpful.
Regards
Rod

---

### Post by Rocket on 2007-02-11
I think I have have awork around for the above problem. X starts ok every time if do not turn the ac power on to the monitor until 30 seconds or so after booting the computer. I suspect it is something to do with the monitor probing. I will try another monitor in due course. Anybody have any ideas.

---

### Post by Rocket on 2007-03-13
Please help, the above post only works some of the time.
Does the following mean that my system somehow thinks it has two video cards, I only have one. If so how do I fix it.
Regards
Rod

rod@study:~$ dmesg |grep -iB3 agpcommand
[17179613.184000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179613.184000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179613.184000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179613.184000] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)

---

