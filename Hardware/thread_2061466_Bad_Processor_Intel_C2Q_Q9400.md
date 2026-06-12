---
title: "Bad Processor??? Intel C2Q Q9400"
date: 2012-09-22
forum: Hardware
---

### Post by wesleykins on 2012-09-22
So, in my experience, processors are "catastrophic failure" devices;  either they work, or they don't.

However, I seem to have a "bad" processor.

For well over a year, my system hard-freezes when trying to encode h.264 or MPEG-4 ASP (xvid) video, and also randomly from time-to-time, at least weekly.  By "hard-freeze" I mean the cursor doesn't move, numlock won't turn on or off, and I have to hold power button for 4 sec. to turn off the machine.

The processor I'm using is a Core2 Quad Q9400, 2.66Ghz, 1333FSB, running on an Asus P5N-D motherboard (which is a DDR2 board).

I'm running bone-stock, no overclocking or other shenanigans, with the stock Intel HSF with copper core.

Over the past 18 months, I've replaced RAM, Power supply, video cards, upgraded BIOS, tried different hard drives, and more, because it *can't* be the processor, right?

It did this under Windows XP for most of this time, as I only switched to Linux about 3 months ago (a switch I should have made *years* ago).  ...so the problem doesn't seem to be the OS.

I can reliably reproduce the hard-lock within 10 seconds by starting a video encode in [Handbrake]("http://handbrake.fr").

Finally, in frustration, I swapped my CPU out with a Core2 Duo E7300, 2.66Ghz, 1066FSB.

*Problem solved.*

How can this be?

The temperatures of the Q9400 seemed high, climbing to over 60degC just before locking up, so I added a ridiculous Noctua heat-pipe cooler and a Seasonic 650W PSU.  The temp now stays under 42C (wow, what a difference!) but the problem persists with the Q9400.

Am I missing something bone-headed or obvious?

I just noticed (while typing this) the difference in FSB between the Q9400 and the E7300.  The P5N-D motherboard definitely supports 1333FSB.  Could it be a RAM problem?

The RAM is 4 sticks of 2GB DDR2 "800Mhz" RAM, or PC26400.  This is the highest the MB supports, so it should be right.

And this is all *new* RAM.  It did the same thing with an older pair of DDR2 800 RAM sticks.

I'm really stuck.

Any suggestions are appreciated...

-Wes

---

### Post by gordintoronto on 2012-09-22
I could be wrong, but it still sounds like an overheating problem. What version of Ubuntu? Have you installed lm-sensors? Conky? Are there case fans blowing air in the front and out the back?

---

### Post by TenPlus1 on 2012-09-23
Suggestions:

Run a lighter spec Ubuntu to save power, something like Xubuntu or Lubuntu (32-bit)...

If it continues to freeze, use RIGHT ALT + PRINT SCREEN + O to safely shut down the system...

Processors should be able to stand up to high temperatures in excess of 70c before the motherboard takes over and shuts it off (check bios settings), but freezing the system makes it seem like something else...

---

### Post by wesleykins on 2012-09-23
> **gordintoronto said:**
> I could be wrong, but it still sounds like an overheating problem. What version of Ubuntu? Have you installed lm-sensors? Conky? Are there case fans blowing air in the front and out the back?

Thanks for the suggestions.  I am running lm-sensors, and it says CPU temp is around 43C, 120mm exhaust fan blowing out the back, no intake fan...  my "Ubuntu" version is Debian Wheezy :redface: but I was already a member of this community, and it used to do this with Windows XP as well, so I don't see how that could be it...  I am running a full Gnome desktop, though.

> **TenPlus1 said:**
> If it continues to freeze, use RIGHT ALT + PRINT SCREEN + O to safely shut down the system...

Processors should be able to stand up to high temperatures in excess of  70c before the motherboard takes over and shuts it off (check bios  settings), but freezing the system makes it seem like something else... 	

Thanks for the shutdown tip.  I don't really think it's the temperature either.  I did, but with this new Noctua HSF it barely get's above 40C with me continuously refreshing "sensors" and watching the temp until it freezes.

I know this isn't a "fix my computer" forum, but I appreciate the help.

-Wes

---

### Post by gordintoronto on 2012-09-23
Right you are, a temperature in the 40s is not "overheating."

If the system crashes in both Windows and Debian, there might be a problem with the memory. Can you boot from a LiveCD and run memtest overnight?

---

