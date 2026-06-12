---
title: "Cannot install edgy on P4M800PRO-M"
date: 2006-12-01
forum: Hardware &amp; Laptops
---

### Post by azelter on 2006-12-01
I have been trying to install edgy (32bit) on the following system:
ECS P4M800PRO-M V2.0 motherboard with a Core 2 Duo 6300 processor
2 X 1 GB sticks DDR2 4200 RAM
Maxtor 200GB HD

So far I have had no success. If I enable verbose mode, I seem to get as far as the line:
squashfs: version 3.0 ...

I tried dapper and also cannot install. I successfully installed Windows Vista RC1 (not that I want it). The only versions of Ubuntu I can get to work is the Gnome 2.10 Live CD which runs kernel 2.6.10-4-386 (like breezy).

If anyone has any ideas of things I could try or check to try to get this system working I would be very grateful. Looking on the net, it does seem that people are running edgy on the same motherboard though, so I am confused as to what might be going on.

Thanks in advance!

---

### Post by azelter on 2006-12-08
In case anyone else has this problem, the solution was to set the viseo card shared memory from 32MB to 64MB in the bios. This was needed as I had 2GB RAM not 1 (in which case 32MB would have been correct). That solved the problem. No idea why it didn't affect vista.

---

### Post by kw1502 on 2006-12-09
I am considering buying the same motherboard as it seems to be adequate for my needs and allows me to use some of my existing hardware (ie DDR400 RAM, PATA hard drives, etc). Have you had any other problems with Edgy and the P4M800PRO-M? Are you satisfied with it and Edgy?

Please provide an update on your experiences.
Thanks

---

### Post by bigmax1627 on 2006-12-12
I've been using this Mobo for a few months now but in a very small case so
I bought a new one and it came in today. All I did was
move everything to the new case, but I mistakingly
removed the power switch and the reset switch without
noting their positions and now I'm running into the
same problem as before, MY computer powers up, The
LED's work, My hard drive spins, my processor's heat
sink fan spins and all the CD-Roms turn on  but my
monitor shows NO PICTURE and I hear no beeps. I had
the same problem in the other case and I know
nothing's wrong with the parts because I was using
them yesterday. I just need to know if ou had the same
problem with this motherboard. If so, or even if not, 
how did you place the power switch and reset switch.
Where did you attach the little speaker that comes
with the cases? I read the manual but it does tell you
much...all it has is a diagram. PLLLLEEEAAAASE HELP
ME!
Thanks in advance, 
JEanmax

---

### Post by azelter on 2006-12-13
This board worked fine with edgy in the end. I had to update to the latest bios as well in order to get round a problem with the network device disapeering after the instalation. The flash update solved that and I have had no other problems so far.

---

### Post by kw1502 on 2006-12-13
Thanks for your response. I will likely get this mobo and install Edgy on it.

---

