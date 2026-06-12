---
title: "How to move PCMCIA to initialize sooner in BOOT sequence?..."
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by trapix22 on 2007-05-27
The PCMCIA card is the LAST thing that gets loaded before the login prompt. I would like to have it initialized sooner in boot process. I'm trying to have USB mount a directory during boot. When it's plugged into USB 1.1 (original on motherboard) IT WORKS fine. When I plug it into pcmcia USB 2.0 (upgrade), the directory is NOT mounted.

-  My research came up with "modify init.d/PCMCIA script" - but my script doesn't have the "chkconfig: 2345 9 96" line those help files call for.

or... 

- "Change the "S20pcmcia" or "S40pcmcia" to a lower number - but none of my "rcX.d" have the "S20pcmcia" or "S40pcmcia" line.

Maybe I just need more simplified instructions. I'd really appreciate the help. Thank you.

---

### Post by trapix22 on 2007-05-29
THIS IS AN UPDATE...

I've re-named pcmcia link to load earlier (from S40 to S20) but that didn't solve it.

What happens is that when I plug the USB into to old USB 1.1 port (orig on motherboard) it works fine. Prompt for LUKS password shows up and continues booting flawlessly. When I plug it into the PCMCIA USB 2.0 card, the card is recognized but the USB dir is not mounted and there is no prompt for password. I get told to "press ctrl+D to continue" or "enter root password for maintenance". And I have no clue where to look next.

I've run into a bunch of articles with similar problems... but no solutions. Anyone? Thank you.

---

### Post by kaptengu on 2007-09-22
Did you find a solution to this problem?
I want to do a similar thing with a SD-card.

---

