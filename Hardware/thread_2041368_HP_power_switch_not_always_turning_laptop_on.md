---
title: "HP power switch not always turning laptop on??"
date: 2012-08-12
forum: Hardware
---

### Post by st2000 on 2012-08-12
Hi,

Not sure if this is an HP-hardware, Ubuntu or (I think Ubuntu 12.04 uses) Grub problem.  But thought I'd try here in the Ubuntu forums first.

I've a brand new HP Pavilion G6 laptop.  I have noticed that, from power off, pressing the power switch does not always keep the laptop powered on.  If I hold the button momentarily, the power LED and fan just power down when I let go.  I have to hold the power switch for several seconds for the laptop to stay powered on!  Which is a bit tricky.  Because if I hold the power switch for too long (about 5 seconds) the laptop will just power down anyways.  Probably by using some sort of failsafe power down timer built into the power supply electronics.

Is this normal?  Is there something missing from Ubuntu or Grub that keeps the power supply on in HP laptops?  

I'm a bit on edge as I've only days before this HP laptop will slip from being a "simple return & replace" fix to the "HP technical support realm".

-thanks

---

### Post by Paddy Landau on 2012-08-19
This sounds like a hardware problem. After just 5 seconds, it is likely that the laptop is still going through the hardware power-up checks and that the software has not yet been given control.

---

### Post by st2000 on 2012-08-19
I would agree except the behavior is inconsistent.  The laptop powers up to the booting process about half of all power on events.  Note, subjective as this observation may sound, that the failed power on events are clumpy.  That is, if the laptop fails to make it to the booting process, it will likely fail several more times before success.  So, one might have problems turning on the computer for one several hour session, followed by being able to turn on the computer as expected for, say, 3 other several hour sessions.  Giving rise to my comment that about half of all power on events results in never making it to the boot up.

So, if it is a hardware problem, it is random.

-thanks

---

### Post by Paddy Landau on 2012-08-19
Hardware problems can indeed be random. I have an old laptop whose screen  started to fail a couple of years ago — it was always random as to  whether the screen would work or not after booting. Finally, after a couple of years, it stopped  working altogether (and suddenly worked, just once, a couple of months ago!).

Take out a stopwatch.
Time how long it takes (on a successful boot) to get past the BIOS hardware check.
Time how long it takes (on a failed boot) to power down.

That should help you find out whether or not the software has taken control yet.

If the software has not taken control, it could be the hardware or BIOS.
If the software has taken control, it could the hardware, BIOS or software.

---

