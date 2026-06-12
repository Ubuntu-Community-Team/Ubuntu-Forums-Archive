---
title: "Huh?? Why Can't I Burn Files Larger than 4Gb to DVD?? (I could before!)"
date: 2008-07-22
forum: General Help
---

### Post by OzzyFrank on 2008-07-22
OK, I dunno what is going on here, as I could burn files larger than 4Gb to disc before, but now can't. I mean, unless I am truly mistaken, I've been able to do this plenty of times in Ubuntu, as I often download DVD ISOs that just fit on a standard blank DVD. But now every program I use fails before it even starts trying to do the burn, and yes, I've rebooted in case it was just something screwy with that session.

My burner is working fine, and in Windows I don't have this problem. Here is the error message from GnomeBaker:

[COLOR="Indigo"]Executing 'genisoimage -gui -V Linux DVD 21 -A GnomeBaker -p Frank -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-ozzman/gnomebaker-GWZWEU | builtin_dd of=/dev/sr0 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
File /home/ozzman/CD & DVD/!! Linux DVD 21 Suse/openSUSE-10.3-GM-DVD-x86_64.iso is larger than 4GiB-1.
-allow-limited-size was not specified. There is no way do represent this file size. Aborting.
:-( write failed: Input/output error[/COLOR]

Once again, I have to stress I have burned single files of 4.1, 4.2 and 4.3Gb before, no problems, and can still do so in Windows. Yet all of a sudden, in Ubuntu none of my programs can handle this. Any idea what is going on, and how to fix it?? I generally prefer doing my burning in Ubuntu, so would hate to have to go into Windows for these simple tasks. Cheers

---

### Post by Taxman415a on 2008-07-22
Have you tried to burn the file with Brasero and/or K3B? What errors do you get with those? 4GB is a filesystem limit, not sure why it's trying to enforce it on you. The '-allow-limited-size was not specified' bit looks suspicious in that it isn't reallizing you're not facing the 4GB limit. At least I'm assuming you're not since you did it before. What filesystems do you have the file on and what are you running on?

---

### Post by OzzyFrank on 2008-07-22
Hi. I tried with **GnomeBaker** and **Graveman**, and also tried creating an .iso with **AcetoneISO2**. Oh, and tried burning it with the CD creator in Nautilus. Should have tried K3B and Brassero, but booted into Windows just to make sure all is fine there. Sure enough, burned the disc no problems in Windows.

And yes, as soon as I saw the 4Gb wall that's being hit in Ubuntu, I was reminded of that being a filesystem issue, and was actually the thing that made me finally upgrade to XP back in the day. In all that time, I've never had to worry about that anymore, but now it's like I'm running Ubuntu 98 SE, hehehe!

I will boot back into Ubuntu, but seriously, if 2 or 3 apps can't do it, and even AcetoneISO2 can't make an .iso image of it, I'd say something is screwy. There have been a lot of system updates lately, and though I am wary of kernel and linux-headers updates, etc, I've been installing them like a good little boy, so wouldn't be surprised if a crappy update has caused this. But I'll get back after trying a few more apps. Cheers

---

### Post by OzzyFrank on 2008-07-22
Oh, and regarding what I'm using... just Ubuntu 64-bit Hardy on an Intel Quad-core... nothing out of the usual. Not like I've done anything whacky like convert my filesystem down from Ext3 to Ext2 (if that's even possible, hehe). All I have done is allow updates through, though I should know better by now, hehe!

---

### Post by mc4man on 2008-07-22
if you don't have a udf ext. on the iso you'll be limited to 4gb max. It should be creating an iso with udf,iso9960 extensions.
technically -iso-level 3 should allow over 4gb. udf always will

---

### Post by OzzyFrank on 2008-07-22
OK, I haven't had to worry about all that before... and not sure about the ISO issues, how I can control them, why I even need to, and why I don't have to worry about any of this in Windows.

The openSUSE .iso I am trying to burn to DVD I didn't create, but have backed up other similar ISOs plenty of times before. As for AcetoneISO2, it always does as it is told, and never gives me anything I can't then burn... but now it can't even begin creating an image.

Like I said, never been a problem before in Ubuntu, but now it is. Windows does not have this issue.

---

### Post by wirelessmonkey on 2008-07-22
is it just this particular iso?   Perhaps this is a file corruption issue? Check the MD5, just for kicks, and compare to the opensuse download site.

---

### Post by mc4man on 2008-07-22
for various reasons i don't use linux burning apps, though out of curiosity gonna try your iso, looks like about 50 min. to dl
this looks similar though only specifies brasero (genisoimage(-allow-limited-size was not specified)
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/205919](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/205919)

---

### Post by OzzyFrank on 2008-07-22
OK, just used **K3b** to create an image of the disc that includes the 4.1Gb openSUSE image. It said it found files larger than 2Gb so was enabling the UDF extension.

**Brasero**, on the other hand, has given me a totally different error message than the other Gnome apps (that just complained about the size of the one file):

[COLOR="Blue"]**The size of the project is too large for the disc even with the overburn option:**

you must delete some files.[/COLOR]

This is, of course, crap, since there is over 100Mb to spare. But since I am now trying to write to a DVD-RW (already did 2 backups in Windows), and it needs to be blanked, this could be an issue. I tried formatting it in **K3b**, but it said I could just write over it (then I decided just to make in .iso image to see if that worked). So now have tried blanking it with GnomeBaker, even using the force option, and it says it completes it in 6 secs, but isn't really blanked. I'm including this info and the error message in case this is all relevent:

[COLOR="Indigo"]*[B] BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD-RW media in Restricted Overwrite mode detected.
:-[ PERFORM OPC failed with SK=5h/ASC=30h/ACQ=04h]: Wrong medium type
0.0%|[/B][/COLOR]

So while it says Completed, it actually hasn't done squat! As for Brasero, it just tells me it failed to erase it. So, OK, back to trying Brasero with a proper blank disc... still no go, which is making it look like a problem with the Gnome apps (since K3b is a KDE app and works just fine, at least when it comes to creating an .iso). Here is the lengthy Brassero error message:

[B][COLOR="DarkRed"]BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=16
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-dry-run
	-r
	-J
	-iso-level
	3
	-udf
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_QIZHEU
	-exclude-list
	/tmp/brasero_tmp_6W4GEU
	-print-size
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -iso-level 3 -udf -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_QIZHEU -exclude-list /tmp/brasero_tmp_6W4GEU -print-size | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: File /home/ozzman/CD & DVD/!! Linux DVD 21 Suse/openSUSE-10.3-GM-DVD-x86_64.iso is larger than 4GiB-1.
BraseroGrowisofs stderr: -allow-limited-size was not specified. There is no way do represent this file size. Aborting.
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2273)[/COLOR][/B]

What has happened to these Gnome burning apps?? Obviously, it isn't the settings in any of these apps, since I never changed them, and checking them, all seems fine. What can be done to fix this situation??

PS: Obviously, my Gnome burners can't even handle blanking a DVD at the moment, so I have to figure this is related. (I'm also assuming KDE apps like K3B could do it, though K3b just told me it didn't need to do it coz I could write straight over it).

---

### Post by OzzyFrank on 2008-07-23
OK, I should know by now I shouldn't assume anything, when it comes to computing, hehe. K3b still gives me Success after trying to erase the DVD, though actually tells me it didn't need to do it, as I can write over it. But since that turns out to be untrue, here is the blanking log:

[B][COLOR="Purple"]System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
ASUS DRW-2014L1T 1.00 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

dvd+rw-format
-----------------------
* BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD-RW media in Restricted Overwrite mode detected.
0.0%:-[ PERFORM OPC failed with SK=5h/ASC=30h/ACQ=04h]: Wrong medium type
|
/

dvd+rw-format command:
-----------------------
/usr/bin/dvd+rw-format -gui -force /dev/scd0 [/COLOR]
[/B]

When I just try to write over it, it fails and I get this output:

[B]System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
ASUS DRW-2014L1T 1.00 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD-RW Restricted Overwrite

K3bIsoImager
-----------------------
mkisofs print size result: 2241769 (4591142912 bytes)
Pipe throughput: 33660928 bytes read, 33656448 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
growisofs: 7.0.1

growisofs
-----------------------
WARNING: /dev/scd0 already carries isofs!
About to execute 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
:-[ PERFORM OPC failed with SK=5h/ASC=30h/ACQ=04h]: Wrong medium type
/dev/scd0: "Quick Grow" session...
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=04h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2241769 -use-the-force-luke=dao:2241769 -speed=5.1 -overburn -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
2241769
I: -input-charset not specified, using utf-8 (detected in locale settings)
This size can only be represented in the UDF filesystem.
Make sure that your clients support and use it.
ISO9660, Joliet, RockRidge, HFS will display incorrect size.
  0.02% done, estimate finish Wed Jul 23 13:54:44 2008
  0.04% done, estimate finish Wed Jul 23 13:54:44 2008
  0.07% done, estimate finish Wed Jul 23 13:54:44 2008
  0.09% done, estimate finish Wed Jul 23 13:54:44 2008
  0.11% done, estimate finish Wed Jul 23 13:54:44 2008
  0.13% done, estimate finish Wed Jul 23 13:54:44 2008
  0.16% done, estimate finish Wed Jul 23 13:54:44 2008
  0.18% done, estimate finish Wed Jul 23 13:54:44 2008
  0.20% done, estimate finish Wed Jul 23 13:54:44 2008
  0.22% done, estimate finish Wed Jul 23 13:54:44 2008
  0.25% done, estimate finish Wed Jul 23 13:54:44 2008
  0.27% done, estimate finish Wed Jul 23 13:54:44 2008
  0.29% done, estimate finish Wed Jul 23 13:54:44 2008
  0.31% done, estimate finish Wed Jul 23 13:54:44 2008
  0.34% done, estimate finish Wed Jul 23 13:54:44 2008
  0.36% done, estimate finish Wed Jul 23 13:54:44 2008
  0.38% done, estimate finish Wed Jul 23 13:54:44 2008
  0.40% done, estimate finish Wed Jul 23 13:54:44 2008
  0.42% done, estimate finish Wed Jul 23 13:54:44 2008
  0.45% done, estimate finish Wed Jul 23 13:54:44 2008
  0.47% done, estimate finish Wed Jul 23 13:54:44 2008
  0.49% done, estimate finish Wed Jul 23 13:54:44 2008
  0.51% done, estimate finish Wed Jul 23 13:54:44 2008
  0.54% done, estimate finish Wed Jul 23 13:54:44 2008
  0.56% done, estimate finish Wed Jul 23 13:54:44 2008
  0.58% done, estimate finish Wed Jul 23 13:54:44 2008
  0.60% done, estimate finish Wed Jul 23 13:54:44 2008
  0.62% done, estimate finish Wed Jul 23 13:54:44 2008
  0.65% done, estimate finish Wed Jul 23 13:54:44 2008
  0.67% done, estimate finish Wed Jul 23 13:54:44 2008
  0.69% done, estimate finish Wed Jul 23 13:54:44 2008
  0.71% done, estimate finish Wed Jul 23 13:54:44 2008

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Linux DVD #21 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-ozzman/k3bIRV0Gb.tmp -rational-rock -hide-list /tmp/kde-ozzman/k3bT1AMsa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-ozzman/k3biqleJa.tmp -no-cache-inodes -allow-limited-size -udf -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-ozzman/k3bFslsob.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Linux DVD #21 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-ozzman/k3ba5UJwb.tmp -rational-rock -hide-list /tmp/kde-ozzman/k3bqCHNNa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-ozzman/k3blJjMua.tmp -no-cache-inodes -allow-limited-size -udf -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-ozzman/k3bxUICCa.tmp[/B]

So now I have no apps in Ubuntu that can erase a friggin' disc... next thing, I'll be sticking discs in and Ubuntu won't even know what they are... probably with an error message like "Unknown: Not a Floppy Disk!". Hehehe...

OK, just tried to blank in **Graveman**, and after 2 seconds it told me it was successful (guess what: it didn't do a thing!).

One last thing I tried was burning the files to disc with **K3b** and, sure enough, no different from when it successfully created an .iso of the disc image (the only thing K3b failed in was erasing the DVD, though it said it didn't need to, and writing over the DVD-RW, which it said it could). So at least one KDE app works in creating ISOs and burning discs with files over 4Gb, but nothing I have seems to be able to format a DVD! Next!

---

### Post by OzzyFrank on 2008-07-23
> **wirelessmonkey said:**
> is it just this particular iso?   Perhaps this is a file corruption issue? Check the MD5, just for kicks, and compare to the opensuse download site.

The images are all fine... I'm well aware how to check them, but thanks. But, even if the openSUSE iso was corrupt, it would still burn to disc, in both ways even (meaning, adding it as a file amongst others to a "Data DVD" it would still get burned... since it still would be a data file, and the burner wouldn't know or care whether it was corrupt or not... and unless the iso was really corrupt, I could burn a bootable openSUSE DVD, but it might not work properly, or one or two unimportant files might be corrupt).

---

### Post by mc4man on 2008-07-23
> 0.0%:-[ PERFORM OPC failed

i'm not sure if your using -rw or +rw but the last time i bought a pack I wasn't paying attention and got -rw,  after about a month I chucked them. One of the issues was this tendency to fail OPC with one of my burners and even though I can turn off the OPC check i prefer to leave it enabled.
There are 2 types of erase, quick and full, the quick way can actually be just that, full takes a while.
> I 00:20:41 Device: [2:0:0] BENQ DVD DD DW1640 BSMB (F:)
I 00:20:41 Media Type: DVD+RW (Disc ID: RITEK-004-48) (Speeds: 2.4x, 4x)
I 00:20:41 Quick Erase: No
I 00:20:41 Erasing Disc...
I 00:36:26 Operation Successfully Completed! - Duration: 00:15:45


---

### Post by OzzyFrank on 2008-07-23
Hi. The RW is -RW (I assume, as it says DVD-RW). They've always worked fine, in Ubuntu or Windows. I have tried both fast and full erasing or formatting, with all apps either telling me it failed, or claiming it was successful. Like I've said, everything was fine before, and not like I have gone into each program and sabotaged the settings, hehe. I've even tried to force UDF etc, to no avail (though I shouldn't need to, since everything has worked fine before).

---

### Post by mc4man on 2008-07-23
If you believe things sometimes get worse before they get better then I guess you could consider this little setback a positive. The large # of burning problems from A-Z that some people have while others don't is somewhat disappointing and doesn't seem to be decreasing.
While the few times I've used the gui apps the burns where mostly ok, if I'm gonna use a gui it would be useful if there actually was one. Options, settings, blank media and source info, burn speed choices, layer break choices, a coherent log,  ect. ect.

---

### Post by OzzyFrank on 2008-07-23
I've actually found many, even most, of the apps I've used in Ubuntu to be quite good, and as full-featured as anything in Windows. Some are even better, but just aren't as cosmetically polished as many in Windows these days. Some even have more options than Windows apps I've used. I'm curious as to what burners you've used in Ubuntu, and what you found wrong with them. And while till now burning in Ubuntu has been a joy, looking around I see this same problem, and others like it, and from many months back. Don't know why it has affected me now, but if I've joined the club as such, looks like I'll be doing a lot more burning in Windows!

---

### Post by bulletxt on 2008-07-23
I won't have internet for a while so I can't reply to any messages.

do you by chance have more than one cd/dvd optical drives? if the answer is Yes, then the current version of acetoneiso2 has issues if you have more than one. current svn does support more than one drive so the only thing I can suggest is to try svn current version.

from a terminal:

svn co [https://acetoneiso2.svn.sourceforge.net/svnroot/acetoneiso2](https://acetoneiso2.svn.sourceforge.net/svnroot/acetoneiso2) acetoneiso2  

open the README file and it will explain how to compile it in 3 fast steps. it's very easy, just give it a try. beware it is svn and currently in development so don't try new burning features since they won't work ;)

---

### Post by OzzyFrank on 2008-07-23
No, only 1 drive, and like I've said, I've done nothing to my system but allow updates. Seems Gnome apps, and AcetoneISO2 which is KDE, are suddenly preventing me from burning to disc or image files larger than 4Gb. And nothing can erase a RW DVD, even K3b which at least lets me burn files >4Gb. I could be wrong, but seems something in the updates has really messed with something these programs use or access.

---

### Post by Taxman415a on 2008-07-23
Those are absolutely some of the strangest errors I've seen. I haven't had a chance to research this a lot and I can't figure out what is going on, but I will try to in a bit. This may require posting to some other sources if we can't solve it here. The good news of course is that it is open source, so there is a fix possible. 

One thing I did want to point out is it is not considered a good idea to blank DVD rw media. It shortens their lifespan for some reason. They are different from CD-rw in that way. You really do just overwrite them.

Here's a last thought. Try burning one of your known good isos when booting from a livecd. (if you have an extra drive use that, if not unetbootin can use an image) That should help isolate if it is something on your system that got corrupted or something about your hardware that Ubuntu doesn't like.

---

### Post by alloftheabove on 2008-07-23
Honestly, even before the 8.04 upgrade ( which I had to do a fresh install for instead! ), I have had trouble writing anything to cd-rw and dvd media (I have dvd-r, can't afford rw!).  Before 8.04, I was trying to burn a cd-r sized iso to a cd-rw and it wouldn't ever recognize that there was a disc in the cd-rw drive.  Now I have a different computer, with a cd-rw drive and a dvd-ram drive ( pretty sweet ), and it won't recognize that there is a dvd-r in the dvd-ram drive.  I haven't tried K3b though, so I'll try that and I'll go back to the latest kernel version, see if that fixes me up.  Be back with some results...

---

### Post by alloftheabove on 2008-07-23
Well changing to the new kernel version screwed my computer up!  Now I'm on my mom's computer.  Sorry, but I won't be able to figure it out lol.

---

### Post by OzzyFrank on 2008-07-23
> **Taxman415a said:**
> That should help isolate if it is something on your system that got corrupted or something about your hardware that Ubuntu doesn't like.

I think you can already rule that out... I must stress I have added or subtracted nothing from my system. Just a few short weeks ago I was happily burning files larger than 4Gb, now all my burners are acting screwy. This is definitely software related, and has to have something to do with updates I've let in over the last month or so.

"Well changing to the new kernel version screwed my computer up!"

I hear ya! Well, I've had some disastrous consequences from kernel updates, but have generally been able to fix them after some hunting around. So I guess they weren't so disastrous, hehe, or I was just too stubborn to give up. But I've read of a few where they could no longer boot into Ubuntu... back on my old P4 with stupid ATI graphics card, upgrades often ended in me having to reset XServer or make do with basic vesa drivers. But I could still burn files > 4Gb any time I wanted!

---

### Post by OzzyFrank on 2008-07-23
> **Taxman415a said:**
> One thing I did want to point out is it is not considered a good idea to blank DVD rw media. It shortens their lifespan for some reason. They are different from CD-rw in that way. You really do just overwrite them.


Thanks for that info. I'm not really all that fussed,since I barely ever use them (they still all look fairly new, and are 2x speed, which should show you how long I've had them, hehe). But that is interesting info I will pass onto others. Anyway, I did try just writing over them, as I mentioned, and GnomeBaker and Brasero complained there wasn't enough room on the disc... meaning they weren't going to blank them, or should I say overwrite them. K3b said it would but, as you can see from the log, it didn't.

[COLOR="DarkGreen"]:-[ PERFORM OPC failed with SK=5h/ASC=30h/ACQ=04h]: Wrong medium type
/dev/scd0: "Quick Grow" session...
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=04h]: Wrong medium type
 media is not formatted or unsupported.
 write failed: Wrong medium type[/COLOR]

---

### Post by OzzyFrank on 2008-07-23
Oh, and just some info to avoid any possible confusion with this 4Gb thing. Any .iso image I have that is over 4Gb, like a full DVD's worth of 4.3Gb, I can happily burn to disc... and I can create .isos of that size, with AcetoneISO2 and I assume the other apps (but definitely AcetoneISO2, as I just did one to be sure). It's just trying to burn single files over 4Gb to either disc or .iso image that it is now failing. Once again, I've done nothing out of the ordinary to my system, especially not change any hardware.

---

### Post by trazart on 2008-08-07
Same problem here. I have just tried to burn a 4.3 GB movie to a DVD and it has failed.

I cant say I could do this before, I dont know.

---

### Post by OzzyFrank on 2008-12-18
Just an update that this doesn't seem to be fixed in Intrepid (or at least the current versions of programs like Gnomebaker and Brasero). Luckily, K3b is still the saviour here.

---

### Post by slaol_121 on 2009-11-24
I am having this same problem (Ironically while trying to burn the OpenSuse 11.2 DVD image to a DVD R).  I ran a md5checksum and confirmed that there is nothing wrong with the .iso image.

I downloaded the 64bit OpenSuse 11.2 DVD iso last night (4.3 gb) and attempted to burn the image to a DVD-rom with brasero in Ubuntu 9.10. I tried twice with two different DVDs and both times the disc burned to 4.0gb before returning with an error saying the file is too big.

The same thing happens if I try to copy the .iso file to my 300gb external - even though I have more than 50gb free.  (I have never had an error come up while copying any file to my external).

Right now I am updating to the latest kernel and will report back to see if this fixes anything.

Thanks! -- Slaol

---

### Post by OzzyFrank on 2009-11-24
Did you try K3B as I suggested? When I had this problem, it was the only way to get around it, so definitely give that a go.

---

