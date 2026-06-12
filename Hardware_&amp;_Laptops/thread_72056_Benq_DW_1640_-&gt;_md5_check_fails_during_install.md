---
title: "Benq DW 1640 -&gt; md5 check fails during install"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by rinsed on 2005-10-05
I recently bought a benq dw 1640 for my dvd burning pleasures amongst some other stuff for my pc. Build everything in and thought i would start with a fresh install of both windows xp and ubuntu 5.04. Windows installed flawlessly and detected the benq drive without problem. I then proceded to install ubuntu wich seemed to go just fine, till it failed with an cannot copy file error. So i did a integrity check of the dvd, wich failed in the first second. So burned a new install cd on via windows and tried again, failed again.... burned a new install cd on my mac, failed again (both failing the md5 checks). So i did a manuall md5 check on my mac, and everything was fine... this puzled me. So just to see if it was maybe my new benq drive i reinstalled my old dvd-rom drive and tried again. The dvd and the 2 cd's all worked perfectly (no md5 errors what so ever). Now this ofcourse is not what i want, i wish to use my benq drive!
the problem i am having sounds simmilar to these two threads allthough they focus not on the drive it self but might be of some help for the people who might solve this mistery.
[http://ubuntuforums.org/showthread.php?t=37916](http://ubuntuforums.org/showthread.php?t=37916)
[http://ubuntuforums.org/showthread.php?t=19228](http://ubuntuforums.org/showthread.php?t=19228)
- rinsed

---

### Post by neufena on 2005-10-05
I also have the same drive and had exactly the same problem during install.  By suing another DVD drive I Installed Ubuntu but now get drive read errors.  
I was actually about to post my own plea for help when I found this post!  My plea is below:
------
I have a BenQ DVDr drive (DW1640) but whenever I try to read from it under Ubuntu (Breezy, amd64) I received read errors.  If I try to copy a file using nautilus and keep pressing 'retry' on the error dialog box the file will copy correctly in the end.
Below is the output to dmesg between attempting to copy a file and the first error dialog:
[ 1364.157446] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1364.367203] ISO 9660 Extensions: RRIP_1991A
[ 1389.046231] hdb: cdrom_read_intr: Bad transfer size 65534
[ 1389.046238]   Trying to limit transfer sizes
[ 1389.046243] end_request: I/O error, dev hdb, sector 5403340
[ 1389.046248] Buffer I/O error on device hdb, logical block 1350835
[ 1389.046280] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[ 1389.046285] ide: failed opcode was: unknown
[ 1389.046289] hdb: drive not ready for command
[ 1389.046306] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[ 1389.046309] ide: failed opcode was: unknown
[ 1389.046312] hdb: drive not ready for command
[ 1389.046329] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[ 1389.046332] ide: failed opcode was: unknown
[ 1389.046336] hdb: drive not ready for command
[ 1389.046352] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[ 1389.046356] ide: failed opcode was: unknown
[ 1389.046381] hdb: drive not ready for command
[ 1389.095740] hdb: ATAPI reset complete
There are a couple of messages in dmesg from boot that concern me:
[   30.771429] NFORCE3-250: not 100% native mode: will probe irqs later
[   30.771433] NFORCE3-250: BIOS didn't set cable bits correctly. Enabling workaround.
[   30.771435] NFORCE3-250: BIOS didn't set cable bits correctly. Enabling workaround.
Could these being related to the problem?
The drive works perfectly under Windows 2000, both reading a writing.  I have the latest firmware for both the drive and bios.
Any ideas?
Thanks in advance,
Neufena

---

### Post by neufena on 2005-10-05
I have an update to my problem:
I decied to play around with hdparm and keep changing settings to try and get the drive to work.  When I enabled DMA the drive began to work fine, no more errors.  I've only done a few test reads of a 250mb file but it seems to be working.  
I made dma permanent and rebooted to be sure, it still works, here's the output of hdparm for my drive:

/dev/hdb:
IO_support   =  1 (32-bit)
unmaskirq    =  1 (on)
using_dma    =  1 (on)
keepsettings =  0 (off)
readonly     =  0 (off)
readahead    = 256 (on)

I know this might not help for installing but if you get the system instgalled with another drive then this may get it working for you.
Let me know how you get on,
Neufena

---

### Post by WetWilly on 2005-10-05
There is a compatibility issue with this drives chipset but Ubuntu devs hasnt acknowlegded it yet. Plz see

[http://ubuntuforums.org/showthread.php?t=71401](http://ubuntuforums.org/showthread.php?t=71401)

[http://ubuntuforums.org/showthread.php?t=70677](http://ubuntuforums.org/showthread.php?t=70677)

and join in at bugzilla to help them realise it isnt a bad disc/drive error.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=16901](http://bugzilla.ubuntu.com/show_bug.cgi?id=16901)


fyi Plenor PX-740a and Benq DW 1640 use the same chipset!

---

### Post by betty on 2005-10-17
Does no one have a step-by-step fix for this BENQ issue?

I'm dying to install ubuntu breezy, but I can't! 

Thanks!
betty

---

### Post by taygan on 2005-10-18
try enabling dma  (you can access it thourhg alt-f2 (or f3??) during install.  I know there's a better way to do this, but I can't find it right now.)

sudo hdparm -d 1 /dev/sda  ( <- that's your device right? or /dev/hda?)

---

### Post by bluetoad on 2005-11-01
I have an Intel motherboard and the via82cxxx seemed to cause a conflict.  So if you have an Intel motherboard this could help

I retraced my steps with the Hoary Live CD

1. Boot into Expert Mode
2. Answer the questions regarding your Locale and keyboard etc
3. When Detect & Mount CD-ROM comes up you'll be presented with a list of modules.  Uncheck via82Cxxx.
4. Continue on, accepting defaults
5. When hdparm parameters come up enter
-d1
6. Continue on
7. I kept unchecking via82cxxx whenever it was presented and accepted defaults otherwise.  You might need to do a sanity check along the way to be safe.

                                                  ...Peter

---

### Post by bluetoad on 2005-11-01
I also put piix at the top of /etc/modules and turned on dma in /etc/hdparm.conf

/dev/hda {
        mult_sect_io = 16
        write_cache = off
        dma = on
}

---

### Post by arito on 2005-11-03
I have this same problem with BenQ DW1640 and my motherboard has a VIA chipset. Maybe it's not a good idea for people with VIA chipset to uncheck via82cxxx during installation? (I got around this problem by using another drive for installation - not very elegant :-/

Ari

---

### Post by izm81 on 2005-12-28
On the bug post ([http://bugzilla.ubuntu.com/show_bug.cgi?id=16901]("http://bugzilla.ubuntu.com/show_bug.cgi?id=16901")), it was solved on the BENQ drive by updating the firmware (see last post).  But how are we supposed to do this if we don't have windows?  :confused:

---

### Post by floobit on 2006-02-25
I am confused by some of the instructions on this thread.  How do I enable dma?  I am a bit of a noob and am having trouble replicating the results.  what I do:
1  insert the x64 build of breezy into my dvd-drive
2  type expert (I've done the following arguments after expert, neither of which work: 
noapic nolapic pci=noacpi   //what was posted, 3rd letter in "nolapic" is an L
noapic no|apic pci=noacpi  //in case the 
noapic noapic pci=noacpi   //poster mis-typed
hdparm -d 1 /dev/hda
3  after choosing my language and country and some other stuff, it tries to detect my hardware.  During this point, I press alt-F2 and and I get the console.  
I then type in sudo hdparm -d 1 /dev/hda.  apparently sudo is not a recognizeable command.  so, I neglect the sudo, and type in hdparm -d 1 /dev/hda and it says no such device exists.  So, I try /dev/hdb, sda, sdb, hdc, hdd, and the only answer other than "the device is not recognized" is for /dev/sda, which says that it's "inappropriate ioctl for device"  I assume I'm trying to enable dma on my sata hd by using /dev/sda.  anyway, some help would be nice.  
 
I'm pretty sure my dvd-writer's on hda, because it's the only ide and my hd is on a sata.  I don't have a via chipset, it's a weird ATI chipset.  
Additionally, I do have the latest chipset firmware upgrade for the benq.

---

