---
title: "Finding and formatting a real SCSI disk"
date: 2009-04-12
forum: Hardware
---

### Post by hjtrost on 2009-04-12
I have just installed Ubuntu 8.04.2 on an old PC - AMD K4-2 450 MHz, 256 MB RAM, on IDE 5 GB disk space, 0.5 GB swap space.  I got the serial mouse to run, the screen resoultion corrected, and grub to offer Windows 98 SE (on the first 2.5 GB of the IDE drive).  Both floppy drives, the CD-RW and the USB ports are recognized.  There is no Internet connectivity yet, that may or may not create another post later.

Now I need to make Ubuntu see my 4 GB SCSI drive, which at this time is unformatted and has no partition.  The Ubuntu installation did not see it.  The interface is an Adaptec AHA-1520B card.

I have put a line

aha152x=0x340,11,7,1

into /etc/modules, and the machine boots okay with it.  I assumed that the SCSI slot number is for the SCSI bus controller on the card, which should usually be #7.  The hard drive is on #1, if I remember correctly (that's not the number 1 in the line in /etc/modules).  The address and IRQ are positively verified from Device Manager under Windows 98 SE, which still sees this disk.  The BIOS does see it as well and reports it on the very first boot screen.

No sign of the disk yet.  I tried "lshw" and "fdisk -l".  The only sign of life is in the output of "dmesg" - 16 kilobytes in size, so below is only the immediate section of it mentioning the SCSI card, plus a few lines after to make sure I don't miss an important one.

Forum searching and googling is pretty unproductive as "SCSI" is thrown at about everything under the sun (like my IDE hard drive which in the "dmesg" output is also named as a SCSI disk, /dev/sda).  Still, what I have done so far is based on results from googling and forum searching.

So where do I go from here?


P.S.: I'm doing this late at night in small installments, so progress and message turn-around will be slow.  That's okay.


[   57.293105] PCI: VIA PCI bridge detected. Disabling DAC.
[   57.293122] Activating ISA DMA hang workarounds.
[   57.293177] Boot video device is 0000:01:00.0
[   57.295708] isapnp: Scanning for PnP cards...
[   57.412126] isapnp: Card 'Adaptec AHA-1520B'
[   57.412144] isapnp: 1 Plug & Play card detected total
[   57.922460] Real Time Clock Driver v1.12ac
[   57.923341] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   57.923942] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   57.925048] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   57.930619] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   57.933225] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

---

### Post by egalvan on 2009-04-12
Does Partition Editor see the drive?

I use PartedMagic LiveCD for partitioning chores, as the version in 8.04.2 is a bit lagging (v0.3.5, and the latest is  0.4.4).

Last time I installed SCSI drives, i did the low-level testing and formating with the adapter BIOS... 
that was an Adaptec 2940UW.

I don't have any experience with your model Adaptec.

and kudos for resurrecting an old  machine, I thought I was the only crazy one out there... :)

---

### Post by hjtrost on 2009-04-13
Small correction - that is an AMD K6-2 processor.

The short update is that I still don't see the drive - remember that it is empty (removed partition using DOS/Windows 98 SE's fdisk tool).

I discovered that during boot-up the SCSI controller reports ID #2 for the drive, so that is what I have now in the aha152x line in /etc/modules - to no avail.  (All of 7, 1 and 2 there give the same result.)  I still don't see the drive.  I have GParted 0.3.5 now on the system, and it does not see it either.

The Parted Magic 4.0 CD I just created today complains that my processor does not offer "cmov", so I'd need to use a different kernel that accommodates that.  There is a tool at the end of the list that looks at hardware - it recognizes the disk but gives the wrong size for it, 33 GB instead of 4 GB.

I'd appreciate any further suggestions.

---

### Post by hjtrost on 2009-04-15
Progress!  I can see the drive and can use it.

However, it does not come online automatically, and there I need some help with a kludge.  First, here is what I did:

1.  Put a line
          options aha152x io=0x340 irq=11 scsiid=7
    into the file "/etc/modprobe.d/options".

2.  Run command
          sudo modprobe aha152x

3.  Run GParted.  The disk is visible as /dev/sdb1.

4.  Put a line
          aha152x
    into the file "/etc/modules".

5.  Reboot.

PROBLEM:  Connecting to the drive fails during boot-up.

6.  Remove the line from "/etc/modules".

7.  Reboot.

8.  Run command
          sudo modprobe aha152x
    which becomes the equivalent of the line I had in "/etc/modules".
    Same problem!!!

9.  Run command
          sudo rmmod aha152x

10. Run command
          sudo modprobe aha152x

DRIVE IS VISIBLE AGAIN.

This sequence is reliably repeatable, i.e., I need

          sudo modprobe aha152x
          sudo rmmod aha152x
          sudo modprobe aha152x

to get the drive to show up successfully.  Below is a cutout from a "dmesg" command output covering the three commands.  The "rmmod" does not leave a trace, and I have split the listing at the point where it was issued.

What I could now use is a script file simulating my handiwork as follows:

     modprobe aha152x
     wait
     sleep 3
     wait
     rmmod aha152x
     wait
     sleep 3
     wait
     modprobe aha152x
     wait
     sleep 3
     mount /dev/sdb1 /work

with the mounting of the disk thrown in for good measure.  The "wait"s and "sleep"s may not all be necessary but I'd like to play it safe.  Now where do I put this file, or a call to it, such that it will be executed with root privileges at the end of the boot-up just before the login prompt is displayed (GUI usually)?

I got this far by continuing to mostly google, specifically for "modprobe aha152x" after I had understood that that command or something equivalent had to happen.  Thanks to all the folks who asked and answered on issues somehow related to this and some other keywords.  The tip I got here on partitioning software is also much appreciated.  I ended up installing GParted from my 8.04.2 CD; Parted Magic 4.0 refuses to work with my processor (missing a "cmov" feature).

I'd appreciate any suggestions.



[  762.865993] aha152x: BIOS test: passed, 1 controller(s) configured
[  762.872387] aha152x: resetting bus...
[  764.127519] aha152x2: vital data: rev=7, io=0x340 (0x340/0x340), irq=11, scsiid=7, reconnect=enabled, parity=enabled, synchronous=enabled, delay=1000, extended translation=disabled
[  764.127577] aha152x2: trying software interrupt, lost.
[  765.127380] aha152x2: irq 11 possibly wrong.  Please verify.



[  840.908854] aha152x: invalid module params io=0x340, irq=11,scsiid=7,reconnect=1,parity=1,sync=1,delay=1000,exttrans=0
[  840.914730] pnp 01:01.00: activated
[  840.914764] aha152x: found ISAPnP adapter at io=0x340, irq=11
[  840.914814] aha152x: BIOS test: passed, 1 controller(s) configured
[  840.925047] aha152x: resetting bus...
[  842.180366] aha152x3: vital data: rev=3, io=0x340 (0x340/0x340), irq=11, scsiid=7, reconnect=enabled, parity=enabled, synchronous=enabled, delay=1000, extended translation=disabled
[  842.180411] aha152x3: trying software interrupt, ok.
[  843.180242] scsi3 : Adaptec 152x SCSI driver; $Revision: 2.7 $
[  843.925310] (scsi3:2:0) Synchronous Data Transfer Request period = 200 ns offset = 8 
[  843.930181] scsi 3:0:2:0: Direct-Access     SEAGATE  ST34501N         0017 PQ: 0 ANSI: 2
[  845.003482] sd 3:0:2:0: [sdb] 8887200 512-byte hardware sectors (4550 MB)
[  845.008190] sd 3:0:2:0: [sdb] Write Protect is off
[  845.008224] sd 3:0:2:0: [sdb] Mode Sense: b7 00 10 08
[  845.013747] sd 3:0:2:0: [sdb] Write cache: disabled, read cache: enabled, supports DPO and FUA
[  845.017453] sd 3:0:2:0: [sdb] 8887200 512-byte hardware sectors (4550 MB)
[  845.019940] sd 3:0:2:0: [sdb] Write Protect is off
[  845.019972] sd 3:0:2:0: [sdb] Mode Sense: b7 00 10 08
[  845.024250] sd 3:0:2:0: [sdb] Write cache: disabled, read cache: enabled, supports DPO and FUA
[  845.024299]  sdb:
[  845.042068] sd 3:0:2:0: [sdb] Attached SCSI disk
[  845.042338] sd 3:0:2:0: Attached scsi generic sg2 type 0

---

### Post by egalvan on 2009-04-15
OK, so how much experience do you have with SCSI stuff?

SCSI counts from zero, 
ID 0  to ID 7, total of eight ID's.
(Your board is limited to eight devices; less the one for the card, leaves seven devices possible to connect.)

the board is ALWAYS ID 7, or the eight unit.

Termination is CRITICAL on SCSI stuff.

BOTH ends must be properly terminated.

Some adapter cards can handle automatic termination.
(sometimes set with the BIOS-based setup firmware)

Very few drives can handle automatic termination.

SCSI cables are VERY quality-conscious. Cheap cables cause nothing but headaches.

SCSI cables are length-limited, they can neither be too long, nor too short.
and the distance between devices is the same thing, neither too long nor too short.


So some questions/observations...

This is an ISA card?

do you have PCI slot available?

Can you switch to a PCI-based card?

I used an Adapted 2940UW under Mandrake (now Mandriva) and it ran "out-of-the-box".
This was more than four years ago, though, so I'm hazy as to the exact detals.

ErnestG

---

### Post by hjtrost on 2009-04-15
Ernest,

thanks for the follow-up.

My computer started out in 1992 as a 33 MHz 486DX screamer of the day, with 8 MB RAM and 210 MB HD, running Windows 3.1.  (Okay, 50 MHz was just out then.)  In 1994, I added a SCSI card for a 1 GB second disk and a 4x CD-ROM.  In 1996 I upgraded to Windows 95 and got a new SCSI card, then one I still have in this machine.  I replaced the motherboard once with a 120 MHz one.  Then, trying to update its BIOS, I scrambled it instead and rebuilt the computer.  New AT motherboard with the AMD K6-2, 128 MB RAM, 8.4 GB HD, Windows 98 SE.  The SCSI card, disk and CD served on.  In about 2004, I inherited a used 4 GB SCSI disk at work, and it went in as well.  In 2006, I retired the computer, hoping to use it later perhaps to control a model railroad layout that I still haven't begun to build, and bought a new one.  The 1 GB disk was failing, and I wanted a CDRW.  Thus the two diappeared, and the 4 GB remains the only SCSI customer in the machine.

Now, Ubuntu is slowly becoming a serious candidate for use at work, so I'd like to have a backup workplace at home.  That's what made me get here.

So to your questions:

The SCSI controller is in the machine for ages.

It is an ISA card (I think).

I have not touched the cabling since I took the old disk and CD out in 2006.

It has worked flawlessly under Windows 98 until I cleaned it up last week (with Windows 98's FDISK) to become available as a secondary disk for Ubuntu.  I have not touched anything in the computer since I extended the RAM to 256 MB a few months ago, in preparation to sometime install Ubuntu.

I know that the controller takes slot 7, and have finally understood that that is the slot to be named in the driver parameters.

The disk sits in slot 2, with the dead 1 GB disk and the CD having lived in slots 0 and 1.

The SCSI BIOS tool is set for automatic termination, and again, under Windows 98 SE everything was fine that way with only the 4 GB disk in slot 2 present.  I used it as a temporary staging area for logical drives on my IDE drive when I reduced those in size to give Ubuntu its primary 5.5 GB.

There may or may not be a PCI slot left.  In any case, I am not inclined to get a new SCSI card.

I was gearing up to test my script idea when I saw your response and will live with running it by hand every time I boot up, or have my .profile do it, until I can find a place to have the boot process run it as more or less the last step before offering the login screen.

Some day I may try to turn "PnP OS" in the main BIOS off (it is on, and one of the more helpful posts I found suggests to turn it off) and see if that does something.  I can live with the script solution.

Cheers,           Jochen

---

### Post by HankB on 2009-04-16
Have you tried adding [FONT="Courier New"]aha152x=0x340,11,7,1[/FONT] to the boot command line in /boot/grub/menu.list? The line should look something like:
```
kernel          /vmlinuz-2.6.27-14-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro quiet splash 
```
I think that will cause the module to be loaded during the boot process. I'm not sure that the kernel can detect the ISA SCSI card like it does with PCI SCSI cards.

I don't know how that will affect the issue you solved by loading - unloading - reloading the module. Could that be related to slow startup of the drive? Perhaps you can get around that by telling the SCSI bus to rescan for devices. I googled "Linux SCSI rescan" and found this:
```
echo "- - -" > /sys/class/scsi_host/host0/scan
```
at [http://jcollie.blogspot.com/2008/05/how-to-re-scan-scsi-bus-on-linux.html](http://jcollie.blogspot.com/2008/05/how-to-re-scan-scsi-bus-on-linux.html).

If you do need to execute something at srartup, look up init.d (as in /etc/init.d) and the command [FONT="Courier New"]update-rc.d[/FONT] to configure init.d scripts.

Good luck getting this working!

-hank

---

### Post by hjtrost on 2009-04-17
SOLVED!

Hank,

I have in the General forum received the suggestion to go with my script call into "/etc/rc.local" and have done that.  I have put a small text file "SCSIisAlive" into the root directory of the SCSI disk, and have wrapped my core script with a test on the presence of this file to prevent repeated execution of my triple command, like this:

if test -r /work/SCSIisAlive ; then
cp /work/SCSIisAlive /home/myaccount/scratch
else
modprobe aha152x
...
mount /dev/sdb1 /work
fi

and this works.  The parameters for the driver are in "/etc/modprobe.d/options" (they are what you suggest).

After all, this is a fairly modern OS thrown at a fairly old clunker.  I'm a happy camper now and feel no need for further digging.

As for the "/boot/grub/menu.lst" file (no "i" in "lst" here), there is a line "kernel" like you describe for the boot drive /dev/hda2, which is on my primary IDE drive.  The SCSI one is only for extended work space.  All I have done to this file is to add my Windows 98 SE installation, which is also on the IDE drive, to the boot list.  I understand too little (like nothing) about "/etc/init.d" and its files to see how it would help me (I read your statement that it could - I'm weary about the timing and interactions in the overall boot process), while "/etc/rc.local" sits at the very end, right where I think I can live best with my crummy script.

Cheers,         Jochen

---

