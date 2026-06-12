---
title: "Installation never completes! VAIO S560"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by leaded on 2006-06-04
I tried several ways to partition the hard drive, but the installer keeps freezing my system somewhere between the partitioning and copying system files. I initially used the Live CD and GParted to set up my partitions. The system froze in the middle of everything. I used Hiren's BootCD and fired up PartitionMagic Pro and successfully partitioned the drive how I wanted it and switched back to the live CD installer and did a manual partition table. Somewhere around the copying system files the whole system hung. I tried to automatic partitioning and slid the slider to about 15% and the system hung around the same place.

What can I try? I'm using the Desktop Gnome CD. I already have XP installed (it's been defragged several times). I've read things about disabling ACPI or whatever but I'm not entirely sure what that means or how to do it. If it takes away critical laptop features then I don't want to try it :(

I'm pretty certain that the hard drive is SATA- could this have something to do with it?

The laptop is a Sony Vaio VGN-S560P. 1.5GB RAM, 1.86GHz Pentium-M. NVidia (I've tried normal and safe graphics mode) GeForce Go 6400 [PCI-Express x16, 256MB].

(I used Ghost to copy my HD to a USB drive in case I blow something up :))
Thanks in advance!

---

### Post by spier on 2006-06-04
Hi, I experimented the same problems weeks ago, exactly with the same 15% hang while I was trying to install dapper along Winxp and Breezy.

Some issues I found that helped other guys but didn`t help me:

[http://www.ubuntuforums.org/showpost.php?p=994989&postcount=12](http://www.ubuntuforums.org/showpost.php?p=994989&postcount=12)

Only after  downloading a fresh copy of Alternate iso (former Install cd, as oposed of Live cd) everything went like a charm and I have the three sistems up.

BTW, my laptop is a Vaio vgn fs740w.

---

### Post by 89c51 on 2006-06-05
check if the installer (in the last report before installation) has the right paths for the partitions

---

### Post by leaded on 2006-06-05
Well, last night I tried everything again. I defragged XP about 6 times until no more progress was made. I then booted up the LiveCD and ran GParted. A lot of people seemed to notice problems if you used the partition editor in the middle of the install and the workaround was to do it first. So I tried it and the system froze in the middle of creating the ext3 partition for /. Then, Windows wouldn't boot.

I'm not going to try and fix the Windows error (one of those ambiguous 0x0000008 or whatever messages) since I used Ghost to back everything up beforehand. Right now I'm reloading the original hard drive image with Ghost. When that's finished in about an hour I'm going to defrag Windows a bunch and then use Partition Magic to prepare the hard drive. Then I guess I'll give the Alternate CD a shot.

Oh, here's a question- The furthest I ever got, the only time I got past the partitioning, was when I did the partitioning manually with Partition Magic. During the installer, it locked up when it was checking the swap partition. Anyone know why that is? Maybe the Live CD just doesn't like my hardware...

---

### Post by Josh Kurtz on 2006-06-05
Please let us know if you get it installed.  I had the same issue on an HP Pavilion N5415.  The farthest I got was 95% but the other 3 times it locked up around the partitioner.

---

### Post by leaded on 2006-06-05
I got Ubuntu to install with the Alternate CD successfully. I guess Partition Magic loaded a bunch of junk onto the filesystem because I formatted it during the text Ubuntu install and it installed just fine (except for some weird bars at the top of each screen during the installation process).

But, Ubuntu will not load. After grub and a successful load thru the starting of services, it freezes after I log in. The "hourglass" (whatever it really is!) came up for a few seconds and the machine locked up. I tried to install Fedora 5 on it after that and the installer did the same thing.

What should I suspect to be going on here? Can someone please help me out?

---

### Post by leaded on 2006-06-06
I edited that above post so I'm "bump"ing this... please help!

---

### Post by Zathrus on 2006-06-07
Hi leaded have you ever had any luck installing any other linux distro on your laptop, I have VAIO S58GP very similar to yours and I've been having all soughts of problems installing any linux distro.

First let me preface everything I'm about to say with "I'm a total amateur" these are just things I've noticed and found to work or not for the most case.

I've narrowed down my problems to two things, firstly I sometimes have problems when pcmcia is being loaded, this was a problem for Debian and Knopix at least, seemed to work with SUSE 10 though. Secondly the SATA drive in these laptops seem to be different maybe a different chipset I dont know but I've had problems with it when trying SUSE 10, Debian and Ubuntu and a few other distros. I did a bit of googling and found that pre kernel 2.6.8 SATA support is poor or non-existent and post linux kernel 2.6.12 SATA support takes a bit of a nose dive. This version of ubuntu is using linux kerenel 2.6.15 which I've been reading some people have had problems with this and their SATA drives. I was hoping to install this version of Ubuntu if the SATA support had been fixed but it seems it's not from what you've said.

The one linux distribution I did have success with (I'm running it right now with no problems) is an old version of Debian testing net install using kernel 2.6.12-1-386. This works fine with my HDD but using a newer version of Debian net install (2.6.15 i think) says it cant find my HDD when it comes time to setup my partitions. One little caveat being I had to disable pcmcia from being loaded before I could boot properly. Now I'm stilling mucking around with this installation, can kind of get power management going and cant get wireless running but I'm not an expert so you may have better luck but at least it is a running version of linux. I did find one guy that claims to have a working install boot CD for debain running 2.6.15 with some hacks to get the HDD working but I couldn't find out what he did.

I dont know if this helps you at all but hopefully it might shed a bit of light on what's going wrong.

---

### Post by leaded on 2006-06-07
Actually you may have helped me out. I didn't think a single thing about PCMCIA. I'm going to try again while disabling it to see if that makes a difference. If that doesn't work, I'm going to try Xubuntu because it may be Gnome-related. I dunno, but once I went thru the text-mode install, it froze as soon as I logged in. Just a wild guess tho... I'll report back what happens. Thanks!

---

### Post by Yoeri on 2006-06-07
Had the sqame problem, installation always hung at 72%, downloaded iso again, burned it to cd and again ... 72%.

Burned the CD at 4x after some reading, tried it again ... works

I read the same problem in the dutch forums. The problem was also solved by burning the cd at lower speed ...

---

### Post by leaded on 2006-11-03
I just wanted to report that 6.10 Desktop and Alternate both fail to install as well. The system locks up on the hard drive partition screen. When this happened when installing 6.06, I created the partitions using a BootCD, but the OS failed to be usable (would randomly lock up).

I haven't tried to newest Fedora, but I'm assuming there's still something wrong with the SATA drivers in my laptop with Linux in general. This is the third time I've tried to install Ubuntu on my Vaio S560 and it's failed on something that looks like a SATA HD issue.

I'd like to report a bug but I don't know how to, what information is relevlant, and even what information to report. If there's some debug mode I can run from the Desktop CD or something, please tell me. I really want to see this issue solved but I don't know how to get involved. Thanks!

---

