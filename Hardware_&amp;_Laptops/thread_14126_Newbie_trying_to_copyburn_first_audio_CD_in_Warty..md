---
title: "Newbie trying to copy/burn first audio CD in Warty."
date: 2005-02-05
forum: Hardware &amp; Laptops
---

### Post by globetrotterdk on 2005-02-05
I am continuing to deal with a problem that I haven't been as of yet able to solve on the Ubuntu Users e-mail list. I am trying to burn a copy of an audio CD in Ubuntu. I have two CD-R, RW, DVD-R drives on my computer, listed in etc/fstab as:

/dev/hdh        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdg        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

/media/cdrom0 is listed as: JLMS XJ-HD165H
/media/cdrom1 is listed as: SONY CD-RW CRX320E

I have the audio CD placed in /media/cdrom0 and the blank CD-R disc in /media/cdrom1 Both Ryhythmbox and Sound Juicer recognize the drives and audio disks in them, though I sometimes have to try 2 or 3 times before they are recognized correctly.

When I try to create an ISO image according to the instructions in the Starter's Guide sudo dd if=/dev/cdrom of=file.iso bs=1024, I get the following:

dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out
0 bytes transferred in 0.014510 seconds (0 bytes/sec)

Not including sudo returns the same:

dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out
0 bytes transferred in 0.016960 seconds (0 bytes/sec)

I have tried gksudo nautilus burn:/// and then chosen CD Creator under the "places" menu. When I drop Wave files that I have ripped from the audio CD on to this window and try to burn a CD, the image creation seems to go fine, when the CD Creator tries to burn the image, I get the following:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
scsidev: '/dev/hdg'
devname: '/dev/hdg'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.90 04/01/14 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: Warning: controller returns wrong size for CD capabilities page.
cdrecord: Warning: controller returns wrong size for CD capabilities page.
cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
cdrecord: Warning: controller returns wrong size for CD capabilities page.
cdrecord: Drive does not support TAO recording.
cdrecord: Illegal write mode for this drive.

I am not really sure what to try now to fix this problem. Does anyone have any ideas?

Cheers,

Brian

---

### Post by malegria on 2005-02-05
Run: ```
sudo gedit /etc/fstab
``` 
Edit these lines:
/dev/hdh /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/hdg /media/cdrom1 udf,iso9660 ro,user,noauto 0 0

to look like:
/dev/hdh /media/cdrom0 udf,iso9660 rw,user,noauto 0 0
/dev/hdg /media/cdrom1 udf,iso9660 rw,user,noauto 0 0

What you did was change the drives from 'ro'(read-only) to 'rw' (read-write) so that you can now burn. Also, GNOME doesn't have a good cd-burner program. I suggest you install K3b and kdelibs to have it run.(this can be easily done by going: Computer ---> System Configuration ---> Synaptic Package Manager.)

And another thing, many little Ubuntu issues can find their answers @ [www.ubuntuguide.org](www.ubuntuguide.org) 

Good luck!

---

### Post by globetrotterdk on 2005-02-06
I installed K3B and here are the results:
gksudo in terminal returns:

2x32/stock/document not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/object not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/text not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/chart not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/code not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/data not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/document not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/object not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/text not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/chart not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/code not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/data not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/document not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/object not valid.
kdecore (KIconLoader)Launched ok, pid = 5658
: WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/text not valid.
ALSA lib pcm_hw.c:549:(snd_pcm_hw_start) SNDRV_PCM_IOCTL_START failed: Broken pipe
ALSA lib pcm_hw.c:549:(snd_pcm_hw_start) SNDRV_PCM_IOCTL_START failed: Broken pipe
ALSA lib pcm_hw.c:549:(snd_pcm_hw_start) SNDRV_PCM_IOCTL_START failed: Broken pipe
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Bluecurve/ group 96x96/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Bluecurve/ group 48x48/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Bluecurve/ group 48x48/stock not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Bluecurve/ group 24x24/stock not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Bluecurve/ group 16x16/stock not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 20x20/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 48x48/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 48x48/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 24x24/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 72x72/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 72x72/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 192x192/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 36x36/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 12x12/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 96x96/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 96x96/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Default/ group 192x192/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Default/ group 96x96/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Default/ group 72x72/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Default/ group 48x48/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Default/ group 36x36/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Default/ group 24x24/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Default/ group 12x12/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Default/ group scalable/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 20x20/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 48x48/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 48x48/devices not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 48x48/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 72x72/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 72x72/devices not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 24x24/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 24x24/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 192x192/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group scalable/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 36x36/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 36x36/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 12x12/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 12x12/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Flat-Blue/ group 96x96/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/gnome/ group 192x192/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/gnome/ group 96x96/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/gnome/ group 72x72/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/gnome/ group 48x48/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/gnome/ group 36x36/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/gnome/ group 24x24/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/gnome/ group 12x12/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/gnome/ group scalable/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/chart not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/code not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/data not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/document not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/object not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/text not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/chart not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/code not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/data not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/document not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/object not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/text not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/chart not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/code not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/data not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/document not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/object not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/text not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/chart not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/code not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/data not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/document not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/object not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/text not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/chart not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/code not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/data not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/document not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/object not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/text not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Human/ group scalable/apps not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Human/ group scalable/devices not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Human/ group scalable/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Industrial/ group 48x48/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Sandy/ group 36x36/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Sandy/ group 12x12/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Sandy/ group 48x48/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Sandy/ group 96x96/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Sandy/ group 72x72/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Sandy/ group 24x24/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Smokey-Blue/ group 48x48/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Smokey-Blue/ group 48x48/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Smokey-Red/ group 48x48/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Smokey-Red/ group 48x48/emblems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/chart not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/code not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/data not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/document not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/object not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 16x16/stock/text not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/chart not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/code not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/data not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/document not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/object not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 24x24/stock/text not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/chart not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/code not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/data not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/document not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/object not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 32x32/stock/text not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/chart not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/code not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/data not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/document not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/object not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 36x36/stock/text not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/chart not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/code not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/data not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/document not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/object not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/text not valid.
wave lookup: want=440.000000 got=440.000000 length=15625
filter: fc=0.816327 fr=1.088435 st=0.362812 is=23777
clearing filter state at:
0) -0.00000000000000000000005200705720978351
1) -0.00000000000000000000003233393856132001
2) +0.00000000000000000000006751608296350812
3) -0.00000000000000000000008444709798887145
4) -0.00000000000000000000008706074611603756
5) +0.00000000000000000000002613585233381543
6) +0.00000000000000000000007671945144993255
7) +0.00000000000000000000001328910693310606
QMetaObject

OK, that is the startup. It seems that among other things, K3B doesn't like that I have installed the Red Hat Bluecurve theme as described in this forum.

When K3B tries to write to CD I get the following:
Errors in K3b progress window:

RAW recording not supported with this writer.
cdrecord returned an unknown error (code 255).
Unknown error 255.
Please send me an email with the last output.

Debugging output:
System
-----------------------
K3b Version:0.11.12 
KDE Version: 3.2.3
QT Version: 3.2.3

cdrecord
-----------------------
scsidev: '/dev/hdg'
devname: '/dev/hdg'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/bin/cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 <snip>).
SCSI buffer size: 64512
/usr/bin/cdrecord: Warning: controller returns wrong size for CD capabilities page.
/usr/bin/cdrecord: Warning: controller returns wrong size for CD capabilities page.
/usr/bin/cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
/usr/bin/cdrecord: Warning: controller returns wrong size for CD capabilities page.
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
<snip>
TOC Type: 0 = CD-DA
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identifikation : 'CD-RW  CRX320E  '
Revision       : 'NYK1'
Device seems to be: Generic CD-ROM.
Using generic SCSI-2       CD-ROM driver (scsi2_cd).
Driver flags   : 
Supported modes: 
FIFO size      : 4194304 = 4096 KB
Encoding speed : 322x (24106 sectors/s) for libedc from Heiko Eißfeldt
pregap1: -1
/usr/bin/cdrecord: Drive does not support RAW recording.
/usr/bin/cdrecord: Illegal write mode for this drive.

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdg speed=40 -raw driveropts=burnfree -eject -text -useinfo -audio -shorttrack /tmp/kde-root/k3bCdCopy0/Track01.wav /tmp/kde-root/k3bCdCopy0/Track02.wav /tmp/kde-root/k3bCdCopy0/Track03.wav /tmp/kde-root/k3bCdCopy0/Track04.wav /tmp/kde-root/k3bCdCopy0/Track05.wav /tmp/kde-root/k3bCdCopy0/Track06.wav /tmp/kde-root/k3bCdCopy0/Track07.wav /tmp/kde-root/k3bCdCopy0/Track08.wav /tmp/kde-root/k3bCdCopy0/Track09.wav /tmp/kde-root/k3bCdCopy0/Track10.wav /tmp/kde-root/k3bCdCopy0/Track11.wav 

After closing down K3B I get this in the terminal:
k3b: WARNING: Can't open /root/.kde/share/apps/konqueror/bookmarks.xml
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
k3b: ERROR: (K3bSongManager) Can't open file /root/.kde/share/apps/k3b/songlist.xml
Mutex destroy failure

ANy ideas about any of this?

Cheers,

Brian

---

### Post by malegria on 2005-02-06
You problem may very well lie with KDE. It does seem it doesn't like that theme which might have not been installed correctly. Or maybe because it's a RedHat theme. I don't use KDE in Ubuntu. I just run GNOME. Sorry.

---

### Post by mirtux on 2005-02-08
For the WARNING problem i think there is no problem, since i have the same errors but k3b is performing well. The same is valid for the errors it gives you when you close the session.
   
 For the main problem i have just an idea: i've read of problem regarding k3b and its use as a non-root user. Try to burn CD's with _*root permission*_ [img]http://www.ubuntuforums.org/images/smilies/icon_cool.gif[/img](**sudo k3b**) and see if the result is the same.
   
   Regards,
   MC

---

### Post by globetrotterdk on 2005-02-08
[QUOTE=][/QUOTE]
 Nope, sudo doesn't help. K3B returns:

System
-----------------------
K3b Version:0.11.12 
KDE Version: 3.2.3
QT Version: 3.2.3

cdrecord
-----------------------
scsidev: '/dev/hdg'
devname: '/dev/hdg'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/bin/cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.90 04/01/14 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/cdrecord: Warning: controller returns wrong size for CD capabilities page.
/usr/bin/cdrecord: Warning: controller returns wrong size for CD capabilities page.
/usr/bin/cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
/usr/bin/cdrecord: Warning: controller returns wrong size for CD capabilities page.
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identifikation : 'CD-RW  CRX320E  '
Revision       : 'NYK1'
Device seems to be: Generic CD-ROM.
Using generic SCSI-2       CD-ROM driver (scsi2_cd).
Driver flags   : 
Supported modes: 
FIFO size      : 4194304 = 4096 KB
Encoding speed : 321x (24069 sectors/s) for libedc from Heiko Eißfeldt
pregap1: -1
/usr/bin/cdrecord: Drive does not support RAW recording.
/usr/bin/cdrecord: Illegal write mode for this drive.

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdg speed=40 -raw driveropts=burnfree -eject -text -useinfo -audio -shorttrack /tmp/kde-brian/k3bCdCopy0/Track01.wav /tmp/kde-brian/k3bCdCopy0/Track02.wav /tmp/kde-brian/k3bCdCopy0/Track03.wav /tmp/kde-brian/k3bCdCopy0/Track04.wav /tmp/kde-brian/k3bCdCopy0/Track05.wav /tmp/kde-brian/k3bCdCopy0/Track06.wav /tmp/kde-brian/k3bCdCopy0/Track07.wav /tmp/kde-brian/k3bCdCopy0/Track08.wav /tmp/kde-brian/k3bCdCopy0/Track09.wav /tmp/kde-brian/k3bCdCopy0/Track10.wav /tmp/kde-brian/k3bCdCopy0/Track11.wav

---

### Post by hashimoto on 2005-02-08
Howabout using xcdroast? Mine works fine with CDR & CDRW though I had to manually add the devices when running the setup as root.

Hashimoto

---

### Post by globetrotterdk on 2005-02-08
Uhmm, unfortunately something else happened in the meantime. Apparently (as this was the only thing I did in the session) the sudo k3b command somehow screwed up my ICE authority file. When I try to boot Ubuntu into Gnome, I get the message: 

"session: (5138) : WARNING **: Unable to read ICE authority file: (location)"

I know this was on the e-mail list, but I thought the thread had something to do with IceWM, which I am not using, so I chucked the thread. Can anyone give the short version so that I can get this cleared up in a jiffy? I am using Warty.

Cheers,

Brian

---

### Post by ubuntu_fan on 2005-02-08
See [http://www.ubuntuforums.org/showthread.php?t=9649](http://www.ubuntuforums.org/showthread.php?t=9649)

a.

---

### Post by globetrotterdk on 2005-02-08
Many thanks that was a real life saver 8-) I used sudo, not local user as mentioned in that thread and ran into the same problem. I still have the problem that I can't burn a CD though. I'll try to reinstall xcdroast, but...

Cheers,

Brian

---

### Post by hashimoto on 2005-02-08
Remember to run sudo xcdroast first time and select the setup. Fill in necessary data to all pages. I had to add /dev/hdc and /dev/hdd. Also tell which foler to use as temporary for copying CD's (something in users home folder) and make sure that all users are enabled (don't remember the actual term used. non-root or something).

Hashimoto

---

### Post by globetrotterdk on 2005-02-08
Started by using sudo xcdroast, but got a message blubbering on about SCSI emulation needing to be turned on as I have 2 ATAPI/IDE CD-R, RW, DVD-R drives. Is this the problem that I have with Nautilus/cdrecord also? I don't get it. I am using Warty, so I shouldn't need SCSI emulation with kernel (whatever) in Warty which is at least  2.4 something, right? I am looking at the X-CD Roast FAQ trying to make heads or tails of it, but without much luck. It seems like I have to add 2 lines to /etc/modules.conf:

options ide-cd ignore='hdg hdd' 
options ide-cd ignore='hdh hdd' 

and then add in grub:

hdg=ide-scsi hdd=ide-scsi (Kernel 2.2.x and most 2.4.x)
hdh=ide-scsi hdd=ide-scsi (Kernel 2.2.x and most 2.4.x)
    or

hdg=scsi hdd=scsi (Kernel 2.4.x only, if the above line does not work) 
hdh=scsi hdd=scsi (Kernel 2.4.x only, if the above line does not work)


Maybe I will have to load the driver manually (???):
/sbin/insmod ide-scsi; /sbin/insmod sg 

Umm and why do more newbies not use xcdroast if they can avoid it?

Cheers,

Brian

---

### Post by zombie1991 on 2005-02-08
[QUOTE=globetrotterdk]Started by using sudo xcdroast, but got a message blubbering on about SCSI emulation needing to be turned on as I have 2 ATAPI/IDE CD-R, RW, DVD-R drives. Is this the problem that I have with Nautilus/cdrecord also? I don't get it. I am using Warty, so I shouldn't need SCSI emulation with kernel (whatever) in Warty which is at least  2.4 something, right? I am looking at the X-CD Roast FAQ trying to make heads or tails of it, but without much luck. It seems like I have to add 2 lines to /etc/modules.conf:

options ide-cd ignore='hdg hdd' 
options ide-cd ignore='hdh hdd' 

and then add in grub:

hdg=ide-scsi hdd=ide-scsi (Kernel 2.2.x and most 2.4.x)
hdh=ide-scsi hdd=ide-scsi (Kernel 2.2.x and most 2.4.x)
    or

hdg=scsi hdd=scsi (Kernel 2.4.x only, if the above line does not work) 
hdh=scsi hdd=scsi (Kernel 2.4.x only, if the above line does not work)


Maybe I will have to load the driver manually (???):
/sbin/insmod ide-scsi; /sbin/insmod sg 

Umm and why do more newbies not use xcdroast if they can avoid it?

Cheers,

Brian[/QUOTE]
 Try this:  [http://gnomebaker.sourceforge.net/](http://gnomebaker.sourceforge.net/)

See if you can get rid of k3b if you want to keep a clean gnome.  I've used k3b exclusively in the past and love it...but boy can it be a bear to install.  The above is a good gnome version of k3b and it even has an Ubuntu deb :-)

---

### Post by globetrotterdk on 2005-02-08
Ok, I'll give that a try.

1) The web site says GnomeBaker needs oggdec and growisofs, but I can't find those listed anywhere in Synaptic.

2) How do I get rid of K3B and make sure all of the KDE dependencies that aren't needed for anything else get trashed?

Cheers,

Brian

---

### Post by globetrotterdk on 2005-02-09
OK, I got GnomeBaker installed. It also worked fine until it needed to burn the CD. Here is the resonse:

cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdg'
devname: '/dev/hdg'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.90 04/01/14 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: Warning: controller returns wrong size for CD capabilities page.
cdrecord: Warning: controller returns wrong size for CD capabilities page.
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 J rg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

Do I have to run as sudo even if my fstab entries:

/dev/hdh        /media/cdrom0   udf,iso9660 rw,user,noauto  0       0
/dev/hdg        /media/cdrom1   udf,iso9660 rw,user,noauto  0       0

Is the problem something else? Anyone?

Cheers,

Brian

---

### Post by globetrotterdk on 2005-02-10
OK, here is an update for anyone reading (???) this: I plugged in a BAFO USB 2 CD-R, RW, DVD-R into my Ubuntu Warty box. It isn't listed in the "computer" window, but if I put an audio CD in, it starts playing and if I place a data CD in, it shows up on the desktop. GnomeBaker will not recognize it, but if I place an unused CD-R in, the CD Creator window pops up. The drive is listed in CD Creator as: CDRW/DVD SBW242U. I tried copying .wav files to the Creator window to burn a CD and successfully burned a CD. I was trying to burn an audio CD, but ended up burning a data CD with .wav files on it. Not really sure how that happened... I have now ascertained that I can burn a CD with my system, but something weird is still happening somewhere.

Cheers,

Brian

---

