---
title: "radeon 9800 playing graffitti when playing video files"
date: 2009-02-21
forum: Hardware
---

### Post by johnnyhop on 2009-02-21
I just replaced a radeon 7200 with a radeon 9800 pro AGP display adapter. The 7200 worked fine while the 9800 gives higher screen resolution it displays annoying light green horizontal bars on the Kubuntu boot screen, thin horizontal lines at random spots on the desktop screen and very annoying "graffiti" while viewing video files. On line streaming in Firefox (Youtube and the like) is fine. After installing the fglrx driver the desktop lines went away.  Any suggestions for ridding the graffiti in the video files playback?

---

### Post by 00b00nt00 on 2009-02-25
Boot from the Kubuntu live CD. Same results?

---

### Post by happycube on 2009-02-25
That sadly sounds like a potential hardware issue - particularly memory related.

The 9800pro is far more demanding on power supplies than a 7200.  If the PSU is marginal or low end that could glitch the card.  Also check the AGP settings, especially if you have a non-intel chipset.

Check the fan, and if it's been stopped for a while the card might've cooked itself. :(  These cards are pretty old now, and being high end the components eventually break down.

I agree that trying a live CD is always a good sanity check, too.

---

### Post by johnnyhop on 2009-02-25
SOLVED! A hardware connectivity issue.  I used a contact cleaner on the copper traces that plug into the AGP slot, likewise on the RAM cards.  Thank you happycube for suggesting hardware issue.  And yes the power supply needs to be adequate.  With three hard drives I chose a 500 watt power supply to allow room for expansion.

---

