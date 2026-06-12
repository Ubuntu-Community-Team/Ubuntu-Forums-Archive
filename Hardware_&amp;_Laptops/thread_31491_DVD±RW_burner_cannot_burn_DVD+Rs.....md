---
title: "DVD±RW burner cannot burn DVD+Rs...."
date: 2005-05-03
forum: Hardware &amp; Laptops
---

### Post by matid on 2005-05-03
Suddenly my DVD±RW burner stopped burning DVD+Rs... When I insert DVD+R disc into the drive it appears on the Desktop as CD-ROM Disc and I cannot burn it. CD-R discs are recognised ok, they appear as Blank CD-R and I can burn w/o any problems.
Do you know how to fix it?

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=matid]Suddenly my DVD±RW burner stopped burning DVD+Rs... When I insert DVD+R disc into the drive it appears on the Desktop as CD-ROM Disc and I cannot burn it. CD-R discs are recognised ok, they appear as Blank CD-R and I can burn w/o any problems.
Do you know how to fix it?[/QUOTE]

Use k3b


[http://www.ubuntulinux.org/wiki/K3BHowto/view?searchterm=k3b](http://www.ubuntulinux.org/wiki/K3BHowto/view?searchterm=k3b)

---

### Post by matid on 2005-05-04
[QUOTE=poofyhairguy]Use k3b[/QUOTE]
I don't like K3B. It's Qt application, moreover I prefer simple apps.
---
I've checked K3B. It gives me ':-( unable to WRITE@LBA=0h: Input/output error' and ':( write failed: Input/output error' when I try to burn DVD.

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=matid]I don't like K3B. It's Qt application, moreover I prefer simple apps.
[/QUOTE]

Did you try Gnomebaker?

Is in the universe.

sudo apt-get install gnomebaker

---

### Post by matid on 2005-05-07
[QUOTE=poofyhairguy]Did you try Gnomebaker?

Is in the universe.

sudo apt-get install gnomebaker[/QUOTE]
Save problem, even with growisofs:

:-( unable to WRITE@LBA=0h: Input/output error
:-( write failed: Input/output error

---

### Post by angrykeyboarder on 2005-05-08
Just out of curiosity ,have you been able to burn DVDs with this hardware under a different operating system (e.g. another Linux distro, BSD or Windows)?

Cuz if not, it may be a hardware problem.

Just a thought...

---

### Post by vyusseem on 2005-11-28
Same problrem here. Common let's resolve it. here is my log:
System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
LG CD-ROM CRD-8520B 1.00 (/dev/hdc, ) at /media/cdrom0 [CD-ROM] [Error] [None]

DVD+R/RW DX082D 11SB (/dev/hdd, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD+R; DVD+RW] [DVD-ROM; DVD+RW; DVD+R; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96R; RAW/R16; RAW/R96R]
K3b
-----------------------
Size of filesystem calculated: 1654011

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv
growisofs: 5.21

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdd obs=32k seek=0'
/dev/hdd: "Current Write Speed" is 8.2x1385KBps.

392429568/3387414528 (11.6%) @0.0x, remaining 35:14
:-( unable to WRITE@LBA=2ec80h: Input/output error
:-( write failed: Input/output error
/dev/hdd: flushing cache
:-( unable to FLUSH CACHE: Input/output error
:-( unable to SYNCHRONOUS FLUSH CACHE: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/hdd=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1654011 -dvd-compat -speed=4

---

### Post by OldSeaDog on 2005-11-28
I have been facing nightmares with my combination of drives as well, so you have my sympathy.  One problem I ran into quite early is that DVD writeable drives want to be Master on the IDE channel.  I can't tell for sure, but is it possible that your CDwriter is Master and your DVDwriter is slave?  You may want to check the order they are on the cable and the jumpers.

---

### Post by vyusseem on 2005-11-28
Hi OldSeaDog,
This CAN BE!
My Master is CD-ROM and DVD-writer is slave! I'll try to switch, thank you!
Oh, what I wouldn't do - just not back to Windows!

---

### Post by vyusseem on 2005-11-29
WAS:

OldSeaDog,
That's it! 
Thank you! Thank you!

AFTER EDIT:
same :)))))))))

---

### Post by vyusseem on 2005-11-29
Sorry to say that, but it worked on one DVD only. I tried another 4 they all failed woth same error :( 
Someone please help!

---

