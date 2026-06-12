---
title: "Plextor 712SA DVD burner doesn't write"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by agatha on 2007-01-13
Hi
I have recently converted this PC to Ubuntu with a great deal of success, but I am stumped with this problem and would appreciate any assistance in the plainest possible language as I am still coming to terms with *basic* Linux commands.

I have used this PC and its peripherals under XP Pro for over 2 years without probs, so I know that the hardware works.

I use a SONY CRX 320E DVD player and the PLEXTOR DVD writer.
When I installed Ubuntu it detected the SONY OK first up, because its a PATA device, whereas the PLEXTOR is a SATA device, like the extra HD drives (the boot disk is a simple 80Gb IDE). It will read but refuses to write - see error messages below.

Whilst I managed to mount the SATA HDs OK I can't get the PLEXTOR to work.
I have tried to edit /etc/fstab to no avail following instructions posted on tuXfile.

The error/debug messages I get from software (GnomeBaker, K3B,Acidrip) is consistently similar to:

" unable to TEST UNIT READY: Input/output error
unable to SYNCHRONOUS FLUSH CACHE: Input/output error " ,and

" :-[ WRITE@LBA=30h failed with SK=0h/ASC=00h/ACQ=03h]: Input/output error
write failed: Input/output error
/dev/sr0: flushing cache
unable to TEST UNIT READY: Input/output error
unable to SYNCHRONOUS FLUSH CACHE: Input/output error"

Please help .

Thank you

---

### Post by robenroute on 2007-01-13
Could you please post more info: what motherboard are you using and what does your fstab look like?

Thanks

---

### Post by agatha on 2007-01-13
Hi 
Thanks for reply.

I use a Gigabyte GA 8I915P Duo (Pro) mobo.

This is my fstab:
"# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hde        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdc1	/media/MyFiles	ext3	defaults	0	0
/dev/sr0        /media/cdrom0	auto	rw,noauto,user,exec	0	0"

The last line is the added entry. Made it up from info found on tuXfile website.

Thankyou.

---

### Post by robenroute on 2007-01-14
Have a look at the the following page, it might shed some light:

[http://www.ofb.biz/article.pl?sid=339]("http://www.ofb.biz/article.pl?sid=339")

By the way, in your fstab file, you have both /dev/hde (your Sony, I presume) and /dev/sr0 (your Plextor) mounted on /media/cdrom0; that can't be good.... ;)

---

### Post by agatha on 2007-01-18
> **robenroute said:**
> Have a look at the the following page, it might shed some light:

[http://www.ofb.biz/article.pl?sid=339]("http://www.ofb.biz/article.pl?sid=339")

By the way, in your fstab file, you have both /dev/hde (your Sony, I presume) and /dev/sr0 (your Plextor) mounted on /media/cdrom0; that can't be good.... ;)

Thanks for the ofb article. Have looked at it and several others. PLextor refuses to write. Took your advice, though and mounted separately on /media/cdrom1. My fstab and/or hdparm.config entries are most likely completely wrong, because I can't digest the info I read properly; but I try.

If you understand the comments in terminal from the mount command and/or the syslog (dmesg | tail) I would appreciate your interpretation. The reference to the "sense key" and "ioctl" appear to be consistent with the debug msgs I get from the software.
Another thing I don't understand is the ref to LBA there.

Thanks again for your help


franz@Rubens:~$ sudo mount /media/cdrom1/ -o unhide
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

franz@Rubens:~$


fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hde        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdc1	/media/MyFiles	ext3	defaults	0	0
/dev/scd0	/media/cdrom1	udf,iso9660 rw,noauto,user,exec     0	0



hdparm.config
...
/dev/scd0 { dma = on io32_support = 1 }


dmesg | tail
[17191822.824000] sr: Current [descriptor]: sense key: Aborted Command
[17191822.824000]     Additional sense: No additional sense information
[17191822.832000] ata3: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/ 00/00
[17191822.832000] ata3: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/ 00/00
[17191822.836000] ata3: translated ATA stat/err 0x51/54 to SCSI SK/ASC/ASCQ 0xb/ 00/00
[17191822.836000] sr0: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[17191822.836000] sr: Current [descriptor]: sense key: Aborted Command
[17191822.836000]     Additional sense: No additional sense information
[17191822.868000] Unable to identify CD-ROM format.
[17192299.788000] Inbound IN=eth0 OUT= MAC=00:0f:ea:4f:67:c2:00:09:5b:1c:9e:52:0 8:00 SRC=192.168.0.127 DST=192.168.0.227 LEN=198 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=178

---

### Post by robenroute on 2007-01-18
I noticed in your latest fstab that your Plextor is referred to as "/dev/scd0", while in the initial fstab you posted, it was "/dev/sr0". Why is this, typo?

Your fstab should read something like:
...
...
/dev/hde /media/cdrom0 auto defaults 0 0
/dev/sr0 /media/cdrom1 auto defaults 0 0
...

Make sure the cdrom1 directory exists in /media and give it the same permissions and user/group settings as /media/cdrom0 (because that one worked). Now, every time your system boots, everything should be mounted correctly.

---

### Post by agatha on 2007-01-23
Thanks for the help. I've changed the fstab.
The Plextor automounts when I insert ablank DVD. The refrence to it as sr0 wa staken from a debug message I got from the authoring software. However, both the Device Manager and the  Disks Manager report it as /dev/scd0. So, that's why I changed it.

The problem however remains. I can't write.
If I point to an ISO file it will run for about 3 minutes and terminate with the message "unhandled error" - but the disk has actually been written to.See attachment 2

If I point to the Video_TS files the system tells me immediately that there is insufficient space (NB on a new DVD) see attachmnents 3 and 3a

Whats wrong ?

---

### Post by robenroute on 2007-01-23
> **agatha said:**
> Thanks for the help. I've changed the fstab.
The Plextor automounts when I insert ablank DVD. The refrence to it as sr0 wa staken from a debug message I got from the authoring software. However, both the Device Manager and the  Disks Manager report it as /dev/scd0. So, that's why I changed it.

The problem however remains. I can't write.
If I point to an ISO file it will run for about 3 minutes and terminate with the message "unhandled error" - but the disk has actually been written to.See attachment 2

If I point to the Video_TS files the system tells me immediately that there is insufficient space (NB on a new DVD) see attachmnents 3 and 3a

Whats wrong ?

Agatha, to be honest (as if I'm normally not honest.... ;) ), I've got no idea. I had a quick look on the forums here, but it seems you're not the only person with a Plex 712SA having troubles. Perhaps you could contact one of these people and leave a message for them asking how they solved their Plex issues.

Sorry I can't help you at this particular moment. Good luck and do keep us posted regarding your progress (if any).

---

### Post by Juissi on 2007-01-25
> **robenroute said:**
> Agatha, to be honest (as if I'm normally not honest.... ;) ), I've got no idea. I had a quick look on the forums here, but it seems you're not the only person with a Plex 712SA having troubles. 

I have a Plextor 712 PATA, never managed to burn a DVD succesfully in Ubuntu. Occassionally I'm able to burn a CD. The burner has no problems whatsoever in Windows XP.

Plextor is considered a quality brand and it is, in a Windows environment. Any suggestions for Ubuntu compatible DVD burners?

---

### Post by robenroute on 2007-02-28
Have a look [here]("http://www.ubuntuforums.org/showthread.php?t=354819"). I've just posted a solution to my own SATA burning problem.

Hope it helps.

---

### Post by agatha on 2007-02-28
Thanks !
I'll try that out soon.

---

