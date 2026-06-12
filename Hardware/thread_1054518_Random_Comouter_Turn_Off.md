---
title: "Random Comouter Turn Off"
date: 2009-01-29
forum: Hardware
---

### Post by joeb1990 on 2009-01-29
This has nothing to do software related but is a very odd ordeal. Once in every 7 times I stand up from my chair my computer reboot. The only clue I have is a lose heatsink on the south bridge indicating a possible loose chip. I just built this computer a few months ago and cannot see anything that would cause this. I have even taken it apart and put it back together just to see if it was a loose connections but it started again. I have no idea what to do? Any ideas?

---

### Post by Yashiro on 2009-01-29
If you wiggle your case does it reboot?

---

### Post by joeb1990 on 2009-01-29
Thats the thing...no its only when the chair gets hit. The chair isnt touching any cords either

---

### Post by Joe2Shoe on 2009-01-30
The chair has a Voodoo curse on it.  Get rid of it now!  And get a new one.

I assume this is a desktop (tower) computer.  Replace the CMOS (RTC - Real Time Clock) 3 Volt Lithium battery on the motherboard (mobo) with an Energizer or Duracell brand, available at OfficeDepot, WalMart, etc.
Even if you just purchased the mobo new, it could have been sitting around for a year or more.  CMOS batteries usually last around 3 years, but the manufacturers usually put cheapo ones in.  If the voltages gets below 3 volts (with a load on it), it will cause reboots, sometimes.  These reboots are random, the chair has nothing to do with it, I hope.

Good luck.
Joe2Shoe.

---

### Post by electrogeist on 2009-01-30
I don't think the south bridge chip would be loose, being soldered to the board you would have bigger problems if it was.  Sometimes those heatsinks are spring-mounted and there can be a little play.  It could be overheating tho

Alot of things can possibly cause a spontaneous reboot or shut off, from just about any component, to a pinched & shorted wire for reset switch or power switch.  A suspected component would be the power supply, alot of PSUs are less than desirable quality.

Strip it down to a bare minimum for troubleshooting and slowly add components back in later. If you have integrated graphics, fall back on that and pull the video card for now...video cards can pull alot of juice.  If you have more sticks of RAM than the minimum to run on then pull some, and swap around. Remove power from the hard drives and boot a live cd distro like knoppix for testing.  Memtest is a recommended utility too, if you can see any errors before it shuts off.  

Do you have an error log in the BIOS setup?  Anything there?  Can you check temps in the BIOS setup right after failure?  Does it feel hotter than hell?  Will it shut off if you just leave it sitting in BIOS setup?

If you are overclocking, go back to stock speeds.

Battery as suggested I suppose is worth a try but usually IME you'd be loosing BIOS settings and date & time vs a shut down.

---

