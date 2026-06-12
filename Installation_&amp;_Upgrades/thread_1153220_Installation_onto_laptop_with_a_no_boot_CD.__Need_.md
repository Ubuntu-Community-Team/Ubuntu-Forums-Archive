---
title: "Installation onto laptop with a no boot CD.  Need opinions please!"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by cdubea on 2009-05-08
I'm a fairly new Ubuntu user and would like some advice. I've got an old Toshiba Laptop that will not boot from the CD. The CD's on these machines were problematic and the CD has been replaced but it won't boot from the CD. This problem is exacerbated by the fact that the machine has a "smartbay" which allows either a floppy drive or a CD but not both at the same time.

The computer had Win98 installed at one point, but now has only DOS installed on the harddrive which loads CD drivers. If I have to I'll reinstall Win98, and use WUBI, but would prefer to install direct.

What's the most straightforward means of getting Xubuntu on this machine?

Thanks

chris

---

### Post by swisstone198 on 2009-05-08
Using another linux machine, mount the cdrom

# sudo mount -o loop /dev/cdrom /mnt

insert your floopy

# dd if=/mnt/install/sbm.bin of=/dev/fd0

then instert your floppy into the target machine and reboot, you should then get the option to install from cd.

let me know how you get on

---

### Post by cdubea on 2009-05-08
A complicating factor is I have no other machines with a floppy drive.  Progress :|

thanks

---

### Post by Idaho Dan on 2009-05-08
cdubea,
I had the same problem with my old HP laptop.
I finally got ahold of an external cd drive that plugs in to a USB slot.
That worked just fine.

Dan.

---

### Post by swisstone198 on 2009-05-08
you could use usb instead of floppy if you have one

---

### Post by logos34 on 2009-05-08
if that old lappy doesn't support usb boot (a lot don't), there is this method (provided it has internet connection):
> 
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

Windows 95/98/ME (using Loadlin)

    *

      Download loadlin.exe.gz from [ftp://elserv.ffm.fgan.de/pub/linux/loadlin-1.6/update-1.6c/](ftp://elserv.ffm.fgan.de/pub/linux/loadlin-1.6/update-1.6c/) and unpack it to boot (If your default compression/archive program doesn't like *.gz files, try 7-Zip from [http://www.7-zip.org](http://www.7-zip.org))
[COLOR="Blue"][Note: link is dead..Get **loadlin1.6d.exe** [here]("http://youpibouh.thefreecat.org/loadlin/").  Put it in 'boot' folder in C: directory][/COLOR]

    *

      Choose Reboot in MS-DOS mode in the shutdown menu or press F8 (Ctrl for Win98/ME) during boot and choose command prompt only in order to start Windows in DOS mode
    * Get into the boot directory and run loadlin: 

cd c:\boot
loadlin linux initrd=initrd.gz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --

Now you should have a network installation going :)

Or try the 'CD Approach' or 'CD Image Approach' on same page. (need Alternate Install CD--won;t work with live cd)

---

### Post by cdubea on 2009-05-10
> **logos34 said:**
> if that old lappy doesn't support usb boot (a lot don't), there is this method (provided it has internet connection):


Or try the 'CD Approach' or 'CD Image Approach' on same page. (need Alternate Install CD--won;t work with live cd)

Okay, I'm still not there yet.  After burning about a dozen CD's to transfer files over to my laptop I'm not any further.

I downloaded loadlin.exe and initrd.gz and saved to the c:/root/ folder on the laptop.

Shutting Win98 down to a DOS prompt and entering in the line above from c:/root/ (or c:/) results in the following message:

LOADLIN v1.6d (C) 1994..2002 Hans Lermen
Image file not found.
Please enter the name of the kernel image file followed by optional
command line parameters for Linux(e.g. root=XXXX)
or @file ( file = param file ) or "empty string" to abort:"

I've manually entered the initrd.gz file, I've expanded initrd.gz into initrd and that doesn't work.  I've tried initrd.gz from jaunty and hardy.

Help?

thanks

chris

---

### Post by logos34 on 2009-05-10
try it one more time, but this time get the archive 'loadlin-1.6d.tgz' (loadlin.exe inside).  Unpack it to 'boot' folder in C: as before

see if that works (maybe something in the pkg has changed, though)

if not, get the alternate install cd iso and try that method

---

### Post by cdubea on 2009-05-10
> **logos34 said:**
> try it one more time, but this time get the archive 'loadlin-1.6d.tgz' (loadlin.exe inside).  Unpack it to 'boot' folder in C: as before

see if that works (maybe something in the pkg has changed, though)

if not, get the alternate install cd iso and try that method

That is what I did, but I unpacked loadlin-1.6d.tgz on my WinXP machine, wrote the files to a CD and then copied them to root on the laptop.  

I've got a copy of the alternate install ISO.  How would I use that?

thanks

chris

---

### Post by logos34 on 2009-05-10
EDIT: I'm not sure the 'CD Image approach', which uses the Alternate Install iso, will work on window98 (which you'd have to reinstall)--the instructions I gave you seem to imply only WindowsNT/2000/XP, but it uses grub4dos to boot, and the latter's project page says
> 
GRUB for DOS is a multi-boot loader or boot manager based on GNU GRUB. It works in various environments like DOS, [COLOR="Red"]Windows9x[/COLOR]/NT/2K/XP, and Linux. Because the booted GRUB is in real mode, almost all operating systems on the disks can be booted then.

so maybe there's a chance

other than that I'm fresh out of ideas.

Well, I have one final thought: if it doesn't work, you can still go the wubi route like you mentioned, but you can then convert xubuntu into a dedicated installation with [LVPM]("http://lubi.sourceforge.net/lvpm.html")

---

### Post by cdubea on 2009-05-13
I'm at wit's end here.  I've reinstalled Win98.  Upgraded the memory to the max allowable (256m).  Wubi won't run, even using the memory switch.

Using a copy of vmlinuz I get loadlin to finally run, but it crashes with the message:

[4294672.131000] **** SET: Misaligned resource pointer: c1385322 Type 00 Len 42

thanks for any further pointers!

chris

---

### Post by upchucky on 2009-05-13
if u can get a pcmcia network card for this machine to connect to a router or a pc, you can install from the internet, (very slow), or install from a home network.

I have an old toshiba 310cds to run my magicjack phone, i use a pcmcia card to connect to the router. I did have to manually set the irq, and memory address. in device manager to get xp to see the card.

I can control the machine from my ubuntu box using a package called synergy.

---

### Post by cdubea on 2009-05-14
> **upchucky said:**
> if u can get a pcmcia network card for this machine to connect to a router or a pc, you can install from the internet, (very slow), or install from a home network.

I have an old toshiba 310cds to run my magicjack phone, i use a pcmcia card to connect to the router. I did have to manually set the irq, and memory address. in device manager to get xp to see the card.

I can control the machine from my ubuntu box using a package called synergy.

I've got a PCMCIA network card.  Can you give specifics on how to do what you suggest?

Thanks!

chris

---

### Post by upchucky on 2009-05-14
to get my pcmcia card talking to my router, i had to set the following in win xp device manager. win 98 has device manager in a different location but you should be able to find it if you are using win 98.

click control panel, right click my computer, select device manager, select network adapters, select the card you are using assuming you have installed the drivers for the card.

under the resources tab, i had to manually enter
memory range FCEFF000 - FCFFFFF
I/O Range DF40 - DF7F
IRQ 11

you may have to check and make sure no other device is using IRQ 11 otherwise it should be fine. 

as for doing a network install, you only need to copy the install cd to a drive on your network, assuming you have the network set up and all machines are talking to each other then start the install from there.

i am sure there are guides in these forums that help you with the network install.

---

