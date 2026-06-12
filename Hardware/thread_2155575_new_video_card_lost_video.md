---
title: "new video card lost video"
date: 2013-06-18
forum: Hardware
---

### Post by opfeld on 2013-06-18
I bought a new msi gt 620 video card and plugged it into my pci 2.0 slot, fan started spinning up, and my monitor gave the message no signal.  So I removed the card and plugged the dvi cable back into the mobo graphics, which I have been using to this point, and again got the no signal message.  Nothing is showing up bios or the lubuntu os.  I moved my monitor to a different computer and it works great.  Is it possible the new video card messed up my motherboard?

---

### Post by mdmcaf on 2013-06-18
Was there any static discharge when you plugged the new video card in? Static killing something these days is somewhat rare, but it's still a possibility.

I would try to reset the BIOS back to defaults via the jumper on the motherboard (the manual will say where it's located and the exact procedure involved in resetting the BIOS). Also, have you tried the new video card in a different machine? It's possible that you got a defective card and that the motherboard got stuck into a mode where it only displays output from a discrete video card.

---

### Post by user_of_gnomes on 2013-06-18
>  Static killing something these days is somewhat rare, but it's still a possibility.

Because the laws of thermodynamics have seen such great changes in the past few years? :) 

> I bought a new msi gt 620 video card and plugged it into my pci 2.0 slot, fan started spinning up, and my monitor gave the message no signal. So I removed the card and plugged the dvi cable back into the mobo graphics, which I have been using to this point, and again got the no signal message. Nothing is showing up bios or the lubuntu os. I moved my monitor to a different computer and it works great. Is it possible the new video card messed up my motherboard? 

Why don't you plug the old videocard back in and see if that works? Check all the cable connections too..

---

### Post by opfeld on 2013-06-18
There was no other video card I just used the onboard graphics but that isn't working any more

---

### Post by opfeld on 2013-06-18
I'm not sure how to flash the bios using the jumpers on the board. I only see a grouping two jumpers and 4 pins... It's an Asus

---

### Post by Yellow Pasque on 2013-06-18
>  It's an Asus 
What kind? (It's probably stamped on the board.)

---

### Post by opfeld on 2013-06-18
Asus m3a78-cm

---

### Post by |{urse on 2013-06-18
Remove the hard drive power and data cables and all rom power cables  Ive seen dying drives lock the system up on boot with no-post, also take whatever your ram is down to 1 stick and try it again. If that doesn't work try a different stick of ram, cmos reset, if that doesnt work reseat the processor. Also make sure you don't have anything extra at all plugged into the system (such as usb devices etc), then try to boot bare metal and work your way back until you find the problem.

---

### Post by Yellow Pasque on 2013-06-18
> **opfeld said:**
> I'm not sure how to flash the bios using the jumpers on the board.

Download the manual. Look at page 1-17 (section 1.9) for CMOS clearing procedure.
[http://www.asus.com/Motherboards/M3A78CM/#support_Download_29](http://www.asus.com/Motherboards/M3A78CM/#support_Download_29)

---

