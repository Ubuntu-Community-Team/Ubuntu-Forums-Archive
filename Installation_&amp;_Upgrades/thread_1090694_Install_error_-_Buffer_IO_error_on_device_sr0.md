---
title: "Install error - Buffer I/O error on device sr0"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by nekorb on 2009-03-08
Hi,

When trying to install Ubuntu 8.10 amd64, the install fails to start as I get the following error:

end_request: I/O error, dev sr0, sector xxxxxx
Buffer I/O error on device sr0, logical block xxxxx 
end_request: I/O error, dev sr0, sector xxxxxx
Buffer I/O error on device sr0, logical block xxxxx 
end_request: I/O error, dev sr0, sector xxxxxx
Buffer I/O error on device sr0, logical block xxxxx 
[it goes on & on...]

I got a few good results from these forums & Google but nothing has seemed to help so here is the situation & what I've tried - I always get the same error unless stated otherwise:

- It is a new PC - Intel Quad core, Supermicro C2SEA mobo, SATA DVD drive & HDD.
- Downloaded the amd64 ISO twice (different mirrors to) & burned it once per download.
- Using the IDE DVD drive from old PC (which works fine with Ubuntu 8.10 x86 on my old PC) on the new PC.
- Using the Ubuntu 8.10 x86 CD on the IDE & SATA DVD drive on the new PC.
- Kubuntu 8.10 x86 gives the same error (I had the CD floating about).
- Boot options I've tried various combos of the ones you get when you press F6, such as noapic, nolapic, acpi=off, acpi=noirq. With noapic, nolapic & acpi=off I got a new error before the one I'm posting about appears, it said "BIOS bug APIC #0 not detected. Forcing use of dummy APIC emulation".
- In the BIOS - changed APCI from 2.0 to 1.0 (no option to disable it). Setting the DVD drive to UDMA0 from UDMA2. Disabling all unused ports (serial, paralell, all the PCI, onboard VGA). Reset BIOS to safe defaults.
- Installing Debian 5 & Fedora 10 (both amd64) work fine. I like to try a few distros now & then but want to stick with Ubuntu as I am familiar with it & could get everything working how I like it.

So I've tried different media, eliminated hardware as best as poss & changed boot options & BIOS settings the best I can. I have a hunch it's something with the installer not liking something on the mobo but am out of ideas.

Any suggestions welcome, as you can see I am pretty happy to try anything & it's annoying me so I want to solve this!

Cheers,
Antony

---

### Post by cariboo on 2009-03-08
I get the same error if I burn the ISO at to fast a speed. I would suggest burning the ISO at the slowest speed possible, my 2 year old dvd burner will still burn a 4X.

Jim

---

### Post by Neo_The_User on 2009-03-08
> **cariboo907 said:**
> I get the same error if I burn the ISO at to fast a speed. I would suggest burning the ISO at the slowest speed possible, my 2 year old dvd burner will still burn a 4X.

Jim

What he said.

---

### Post by nekorb on 2009-03-09
Thanks, burned at 1x & still same problem with this disk :(

---

### Post by jtu on 2009-03-09
I've had this same problem in spades, usually with the 8.10 alt CD. I've burned it on 3 different machines, 2 different types of CDR disks, and tried using the CDs on 4 drives (one machine has 2) and every time when I try to check CD integrity it fails, usually with the same error msg (sector numbers different from the live CD). The sector numbers are more or less the same every time it fails, regardless of where the CD was burned or where it was tested.

The only common factor is that all the burning was done under OS/2 using cdrecord. I have XP partitions on 2 of the 3 machines, but no burner program for WIN, and I'm trying to create an initial Linux partition so there are no other options (other than booting from the live CD).
:(

---

### Post by jtu on 2009-03-09
I should mention that the burns were done at slow speeds.

---

### Post by Neo_The_User on 2009-03-09
Remember, sr0 is the nickname for its real device (/dev/scd0)

---

### Post by nekorb on 2009-03-10
@jtu - I'd recommnend CDburnerXP if you need burning software for Windows, it's free & does what I need it to. 

NB. I have burned using this & also Nero on a laptop & same error. I'm sure it's a compatibiliy issue rather than media from the amount of burns I've tried. Other distros work fine as well. Maybe I'll just stick with Debian 5 as that's working OK, apart from the Nvidia drivers.

---

### Post by jtu on 2009-03-10
Burning a dvd won't help me much because the machine where I want to install only has CD drives.

However, what flags are needed for dvddao?

---

### Post by Neo_The_User on 2009-03-10
/etc/fstab output along with all the other stuff:

```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Re-connect your CD-ROM drive's PATA or SATA connector and see if that helps.

---

### Post by jtu on 2009-03-10
> **jtu said:**
> Burning a dvd won't help me much because the machine where I want to install only has CD drives.

However, what flags are needed for dvddao?

> **Neo_The_User said:**
> /etc/fstab output along with all the other stuff:

```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I meant was anything additional needed to make the DVD bootable, or is that all in the iso?

tnx

---

### Post by Neo_The_User on 2009-03-10
> **jtu said:**
> I meant was anything additional needed to make the DVD bootable, or is that all in the iso?

tnx

I'm lost, sorry. Please explain what you mean.

---

### Post by l3east on 2009-03-10
Omg im getting this stupid error too.I really want ubuntu :( i have a hp nc6230

---

### Post by avtolle on 2009-03-10
> **jtu said:**
> I meant was anything additional needed to make the DVD bootable, or is that all in the iso?

tnx
The DVD will be bootable, if the md5sum of the iso is correct, it is burned as an image at low speed, and your computer is set to boot from CD/DVD. There is no need for a "boot floppy", etc., to boot from the CD (or DVD, in your case).

And, if your drive is operating correctly.

---

### Post by pot_pie on 2009-03-24
I was getting this same error installing Ubuntu 8.10 Server 64 from a CD burned at 48x. I reburned at 12x Disc-at-Once/96 in Nero and the install then went through without issue.

---

### Post by The Pinny Parlour on 2009-03-25
I'd say the common theme us that your all using Samsung optical drives?  I get this error all the time whenever I use Samsung optical drives.  The one I get errors with right now is: TS-H653

---

