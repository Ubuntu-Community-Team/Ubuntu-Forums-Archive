---
title: "LPT LCD not working"
date: 2010-09-20
forum: Hardware
---

### Post by ts230 on 2010-09-20
So, I have a 20x2 LPT LCD set up on my Ubuntu machine, but all it does show is every line filled with black boxes. Why's this, and how would I go about fixing this?

I have both LCDd and LCDProc installed and running, but still no dice. I tried every LPT port number, and even the wiring mode. I know it's winamp, but I still can't get it to work. Is there a specific mode I have to set in the BIOS to get the LCD to work, like ECC or whatever? I have no idea what it's at right now, or if I am able to change that through Ubuntu without rebooting into the BIOS as I don't have the required physical access to the server right now.

Help me please! I've tried just about everything, and I used [this tutorial]("http://ubuntuforums.org/showthread.php?t=664306") for the installation. 
Is there a command at all that could tell me if it detects the LCD on the LPT port? I hope that this is just a configuration/software issue, not an issue with my LCD.

---

### Post by Fafler on 2010-09-20
The first thing to do is to test it on another computer. It's been awhile since the last time i played around with these, but i think some of them display black bars until the host sends the first command to the display.

LCDproc doesn't use ECC or EPP to communicate with the display. It's the integrated LPT port on your mainboard? It should be accessible through the legacy I/O ports, used back in the good ol' ISA bus days, and i think thats still what LCDproc uses.

I'm pretty sure the Winamp wiring scheme doesn't allow any kind of read back from the display, so no, there's no way to know if it detects the display.

---

### Post by ts230 on 2010-09-20
> **Fafler said:**
> The first thing to do is to test it on another computer. It's been awhile since the last time i played around with these, but i think some of them display black bars until the host sends the first command to the display.

LCDproc doesn't use ECC or EPP to communicate with the display. It's the integrated LPT port on your mainboard? It should be accessible through the legacy I/O ports, used back in the good ol' ISA bus days, and i think thats still what LCDproc uses.

I'm pretty sure the Winamp wiring scheme doesn't allow any kind of read back from the display, so no, there's no way to know if it detects the display.


Hmm, what kind of other computer would work? I'm 'fraid I can't find a Windows computer with an LPT port nearby, but I know I got the LCD working a few years back, and since then it's been sitting in a box, untouched.

Yeah, it's an onboard LPT port. I'm just incredibly confused.

---

### Post by Fafler on 2010-09-20
Any kind /should/ work. Just like yours ;-)

---

### Post by ts230 on 2010-09-20
> **Fafler said:**
> Any kind /should/ work. Just like yours ;-)

Except the one with Ubuntu is the only one that comes with an LPT port. Do you think I should just screw the LPT LCD and get a USB or serial one?

---

