---
title: "I need help with ubuntu and windows vista"
date: 2008-11-09
forum: General Help
---

### Post by azv31 on 2008-11-09
Hello guys!

First of all sorry if somebody already asked this, if there is a solution for this please point me in the right direction.

HERE'S MY PROBLEM.

Today I visited the Ubuntu site and realized there was a new version available for download 8.10, so i said to myself "I got get this one" so i did, after that I installed Ubuntu on a USB stick, following the on-screen steps, I chose the right options and all that until I got to the last option "Boot Loader", I chose advanced and I remember there were many option from which

    * Windows Vista longhorn (sd1 , I think?)
    * Windows Vista longhorn (sd2, I think)
    * USB Rally (the one where I installed UBUNTU)

I chose the first option "Windows Vista Longhorn" and the UBUNTU started to install on the usb stick, after installation was done it asked me to restart the computer, eject CD and press enter, I did. And here is where the problem started.
The computer restarted normally but it never loads Windows vista nor UBUNTU, I can't boot to CD, can't access safe mode, I can't boot to anything I only get a BLANK screen with a cursor line. I am only able to acces the BIOS settings.
PLEASE HELP, what can I do?



This my laptop information

Gateway FX
4GB RAM
64BIT
Windows Vista Home Premium


Thank you in advance!

---

### Post by easoukenka on 2008-11-09
Well I would say popin a live cd and take a look at /boot/grub/menu.lst

couldn't tell you exactly what to put in there but try slimming it down to just ubuntu and modifying something.  I am not an expert but that is what I would try.  There is a gui option for editing the grub think its called grubbed.

---

### Post by caljohnsmith on 2008-11-09
How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by azv31 on 2008-11-09
Guys I can't boot any CD, the only thing i can access on my laptop is the BIOS settings and BOOT Options, even if i chose to boot from live CD the computer won't boot, only a blank screen appears

---

### Post by caljohnsmith on 2008-11-09
You previously implied that you were able to boot from the Live CD to install to your USB drive; installing Ubuntu to your USB drive should not affect whether you can boot your CD drive or not, so maybe you have a hardware problem. Since you can go into BIOS, I would check to make sure your CD drive is first in the boot order.

---

### Post by azv31 on 2008-11-09
Sorry, maybe I did not explain properly.

I was able to boot a live CD before installing it to the USB, that was when my computer was working properly, it all began when the Ubuntu installation finished and it asked me to restart.

---

### Post by azv31 on 2008-11-09
Hello guys!
I installed UBUNTU dekstop 64 bit last night into a USB stick and when installation was done I restarted and now I can't access windows vista NOR Ubuntu, I cannot even boot a live cd or any other cd.
Help PLEASE!

**[SIZE="4"]Things you should know:[/SIZE]**
[LIST]
[*]I have Windows vista 64 bit, gateway 4GB ram 
[*]I CANNOT boot any cd, I only get a blank screen with a cursor
[*]I CAN only access the BIOS settings and boot options but even if I choose to boot from CD it won't work.
[*]Evidently, I can't access windows vista, nor UBUNTU
[*]My computer is 3 months old so I don't think is a hardware problem, but I don't discard that possibility.
[/LIST]

Please help me I have very important data in my laptop and I don't want to loose it, What can i DO?

Thanks in advance.

---

### Post by inmytaxi on 2008-11-12
I'm having problems of my own, but you could pull the hdd, attach it to a (I have an Inland) USB to IDE / Sata adapter, copy off your files, and format it on a different computer.

Problem is you might have bios issues, can you reset the bios by pulling the battery?

---

### Post by Slim Odds on 2008-11-12
I agree with some of the previous posters.....

There is no way to disable CD boot by installing Ubuntu. No matter how badly one screws it up.

The BIOS boots from the CD. No middleman.

---

### Post by athaki on 2008-11-12
so pop in the vista cd and click repair your computer go to a command line and type in bootrec.exe /fixboot and bootrec.exe /fixmbr.  You'll get vista back.  then try to install ubuntu again.

---

### Post by TeXtonyx on 2008-11-12
The problem started when you installed grub to sd1. You need to 
put the grub files into a Ubuntu partition not a Windows partition.
It probably would have worked ok, if you left the default on, which
is hd0 = sda, which installs to the MBR not into a partition. 
The problem would be if you tried to boot to Vista when you didn't
have the USB drive attached. 

If you had selected installing grub to the USB drive, it would have
worked. To boot Ubuntu, you'd have to use the Super Grub disk. Or
adding Ubuntu to the Vista bootloader menu options with Easybcd
would likely have worked.

There is another thread much like this one: "lost my ubuntu and Vista
please help". The first thing to logically suspect is the cd or
the cdrom drive is physically broken when one can't boot from 
the cd. However, in the thread above, the OP can boot the Vista
cd, but it says the drive is in the wrong format and quits. BUT,
he can't boot the live cd. That rules out a bad cdrom drive, bad
bios settings and very likely bad cd since he used it recently.

Have you tried the vista install cd, running bootrec from Recovery
Console? It worked differently in the other thread. There is also
a Vista recovery cd available at neosmart which caljohnsmith said 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
In case you have that recovery disk that comes with OEM laptops.

You don't need USB drive now, unless you want to install Vista
from scratch on it and then clone Vista to the whole drive. 
Then resize/shrink Vista. Ok, I think you should unhook the USB
drive, move boot from cd to top of boot order list and put your
drive 0 which is the first drive or sda second on list. Then try 
to delete the MBR and rewrite a standard MBR. Then delete your
whole drive, all the partitions. Then install Vista(s) again.

Later your basic install of Ubuntu on USB drive is still OK.
Reinstall grub, either to the Ubuntu USB drive or to the 
MBR of hd0 which will overwrite the Vista MBR. I fixed this
situation once by cloning another drive to the bad drive. They
make these laptop to desktop drive converters. 

Also, these ideas overwrite your data, so be aware of that in
case you haven't made a backup. Another thing is that I think
if you made a small ext3 /boot partition on your Vista drive
you can install grub there which will work with Ubuntu on the
USB drive when you have it hooked up. I'm not sure of that.

---

