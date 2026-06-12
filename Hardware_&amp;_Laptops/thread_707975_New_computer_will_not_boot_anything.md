---
title: "New computer will not boot anything"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by madmatrixz3000 on 2008-02-25
So I just built a new computer ground up except for the HDD from my old desktop.

I went to boot up and I could get to my Opticals, and my Grub menu.  But nothing will boot beyond this point.

Windows gives me a "Starting Up" or similar one line loading screen which lasted for hours.
Ubuntu just goes blank.
My Windows recovery CD gives me a Stop: C0000221 Unkown Hard Error
    \SystemRoot\System32\ntdll.dll

Please help I have no idea what to do to get my PC to boot and cannot afford to have to bring it somewheres.

---

### Post by suibhne on 2008-02-25
What's your internal set-up? is there anything sharing your IDE cable?

---

### Post by madmatrixz3000 on 2008-02-25
booting from SATA

---

### Post by madmatrixz3000 on 2008-02-25
How do I not extend to x64 cause I just need to have x86

---

### Post by oldsoundguy on 2008-02-25
get yourself a boot disk (floppy will do) from [http://www.bootdisk.com/](http://www.bootdisk.com/) and boot up and see if you can even SEE the hard drive.   You may have an issue even as far as cable condition or even LOOSENESS to power.

---

### Post by madmatrixz3000 on 2008-02-25
Definitly can see my HDD I can get to my Grub screen.  However I am extending or expanding or whatever into 64bit mode.  I cannot find the part in bios to stop this

---

### Post by suibhne on 2008-02-25
make sure RAID is disabled 

can you post exactly what it says on your screen?

---

### Post by madmatrixz3000 on 2008-02-26
How would I disable raid and which screen are you talking about?

---

### Post by suibhne on 2008-02-26
> **madmatrixz3000 said:**
> Definitly can see my HDD I can get to my Grub screen.  However I am extending or expanding or whatever into 64bit mode.  I cannot find the part in bios to stop this

1 - what does it say in GRUB about your HDD?

2-If i recollect correctly, you can disable RAID in the BIOS (ie don't set the connector as RAID)

---

### Post by madmatrixz3000 on 2008-02-26
It gives me the same grub load screen as the HDD did in my other PC with my P4

---

### Post by madmatrixz3000 on 2008-02-26
My friend said it was possibly a problem with my RAM not seating correctly/ in the wrong RAM slots.

My MB has RAM slots A1 A2 B1 and B2 where should my 2 1Gb cards go?

---

### Post by suibhne on 2008-02-26
> **madmatrixz3000 said:**
> My friend said it was possibly a problem with my RAM not seating correctly/ in the wrong RAM slots.

My MB has RAM slots A1 A2 B1 and B2 where should my 2 1Gb cards go?

1-try my bios tip first (see below)

2-How much memory have you in total? can you send me a pic of your memory slots? Do you only have 2 gig sticks?

---

### Post by suibhne on 2008-02-26
I mean 'two 1gig sticks'


BTW

As a general rule you need to pair off your memory - either in slots 1 and 3 or slots 2 and 4 - but this can depend on your motherboard

---

### Post by madmatrixz3000 on 2008-02-26
bios tip?

---

### Post by suibhne on 2008-02-26
disable RAID :-)

---

### Post by madmatrixz3000 on 2008-02-26
How?

---

### Post by suibhne on 2008-02-26
via your BIOS - reboot your machine and go into the BIOS before Ubuntu kicks in

---

### Post by suibhne on 2008-02-26
it'll be F1 or F2 or delete - the option will be displayed when you turn your machine on

---

### Post by madmatrixz3000 on 2008-02-26
I went into BIOS setup and could not find any raid settings.  My  MOBO has no Raid Settings

---

### Post by suibhne on 2008-02-26
well, I'm away to bed-

can you post me a detailed description of all your hardware specs? I'll have look tomorrow to see if i can solve your problem

---

### Post by lswest on 2008-02-26
well, quick info on the RAM, usually RAM won't function properly unless they're both in the 1, or the 2 slots (e.g. A1, B1, or A2, B2).  (generally the RAM slots are colour-coded, match up the colours and insert a RAM into each, for example, Grey-Grey instead of Grey-Blue or w/e the colours are)  Hope it helps.  And a last idea: maybe since it's in a new PC it's missing drivers it needs for a specific piece of hardware, preventing it from booting?  just a thought.

*edit* didn't realize someone suggested the RAM bit before, my bad :P

---

### Post by oldsoundguy on 2008-02-26
usually the users manual will have what slots are to be used for ram when there is a multiple choice.  If you don't have a manual, go to the manufacturer's site and download a copy (lot of new laptops don't come with a manual.)  IF not available there, go to the FCC site an plug in the FCC number into the search box.  (on desktops that is the number on the motherboard) Most likely you will find a PDF attached to the general FCC description.

---

### Post by madmatrixz3000 on 2008-02-28
So I was able to boot from an IDE drive so I will install my old SATA PCI card and download the drivers to that cause I know that once that is installed i can boot from that, but I want to run at full 3Gb/s instead of 1.5 like my card will support.

---

### Post by madmatrixz3000 on 2008-02-28
Here are links for my hardware:

MOBO:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813138034](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138034)

SATA HDD:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148215](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148215)

---

### Post by madmatrixz3000 on 2008-02-28
Does anyone know from this bios how to setup my SATA drive with my MOBO

---

### Post by madmatrixz3000 on 2008-02-28
OK so there is an option on my setup disk to "Preinstall 32Bit SATA Raid Driver (F6 during Windows Setup)" is that how to setup my SATA drive w/ the MOBO

---

### Post by madmatrixz3000 on 2008-02-28
Bump

---

### Post by suibhne on 2008-03-02
Can you post the following:

Primary IDE : 
Secondary IDE : 
Third IDE : 

Under the BOOT BIOS column:

1st Boot Device: 
2nd Boot Device: 
3rd Boot Device:


?

---

