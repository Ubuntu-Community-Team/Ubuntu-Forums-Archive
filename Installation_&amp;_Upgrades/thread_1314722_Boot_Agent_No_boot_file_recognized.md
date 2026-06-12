---
title: "Boot Agent: No boot file recognized"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by Spazmunki13 on 2009-11-04
Hey all,

I'm been installing an reinstalling Ubuntu 9.10 (I think) since last night. The installation goes perfectly until it asks me to reboot to load Ubuntu through the boot system and then I get an error saying the "Intel Boot Agent GE v. 1.2.28: no boot file recognized"

I always get the error no matter how many times I install no matter how I install.

I want a solo boot (?) of Ubuntu.

Can anyone help?

Thank goodness Ubuntu can run with just a CD! *chorus chant*

Thanks in advance. :)

Matt

---

### Post by mechro on 2009-11-04
It's probably a BIOS setting that needs changing. 

If you know nothing about entering and editing the BIOS then we'll need more hardware information e.g. motherboard.

---

### Post by Spazmunki13 on 2009-11-04
Thanks for the quick reply.

I have been in BIOS before, I'd just need to know what to do in there.

Matt

---

### Post by mechro on 2009-11-04
:D :D

Hence my request for motherboard information so I can wander off, find a PDF manual for your motherboard and have a good read while drinking coffee. 

;) ;)

---

### Post by Spazmunki13 on 2009-11-04
I wouldn't be able to tell which Motherboard I have off the top of my head but would I be able to look it up through the cd boot of Ubuntu? (which is all I have left resembling a computer)

---

### Post by mechro on 2009-11-04
Never mind. This might be it...

> How Intel® Boot Agent Works 
The Intel® Boot Agent is seen by the host computer as a boot device. The BIOS inserts the Boot Agent into the list of boot devices. When the Boot Agent is ahead of any other bootable device in the list, it will execute and attempt to boot the machine. 

To prevent the Boot Agent from executing, enter your systems BIOS configuration and find the boot device order settings. Move the boot agent further down the list, preferably after the hard drive or whatever device you prefer to boot from.

[http://www.intel.com/support/network/sb/cs-008018.htm](http://www.intel.com/support/network/sb/cs-008018.htm)

---

### Post by Spazmunki13 on 2009-11-04
Thank you very much, I'll try that. And I'll be back with an update. :D

---

### Post by Spazmunki13 on 2009-11-04
I tried changing the Boot order but it didn't change anything to have Hard Drive first. I'll check the intel support site for info.

Thanks again.

---

### Post by mechro on 2009-11-04
Intel only comes into the picture re the Boot Agent.

If you don't know your motherboard info, can you tell me what type of BIOS you have? For example in my BIOS all the pages are headed "**Phoenix - AwardBIOS CMOS Setup Utility**". Can you post anything similar?

---

### Post by Spazmunki13 on 2009-11-04
The BIOS text I get is "Winfast PX7300LE TDH VGA BIOS V01.24.2006"

EDIT: I think this is it: [http://www.leadtek.com/eng/tv_tuner/overview.asp?pronameid=259&lineid=6&act=1](http://www.leadtek.com/eng/tv_tuner/overview.asp?pronameid=259&lineid=6&act=1)

EDIT 2: I think I should download the driver but Ubuntu's CD boot won't allow. :(

---

### Post by mechro on 2009-11-04
Which of the following, if any, main menu items appear in your BIOS?...
[B]
Standard CMOS Features

BIOS Feature

Advanced BIOS Features[/B]

---

### Post by Spazmunki13 on 2009-11-04
Should I be looking at the system startup or inside the BIOS itself?

---

### Post by mechro on 2009-11-04
What do you mean by system startup?

The menu items I'm looking for are in the BIOS.

---

### Post by Spazmunki13 on 2009-11-04
Well the BIOS text I got from the screens that appear when the system is starting up.

---

### Post by mechro on 2009-11-04
There might be some misunderstanding here. You said...

> I have been in BIOS before, I'd just need to know what to do in there.

So my question is, which key are you pressing to get in the BIOS? If you don't know what I mean then you haven't been "in BIOS before" and we need to start again.

---

### Post by Spazmunki13 on 2009-11-04
I press F2 to get into BIOS.

And I took pictures because I wasn't sure I what I was looking for.

The first being the text I gave you and the second a picture of the boot agent screen. I'm not sure if I'm allowed but I have two other pictures of the BIOS menu I can send you but I have no more room for the attachments so I'll send them in the next reply.

I really appreciate all you're doing for me. :)

---

### Post by Spazmunki13 on 2009-11-04
Here are the two others.

---

### Post by mechro on 2009-11-04
Thanks, I'm now tracking down the motherboard manual. Are any of the following recognisable as your system?...

	Intel® Desktop Board D945PWM
	Intel® Desktop Board D945PVS
	Intel® Desktop Board D945PSN
	Intel® Desktop Board D945PLRN
	Intel® Desktop Board D945PAW

I think the BIOS is the same for all these so the first thing you could try is Press F10 at power-on, select a boot device and press Enter.

---

### Post by mechro on 2009-11-05
Hmm, after having a good look at those screenshots there doesn't appear to be much wrong. 

I'm wondering if your original bootloader is still there and can't find a file system. When you installed Ubuntu you might not have specified Ubuntu's Grub bootloader to write the Master Boot Record... easily done but easily fixed.

I've got to go now, but if you still can't boot have a look here about fixing Grub bootloader...

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Spazmunki13 on 2009-11-05
The F10 thing worked.

Thanks a lot for your help!

:)

EDIT: Now it won't work. :( But I was able to boot from first hard disk on the cd.

---

### Post by mechro on 2009-11-05
F10 may only be a one time thing i.e. you'd have to press F10 every time you booted. Try it and see. Obviously that's not a permanent solution so we still need to fix either the BIOS or the MBR (Master Boot Record).

From the Live CD or your Ubuntu installation open a Gnome Terminal found under **Applications > Accessories > Terminal**. Type and enter the following command at the prompt...

```
sudo fdisk -l
```

It will ask for a password: from the Live CD just press enter, from Ubuntu installation enter your username password.

Post the results here.

---

### Post by Spazmunki13 on 2009-11-05
I tried doing the F10 thing and it hasn't worked since and I just realized (after 3 years) that my pc has TWO hard drives! Hah! lol I feel like a noob...

Anyways, this is what terminal gives me...

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c3f6117

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18705   150247881   83  Linux
/dev/sda2           18706       19456     6032407+   5  Extended
/dev/sda5           18706       19456     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c3f6117

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18705   150247881   83  Linux
/dev/sdb2           18706       19456     6032407+   5  Extended
/dev/sdb5           18706       19456     6032376   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

---

### Post by mechro on 2009-11-05
That's possibly a RAID set up.

Anyway, boot into the Ubuntu installation (not the Live CD) using CD or F10

Type and enter the following command in a Gnome Terminal...

```
sudo grub-install /dev/sda
```

Do the same for the other disk...

```
sudo grub-install /dev/sdb
```

Reboot.

---

### Post by Spazmunki13 on 2009-11-05
It's not working. :( I think I'm going to have to reinstall, again...

---

### Post by mechro on 2009-11-06
Are you still getting the "Boot Agent" error?

If you're doing a reinstall then I'd recommend trying to work out why your original install seems to be mirrored on two drives. That looks like a RAID set up which I know nothing about.

A simple solution might be to try installing with only one of the drives plugged in. If you get the same error with one drive it would suggest you need to investigate further your BIOS and possibly motherboard jumper settings.

---

### Post by Spazmunki13 on 2009-11-06
Alright, I'll try that. But will the second hard drive be usable once this mess is over with?

---

### Post by mechro on 2009-11-06
> **Spazmunki13 said:**
> But will the second hard drive be usable once this mess is over with?

If it's a standard hard drive it will be usable if it's not been made unusable. If it's unusable you can make it usable if you can figure out what the computer manufacturer did to make it unusable. ;)

A motherboard/computer/BIOS manual would help.

---

### Post by mechro on 2009-11-06
Result! I just found this...

[http://download.intel.com/support/motherboards/desktop/sb/biosglossarybymenu_v09.pdf](http://download.intel.com/support/motherboards/desktop/sb/biosglossarybymenu_v09.pdf)

A quick read reveals there are some RAID settings that are possibly relevant to your system.

---

### Post by Spazmunki13 on 2009-11-06
I just tried going through the install with only one hard drive connected but it seems like they both need to be connected for either one to work.... at least with the install because nothing shows up in the Partition part of the install. Though I can still use the computer apparently.

What is a RAID?

---

### Post by mechro on 2009-11-06
RAID comes in various configurations. It's for copying/cloning/mirroring using two or more drives to aid back up and error correction. I would say it's more used and useful in a commercial environment.

Are you looking at that manual? Can you figure out how to disable RAID in the BIOS?

---

### Post by Spazmunki13 on 2009-11-06
Yes, I think this is what I have to do.

Drive Configuration > Configure SATA as > IDE
                             > Intel Raid Technology > Disabled
Peripheral Configuration > Secondary SATA Controller > IDE

EDIT: I went through and none of the RAID settings seem to be enabled... also after about 5 minutes the BIOS doesn't recognize my keyboard and I had to shut down by pressing the power button.

---

### Post by Spazmunki13 on 2009-11-06
I just realized something... I get this error when the live cd is load:

> Buffer I/O error on device sr0, logical block XXXXXXAnd it appears a couple of times with different numbers.

So I looked it up and it said there might be a problem with the CD so I'll try burning another CD and see if that changes anything.

EDIT: Burning the CD gives me an error.

EDIT: This is the error:

> Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1799)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_L1CE3U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_OHCE3U.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage There is a checksum already 0
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_current_track
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
    wodim
    -v
    dev=/dev/sr1
    speed=4
    driveropts=burnfree
    fs=16m
    -data
    -nopad
    /home/ubuntu/Desktop/ubuntu-9.10-desktop-i386.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: No write mode specified.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Asuming -tao mode.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Future versions of wodim may have different drive dependent defaults.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr1'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr1'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.9
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Errno: 5 (Input/output error), read buffer scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stderr: CDB:  3C 00 00 00 00 00 00 FC 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stderr: Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 02 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Version        : 5
BraseroWodim stderr: Sense Key: 0x0 No Additional Sense, Segment 11
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Response Format: 2
BraseroWodim stderr: Sense Code: 0x00 Qual 0x02 (end-of-partition/medium detected) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Capabilities   : 
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Vendor_info    : 'CyberDrv'
BraseroWodim stderr: cmd finished after 126.065s timeout 40s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Identification : 'CW088D CD-R/RW  '
BraseroWodim stdout: Revision       : '15HF'
BraseroWodim stdout: Device seems to be: Generic mmc CD-RW.
BraseroWodim stdout: Current: 0x000A (CD-RW)
BraseroWodim stdout: Profile: 0x000A (CD-RW) (current)
BraseroWodim stdout: Profile: 0x0009 (CD-R) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-2 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1806336 = 1764 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: wodim: Cannot load media.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   689 MB        
BraseroWodim stderr: HUP
BraseroWodim stdout: Total size:      792 MB (78:30.24) = 353268 sectors
BraseroWodim stdout: Lout start:      792 MB (78:32/18) = 353268 sectors
BraseroWodim stdout: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2769)


---

### Post by mechro on 2009-11-07
> I just realized something... I get this error when the live cd is load:

Quote:Buffer I/O error on device sr0, logical block XXXXXX

When do you get that error? Is it when you boot from the CD? I don't understand how you've been able to run the LiveCD if you're now saying it gives an error? :confused:

Can you tell me more about how you installed Ubuntu? Either tell me exactly what version you used or show me where you got your original iso. I'm not even sure if you used a CD to install so any information would be helpful.

---

### Post by Spazmunki13 on 2009-11-07
Yeah, I get the error when it's loading the live CD.

I've been trying to install Karmic Koala (9.10) from a CD.

I checked the iso files MD5SUM and it matches the correct one from the list on the ubuntu website.

I tried installing XP on one drive and Ubuntu on the other but I still wouldn't boot with the "no file recognized" error.

---

### Post by mechro on 2009-11-07
It's probably a hardware problem. Faulty cable, faulty CD/DVD drive, dirty lens, etc. etc.

Did you use the CD/DVD drive regularly in Windows?

---

### Post by Spazmunki13 on 2009-11-07
Yeah, but mostly my CD Drive but it does the same on my DVD Drive.

EDIT: I'm waiting for an external DVD Drive though that I recently ordered, I'm hoping to get it this week so I'll be able to try it out on there.

EDIT: Also I noticed that GRUB doesn't seem to get installed with Ubuntu. Is that possible? I thought it came within the CD?

---

### Post by mechro on 2009-11-07
Here are the partitions on one of your drives...

> /dev/sda1 1 18705 150247881 83 Linux
/dev/sda2 18706 19456 6032407+ 5 Extended
/dev/sda5 18706 19456 6032376 82 Linux swap / Solaris

I assume /dev/sda1 is the Ubuntu installation. In /dev/sda1 is a /boot folder which contains your Grub files. Right at the start of the drive is the Master Boot Record. If Grub also writes to the MBR which is the default installation then you can boot whatever operating systems are listed in Grub when you power up. If Grub doesn't write to the MBR then you have to use another method of booting the Grub configuration in /boot, such as using a CD or a floppy disc.

Now, for some reason when you installed Ubuntu, Grub didn't write to the MBR. We tried to do it with the grub-install command but it didn't work.

Grub is definitely installed with Ubuntu it's just not working for you.

It's very odd that you have two drives that look to be exact copies of each other, hence my thinking it was a RAID set up. Not being able to get Grub on the MBR suggests a BIOS setting problem. But nothing seems to work. Now with your CD problems things are going rapidly downhill.

If you try a reinstall, do you get any clues as to why you have the copies on two drives?

---

### Post by Spazmunki13 on 2009-11-07
I don't know if this helps, but when I install Ubuntu it doesn't ask me which hard drive to install it on. It just allows me to partition it (whatever that may be.)

---

### Post by mechro on 2009-11-07
> **Spazmunki13 said:**
> I don't know if this helps, but when I install Ubuntu it doesn't ask me which hard drive to install it on. It just allows me to partition it (whatever that may be.)

As I said, seeing it as one drive suggests RAID.

I get the feeling that Intel have set it up to make it as difficult as possible to run it any other way than the way they want you to run it. You need a hardware guru.

---

### Post by Spazmunki13 on 2009-11-07
My computer was custom made by a friend of my mom's...

I'm about to give up to return to the dreaded Windows... :(

EDIT: Maybe if I try an older version of Ubuntu?

---

### Post by mechro on 2009-11-07
> **Spazmunki13 said:**
> My computer was custom made by a friend of my mom's...



Isn't that your guru? Could they help? It might be cables and/or jumper settings inside your computer.

---

### Post by mechro on 2009-11-07
> **Spazmunki13 said:**
> 

EDIT: Maybe if I try an older version of Ubuntu?

Might be worth trying. But it might be worth trying a different Linux Distro. Trouble is there's hundreds of them. I'd suggest Linux Mint, OpenSuse, Mandriva.

---

### Post by Spazmunki13 on 2009-11-07
My mom isn't in touch with them anymore. Would it be complicated to get those other distros installed? Is there any coding?

---

### Post by mechro on 2009-11-07
They have similar desktops and graphical stuff like Ubuntu. Coding is there if you want it just as in Ubuntu.

Linux Mint is actually built on Ubuntu so you'll find that quite familiar apart from the theme.

[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

---

### Post by Spazmunki13 on 2009-11-08
I FINALLY got it working! :D (I double check that, maybe even triple check that just to make sure)

I was pulling at strings and decided to look up something on google though I can't remember what and I got this negative review of Ubuntu... anyways reading through it the person mentioned they had to go into "Advanced" at the end of the install because Ubuntu wasn't recognizing the hard drives in the correct booting order.

So I decided to give it a try and it worked! :D

All I did was switch the (hd0) to (hd1).

Thanks a lot for your help Mechro, it was very much appreciated. :)

Matt

---

### Post by mechro on 2009-11-08
That's brilliant.

I'm still totally baffled. If you remember the grub-install we did, that should have put Grub in (hd0) and (hd1).

Anyway, I'm glad you solved it. Cheers :D

---

### Post by Spazmunki13 on 2009-11-15
Argh! It's happened again.

I messed up Ubuntu by trying to format my second hard drive and I'm back at step one of not being able to install Ubuntu again.

So scratch the whole (hd0) and (hd1) thing cause it obviously didn't work. Must've been luck...

---

### Post by mechro on 2009-11-15
Perhaps you should try Super Grub Disk. At least it will probably boot your Ubuntu even if you can't yet fix your boot loading problems.

Super Grub Disk will find any installed systems and enable you to boot them.

Information...

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

Download...

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

Go for the **super grub disk 0.9799.iso**

---

### Post by Spazmunki13 on 2009-11-17
Thanks again Mechro. :)

I'll give that a try.

---

