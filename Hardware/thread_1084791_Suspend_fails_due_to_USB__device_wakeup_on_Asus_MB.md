---
title: "Suspend fails due to USB  device wakeup on Asus MB"
date: 2009-03-02
forum: Hardware
---

### Post by snowyowlster on 2009-03-02
My Asus P4C800 Motherboard would always come out of suspend in 8 seconds or so. After some googling around, I found that setting the jumpers on the Motherboard to +5VSB (wakeup from S3 and S4 sleep modes)  rather than the default +5V (wake up from S1 sleep mode)  fixed the problem and now when the computer goes into suspend - it stays there until the powerbutton is pressed.

---

### Post by Redsandro on 2010-07-01
Hi, I know this topic is oldish, but I have a similar problem. My computer won't suspend or hibernate. Hibernate shuts down my computer, requiring a normal boot, and suspend comes back immediately like you said.

However, I cannot find anything about that jumper in the manual. I have the Asus P4C800 Deluxe motherboard.

Can you say something more about it? Where is the jumper on the motherboard or what page in the manual mentions it?

---

### Post by Redsandro on 2010-07-01
I found this in the *P4C800 Deluxe* manual.

> **USB device wake-up (3-pin USBPW12, USBPW34. USBPW56, LJSBPW78)**

Set these jumpers to +5V to wake up the computer from S1 sleep mode (CPU stopped, DRAM refreshed, system running in low power mode using the correct USB devices. Set to +5SB to wake up from S3 and S4 sleep modes (no power to CPU, DRAM in slow refresh, power supply in reduced power mode). The USBPWR12 and USBPWR34 jumpers are for the rear USB ports. The USBPWR56 and USBPWR78 jumper is for the internal USB header that you can connect to the front USB ports.

[img]http://ubuntuforums.org/attachment.php?attachmentid=162119&stc=1&d=1278033323[/img]


But that's something different, right? It's about waking the computer through using USB devices. Clicking the mouse or banging your head on the keyboard.

I will have to wait 'till I can reboot my machine to check what position these are in for me.

---

### Post by Redsandro on 2010-07-01
I switched the jumpers to your suggestion.

I also put my Suspend to S3 Only in BIOS because [I read about it]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/75497/comments/25")

But it still comes right back up after suspend. I lost the two bottom-most USB ports in the back of the computer with these jumpers and settings though. Very strange.

Any advise on suspend/hibernate for P4C800 is very welcome!

---

