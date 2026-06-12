---
title: "CD Burner: Help!"
date: 2005-10-01
forum: Hardware &amp; Laptops
---

### Post by taco on 2005-10-01
I have helped myself as much as possible through use of google and this forum.

Ubuntu is only recognizing my cdwriter as a CD Rom.

I will go ahead and post the outputs that were asked for in similar threads.

```
mike@71-8-63-117:~$ grep -i hdc /var/log/messages.0
Sep 27 22:34:50 localhost kernel: [4294672.047000]     ide1: BM-DMA at 0x10a8-0x 10af, BIOS settings: hdc:pio, hdd:pio
Sep 27 22:34:50 localhost kernel: [4294673.595000] hdc: CR-4804TE, ATAPI CD/DVD- ROM drive
Sep 27 22:34:50 localhost kernel: [4294676.038000] hdc: ATAPI 24X CD-ROM CD-R/RW  drive, 2048kB Cache
mike@71-8-63-117:~$ sudo hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
mike@71-8-63-117:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
mike@71-8-63-117:~$
```

Now, I was given the impression that I needed to change the hdc to hda.

Am I correct?

My other post was moved to this forum, is why I am posting my question here.

---

### Post by taco on 2005-10-01
I also want to add that i have no clue as to why it is bringing up 2 devices when i only have one cd/cdrw device.

---

### Post by taco on 2005-10-01
-bump-

---

### Post by taco on 2005-10-02
-rebump-

---

### Post by bjweeks on 2005-10-02
This is the wrong forum to post this in, you will get more help by posting this in the proper forum. Eg. 5.04 hardware help

---

### Post by GTvulse on 2005-10-02
Hmmm.... Does the output of ```
cdrecord dev=ATA:1,0,0 -prcap
``` detect the drive as a CD-RW device?

---

### Post by taco on 2005-10-02
-edited-

---

### Post by taco on 2005-10-02
[QUOTE=dradul]Hmmm.... Does the output of ```
cdrecord dev=ATA:1,0,0 -prcap
``` detect the drive as a CD-RW device?[/QUOTE]
```


mike@71-8-63-117:~$ cdrecord dev=ATA:1,0,0 -prcap
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-9-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: 'ATA:1,0,0'
devname: 'ATA'
scsibus: 1 target: 0 lun: 0
Warning: Using badly designed ATAPI via /dev/hd* interface.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'MITSUMI '
Identifikation : 'CR-4804TE       '
Revision       : '2.6C'
Device seems to be: Philips CDD-522.

Drive capabilities, per MMC page 2A:

  Does read CD-R media
  Does write CD-R media
  Does read CD-RW media
  Does write CD-RW media
  Does not read DVD-ROM media
  Does not read DVD-R media
  Does not write DVD-R media
  Does not read DVD-RAM media
  Does not write DVD-RAM media
  Does support test writing

  Does read Mode 2 Form 1 blocks
  Does read Mode 2 Form 2 blocks
  Does read digital audio blocks
  Does restart non-streamed digital audio reads accurately
  Does not support Buffer-Underrun-Free recording
  Does read multi-session CDs
  Does read fixed-packet CD media using Method 2
  Does not read CD bar code
  Does read R-W subcode information
  Does not return R-W subcode de-interleaved and error-corrected
  Does not read raw P-W subcode data from lead in
  Does return CD media catalog number
  Does return CD ISRC information
  Does support C2 error pointers
  Does not deliver composite A/V data

  Does play audio CDs
  Number of volume control levels: 2
  Does not support individual volume control setting for each channel
  Does not support independent mute setting for each channel
  Does not support digital output on port 1
  Does not support digital output on port 2

  Loading mechanism type: tray
  Does support ejection of CD via START/STOP command
  Does not lock media on power up via prevent jumper
  Does allow media to be locked in the drive via PREVENT/ALLOW command
  Is not currently in a media-locked state
  Does not support changing side of disk
  Does not have load-empty-slot-in-changer feature
  Does not support Individual Disk Present feature

  Maximum read  speed:  4234 kB/s (CD  24x, DVD  3x)
  Current read  speed:  4234 kB/s (CD  24x, DVD  3x)
  Maximum write speed:   706 kB/s (CD   4x, DVD  0x)
  Current write speed:   706 kB/s (CD   4x, DVD  0x)
  Buffer size in KB: 2048
```

---

### Post by GTvulse on 2005-10-03
You are being neurotic! (Neurosis: the ability to find a problem to every solution). :-)

See the output:
```
Drive capabilities, per MMC page 2A:
Does read CD-R media
Does write CD-R media
Does read CD-RW media
Does write CD-RW media
```
You're CD-RW is recognized just fine.

You cutted and pasted together three lines that are output at different stages of the bootup process (several lines apart from each other!!!) and created yourself a horrible mental movie. Bet you are into disaster movies.  :p 

You may want to edit your /etc/default/cdrecord file to contain the following lines (read the comments in the file first!):
```
CDR_DEVICE=cdrw
cdrw=           ATA:1,0,0       -1      -1      ""

```
where the columns are separated by tabs, not spaces. These lines will make your CD-RW cdrecord's default so that you don't need to type "dev=ATA:1,0,0" every time you want to burn a CD from the command line. The name is irrelevant as long as there are no spaces; you could call it "supercalifragilisticspialidosus" if you wish. :-)

---

### Post by taco on 2005-10-03
[angry ubuntu n00b]dev=ATA:1,0,0 in the terminal does nothing. I tried burning a disc shortly after i entered this and it said "please insert blank disc" all of my cdr discs are blank.

Am I to assume that adding these lines in would do the same thing? (yes, i see that you'd have to open it with a text editor)

X that, just give me a f*#king hammer.[/angry ubuntu n00b]

---

### Post by GTvulse on 2005-10-03
You should see me when I go in a neurotic spin!  :twisted: 

I missed this line in the output:
```

Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted

```
Try with ```
sudo cdrecord dev=ATA:1,0,0 -sao your_image.iso
``` or run ```
sudo dpkg-reconfigure cdrecord
``` and pick the option to run it as suid root.

BUT... By default, Gnome's automounter detects when you insert a blank disc and will pop up an icon on the desktop. When this happens gnome's own burner application takes control and locks out the block device (/dev/hdc in this case) to prevent interference from other processes trying to write to the blank disc. You can solve this by several means:
[list=1]
[*] Unmount, not eject, the device before accessing it with cdrecord, using the command ```
sudo umount /dev/hdc
``` Or,
[*] Use a dedicated application that takes care of the details for you, such as GnomeBaker or Graveman for Gnome (both are in Universe), or K3b for KDE. Or,
[*] My personal favorite, use Gnome's CD/DVD burning facilities. In any Nautilus explorer window go to CD/DVD Burner in the "Go" menu, drag and drop the files you want written to the CD and then you write them by selecting a command in the file menu. Or type Control-L and type "burn:///" and return. Copying ISO files is equally easy, right-click on the disc image icon and select "write to CD/DVD". Easier than the builtin burner in Windows XP, IMO.
[/list]
When you feel more at ease with Linux you may even produce your own ISO images with mkisofs (a command line utility) instead of using the graphical interface.

---

### Post by taco on 2005-10-04
Ahhh! Just what I needed. The gui burning still doesn't work, but that isn't a must.

Thanks dradul! :)

---

