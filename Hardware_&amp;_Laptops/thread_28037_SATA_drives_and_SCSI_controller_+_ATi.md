---
title: "SATA drives and SCSI controller + ATi"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by Dinler on 2005-04-18
Hello!

I have installed Ubuntu Warty before and it worked perfect but I can't install Hoary directly from the CD, i must upgrade to Hoary because my drives are not found in the paritition section/part. The new kernel could not find my drives but the old one can...

I am using 2x250GB drives with Intel 82801FB Controller.

PLEASE HELP MEE!

BTW, i am getting MESA when i am running fglrxinfo. I have read at least 100 pages about ubuntu + ati, debian + ati but 3d doesn't work with my X800XT VIVO. I says something about kernel-modules and fglrx when i start Ubuntu!

I am a new member, btw :p
(from Sweden)

I am not an expert so write so i can understand, please  :-?


Thanks!
Dinler

---

### Post by alastair on 2005-04-18
For the SATA drive issue - check your BIOS. It might be that you need to set the BIOS to be (perhaps) "legacy" (or similar) for the SATA support. Maybe.

For X - post :

/var/log/Xorg.0.log
/etc/X11/xorg.conf

---

### Post by Dinler on 2005-04-18
[QUOTE=alastair]For the SATA drive issue - check your BIOS. It might be that you need to set the BIOS to be (perhaps) "legacy" (or similar) for the SATA support. Maybe.

For X - post :

/var/log/Xorg.0.log
/etc/X11/xorg.conf[/QUOTE]

I can choose:
RAID
NATIVE
COMPATIBLY (P-ATA: PRIMARY, SECONDARY, DISABLED)
AHCI

If i choose Compatibility mode with Primary, my first drive will be found. If I choose Secondary my second díve will be found and if i choose Disable will both drives be founded but not mine cd/dvd-roms!

 :|

---

### Post by alastair on 2005-04-18
Well ... what about "PATA" mode? Or even (maybe) AHCI?

---

### Post by Dinler on 2005-04-19
[QUOTE=alastair]Well ... what about "PATA" mode? Or even (maybe) AHCI?[/QUOTE]

If I choose AHCI it says sata disk 01 (or something) time out! 
And i cant AHCI becaise if I choose PATA mode to disable cant my cd/dvd-roms be found

---

### Post by ggnore on 2005-04-19
[Check it out](http://ubuntuforums.org/archive/index.php/t-18808.html)

---

### Post by Dinler on 2005-04-19
[QUOTE=ggnore][Check it out](http://ubuntuforums.org/archive/index.php/t-18808.html)[/QUOTE]

So, it's a bug?

Check this out:
[http://dinler.no-ip.com/bios1.JPG](http://dinler.no-ip.com/bios1.JPG)
[http://dinler.no-ip.com/bios2.JPG](http://dinler.no-ip.com/bios2.JPG)

But the questition is, why are native sata supported in warty and not in hoary?

Please, i will run Ubuntu Hoary so early i can   :|

---

### Post by Dinler on 2005-04-19
[QUOTE=Dinler]So, it's a bug?

Check this out:
[http://dinler.no-ip.com/bios1.JPG](http://dinler.no-ip.com/bios1.JPG)
[http://dinler.no-ip.com/bios2.JPG](http://dinler.no-ip.com/bios2.JPG)

But the questition is, why are native sata supported in warty and not in hoary?

Please, i will run Ubuntu Hoary so early i can   :|[/QUOTE]

Come on!  ](*,)

---

### Post by olvesh on 2005-04-19
[QUOTE=Dinler]So, it's a bug?

Check this out:
[http://dinler.no-ip.com/bios1.JPG]("http://dinler.no-ip.com/bios1.JPG")
[http://dinler.no-ip.com/bios2.JPG]("http://dinler.no-ip.com/bios2.JPG")

But the questition is, why are native sata supported in warty and not in hoary?

Please, i will run Ubuntu Hoary so early i can   :|[/QUOTE]

I would say it is a bug.
I am able to boot a system using 2.6.8, but not kernel 2.6.10 (hoary default), that is all I know. I guess that this is a kernel configuration issue, as some modules needed for mounting/accessing my sata-drives are not in the initrd image. 

By using legacy mode, I can access my sata-drives as old-fashioned p-ata drives, but since my system already has two cd/dvd drives, one at each ide channel,  I have to mess around moving both cd/dvd-drives to one ide-channel, and map the drives to the other one (only two ide-channels can be mapped, so I have to disable one of the real channels to be able to reach both disks. 
So suggesting using legacy(compatible) mode is not acceptable to me.

I tried AHCI, and it works in 2.6.11 but that kernel is not stable for hoary (yet).  
This bug has existed in later versions of the 2..9 and 2.6.10 kernels, I have brought some light to it on mailing lists, and in the forums, but there seem to be little knowledge about how to fix the problem...

Now  I am stuck with a hoary installation with 2.6.8 kernel...

Bottom line - I have a system with fairly new hardware, and it has stopped working as it did in earlier versions, I'll call that a bug any day.

Hope someone can help us with this.. 

Thanks for being patient with my rants

Olve

---

### Post by Dinler on 2005-04-20
[QUOTE=olvesh]I would say it is a bug.
I am able to boot a system using 2.6.8, but not kernel 2.6.10 (hoary default), that is all I know. I guess that this is a kernel configuration issue, as some modules needed for mounting/accessing my sata-drives are not in the initrd image. 

By using legacy mode, I can access my sata-drives as old-fashioned p-ata drives, but since my system already has two cd/dvd drives, one at each ide channel,  I have to mess around moving both cd/dvd-drives to one ide-channel, and map the drives to the other one (only two ide-channels can be mapped, so I have to disable one of the real channels to be able to reach both disks. 
So suggesting using legacy(compatible) mode is not acceptable to me.

I tried AHCI, and it works in 2.6.11 but that kernel is not stable for hoary (yet).  
This bug has existed in later versions of the 2..9 and 2.6.10 kernels, I have brought some light to it on mailing lists, and in the forums, but there seem to be little knowledge about how to fix the problem...

Now  I am stuck with a hoary installation with 2.6.8 kernel...

Bottom line - I have a system with fairly new hardware, and it has stopped working as it did in earlier versions, I'll call that a bug any day.

Hope someone can help us with this.. 

Thanks for being patient with my rants

Olve[/QUOTE]

WORD!
(...again)

---

### Post by Dinler on 2005-04-20
Can some Ubuntu developer or crew tell us when or if this bug will be solved?
I have some Ubuntu cd's order but can't use them...

I'm open for tips:
hamdidinler [at] hotmail [dot] com

---

