---
title: "8 in 1 card reader not working (PCMCIA)"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by gmillikan on 2006-10-01
When I put my camera SD card in my card reader in my laptop, Ubuntu is not recognizing it.  This is a dual boot and on the XP Pro side, it picks up the card no problem so I know there's nothing wrong with the hardware.  Any thoughts?

---

### Post by ethan961 on 2006-10-02
Funny, whenever I plug a sd card into my computer Ubuntu recognises it fine, unlike Knoppix etc. Have you tried a reboot after you plugged it in? Does gparted recognise it? Hope I can be of assistance.

---

### Post by lutra on 2006-10-03
> **gmillikan said:**
> When I put my camera SD card in my card reader in my laptop, Ubuntu is not recognizing it.  This is a dual boot and on the XP Pro side, it picks up the card no problem so I know there's nothing wrong with the hardware.  Any thoughts?

As another users suggests kernel version 2.6.15-23 do mount correctly media cards. At least also in my case, a 5in1 pcmcia reader. More recent versions of the kernel all fails to correctly mount cards.

---

### Post by gmillikan on 2006-10-08
Haven't tried plugging in card and then rebooting, I'll try that next.  But it doesn't seem like that would help since the 8 in 1 card reader is always in -- it seem like it would always recognize the 8 additional drives, even if there was nothing in them...

I'll run gparted here off of external CD and see if that picks it up.

---

### Post by ethan961 on 2006-11-01
Windows always detects all 3 of the drives (on my card reader) for me, even with nothing in them - BUT Ubuntu never has detected the empty drives for me. Never. Shows how smart Linux is, compared to Windows!! AND, my jumpdrive never works at school on those M$ infected PC's, windows will never mount it. Just the opposite for Ubuntu.

---

