---
title: "Lost my SATA storage disk"
date: 2009-03-30
forum: Hardware
---

### Post by budluva04 on 2009-03-30
Yesterday I went to go shutdown the computer yesterday to upgrade my CPU from an AMD X2 5000+ brisbane to an X2 7750 Kuma and also added a front 120mm case fan, and the shutdown hung on me, for reason's I could not tell, and I had to kill my box with the power button...now when I go to boot this PC my BIOS doesn't recognize my SATA 500gb Seagate disk...

At first I thought it was the PSU being maxed out and not enough juice to the disk, well, I tried unplugging the new case fan...BIOS still didn't recognize the disk...ok well then I thought the new power requirements of the Kuma CPU where to much, (Brisbane 65W cpu, Kuma 95W cpu) so i tried unplugging everything, all 3 case fans (2x120mm 1x140mm), IDE DVD burner, and my other 500gb IDE drive, so the only thing's that were getting power where the motherboard, cpu, heatsink fan, PCI-E GFX card, the front case led's, and the suspect SATA disk...BIOS detects NOTHING... Now I'm thinking the disk has no power, my PSU has 2 SATA power cables, with 2 ends each, (4 SATA peripheral's total) I tried everyone, BIOS still doesn't detect it, BUT I took the drive out of the mount and set it on the bottom of the case and I can feel it with my hand spinning up, it has power...

I've tried all that I can at the moment short of swapping the SATA cable or the motherboard, I don't have enough spare SATA parts to do this...so I leave this open to anyone with some suggestions for me? I can either clean off my old Brisbane CPU and re-mount the heatsink which isn't the easiest job, or swap SATA cable, or take the disk back and see if they'll give me a new one...

FYI, all parts were purchase within the last 2 months, all brand new...

Any suggestions are welcome...

---

### Post by joemacnz on 2009-03-30
Not sure about your chipset or stuff, but when I was having SATA/booting issues, [ this ](http://ubuntuforums.org/showthread.php?t=783773) fixed it for me.

---

### Post by budluva04 on 2009-03-30
Thanks for the reply, maybe i'll look for a SATA to IDE adapter, or try a new SATA cable...

This is not something that has to do with GRUB/Linux/Ubuntu as my BIOS won't even detect the drive.

ASUS M2N68-AM
AMD X2 7750 (Kuma)
Artic Cooling Freezer 64 PRO
EVGA 9800 GTX+ 512MB
2GB Kingston HyperX
500GB Seagate IDE
500GB Seagate SATA (suspect)
1x140mm 2x120mm Antec Smartcool Fans
Antec Earthwatts 380W PSU

---

### Post by budluva04 on 2009-03-31
bump any ideas

---

### Post by cariboo on 2009-03-31
Have you tried resetting the BIOS to see if the drive is detected?

Jim

---

### Post by budluva04 on 2009-03-31
i cleared bios to setup defaults, yes...think a cmos reset is in order?

---

### Post by budluva04 on 2009-03-31
does anyone have any other thoughts? should i return the drive?

---

### Post by budluva04 on 2009-04-03
bump

---

### Post by lnxnut on 2009-04-04
Just a suggeston, is there an updated bios for your board on the manufacturer's website?  I noticed you have an ASUS board, which I really like ASUS, but the last few computers I built with their board I had to update the bios to get anything to work.  Also, I noticed your drive is a seagate, I have a 250mb seagate sata2 drive and kept getting soft test failed during bootup and it finally went out, I bought a new seagate and I'm getting the same error message with it but it hasn't went out yet.  I'm kinda thinking there might be a problem with seagate sata2 drives.

---

### Post by budluva04 on 2009-04-25
ok i have updated my bios, and i recently had my laptop system board crack, so i had the spare 2.5" sata disk from it out of my laptop, and i plugged it into my desktop, the bios recognized the drive, but when i booted ubuntu, i couldn't see it mounted, or listed in sudo fdisk -l, i saw an sda but not an sdb in /dev/ so i dunno, and that was the last i saw of it, bios hasn't seen it yet either, and it doesn't even sound like the drive is spinning anymore on boot, is there something frying my sata disks? my pata which my / partition is on has had no problems, even my pata dvd writer works no problems, something is f'd up with my sata disks and i can't figure it out, might it be too low of a power supply? i have an antec earthwatts 380w running 2x120mm fans, 1 140mm fan, 1 500gb 7200rpm PATA disk, PATA dvd rw, and a 9800GTX+, think my power supply can't handle the system with the sata disks plugged in and its frying them?

---

