---
title: "CPU overclocked, but doesn't seem to recognize"
date: 2011-08-05
forum: Hardware
---

### Post by Neutrosider on 2011-08-05
Hello :)
I Overclocked my E6600 from 2,4 GHz to 3,21 GHz, and it's also shown while booting, but when i open the cpu information window of the nvidia sysinfo software it shows my cpu runs either at 1596 MHz (when no "big" software is open) or at  2394 MHz (for example when a game is running). I never saw it showing any other frequency, although its overclocked at 3.21 GHz.

is this a mistake of the software or is ubuntu just ignoring that my cpu is overclocked?

---

### Post by Neutrosider on 2011-08-06
*PUSH*

does someone know?

---

### Post by headvampyre@hotmail.co.uk on 2011-08-06
Have you got Intel SpeedStep enabled? SpeedStep automatically downthrottles your CPU unless its under a heavy usage when it will throttle it to the highest clock speed. Also, whats your CPU multiplier? It should be the highest value to use the highest CPU clock possible.

---

### Post by Neutrosider on 2011-08-06
thanks. ill check that after dinner (its 20:13 here in germany) :)

---

### Post by headvampyre@hotmail.co.uk on 2011-08-06
Okay :) I'll be on to help until about 5am for you then(UK) :) That should sort it tho :)

---

### Post by Neutrosider on 2011-08-06
my multiplier is at 9. i can chosse between 6,7,8 and 9. so its at its highest value. SpeedStep was really enabled. I disabled it and now the nvidia sysinfos shows me my cpu is at 3204 MHz :) btw my FSB is at 356.

the describtion on the right told me that speedstep would allow the OS to set the CPU frequency. Does that mean that ubuntu controls it? because i always thought it would be controlled by the BIOS.

---

### Post by gordintoronto on 2011-08-06
If you keep your CPU at its highest speed, it uses more electricity and generates more heat than it needs to. Heat is what kills computers.

---

### Post by Neutrosider on 2011-08-06
thanks. i know, but will ubuntu be able tu use the 3,2 GHz if speedsteps is activated?

---

### Post by headvampyre@hotmail.co.uk on 2011-08-07
Yeah, but it'll only throttle when there's a high amount of CPU usage, such as playing games, watching movie's and flash, etc.

---

### Post by Neutrosider on 2011-08-11
i checked that. i startet some games so both cores are at 100%, but nvidia sysinfo still says my cpu runs at 2394 MHz, why? i mean it should have throttled to 3,2 GHz. why is it still alt 2,4 GHz, even if both cores are at 100%?

---

### Post by Neutrosider on 2011-08-12
does anyone has an idea?

---

### Post by Adrastus on 2012-03-19
Bump.

I'm having a similar problem with Core i7 930 OC'd to 3.4 GHz but not showing up in Ubuntu.

---

