---
title: "general hardwares questions"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by raven on 2005-10-05
I have 2 questions on Linux and hardwares in general

1- I have a Bios that do not detect HD larger than 80gig
    a friend told me that Linux does not query the bios and 
    it will detect more than 80gig (cause win does not accept HD
    larger than bios detected HD)
    so if I install a 200gig, even when the bios detect 80gig, when I install
    Linux, it will show 200gig. Is that true ?

2- I have kubuntu installed on a PIII450 and working perfectly
    if I buy a new PC, can I just take my old HD, and install it in the new PC
    or mirror my HD (ghost) does it works automatically, even if it is on a new MotherBoard
    and a new chipset. or it will need to be installed again when you 
    change motherboard (cause drivers issues) ?

---

### Post by John.Michael.Kane on 2005-10-05
Answer to question one:"Yes and No"
The BIOS is used at bootup time.  When booting (eg with LILO or GRUB) the BIOS is needed to load the kernel into memory.  Once the kernel is loaded, then
the BIOS is read for some setup information (more accurately, the CMOS
RAM).  Eventually the kernel is running.  Then the BIOS isn't needed anymore.

Answer to question two: Use of gost has been shaky some have used it with out issues some have not. your best option would be to back up all files you need, and clean install your distro..

I hope this helps....

---

### Post by raven on 2005-10-05
thanx for the reply SD-Plissken
not quiet cause the questions had 2 part (we will forget ghost)
here is my 2 questions again

1- I want to buy a new HD 200gig,
but my bios only detect 80gig
can I install linux on to the HD 200gig and linux would detect 200gig
even my bios detect only 80gig MAX ?

2- I have PC1 and PC2 not identical
PC1 have a Linux install working perfectly
PC2 is a new PC no HD
can I take out the HD of PC1 and install the HD of PC1 into PC2
and if Linux would work ?

---

### Post by John.Michael.Kane on 2005-10-05
depends what distro it is. if it's unbutu or debian based then you should be fine. and should not loose any info at all. some distros are picky about doing that.

---

### Post by raven on 2005-10-05
[QUOTE=SD-Plissken]depends what distro it is. if it's unbutu or debian based then you should be fine. and should not loose any info at all. some distros are picky about doing that.[/QUOTE]

thanx, yes it is kubuntu

---

