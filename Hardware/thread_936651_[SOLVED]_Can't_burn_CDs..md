---
title: "[SOLVED] Can't burn CDs."
date: 2008-10-03
forum: Hardware
---

### Post by PeregrinGo on 2008-10-03
I'm new to Ubuntu (I've only been using it a couple months now), and up until now, I've found answers and solutions for most all problems and errors I have encountered. Given that I mostly use my flash drive for small file transfers, I haven't even attempted to burn a CD until now. However, upon trying to create an ".iso" disc of Partition Logic, I have consistently come up against an error. Depending on whether I use Brasero, CD/DVD Creator or simply right click, the message I receive may vary slightly. I have tried multiple media and write speeds. I have looked and looked via google and the forums, but so far nothing seems to quite match this issue.

I recorded my last Brasero Session log and thought this might assist someone in assisting me. Thanks in advance!

-------------------------

Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
Inconsistent flag: you can't use flag on_the_fly (brasero_burn_check_session_consistency burn.c:1810)
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum deactivating
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum output set (IMAGE) image = /tmp/brasero_tmp_OA8JIU toc = (null)
BraseroMd5sum called brasero_job_get_session_output_size
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum called brasero_job_set_current_action
BraseroMd5sum called brasero_job_start_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum setting new checksum 4e1a26405d226564730087b44d0afae5 ((null) before)
BraseroMd5sum finished track successfully
BraseroMd5sum stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_Y8VPIU toc = (null)
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
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
	dev=/dev/scd0
	gracetime=0
	speed=5
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/harold/Desktop/partlogic-0.69.iso
BraseroWodim launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/scd0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.6
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
BraseroWodim stdout: Vendor_info    : 'CENDYNE_'
BraseroWodim stderr: cmd finished after 347.571s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Identification : '481648AX        '
BraseroWodim stdout: Revision       : '120F'
BraseroWodim stdout: Device seems to be: Generic mmc CD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-2 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1806336 = 1764 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: wodim: Cannot load media.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim stdout: Track 01: data     9 MB        
BraseroWodim stdout: Total size:       10 MB (01:02.81) = 4711 sectors
BraseroWodim stdout: Lout start:       10 MB (01:04/61) = 4711 sectors
BraseroWodim stdout: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2273)
------------------------

---

### Post by PeregrinGo on 2008-10-03
>>Bump<<

---

### Post by PeregrinGo on 2008-10-03
::Bump::

---

### Post by melojo on 2008-10-03
try installing k3b or xcdroast and see if it works.

---

### Post by melojo on 2008-10-03
You can install both with the package manager or type this in a console
sudo apt-get install k3b or sudo apt-get install xcdroast

---

### Post by PeregrinGo on 2008-10-03
I appreciate your reply. I'm in the process of downloading it now, but because of my location deep in the sticks, my only connection comes via dialup. I'm somewhat doubtful this will work, as Brasero and Nautilus failed to function. But I'm gonna give it a shot. I'll let you know what happens.

---

### Post by PeregrinGo on 2008-10-03
Unfortunately, K3b (which I was able to download after about 2 hours) does nothing to remedy this issue. It registered the following error: "Cdrecord has no permission to open the device."

The debugging output produced the following:
--------------------------------------------
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
CENDYNE_ 481648AX 120F (/dev/scd0, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

CREATIVE CD5233E-CF 1.04 (/dev/scd1, ) [CD-ROM] [Error] [None]
K3bIsoImager
-----------------------
mkisofs print size result: 17328 (35487744 bytes)
Pipe throughput: 124928 bytes read, 104448 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'CENDYNE_'
Identification : '481648AX        '
Revision       : '120F'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1806336 = 1764 KB
FIFO size      : 12582912 = 12288 KB
Errno: 5 (Input/output error), read buffer scsi sendcmd: no error
CDB:  3C 00 00 00 00 00 00 FC 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 02 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x02 (end-of-partition/medium detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 187.512s timeout 40s
/usr/bin/wodim: Cannot load media.
/usr/bin/wodim: Cannot eject media.
Track 01: data    33 MB        
Total size:       38 MB (03:51.06) = 17330 sectors
Lout start:       39 MB (03:53/05) = 17330 sectors

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=10 -tao driveropts=burnfree -eject -multi -xa -tsize=17328s - 

mkisofs
-----------------------
17328
I: -input-charset not specified, using utf-8 (detected in locale settings)

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid rFw2bQ280083-02 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-harold/k3bE1nF0a.tmp -rational-rock -hide-list /tmp/kde-harold/k3bQcwS5a.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-harold/k3blMOzlc.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-harold/k3bkI27Xa.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid rFw2bQ280083-02 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-harold/k3bFECPXb.tmp -rational-rock -hide-list /tmp/kde-harold/k3bmS7Lgc.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-harold/k3bVHu0fb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-harold/k3b34RXha.tmp 
------------------------------------------------


Is there anyone with a similar problem and/or solution?

---

### Post by PeregrinGo on 2008-10-03
>>bump<< please help >>bump<<

---

### Post by melojo on 2008-10-04
What happens if you run it with sudo k3b in a terminal. 
sorry it took so long to replay I had to goto work.
Try this link and see if it is useful. its an old one
[http://ubuntuforums.org/showthread.php?t=217472&highlight=k3b+cdrdao](http://ubuntuforums.org/showthread.php?t=217472&highlight=k3b+cdrdao)

---

### Post by Sef on 2008-10-04
> >>bump<< please help >>bump<<


Please don't bump your thread unless 24 hours has gone by.  Thank you.

---

### Post by Yellow Pasque on 2008-10-04
```
gksudo gedit /etc/group
```
Add your user to the cdrom group. See if this fixes the problem. If not, post another log from Brasero.

---

### Post by PeregrinGo on 2008-10-04
> **Sef said:**
> Please don't bump your thread unless 24 hours has gone by.  Thank you.

Ok. I'm sorry: I'm new here, and I just didn't want it to get lost in the fray. :)

---

### Post by PeregrinGo on 2008-10-04
I really appreciate the assistance you two have sought to give. I tried everything outline in the other post as well as the other suggestions you have made. But, as of yet, still no fix. 

When trying to get follow the instructions for Error 2 in the post previously mentioned, I get the errors that appear below:

-------------------------
harold@harold-desktop:~$ sudo chmod 4755 /usr/bin/cdrecord
[sudo] password for harold: 
harold@harold-desktop:~$ sudo chmod 4755 /usr/bin/cdrecord.mmap
chmod: cannot access `/usr/bin/cdrecord.mmap': No such file or directory
harold@harold-desktop:~$ sudo chmod 4755 /usr/bin/X11/cdrecord.mmap
chmod: cannot access `/usr/bin/X11/cdrecord.mmap': No such file or directory
harold@harold-desktop:~$ sudo chmod 4755 /usr/bin/cdrdao
harold@harold-desktop:~$ sudo chmod 4755 /usr/bin/X11/cdrdao
-------------------------


I tried using Brasero and then K3b after attempting the fixes outlined in that post, I get the following messages: 

[LIST=1]
[*]cdrecord returned an uknown error (code 255)
[*]Sometimes using TAO writing mode solves this issue.
[/LIST]


I was going to do try specifying the TAO mode before posting again, but the CD burner freezes up and won't eject, or do anything, for that matter. Thus, I'll have to reboot yet again before I can update you on that one.

---

### Post by melojo on 2008-10-04
> **PeregrinGo said:**
> I really appreciate the assistance you two have sought to give. I tried everything outline in the other post as well as the other suggestions you have made. But, as of yet, still no fix. 

When trying to get follow the instructions for Error 2 in the post previously mentioned, I get the errors that appear below:

-------------------------
harold@harold-desktop:~$ sudo chmod 4755 /usr/bin/cdrecord
[sudo] password for harold: 
harold@harold-desktop:~$ sudo chmod 4755 /usr/bin/cdrecord.mmap
chmod: cannot access `/usr/bin/cdrecord.mmap': No such file or directory
harold@harold-desktop:~$ sudo chmod 4755 /usr/bin/X11/cdrecord.mmap
chmod: cannot access `/usr/bin/X11/cdrecord.mmap': No such file or directory
harold@harold-desktop:~$ sudo chmod 4755 /usr/bin/cdrdao
harold@harold-desktop:~$ sudo chmod 4755 /usr/bin/X11/cdrdao
-------------------------


I tried using Brasero and then K3b after attempting the fixes outlined in that post, I get the following messages: 

[LIST=1]
[*]cdrecord returned an uknown error (code 255)
[*]Sometimes using TAO writing mode solves this issue.
[/LIST]


I was going to do try specifying the TAO mode before posting again, but the CD burner freezes up and won't eject, or do anything, for that matter. Thus, I'll have to reboot yet again before I can update you on that one.

Where you able to burn using sudo? 
sudo k3b

---

### Post by IgnorantGuru on 2008-10-04
Personally, first thing I would do is get wodim out of the loop.  Even if it's not the problem it will only complicate your troubleshooting, and it could very likely be your problem.  wodim is a buggy replacement for the genuine cdrecord (part of cdrtools).  Many people have found that replacing wodim with the genuine cdrecord solves their burning issues.

[http://ubuntuforums.org/showthread.php?t=851707](http://ubuntuforums.org/showthread.php?t=851707)

How to remove wodim
[http://ubuntuforums.org/showpost.php?p=5552555&postcount=5](http://ubuntuforums.org/showpost.php?p=5552555&postcount=5)

Possibly related bug:
[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076)

The issue:
[http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html)

---

### Post by PeregrinGo on 2008-10-04
> **melojo said:**
> Where you able to burn using sudo? 
sudo k3b

I tried burning at 4x (for CDs, not DVDs) using gksudo k3b, and it didn't work, but the this time I received a different error. It told me to lower the burn speed and suggested the problem might be buffer underun. I am going to reboot (CD drive basically locks up after a failed burn attempt) and try again lowering the speed to 1x and specifying the TAO burn mode. If that doesn't work, I'll try eliminating wodim and getting the genuine cdrecord. =o)

---

### Post by PeregrinGo on 2008-10-04
> **IgnorantGuru said:**
> Personally, first thing I would do is get wodim out of the loop.  Even if it's not the problem it will only complicate your troubleshooting, and it could very likely be your problem.  wodim is a buggy replacement for the genuine cdrecord (part of cdrtools).  Many people have found that replacing wodim with the genuine cdrecord solves their burning issues.

[http://ubuntuforums.org/showthread.php?t=851707](http://ubuntuforums.org/showthread.php?t=851707)

How to remove wodim
[http://ubuntuforums.org/showpost.php?p=5552555&postcount=5](http://ubuntuforums.org/showpost.php?p=5552555&postcount=5)



When I try this, I get the following error:
------------------------------------------------------------
harold@harold-desktop:~/cdrtools/cdrtools-2.01.01$ sudo make
[sudo] password for harold: 
RULES/rules.top:43: RULES/ldummy.lnk: No such file or directory
		W A R N I N G	Messages like:

gmake[2]: Entering directory `/tmp/cdrtools-2.01/libschily'
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/cvmod.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/dat.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fcons.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fdown.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fdup.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/ffileread.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/ffilewrite.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fgetline.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fgetstr.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/file_raise.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fileclose.d: No such file or directory
....

are caused by a GNU make bug and not by the Schily makefile system.

The related bug has been reported to the GNU make maintainers in 1998 but
as the bug has not yet been fixed, it seems that GNU make is unmaintained :-(
A working highly portable make program is at [ftp://ftp.berlios.de/pub/smake](ftp://ftp.berlios.de/pub/smake)
RULES/rules1.top:242: incs/Dnull: No such file or directory
RULES/rules1.top:249: incs/Dcc.i686-linux: No such file or directory
RULES/rules.top:70: RULES/i686-linux-cc.rul: No such file or directory
RULES/rules.cnf:66: incs/i686-linux-cc/Inull: No such file or directory
RULES/rules.cnf:67: incs/i686-linux-cc/rules.cnf: No such file or directory
	==> MAKING DIRECTORY "incs/i686-linux-cc/Inull"
	==> CONFIGURING RULES "incs/i686-linux-cc/rules.cnf"
creating cache ./config.cache
checking host system type... Invalid configuration `unknownCPU-unknownMFR-unknownOS': machine `unknownCPU-unknownMFR' not recognized

checking if sh is bash... no
checking if /bin/sh is bash... no
checking whether sh -ce is broken... yes
checking whether /bin/sh -ce is broken... yes
checking whether /bin/bosh is a working shell... no
checking for object suffix... o
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for EMX/OS2 environment... no
checking for executable suffix... configure: error: installation or configuration problem: compiler cannot create executables.
make: *** [incs/i686-linux-cc/rules.cnf] Error 1
------------------------------------------------------------

---

### Post by IgnorantGuru on 2008-10-04
> **PeregrinGo said:**
> When I try this, I get the following error:

Maybe you just need...

```
sudo apt-get install build-essential
```

---

### Post by PeregrinGo on 2008-10-04
> **IgnorantGuru said:**
> Maybe you just need...

```
sudo apt-get install build-essential
```

Guru, you must be a real Ubuntu Wizard, because that enabled me to carry out the rest of the steps you outlined with regards to "cdrecord". 

After following each step to the letter of the law, I opened Brasero to attempt a burn with it first. No surprise here, it just flat didn't work. But, at least this time the CD writer didn't freeze up, and I was able to eject the disc. 

I subsequently tried a burn with K3b. Problem here was that after inserting the disc, the writer went haywire, spinning up, but never recognizing the CD. This essentially locked up the drive and prevented ejection until rebooting.

When I logged back in, I tried "gksudo k3b", entered my root password and tried again. I received the same result as when logged in normally. But, the terminal registered some interesting stuff, and I thought that maybe someone knowledgeable, like yourself, might be able to decipher it: (Please see attached document.)

---

### Post by IgnorantGuru on 2008-10-05
> **PeregrinGo said:**
> I subsequently tried a burn with K3b. Problem here was that after inserting the disc, the writer went haywire, spinning up, but never recognizing the CD. This essentially locked up the drive and prevented ejection until rebooting.

This statement makes me seriously question whether you're dealing with a defective drive (which is not unusual).  At $30 for a replacement DVD/CD burner, you'll want to keep that option in mind.

It would be good to test the driver thoroughly.  Can it read CDs, accept blank CDs, etc?  If you have any other OS to use, can you burn from that OS or do you get errors there too?  One free liveCD which can be used for this is SystemRescueCD, which can be placed on a USB key for booting.

If it were my system, before I spent further time troubleshooting Ubuntu, I would use another OS (probably SystemRescueCD) to see if I could burn.  IOW, is there anything to indicate this drive is functional?  If I couldn't find anything to indicate that, I would spend the $30 on a new drive and keep the old one in a drawer as a possibly functional backup  (to be tested later on another system).

The error logs aren't telling me much, but perhaps someone else here can get more out of them.  The burn process doesn't even seem to be starting.  "cannot load media" seems to be a recurring theme.  Between that and the drive locking up when a blank is inserted, I'm wondering if the drive even registers that it has burnable media in it.  Maybe the software errors are just the drive's failure to detect the media?

---

### Post by PeregrinGo on 2008-10-05
The drive actually recognizes CDs and media for the purposes of reading previously stored and/or filed information. It also "recognizes" the blank medium for starting the burn process anyway. But you're right, once the writer winds up to do its work, it as if it suddenly stops functioning. 

I have an old XP system that I was going to change to Ubuntu, but prior to doing so, I'll retest this writer with it. (It always worked perfectly until the Uby install.)

I may also switch out that machine's writer and see if it funtions.

I really appreciate all the help and work you (and others) have put into this.

---

### Post by PeregrinGo on 2008-10-05
It turns out you were right Guru, turns out the writer had gone kaput. I tested an old 24x writer and it worked fine in k3b (although Brasero still seems to be a no-go). I also tried the other Cendyne writer out on an old XP machine and it failed to function properly with it either. So thanks again for all your help.

---

### Post by metalguy639 on 2012-02-22
> **IgnorantGuru said:**
> Personally, first thing I would do is get wodim out of the loop.  Even if it's not the problem it will only complicate your troubleshooting, and it could very likely be your problem.  wodim is a buggy replacement for the genuine cdrecord (part of cdrtools).  Many people have found that replacing wodim with the genuine cdrecord solves their burning issues.

[http://ubuntuforums.org/showthread.php?t=851707](http://ubuntuforums.org/showthread.php?t=851707)

How to remove wodim
[http://ubuntuforums.org/showpost.php?p=5552555&postcount=5](http://ubuntuforums.org/showpost.php?p=5552555&postcount=5)

Possibly related bug:
[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076)

The issue:
[http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html)

Thanks! Totally worked for me :)

---

