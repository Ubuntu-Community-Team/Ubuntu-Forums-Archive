---
title: "HELP! Installed updates and now X not coming up!"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by warped6 on 2009-01-28
HELP! HELP! HELP!

I installed some updates this morning on my laptop running 8.10. When it was done it said it required a reboot. No worries. Rebooted and when it got to the point where X comes up and asks for user id my screen starts flashing all white. :cry: I can almost make out some icons but not really.

I was able to bootup using the previous kernel but would like to know how to fix my problem.

Again it's 8.10 with all the latest fixes. It is running an ATI video card with the ATI video driver. What do you need to know and I'll post it.

Mike

edit:
Removed and reinstalled the ATI driver, solved my problem.

---

### Post by lakersforce on 2009-01-28
Enter Grup, boot up in recovery mode and use the "xfix" option, reboot.

---

### Post by warped6 on 2009-01-28
> **lakersforce said:**
> Enter Grup, boot up in recovery mode and use the "xfix" option, reboot.

Sadly I tried that first. Same problem. :-(

---

### Post by em4r1z on 2009-01-28
I have the same problem. If your system was up to date, the updates were a new kernel (linux-generic, linux-headers, etc.) and gnome-power-manager. I tried booting up with the previous kernel (normal and recovery modes) with no luck.
I think the problem is the NVIDIA driver.

---

### Post by 451422 on 2009-01-28
This is exactly an NVidia incompatibility.  I don't know how many times, Ubuntu does this.  If they are going to push out an update of this nature, why don't they test the basics first.  It is not like video is a new thing.

I will be tinkering with this later today.  If any progress is made I will post.  I worked fine on the prior version of 8.10 with version .177 NVidia drivers.

In the meantime you can press "esc" on the GRUB menu and manually select the previous kernal and the system works just fine.

Does anyone know how to undo the recent install for the update?:(

---

### Post by warped6 on 2009-01-28
> **451422 said:**
> This is exactly an NVidia incompatibility.  I don't know how many times, Ubuntu does this.  If they are going to push out an update of this nature, why don't they test the basics first.  It is not like video is a new thing.

I will be tinkering with this later today.  If any progress is made I will post.  I worked fine on the prior version of 8.10 with version .177 NVidia drivers.

In the meantime you can press "esc" on the GRUB menu and manually select the previous kernal and the system works just fine.

Does anyone know how to undo the recent install for the update?:(

I have an ATI video card not Nvidia if that makes any difference as far as debugging the problem. And yeah I went to previous kernel. Lost some eye candy but it's functional at least.

---

### Post by em4r1z on 2009-01-28
> **451422 said:**
> In the meantime you can press "esc" on the GRUB menu and manually select the previous kernal and the system works just fine.Why the problem persists no matter what kernel I load, the X server doesn't start. If I start in recovery mode and run aptitude (to reinstall the NVIDIA driver), the system states it was loaded as read-only and I cannot proceed. Any leads?

---

### Post by ghettofreeryder on 2009-01-28
Do you have dkms installed.  Maybe try sudo apt-get install dkms if you dont.

---

### Post by shark1997 on 2009-01-28
try using startx

---

### Post by 451422 on 2009-01-28
> **warped6 said:**
> I have an ATI video card not Nvidia if that makes any difference as far as debugging the problem. And yeah I went to previous kernel. Lost some eye candy but it's functional at least.

So, Wow, you have the same issue then with ATI drivers?  If that is the case, then a major screw job on Ubuntu's part.

---

### Post by em4r1z on 2009-01-28
Why the problem was gone worse, after a couple of restarts (I've posting through a live CD), there's a kernel panic during the booting process that frezees the system, no matter what kernel or mode I try. I couldn't even try a solution!
I backed up what I needed and I'm ready to try any ideas to solve this.

---

### Post by 451422 on 2009-01-28
> **em4r1z said:**
> Why the problem persists no matter what kernel I load, the X server doesn't start. If I start in recovery mode and run aptitude (to reinstall the NVIDIA driver), the system states it was loaded as read-only and I cannot proceed. Any leads?

Go into the recovery mode, if you can.  Then once x desktop starts select on the tool bar System>Administration>Hardware Drivers.  Try downgrading the drivers from the most current, NVidia .177 down to the lowest.  Reboot and see if that does it for you.  No guarantee, but would presume this is safer than hacking too deep into it until a fixed is discovered.

Definitively stay away from installing drivers outside of Ubuntu by going directly to NVidia's site and compiling them  yourself.  If Unbuntu cannot figure it out, the NVidia or ATI probably haven't had the opportunity to test them either.

---

### Post by warped6 on 2009-01-28
> **451422 said:**
> So, Wow, you have the same issue then with ATI drivers?  If that is the case, then a major screw job on Ubuntu's part.

I have an identical setup on another hard drive (I swap drives depending on what project I'm working on. Don't want one to interfere with the other and need the disk space. Anyway...) I HAVEN'T loaded on the updates to my second hard drive. When I swap them I will make a list of what it is trying to update and maybe install them 1 at a time to find the culprit who messed me up.

---

### Post by 451422 on 2009-01-28
> **warped6 said:**
> Sadly I tried that first. Same problem. :-(

Did you try the "startx" command as suggested by Shark?

---

### Post by ghettofreeryder on 2009-01-28
Have you guys tried to install dkms, then reboot?

---

### Post by giantoz on 2009-01-28
I had the same problem today as well.  I also have an ATI driver.

did a fresh install because I don't know how to deal with something like that.  now the update manager icon is showing an update for: linux headers, linux headers-generic, linux image-generic, and libc-dev.  Im really afraid of updating now...what do I do?  what will installing dkms do?  thanks for any help

---

### Post by warped6 on 2009-01-28
> **451422 said:**
> Did you try the "startx" command as suggested by Shark?

I can't. When X starts after booting up the screen starts flashing right away. I don't get a chance to sign on or anything. I haven't tried doing a startx in safe mode.


Looking at the list of updates and I see they updated the kernel and the restricted drivers module. Could one of these be the problem? Can I load on the kernel update without the restricted drivers module or would that cause more problems?

---

### Post by 451422 on 2009-01-29
Got it.

Yesterday I didn't have too much time to tinker with this accept later in the day. The first thing I did this morning was go to the console after I received a blue screen of the failure to load the nVidia drivers.  After I logged in and did "sudo su," I then performed "apt-get upgrade."  It updated various nVidia drivers and other various libraries.   The way to get to this is via GRUB recovery console.  This may not be the exact name, but it is always choice number two of two for the new kernel update from yesterday.

After I performed the dkmg, I then did the "repair" x server (something like that).  After this, the system went into successfully.  I then changed my nVidia drivers back to .177 version which is recommended by Ubuntu.

I am by no means an guru of Linux, but I have learned one thing from this experience.  Wait a while prior to performing the update.:p

---

### Post by warped6 on 2009-01-29
OK thanks I'll give it a shot tonight. I'm up and running at work on the previous kernel and don't have time to try it today.

I'll report back one way or another. (Keeping my fingers crossed)

---

### Post by zika on 2009-01-29
> **451422 said:**
> I am by no means an guru of Linux, but I have learned one thing from this experience.  Wait a while prior to performing the update.:p
I've come to same conclusion at the time I've upgraded from 8.04 to 8.10RC and had to reinstall 8.04 or not have wired connection (NM and its problem with ethernet chipset). but at that moment I was just recklessly unpatient. how to differentiate after several days or so, what, of more than a dozen of available updates, is the old one that aged enough and what is the today's disaster one... ? as far as I know there is no release date on them once You open the window for update. just to keep aside a fact that I'm always more prone to update then to wait ... ;) the only good thing about situations like this is that I learn more while coping with them than I would for at least a week of comfortable use ... :lol:

---

### Post by ramblin' wreck on 2009-01-29
Yeah, I have an ATI Radeon and had similar issues. I updated blindly not realizing it was  new kernel... Everytime I booted it would blink through the login screen, and then slowly load the desktop. Every window I opened rendered super slow and I could barely get the thing restarted. I had to uninstall all the ATI 3rd party drivers, boot up into the previous kernel and then re-install the video drivers...

No matter what I tried I couldn't get the newer kernel to work with my card (Radeon HD 2600 pro, very linux friendly).

BUT A QUESTION: no one answered the prior question about how dkms would help with kernel updates not working with video drivers. Did anyone with the video issues try this already?

---

### Post by 451422 on 2009-01-29
> **ramblin' wreck said:**
> BUT A QUESTION: no one answered the prior question about how dkms would help with kernel updates not working with video drivers. Did anyone with the video issues try this already?

I covered it earlier in post regarding the nVidia drivers.  First, I used apt-get upgrade, then DKMS, and then repair x-server.  This was completed within the recovery console of the new kernel via the update that was made available yesterday.

---

### Post by markbuntu on 2009-01-29
Kernel updates will never support proprietary drivers that are not in the repos so you should be expecting this to happen. 

As a result, x will fail on restart due to dkms module problems, kernel updates will install the dkms module from the repos which is the wrong one if you are using a driver you got from ati or nvidia or with envy.

However, this is easily remedied if proper precautions ar taken. Make sure you save the driver download somewhere convenient. I keep mine on my desktop. 

Before you install a new driver remove completely any previously installed proprietary driver because leaving old drivers lying around will create dkms module conflicts on kernel updates causing no driver dkms modules to be loaded into the kernel. This used to happen to me all the time on Hardy.

Disable all desktop visual effects before rebooting into the new kernel. Compiz will still try to start on the VESA driver so you will get a white or black screen or maybe some colorful stripes.

If reboot fails to start x. reboot into recovery mode and choose fix x then resume when that finishes. When you get back to your desktop just reinstall the driver. If you have forgotten to turn off compiz (desktop visual effects) and get a white or black screen after you login, change session to gnome safe mode from the login screen and you should get back to your desktop. Then you can run the installer again.

I have been doing this for many many kernel updates. It took me less than five minutes to get back to normal after today's kernel update.

In the past I would just dpkg the kernel modules and reboot but now that the fglrx installer works I just run that again and reboot. It even uses my old settings.

---

### Post by alexcckll on 2009-01-29
Oh for goodness' sake!  Not AGAIN surely?

OK - that's me holding off for at least a week...

Or are Intel 3100 cards OK?  Lenovo R61i here...

---

### Post by warped6 on 2009-01-30
OK so did some more playing around.

Boot up Ubuntu 8.10 Kernel 2.6.27-11-generic
Get splash screen
Get text based login
login
key in startx
lots of text shows up the last few lines say
backtrace followed by lines numbered 0-8
saw signal 11. server aborting
giving up

try doing an apt-get update
fails no public key

Boot up 2.6.27-11-generic (recovery mode)
try xfix - it does it thing
resume 
I see dkms fly by listed under it is
fglrx 8.561
also see
xorg-server 2:1.5.2-2ubuntu3

everything does the same as before.

boot up under 2.6.27-9-generic
update manager says updates available, looks to be the same kernel updates. Try loading those on again, same results.

OK so where do I go from here?

FYI... I did load on the 2.6.7-11 updates on a Lenovo S10 (my daughter's, cute little box) and they went on with no problem.

---

### Post by 451422 on 2009-01-30
> **markbuntu said:**
> Kernel updates will never support proprietary drivers that are not in the repos so you should be expecting this to happen...................

However, this is easily remedied if proper precautions ar taken. Make sure you save the driver download somewhere convenient. I keep mine on my desktop...........

Your course or approach maybe valid, but it is not within the context of the original post.  The nVidia drivers previously installed with the earlier kernel and the update are nVidia drivers blessed and shipped with the Unbuntu distribution.  In other words, no drivers were installed from any third-party sites.

Again, within the context of this message the resolutions are working within the available boot up options Ubuntu ships within GRUB.

---

### Post by 451422 on 2009-01-30
> **warped6 said:**
> OK so did some more playing around.

Boot up Ubuntu 8.10 Kernel 2.6.27-11-generic
Get splash screen
Get text based login
login
key in startx
lots of text shows up the last few lines say
backtrace followed by lines numbered 0-8
saw signal 11. server aborting
giving up

try doing an apt-get update
fails no public key

Boot up 2.6.27-11-generic (recovery mode)
try xfix - it does it thing
resume 
I see dkms fly by listed under it is
fglrx 8.561
also see
xorg-server 2:1.5.2-2ubuntu3

everything does the same as before.

boot up under 2.6.27-9-generic
update manager says updates available, looks to be the same kernel updates. Try loading those on again, same results.

OK so where do I go from here?

FYI... I did load on the 2.6.7-11 updates on a Lenovo S10 (my daughter's, cute little box) and they went on with no problem.

Carefully read this entire thread.  I suggest creating a new post as this problem is not in the context of the original post.

---

### Post by 451422 on 2009-01-30
> **alexcckll said:**
> Oh for goodness' sake!  Not AGAIN surely?

OK - that's me holding off for at least a week...

Or are Intel 3100 cards OK?  Lenovo R61i here...

Er, ok.  More data is needed.  If this is regarding graphics within the context of the original post, please provide more details.  Otherwise, create a new post.

---

### Post by warped6 on 2009-01-30
> **451422 said:**
> Carefully read this entire thread.  I suggest creating a new post as this problem is not in the context of the original post.

I have read it (I started it) and the problem still exists. X is still not coming up. The problem has changed slightly from a flashing screen to now it doesn't start at all. I just dumped all of the stuff in my previous post in hopes that someone could point me in some direction as to how to fix it.

---

### Post by fudoki on 2009-01-30
> **451422 said:**
> This is exactly an NVidia incompatibility.  I don't know how many times, Ubuntu does this.  If they are going to push out an update of this nature, why don't they test the basics first.  It is not like video is a new thing.

I will be tinkering with this later today.  If any progress is made I will post.  I worked fine on the prior version of 8.10 with version .177 NVidia drivers.

In the meantime you can press "esc" on the GRUB menu and manually select the previous kernal and the system works just fine.

Does anyone know how to undo the recent install for the update?:(

Ditto for me.  My system with an AMD 5200+ X2 (on an Asus MLI Deluxe MB) and BFI Nvidia 7600GT card came up fine in Server, RT, and Generic; but my newest computer build, an AMD Phenom 9950 Agena X4 system (on an Asus M3A-H/HDMI Nvidia 780G chipset) with an Nvidia GeForce 9500GT 512Mb video card was unable to load the .23 kernel in the Generic, RT, or Server variants.

Unlike the .22 upgrade, where the RT and Generic variant would load after the update, and after the update a couple weeks later, the Server variant (which is what I normally use on the X4, 8Gb beast) would finally load; the .23 update only loaded once in the RT variant, and immediately caused a memory leak, a 100% CPU usage in Processor 0 (as a User process), and when I attempted to load Top and ksysguard to identify the offending process I got a hard hang, requiring a "Reset Button" reboot.  After that system hang, the X server refused to load in RT, even after dropping back to the .22 Server kernel and re-installing the restricted drivers and nvidia-glx-new for .23.

WARNING: I tried to perform the re-install from the "recovery" text mode (dropping to a "root" prompt) in both the .23 Server and RT kernel variants.  BOTH OF THESE PRODUCED CORRUPTED FILES AND HUNG EITHER DURING DOWNLOAD OR INSTALLATION, RESULTING IN A RESET REBOOT EACH TIME AND MODERATE REISERFS DISK CORRUPTION.

This indicates a serious problem in the underlying binaries, since they are unreliable in a 100% "text console" mode.

Thankfully, only the "kernel-restricted" files I was trying to re-install were corrupted (so far as I can discern).  These had to be manually deleted from a terminal and re-installed from .22; but the Xserver still will not load the Nvidia driver in any form of the new .23 update.

The .22 variants (Server, RT, and Generic) still runs beautifully and the graphics and speed (and system integrity) are simply outstanding.

Come on Ubuntu techs - test this stuff on the newest Nvidia cards if you can.  .23 runs on the 7600 series and about half the 7800 series (from my limited testing here - and talking with friends who are almost all present or former computer professionals, both hardware and software, running Linux) - so it appears to be a problem with the newer cards.

Hope these results help folks, and the Ubuntu staff, isolate the problem.  One thing is certain, the binary "kernel-restricted" modules have a serious problem with 78xx, 8xxx, and 9xxx chipsets - based on the hard hangs and segfaults folks have experienced here in Athens, GA. with these modules.

My advice: run .22 until this stuff gets re-compiled with a good driver from Nvidia.

fudoki

---

### Post by fudoki on 2009-01-30
As for uninstalling the update, this is not necessary as each kernel version has it's own "Kernel-restricted" files and the "nvidia-glx-new" module was unchanged; so you can simply use the older version and that version will automatically use the working .22 support files.

fudoki

---

### Post by warped6 on 2009-01-30
SOLVED! Well for me anyway. I removed the ATI drivers (apt-get remove fglrx*) and then reinstalled them (apt-get install fglrx*). I had to reactivate screen effects but everything is back up and running.

---

### Post by jfmxl on 2009-01-30
I installed the same update and although I have video and X it's stuck at 800x600 resolution with no way to change it. I'm going to try to revert to the old kernel... and discontinue ubuntu upddates from now on! 

This is not the first time they've screwed up my machine. And this is relatively mild. 

The last time they screwed X completely, as for the poor folks above. My sympathies. I wonder if they test things at all at ubuntu, and how many machines they trash with their "updates"? I guess it's my own fault for assuming they'd fix whatever was wrong in their update process. They clearly do not care.

---

