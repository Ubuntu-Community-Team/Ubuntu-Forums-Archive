---
title: "Can't burn DVDs!"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by Dinchamion on 2007-12-29
First of all, I'm sorry if this is in the wrong section, but this seemed the most appropriate.

My problem is that I cannot burn DVDs. I insert the disc, fire up Brasero, it starts to write, but at 26MB written it just hangs there, then the progress bar jumps to 100% and it returns with an unhandled error and ejects the - already ruined - disc.

The wierd part is that I used this same drive and this same program to burn isos and CDs before without a problem. I haven't changed anything on the system.

Here is Brasero's log:

```
imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
Session starting:
	flags			= 8563 
	media type	= 0
	speed		= 8
	track type		= 6
	track format	= 3
	output		= none
job (BraseroGrowisofs) set_source
imager (BraseroGrowisofs) set_output_type
recorder (BraseroGrowisofs) set_drive
imager (BraseroGrowisofs) set_output
imager (BraseroGrowisofs) unsupported operation (in brasero_imager_set_output at burn-imager.c:142)
job (BraseroGrowisofs) set_task
imager (BraseroGrowisofs) get_size
process (BraseroGrowisofs) getting varg
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-dvd-compat
	-use-the-force-luke=tty
	-Z
	/dev/hda
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_qRb54r/brasero_tmp_UQ2D4T
	-exclude-list
	/tmp/brasero_tmp_qRb54r/brasero_tmp_IT2D4T
	-print-size
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stderr: Using GHOST000.MKV;1 for  /Ghost_in_the_Shell_SAC_04.mkv (Ghost_in_the_Shell_SAC_06.mkv)
process (BraseroGrowisofs) stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_qRb54r/brasero_tmp_UQ2D4T -exclude-list /tmp/brasero_tmp_qRb54r/brasero_tmp_IT2D4T -print-size | builtin_dd of=/dev/hda obs=32k seek=0'
process (BraseroGrowisofs) stderr: Using GHOST001.MKV;1 for  /Ghost_in_the_Shell_SAC_06.mkv (Ghost_in_the_Shell_SAC_08.mkv)
process (BraseroGrowisofs) stdout: HUP
process (BraseroGrowisofs) stderr: Using GHOST002.MKV;1 for  /Ghost_in_the_Shell_SAC_08.mkv (Ghost_in_the_Shell_SAC_11.mkv)
process (BraseroGrowisofs) stderr: Using GHOST003.MKV;1 for  /Ghost_in_the_Shell_SAC_11.mkv (Ghost_in_the_Shell_SAC_01.mkv)
process (BraseroGrowisofs) stderr: Using GHOST004.MKV;1 for  /Ghost_in_the_Shell_SAC_01.mkv (Ghost_in_the_Shell_SAC_13.mkv)
process (BraseroGrowisofs) stderr: Using GHOST005.MKV;1 for  /Ghost_in_the_Shell_SAC_13.mkv (Ghost_in_the_Shell_SAC_03.mkv)
process (BraseroGrowisofs) stderr: Using GHOST006.MKV;1 for  /Ghost_in_the_Shell_SAC_03.mkv (Ghost_in_the_Shell_SAC_05.mkv)
process (BraseroGrowisofs) stderr: Using GHOST007.MKV;1 for  /Ghost_in_the_Shell_SAC_05.mkv (Ghost_in_the_Shell_SAC_07.mkv)
process (BraseroGrowisofs) stderr: Using GHOST008.MKV;1 for  /Ghost_in_the_Shell_SAC_07.mkv (Ghost_in_the_Shell_SAC_09.mkv)
process (BraseroGrowisofs) stderr: Using GHOST009.MKV;1 for  /Ghost_in_the_Shell_SAC_09.mkv (Ghost_in_the_Shell_SAC_10.mkv)
process (BraseroGrowisofs) stderr: Using GHOST00A.MKV;1 for  /Ghost_in_the_Shell_SAC_10.mkv (Ghost_in_the_Shell_SAC_12.mkv)
process (BraseroGrowisofs) stderr: Using GHOST00B.MKV;1 for  /Ghost_in_the_Shell_SAC_12.mkv (Ghost_in_the_Shell_SAC_02.mkv)
process (BraseroGrowisofs) stderr: Total extents scheduled to be written = 2283934
growisofs (BraseroGrowisofs) set_total
process (BraseroGrowisofs) stderr: HUP
job (BraseroGrowisofs) asked to stop
	status	= 0
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
job (BraseroGrowisofs) set_rate
recorder (BraseroGrowisofs) set_drive
recorder (BraseroGrowisofs) set_flags
job (BraseroGrowisofs) set_task
recorder (BraseroGrowisofs) record
process (BraseroGrowisofs) getting varg
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-dvd-compat
	-speed=8
	-use-the-force-luke=tty
	-use-the-force-luke=tracksize:2283934
	-Z
	/dev/hda
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_qRb54r/brasero_tmp_UQ2D4T
	-exclude-list
	/tmp/brasero_tmp_qRb54r/brasero_tmp_IT2D4T
	-V
	GITS_SAC_1-13
	-A
	Brasero-0.6.1
	-sysid
	LINUX
	-v
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_qRb54r/brasero_tmp_UQ2D4T -exclude-list /tmp/brasero_tmp_qRb54r/brasero_tmp_IT2D4T -V GITS_SAC_1-13 -A Brasero-0.6.1 -sysid LINUX -v | builtin_dd of=/dev/hda obs=32k seek=0'
process (BraseroGrowisofs) stderr: genisoimage 1.1.6 (Linux)
process (BraseroGrowisofs) stderr: Using GHOST000.MKV;1 for  /Ghost_in_the_Shell_SAC_04.mkv (Ghost_in_the_Shell_SAC_06.mkv)
process (BraseroGrowisofs) stderr: Using GHOST001.MKV;1 for  /Ghost_in_the_Shell_SAC_06.mkv (Ghost_in_the_Shell_SAC_08.mkv)
process (BraseroGrowisofs) stderr: Using GHOST002.MKV;1 for  /Ghost_in_the_Shell_SAC_08.mkv (Ghost_in_the_Shell_SAC_11.mkv)
process (BraseroGrowisofs) stderr: Using GHOST003.MKV;1 for  /Ghost_in_the_Shell_SAC_11.mkv (Ghost_in_the_Shell_SAC_01.mkv)
process (BraseroGrowisofs) stderr: Using GHOST004.MKV;1 for  /Ghost_in_the_Shell_SAC_01.mkv (Ghost_in_the_Shell_SAC_13.mkv)
process (BraseroGrowisofs) stderr: Using GHOST005.MKV;1 for  /Ghost_in_the_Shell_SAC_13.mkv (Ghost_in_the_Shell_SAC_03.mkv)
process (BraseroGrowisofs) stderr: Using GHOST006.MKV;1 for  /Ghost_in_the_Shell_SAC_03.mkv (Ghost_in_the_Shell_SAC_05.mkv)
process (BraseroGrowisofs) stderr: Using GHOST007.MKV;1 for  /Ghost_in_the_Shell_SAC_05.mkv (Ghost_in_the_Shell_SAC_07.mkv)
process (BraseroGrowisofs) stderr: Using GHOST008.MKV;1 for  /Ghost_in_the_Shell_SAC_07.mkv (Ghost_in_the_Shell_SAC_09.mkv)
process (BraseroGrowisofs) stderr: Using GHOST009.MKV;1 for  /Ghost_in_the_Shell_SAC_09.mkv (Ghost_in_the_Shell_SAC_10.mkv)
process (BraseroGrowisofs) stderr: Using GHOST00A.MKV;1 for  /Ghost_in_the_Shell_SAC_10.mkv (Ghost_in_the_Shell_SAC_12.mkv)
process (BraseroGrowisofs) stderr: Using GHOST00B.MKV;1 for  /Ghost_in_the_Shell_SAC_12.mkv (Ghost_in_the_Shell_SAC_02.mkv)
process (BraseroGrowisofs) stderr: Writing:   Initial Padblock                        Start Block 0
process (BraseroGrowisofs) stderr: Done with: Initial Padblock                        Block(s)    16
process (BraseroGrowisofs) stderr: Writing:   Primary Volume Descriptor               Start Block 16
process (BraseroGrowisofs) stderr: Done with: Primary Volume Descriptor               Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   Joliet Volume Descriptor                Start Block 17
process (BraseroGrowisofs) stderr: Done with: Joliet Volume Descriptor                Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   End Volume Descriptor                   Start Block 18
process (BraseroGrowisofs) stderr: Done with: End Volume Descriptor                   Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   Version block                           Start Block 19
process (BraseroGrowisofs) stderr: Done with: Version block                           Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   Path table                              Start Block 20
process (BraseroGrowisofs) stderr: Done with: Path table                              Block(s)    4
process (BraseroGrowisofs) stderr: Writing:   Joliet path table                       Start Block 24
process (BraseroGrowisofs) stderr: Done with: Joliet path table                       Block(s)    4
process (BraseroGrowisofs) stderr: Writing:   Directory tree                          Start Block 28
process (BraseroGrowisofs) stderr: Done with: Directory tree                          Block(s)    2
process (BraseroGrowisofs) stderr: Writing:   Joliet directory tree                   Start Block 30
process (BraseroGrowisofs) stderr: Done with: Joliet directory tree                   Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   Directory tree cleanup                  Start Block 31
process (BraseroGrowisofs) stderr: Done with: Directory tree cleanup                  Block(s)    0
process (BraseroGrowisofs) stderr: Writing:   Extension record                        Start Block 31
process (BraseroGrowisofs) stderr: Done with: Extension record                        Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   The File(s)                             Start Block 32
process (BraseroGrowisofs) stderr:   0.22% done, estimate finish Sat Dec 29 08:58:24 2007
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   0.44% done, estimate finish Sat Dec 29 08:58:24 2007
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   0.66% done, estimate finish Sat Dec 29 08:58:24 2007
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr: /dev/hda: "Current Write Speed" is 8.2x1352KBps.
process (BraseroGrowisofs) stderr: :-[ WRITE@LBA=250h failed with SK=4h/ASC=08h/ACQ=03h]: Input/output error
process (BraseroGrowisofs) stderr: :-( write failed: Input/output error
job (BraseroGrowisofs) asked to stop
	status	= 1
	error		= 1
	message	= "Unhandled error, aborting"
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
process (BraseroGrowisofs) stderr: :-( write failed: Input/output error/dev/hda: flushing cache
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) stderr: /dev/hda: updating RMA
process (BraseroGrowisofs) stderr: /dev/hda: closing disc
process (BraseroGrowisofs) stderr: EOF
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
Session error : Unhandled error, aborting
```

I did a forum search, but while I found a topic with a very similar problem, there weren't any solution.

I'm gonna try out other programs now, but before neither Gnomebaker nor Nerolinux worked, both coming back with error messages.

Any help or suggestion would be appreciated! (Buying a new drive is kinda out of the question... :()

---

### Post by bwtranch on 2007-12-29
I would try another program first. I like K3b myself. Good luck.

---

### Post by kens8 on 2008-01-24
I'm just bumping this post because I have the same problem.

---

### Post by chrisdeckard on 2008-01-24
I'd second using k3b as well.  Excellent program.  If it continues to happen in k3b, it's probably a hardware problem.

-Chris

---

### Post by thedaylights on 2008-01-29
I'm also having this problem with the same error message. I tried the default dvd burning software first, then Brasero. Both failed. 

I'm using a Lenovo Lightscribe external DVD burner.

---

### Post by GreenMeanie on 2008-02-01
Are you using a Lite-on burner?
I have the same problem.

---

### Post by dangerousice on 2008-02-14
I too have this problem.  I was able to burn dvds with brasero but not anymore and i have tried several diff programs including k3b but none work.  I can burn dvds with the same drives in Vista so i know it's not the hardware.  Last time i had this problem i just formatted and of course it work but i dont think that is the best way to go about this so if anyone can help i would be your slave for all time!!

---

### Post by Invisible_Kid on 2008-02-15
> **thedaylights said:**
> I'm also having this problem with the same error message. I tried the default dvd burning software first, then Brasero. Both failed. 

I'm using a Lenovo Lightscribe external DVD burner.

I can confirm the problem, I'm also using an external ligthscribe burner, it's an HP dvd640

I was able to burn dvds with no problems in feisty with xcdroast or k3b, but since I upgraded to feisty I can't do it anymore.

I hope this issue gets solved soon!!!:(

---

### Post by Kat of Zion on 2008-03-05
Im having the same problem myself.  I did check libdvdread3 and it is current.  I did clear out the .dvdcss folder as another external thread suggested.

Im running out of ideas!:confused::mad:

```

System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-E10L LE05 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

HL-DT-ST DVD-RW GWA-4082N CG02 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]
Burned media
-----------------------
DVD+R Dual Layer

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:3383907 -dvd-compat -overburn -use-the-force-luke=bufsize:32m 


```

---

### Post by andrew.46 on 2008-03-11
Hi,

 Have you tested your drive by simply using a growisofs command?  I have been working on backing up $HOME and /etc using growisofs using the following:

```
 growisofs -dvd-compat -speed=8 -Z /dev/dvd \
            -R -J -r -V Backup_`date +"%Y%m%d"` \
            -allow-multidot -allow-leading-dots -l -pad \
            -graft-points "/Backup/home/=/home/andrew" \
           "/Backup/etc/=/etc" \
            && eject /dev/dvd
```

and toying with adding backups (on a RW of course):

```
growisofs -dvd-compat -speed=8 -M /dev/dvd \
            -R -J -r -V Backup_Files \
            -allow-multidot -allow-leading-dots -l -pad \
            -graft-points "/`date +"%Y%m%d"`/home/=/home/andrew" \
           "/`date +"%Y%m%d"`/etc/=/etc" \
            && eject /dev/dvd
```

So you could try the bare command line and that might eliminate a few possible problems?

            Andrew

---

### Post by splendid on 2008-03-11
I am unable to burn DVD's in K3b.  When asked to insert blank DVD, I put the disc in and the system never recognizes it.  When I was using 5.10, I did not have any problems.  Any ideas?????

---

### Post by majlokor on 2008-03-12
don't wanna sound silly, but have you tried to use different blank media(different brands of cds and dvds)?

---

### Post by splendid on 2008-03-15
Thanks that did it.  Who would have thought that TDK DVD's would not work, and Kodak ones would.  I have been using TDK products for 25 years.

Appreciate the help.

---

### Post by alanbshepard70 on 2008-03-19
I'm having the same problem as everyone else. I could burn DVDs fine until one day it just started giving me the same error as previously mentioned "Unhandled Exception - Aborting". I've tried K3b, brasero, Gnomebaker, cdrecord, growisofs, etc... and none have worked. Several bug reports have been made such as this one [https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/15424](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/15424) but no progress has been made that I'm aware of. I'm in desperate need of a way to burn DVDs. Like many others I can burn CDs and DVD-+RWs just fine but DVD-+R discs fail every time. I'm now the proud owner of several new coasters and I'd like to avoid owning more of them. Someone has to know what's going wrong and how to fix it. Coders of America unite and help us poor saps straighten this out, please, please, please and thank you.

---

### Post by pliz on 2008-03-20
Surprisingly this has not been fixed yet. I am not sure how many people are suffering from being unable to burn DVD/CDs but on all 3 machines I have tried it - it fails. Burning does not work neither in Gutsy nor in Hardy, so no hope for burning under linux even in the upcoming release. I have also tried a debian live CD with the same results. Everything is described here:

[https://bugs.launchpad.net/ubuntu/+bug/202736](https://bugs.launchpad.net/ubuntu/+bug/202736)

Together with an output log from brasero. Although not a single program is working for burning - I tried nautilus, k3b, gnomebaker.

Is anyone here who actually can use their burners with gutsy or hardy? I have read somewhere that the problem is in the kernel when there are sata and ata devices present simultaneously, but why is not this fixed yet? It has been a good half a year already.

---

### Post by pliz on 2008-03-21
So *nobody* has problems with burning? May this three very different hardware configurations I have are not representative of what people are using?

Sad.

---

### Post by thedaylights on 2008-03-28
I'm curious if people are having trouble with external DVD writers, or internal. I have an external: Lenovo USB Multiburner3.

tried Brasero and K3B, both failed. I'm going to try a different DVD manufacturer next. I'm using Sony discs.

---

### Post by Invisible_Kid on 2008-03-28
I think most of us are having problems with external burners, I hope this gets solved for Hardy, because I hate having to switch to effin windows just to burn some dvds....

---

### Post by thedaylights on 2008-04-02
I tried using a different manufacture of DVD and it worked! I was using Sony DVD +R under Windows, and they worked. They stopped working with Ubuntu. Now I've tried Memorex DVD -R and it works!

Maybe it's a DVD-R vs. DVD+R issue. Maybe it's a quality issue. They Sony's are on a spindle and cheaper, the Memorex's are individually wrapped pricey ones.

---

### Post by Teva on 2008-04-10
I have a Toshiba laptop and I'm running 2.6.22-14-generic. It has a TSST TS-L632D CD/DVDW drive. I'm able to burn DVD+Rs no problem however, I'm having major problems trying to burn DVD+R dual layer. Every time I try I get an error message and then my drive locks up and won't eject the disc. I have to resort to restart the computer while the drive is still chirping away. The drive is making noise the whole time as if it's having a hard time trying to read the disc. The kicker is that I was able to burn those same DVD+R DLs about a month ago. I don't know what has been updated or installed but now I can't burn dual layered discs. I've tried different discs and different brands. I've searched Google for answers but no luck. Anyone experience anything similar with dual layered discs?

---

### Post by sylv1 on 2008-04-22
Same problem here.
Cannot burn DVDs on my external drive (HP DVD640) since upgrade to Gutsy.
Burning CDs is fine and hardware works fine on Windows.
Hope this gets fixed...

---

### Post by &amp;wP*!) on 2008-05-04
I have bought a fresh LG GH20NS10 DVD+/-R,RW,RAM SATA Burner.

I works with Nero on Windows XP. But it does not work with Brasero neither on Gutsy 7.10 nor Hardy 8.04:

```
BraseroGrowisofs stderr:   2.58% done, estimate finish Sun May  4 19:55:06 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   2.84% done, estimate finish Sun May  4 19:53:35 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: :-[ WRITE@LBA=97f0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_set_current_action
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2270)
```
My motherboard is old, supports 2 channels in UDMA/100 for SATA (ver 1.0), but LG's driver is able to do UDMA133. [UDMA/100]("http://www.samsung.com/global/business/hdd/learningresource/whitepapers/LearningResource_UDMA100.html") even supports 66 MByte/s. [16x DVD speed]("http://www.osta.org/technology/dvdqa/dvdqa4.htm") is just 1/3 of this.

Since it is running on Windows XP with Nero perfectly, this is definitely an issue of Brasero, DVD SATA driver of Linux or operating system itself. Since LG did not publish any driver, I cannot go on. I have lost 5 DVD+R discs and it costs a lot of test time for me.

I hope this issue will be fixed, or we are stick into Windows again...

I can feed you any kind of technical data if you want. I am sure that everyone needs a stable status on this issue...

---

### Post by Xizorbg on 2008-06-07
Same here using Hardy, AMD64, Internal Plextor PX-800A,  Using both Brasero, K3B, - DVD and CDs!

Please post if you figure this out!

Thanks,
X:guitar:

---

### Post by elihu2 on 2008-07-06
Same here, although it seems I can burn CD's. Just not DVD plus or minus R. Can burn to DVD-RW. Perhaps the quality of the DVD is the issue. I did recently run out of 8X DVD's and all that's available is 16X. Another rabbit hole to go down.

However, what really perplexes me is that my older box with Sony DVD Writer, running Linux Mint 4.0 was able to make me a copy on DVD+R of a disk. The brand disk (NEXXTECH) was rejected by my main DVD burner.

Take your pick: hardware, disk manufacturer, write speed, driver, kernel. Wouldn't surprise me if this fix takes a while longer. I'd be happy to send along any logs, but my results are about the same as above.

:confused:

---

### Post by elihu2 on 2008-07-06
Interesting reading:

[https://answers.launchpad.net/ubuntu/+question/7142](https://answers.launchpad.net/ubuntu/+question/7142)

As I read, problems result fron the burner being identified as /scd0 and changing the device id to /hdc0 alleviates this. This is about my skill level. Anyone want to take a crack at it and report results?

---

### Post by !nkubus on 2008-07-14
Same problems here with a A LITE-ON Drive

---

### Post by neill on 2008-07-20
what command do i run to check my external USB DVD burner ?

how can i force hd rather than sd ?

ta

/neill

---

