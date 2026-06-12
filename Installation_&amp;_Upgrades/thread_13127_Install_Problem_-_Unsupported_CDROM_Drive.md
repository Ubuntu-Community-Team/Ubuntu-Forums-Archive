---
title: "Install Problem - Unsupported CDROM Drive"
date: 2005-01-29
forum: Installation &amp; Upgrades
---

### Post by nzjrs on 2005-01-29
Hey,

I just tried to install UBUNTU and failed ;-(. The installation had only just begun, before a message appeared saying the the CR/ROM could not be detected / the drive was un supported. There was also an option to create a boot floppy at this point.

The live CD failed to work also.

My system is a relatively new Shuttle SB75G2 with a Sony DRU-710A Dula Layer DVD Writer.

I was wondering what I should do now? Is there another installation option??

John

p.s. I do not have a floppy drive. Should I temporrilly replace my CDROM drive for installation, and swap it back in later? with the booted UBUNTU support the drive?

---

### Post by nzjrs on 2005-01-29
Anyone - A friend told me an install from network may work around this - any ideas?

---

### Post by mattisking on 2005-02-01
I wish I could help you. I wish someone would respond. I've tried to answer the same question, even on the mailing lists with no response. It's frustrating. I also have a relatively new ABIT Digidice, much along the same lines as your Shuttle and I have the same problem. I want to try Ubuntu on my MAIN PC but I can't get it to install. So, Windows remains my main OS. Ubuntu runs on my old PC very nicely. Ah well.

---

### Post by ?eter on 2005-02-02
I think you might be both having the same problem I am.

If you are running a SATA HDD with IDE emulation, you will not be able to detect your Cd-ROM.

No-one seems to be able to help with a simple solution to it (I read something about re-compiling the kernel). But it is a known bug and will hopefully be fixed for the next release.

?eter

---

### Post by Ray Hamilton on 2005-02-02
I have a similar problem.  I don't have a SATA drive.  My PC is at least 3 years old and so  has no fancy new hardware.  I have installed Mandrake 9.0 and 10.0 successfully and was looking to replace it.

---

### Post by nzjrs on 2005-02-05
I tried about half a dozen more times, and couldnt get it to work. 

I even went and bought a SATA to PATA adapter and this time the installer froze at 91%.

Do you think the solution posted at 

[http://www.ubuntuforums.org/showthread.php?t=11678&highlight=sata](http://www.ubuntuforums.org/showthread.php?t=11678&highlight=sata)
(Near the bottom)

is a work around (in my case). Althoug i realy want to see it work for everyone.

How bout a network install?

---

### Post by phorim on 2005-02-05
[QUOTE=?eter]I think you might be both having the same problem I am.

If you are running a SATA HDD with IDE emulation, you will not be able to detect your Cd-ROM.

No-one seems to be able to help with a simple solution to it (I read something about re-compiling the kernel). But it is a known bug and will hopefully be fixed for the next release.

?eter[/QUOTE]
 
I just fixed this on my machine!  

I had some incorrect settings in the BIOS for my hard drive controllers.  My BIOS is obviously different than most, but for my MSI NEO2, I went to "Integrated Peripherals" -> "On Chip IDE Configuration" and set "ATA Configuration" to "S-ATA Only", set "On-Chip ATA(s) Operate Mode" to "Native Mode" set "P-ATA Keep Enabled" to "Yes".

My current setup is booting off a SATA drive, with my CDROM on the PATA controller.  Before I made the changes, my "On Chip IDE Configuration" was set to "P-ATA + S-ATA".  I thought I needed this because I had both types of drive.  I was wrong.

With these changes, my system now screams!  It brings up Grub in 1/20th the time it was taking previously.  I'm betting that some problems I was having with Mepis are now over as well, but I haven't tried to reload it yet.

I hope this helps someone.

Cheers,
Jim

---

### Post by arthureggplant on 2005-02-05
I have basically the same hardware. I was able to fix this problem with the following: 

1. boot up installer as normal
2. Choose Language
3. Skip to tty2 by hitting alt-F2
4. do:

    insmod /lib/modules/2.6.xxxxx/kernel/drivers/cdrom/cdrom.ko
    insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-core.ko
    insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-generic.ko
    insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-cd.ko
    insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-core.ko


5. Return to tty1 by hitting alt-F1
6. Continue as usual loading other modules after the above are in place.

I got this from a bug fix forum, and it wasn't quite right, but the above worked for me (i just installed and am typing from ubuntu)

---

