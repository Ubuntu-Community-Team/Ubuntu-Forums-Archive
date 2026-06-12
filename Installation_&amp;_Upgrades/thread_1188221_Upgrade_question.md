---
title: "Upgrade question"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by kd0afk on 2009-06-15
I am using Ubuntu 9.04 and I like it but I really can't see any difference between 8.10 and 9.04 except for the fact that I can't run Blender now and there are some other graphics issues. My question is, if an upgrade is going to downgrade a pretty important part of a laptop or desktop computer, namely the graphics (if graphics weren't important then why don't we just go back to DOS) why is it released before ALL of the effects on the graphics are investigated and tested clean? If it is just in order to meet a release deadline, let me ask another question, if you went to buy a new car and you crashed it because the brakes weren't installed you probably would be pretty upset, I know I would be. And if the reason they didn't install the brakes was because they had to roll the car off the assembly line on time....... I think you get the point.

---

### Post by reclinerspud on 2009-06-15
I agree This has happend to me several times.

---

### Post by raymondh on 2009-06-15
> **kd0afk said:**
> I am using Ubuntu 9.04 and I like it but I really can't see any difference between 8.10 and 9.04 except for the fact that I can't run Blender now and there are some other graphics issues. My question is, if an upgrade is going to downgrade a pretty important part of a laptop or desktop computer, namely the graphics (if graphics weren't important then why don't we just go back to DOS) why is it released before ALL of the effects on the graphics are investigated and tested clean? If it is just in order to meet a release deadline, let me ask another question, if you went to buy a new car and you crashed it because the brakes weren't installed you probably would be pretty upset, I know I would be. And if the reason they didn't install the brakes was because they had to roll the car off the assembly line on time....... I think you get the point.

I will not speak in behalf of the devs or canonical.  I prefer to give them the benefit of the doubt in return for making a distro I like to use.  

My thoughts on this subject revolves around the drivers that manufacturers put out to make our specs work.  Note that when a manufacturer decides NOT to support a specific applinace they have with the necessary drivers per kernel we use ... then we, in open source, have trouble and are forced to come up with workarounds which may or may not work ... hence a lot of frustrations and hair pulled.  Some manufactureres are linux-friendly and provide the essential drivers for our equipment and kernel use.  Some are not.  That is what I think is critical.

Because of that, I always prefer to test the version in live session mode first to see if it reacts well with my hardware specs.

Just my 2 cents worth of opinion.  No flame wars intended.

---

### Post by kd0afk on 2009-06-15
> **raymondhenson said:**
> I will not speak in behalf of the devs or canonical.  I prefer to give them the benefit of the doubt in return for making a distro I like to use.  

My thoughts on this subject revolves around the drivers that manufacturers put out to make our specs work.  Note that when a manufacturer decides NOT to support a specific applinace they have with the necessary drivers per kernel we use ... then we, in open source, have trouble and are forced to come up with workarounds which may or may not work ... hence a lot of frustrations and hair pulled.  Some manufactureres are linux-friendly and provide the essential drivers for our equipment and kernel use.  Some are not.  That is what I think is critical.

Because of that, I always prefer to test the version in live session mode first to see if it reacts well with my hardware specs.

Just my 2 cents worth of opinion.  No flame wars intended.

I agree fully, but, if a driver or something works on a distro then don't mess with it. What is the phrase? If it aint broke don't fix it.
Also, it is kind of hard to test EVERYTHING about a distro before installing it.
I like the program Blender and it worked when I tried the live cd of 9.04 but when I installed it, it messed up. NOBODY has replied to my thread about it but that is a whole other bitch I have. I've been trying to get it fixed for about a month now.

---

### Post by raymondh on 2009-06-15
> **kd0afk said:**
> I agree fully, but, if a driver or something works on a distro then don't mess with it. What is the phrase? If it aint broke don't fix it.


As I (agree) with you. 

I believe (too) that as the kernel grows and upgrades, it is meant to grow to a more efficient kernel whilst keeping it light.  Remember that our OS (ubuntu, for you and I) came from an .iso file that is only 700mb (give or take).  That ..... "lightness".... is one of the advantages I like about linux/Ubuntu.  Compare this to win7 which started at 14GB (at beta) and about 12GB (RC).  At the release date, It may be about 10-12 GB heavy.  What I am trying to say is that it is unfortunate for us as we have to struggle when our 'ain't broke' drivers and kernels are no longer there when a new version comes out ..... but if canonical releases a kernel/OS that will encompass everything ... it might be GBs' heavy and thus we lose the advantages (percieved or real) of having a "light" OS.

Care to share the thread you had about your blender issue?  I am no expert hence cannot give promises except that I will look at it and give it a try :)

---

### Post by raymondh on 2009-06-15
As a side note (twist) to this .... and to minimize more hair-pulling for me, I have gotten to install a working version on one HD while another release on another drive.  I put the new release on the second drive so I can work at it while/without losing my main working version.

I am just sharing this because I have come to expect that each version release will have some birthing pains and this is my way to cope with the matter.  I use a 2 drive set-up so I can always boot into either.  Of course, this is moot if I only have 1 HD.

Just sharing while waiting for your link. :)

---

### Post by kd0afk on 2009-06-15
Here is the link.
[http://ubuntuforums.org/showthread.php?p=7461863#post7461863](http://ubuntuforums.org/showthread.php?p=7461863#post7461863)

---

### Post by raymondh on 2009-06-15
> **kd0afk said:**
> Here is the link.
[http://ubuntuforums.org/showthread.php?p=7461863#post7461863](http://ubuntuforums.org/showthread.php?p=7461863#post7461863)

Hello,

Following your link as well as the sub-links ... what fixes have you tried so far?

---

### Post by kd0afk on 2009-06-15
> **raymondhenson said:**
> Hello,

Following your link as well as the sub-links ... what fixes have you tried so far?

Tried the Jaunty Intel guide: [http://ubuntuforums.org/showthread.php?p=7461982#post7461982](http://ubuntuforums.org/showthread.php?p=7461982#post7461982)
I am still trying to figure out how to change the settings on my graphics card.
Here are my stats:
System information report, generated by Sysinfo: 6/15/2009 2:59:08 PM
[http://sourceforge.net/projects/gsysinfo](http://sourceforge.net/projects/gsysinfo)

SYSTEM INFORMATION
    Running Ubuntu Linux, the 5.0 release.
    GNOME: 2.26.1 (Ubuntu 2009-05-06)
    Kernel version: 2.6.28-11-generic (#42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009)
    GCC: 4.3.3 (i486-linux-gnu)
    Xorg: unknown (24 May 2009  12:33:40AM) (24 May 2009  12:33:40AM)
    Hostname: HAL
    Uptime: 0 days 0 h 33 min

CPU INFORMATION
    GenuineIntel, Intel(R) Celeron(R) M processor         1.50GHz
    Number of CPUs: 1
    CPU clock currently at 1496.269 MHz with 1024 KB cache
    Numbering: family(6) model(13) stepping(8)
    Bogomips: 2992.53
    Flags: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts

MEMORY INFORMATION
    Total memory: 481 MB
    Total swap: 1419 MB

STORAGE INFORMATION
    SCSI device -  scsi0
        Vendor:  ATA      
        Model:  HTS541040G9AT00  
    SCSI device -  scsi1
        Vendor:  MATSHITA 
        Model:  UJDA760 DVD/CDRW 

HARDWARE INFORMATION
MOTHERBOARD
    Host bridge
        Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Toshiba America Info Systems Device 0001
    PCI bridge(s)
        Intel Corporation 82801 Mobile PCI Bridge (rev 83)
        Intel Corporation 82801 Mobile PCI Bridge (rev 83)
    USB controller(s)
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
        Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
        Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
    ISA bridge
        Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
    IDE interface
        Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Device 0001

GRAPHIC CARD
    VGA controller
        Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Toshiba America Info Systems Device 0005

SOUND CARD
    Multimedia controller
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Toshiba America Info Systems Device 0412

NETWORK
    Ethernet controller
        Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
        Subsystem: Toshiba America Info Systems Device 0001
    Modem
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
        Subsystem: Toshiba America Info Systems Device 0001

---

### Post by raymondh on 2009-06-15
Let me research a bit in launchpad .... they may have a fix already ...... also, i will log-off for about 2 hrs. as I need to pick up my kids.  Will check back.

---

