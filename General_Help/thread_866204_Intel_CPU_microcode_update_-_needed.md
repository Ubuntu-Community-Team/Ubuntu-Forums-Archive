---
title: "Intel CPU microcode update - needed?"
date: 2008-07-21
forum: General Help
---

### Post by Krupski on 2008-07-21
Hi all,

I'm running a RAID-1 file server box using Ubuntu 8.04.1 64 bit server on an Intel DG33BU motherboard (Core 2 Duo E6700 cpu) flashed with the latest bios (v0437 - 21 May 2008 ).

The bios update clearly shows, among other things, a "processor update" which I assume is a microcode update.

If this is true, does the processor update "stick" when booting into Ubuntu server, or do I need to ALSO install "microcode.ctl" and the appropriate "microcode.dat" file?

Thanks in advance!

-- Roger

---

### Post by fjgaude on 2008-07-22
AFAIK, what you did is all that is required. The microcode goes into the CPU and any software or whatever has nothing to do with it. The BIOS update is all that is needed.

Try it and see... let us know how you are doing.

---

### Post by Krupski on 2008-07-22
> **fjgaude said:**
> AFAIK, what you did is all that is required. The microcode goes into the CPU and any software or whatever has nothing to do with it. The BIOS update is all that is needed.

Try it and see... let us know how you are doing.

Well... from what you said, it seems like I don't need to do it. And, how would I know if it made a difference anyway?

---

### Post by fjgaude on 2008-07-23
I'm sure Linux has some tool to see what the CPU has, but I've never had to use such... the BIOS flash updates have always been all I needed.

Well, see if anything has changed... such microcode has likely to do with an abscure bug in the chip.

My Intel Duo has been a marvel of performance.

---

