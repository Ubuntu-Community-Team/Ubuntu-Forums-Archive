---
title: "Ubuntu 7.10 on Thinkpad T61p 6457-5KU"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by rybu on 2007-09-04
Hi forum people.  This thread will document my installation & teething problems for Ubuntu 7.10 on a Lenovo Thinkpad T61p.  

First of all, let me say the reasons I chose Ubuntu 7.10:

1) The previous stable release, 7.04 dies horribly during the initial boot-up on the install CD.
2) I've also tried installing openSUSE 10.2 and Gentoo 2007.  Gentoo also dies horribly.  openSUSE installs, and it wasn't hard to install the graphics driver but I found openSUSE to be not very friendly, and basic things like audio and wifi I couldn't get working. 

From the install CD, the VGA graphics mode works fine.  Ubuntu seems to choose some out of date graphics driver for my NVIDIA card, which works in a few resolutions but not 1920x1200.  After installing Ubuntu and doing an update, the new driver is installed and 1920x1200 works fine although it seems to be a little gung-ho on playing around with dimming, I've yet to figure out what's causing that, but the brightness just jumps around sometimes.  

After the update, I did run into a boot script problem that several people seem to have run into for various reasons.  Here's the thread w/my post: [http://ubuntuforums.org/showthread.php?t=413975](http://ubuntuforums.org/showthread.php?t=413975)

wifi worked straight off the install cd, same with cable ethernet.  Audio didn't work initially, but after following the instructions to update the alsa drivers: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

audio works now, with some problems.  One problem is if I go to Preferences -> Sound and run any test, I get a loud sustained tone coming out of the speaker.  The volume buttons don't control how loud it is, nor the main system slider for volume. 

Right now I'm mainly trying to get my standard collections of applications to run.  mplayer  plays audio but not movies. amarok does not load. xine plays movies fine, but uses way too much processor time (100%, and it complains that my duo core system is too slow). Googleearth doesn't work but I've found out that it's because the linux distro only has a 32-bit binary, so I imagine I could find a work-around. regina-normal does not compile -- this is not so much of interest to the forum unless I find an interesting reason why.  Hopefully that'll be sorted-out soon. 



Here are a few example dumps of failures:

```

rybu@rybu-laptop:~/movies$ amarok
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault (core dumped)

rybu@rybu-laptop:~$ amarok -v
Qt: 3.3.7
KDE: 3.5.7
Amarok: 1.4.7



rybu@rybu-laptop:~/movies$ mplayer TG_Koenigsegg.flv 
MPlayer 2:1.0~rc1-0ubuntu11 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing TG_Koenigsegg.flv.
libavformat file format detected.
VIDEO:  [FLV1]  320x240  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 22050 Hz, 1 ch, s16le, 8.0 kbit/2.27% (ratio: 1000->44100)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [x11] 320x240 => 320x240 Planar YV12 


MPlayer interrupted by signal 11 in module: decode_video
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

Other than this crash issues, the slowness of xine is disturbing.  Any ideas?  Let me know if you need any additional information. 


I'll add more to this thread as various issues get resolved / develop.  I haven't looked into the fingerprint reader, or the webcam, or tried burning DVDs, etc... all to come.

---

### Post by rybu on 2007-09-04
Another crashed app:

```

rybu@rybu-laptop:~$ ktorrent 
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOP aborting call from 'anonymous-12816' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
DCOP aborting call from 'anonymous-12805' to 'ktorrent'
ERROR: Communication problem with ktorrent, it probably crashed.


rybu@rybu-laptop:~$ ktorrent -v
Qt: 3.3.7
KDE: 3.5.7
KTorrent: 2.2.1

```

So there seems to be a pattern here of problems with Qt.

---

### Post by softtower on 2007-09-05
I apologize for not very useful advise, but if I were you I would try to get back to 7.04 and find out exactly *why* it dies horribly. I also have T60p and was so impressed with Linux compatibility that even [blogged about my experience a bit here]("http://kontsevoy.blogspot.com/2007/08/best-notebook-for-linux.html").

The only difference between our machines, as it seems, is the video card. I would try to get "Alternate install CD" for 7.04, install in text mode and manually add video drivers later.

Also I would check what is in your BIOS.

---

### Post by rybu on 2007-09-05
If I knew how to figure out why it died horribly, I might have tried to keep 7.04 running.  Problem is, I don't know how.  I'd love to have someone that knew every line of ubuntu's code like the back of their hand, especially if she was a cute young doctor with some spare cash.. but I don't.  So I went with what was easier.  I can live without amarok and ktorrent for a while.  Enough of my most frequently used apps are working for now for the laptop to be functional.  I'll stick out this alpha release for a while yet.

I filled out a bug report: [https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/137445](https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/137445)

as I figure it's a kdelibs problem.

---

### Post by rybu on 2007-09-08
Things seem to be coming together.  The bugs I listed above have mostly dissapeared in recent revisions to Ubuntu 7.10.

Instructions to get NVIDIA native drivers, audio drivers, fingerprint reader, etc, etc, working are all appearing here:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61#Video](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61#Video)

Things are looking up. 

Some of the DRI apps crash now, but more and more functionality is appearing.  Happy happy.

---

### Post by lamborghiniwang on 2007-09-11
Thanks for the information rybu! 
My 14" T61p will arrive in a few days, and the information you provided in this post is exactly the one that I am looking for. :)
Hopefully the problems will be solved when Gusty finally comes out.

---

### Post by rybu on 2007-09-12
Glad I could help.  If I didn't have another machine up and running (a thinkpad t30) I probably wouldn't be experimenting like this.  

At present the main thing I'd like to have straightened out is the X server. Getting a 2nd monitor to work.  It's possible to get a working 2nd monitor which functions as a 2nd display, but X is pretty clunky and slow.  I think maybe the latest driver from NVIDIA isn't quite fully adapted to the 570M.  But I also think there's problems with ubuntu as X is slower with the most recent kernel (2.6.22.11) than with the previous (2.6.22-10).  I don't know if it's the kernel or all the 100+ other modifications that happened in the past 2 days. Hopefully all will be straightened out soon.  At present I'm too busy to fill out bug reports.  If the bugs persist until this weekend, I'll fill out a report then...

---

### Post by rybu on 2007-09-13
Today I updated to:

xserver-xorg-core (2:1.3.0.0.dfsg-12ubuntu4)

and my window resizing problems (slowness) went away.   I had to rebuild the NVIDIA drivers in the process (once I entered my password in the login screen it would crash X. a rebuild fixed that).  Resizing windows is nice and fast again. 

But the screen saver and glxgears keeps on crashing X.  I assume this is because they're just not as up to date as the rest of the core modules.   Is this the case?    I suppose the easiest way to find out would be to locate the code for glxgears, and the screen saver and recompile them to see if that leads to any improvement...

Ah, the glxgears problem is part of a much bigger xorg - NVIDIA problem.  Bug report here:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/130325](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/130325)

As suggested in the above thread, turning off desktop effects solves this problem. You don't even need to restart X.  Very simple.

---

### Post by rybu on 2007-09-15
At present I'm not having any luck getting bluetooth to operate.  I can't even get the little "bluetooth lamp" to light up, below the monitor.  On the thinkpad t30 there was a button.  But on the t61 I guess there's a software trigger... somewhere...

update: bluetooth works fine now.   Here are the steps:

Step 1: run "sudo modprobe thinkpad-acpi"

Step 2: to enable bluetooth (and turn on the bluetooth light), type "echo enable > /proc/acpi/ibm/bluetooth" as root, or copy that into a script and run via sudo.  To disable: "echo disable > /proc/acpi/ibm/bluetooth" again either as root or turn it into a script. 

Once bluetooth is enabled, all the standard bluetooth tools work: bluez-utils, the bluetooth analyzer, etc.

This information was derived from the newly updated wiki:  [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61#Video](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61#Video)

Thanks Darrena.

---

### Post by rybu on 2007-09-15
The next thing I'd like to do is get my webcam working.  It's a USB webcam from Lenovo.   There it is:

[img]http://gizmologia.com/wp-content/uploads/2006/10/lenovo-webcam.jpg[/img]

The specifics: Lenovo USB webcam, FRU40Y8177, PN: 40Y8519. 

Apparently it's a UVC webcam so these drivers "should work":

[http://openfacts.berlios.de/index-en.phtml?title=Linux_UVC](http://openfacts.berlios.de/index-en.phtml?title=Linux_UVC)

A uvcvideo driver is present in ubuntu 7.10 but on compiling the new one it's clear to me they're very different beasts:

Old: -rw-r--r-- 1 root root 73376 2007-09-07 13:39 /lib/modules/2.6.22-11-generic/ubuntu/media/usbvideo/uvcvideo.ko

New: -rw-r--r-- 1 root root 860498 2007-09-15 18:27 /lib/modules/2.6.22-11-generic/kernel/ubuntu/media/usbvideo/uvcvideo.ko

Simple question: how do I create /dev/video0 and link it to one of those two video drivers?  I'd like to see if one of them works...

---

### Post by lamborghiniwang on 2007-09-20
OK, my 14" T61p finally arrived yesterday. I only tried Feisty. X won't start initially but after installed the Nvidia driver using Envy, it works fine now. Surprisingly the bluetooth light can be turned on/off using Fn+F5, however Feisty can't recognize the 4965AGN card and I haven't got a chance to fix the problem yet. There were some random issues popping up now and then, so Feisty is not running as stable as it does on my T60.

I am not sure if I should keep Feisty or install Gusty Tribe 5. According to ThinkWiki, there is a chance that wifi will work automatically in Gusty T5, which is important since we don't have a wired LAN in the office. On the other hand, I am worrying about the stability of Gusty T5. I will defend my thesis in a month and I need the laptop to finish writing my thesis, so if I lose some of my work because of the instability of Gusty it will be a disaster. :(

---

### Post by rybu on 2007-09-20
Fn+F5 does not work to enable bluetooth in 7.10, unfortunately.  I wonder how I could set up that keybinding.

Regarding wifi, yeah, it worked straight off the install CD, no fussing about required on my part.

So far anyhow, I've found 7.10 to be pretty stable.  I'm not taking any chances -- any file that gets modified on my system immediately gets backed-up onto a USB hard drive. 

Good luck on finishing your thesis.  The distraction of an unstable system might be too annoying.  I locked myself up in my apartment for two months, drank lots of tea and just avoided the rest of the world for that period of my life...

---

### Post by bliffle on 2007-09-20
Maybe it's the pre-release 7.10. I tried Kubuntu 7.10 on an old Thinkpad 570 a couple weeks  ago and had many problems, so I dropped back to kubuntu 7.04 and it went in and worked right away (except for the usual dialup and wifi problems, of course).

---

### Post by lamborghiniwang on 2007-09-21
OK, I installed Gusty using the alternative installation CD, but have some problems here. 

1) Gusty didn't detect the Windows XP that is already installed in the HDD, it also didn't allow me to choose where to install GRUB, instead it installed GRUB into MBR (I wanted to install it into /boot partition). Also, when I boot into GRUB, there is no option for XP so I had to boot into safe mode and manually insert the XP boot option into menu.lst.

2) The normal boot-up for Gusty doesn't work. I can see the boot splash (the loading bar), but as soon as  gdm starts up, the screen turns into black and hang, Ctrl-Alt-F1 doesn't work (I believe the system is still running because I can reboot the system with Ctrl-Alt-Delete, it just won't display anything on the screen). If I disable the splash option in grub, I can see all the boot log until gdm starts, then the screen turns into black again. If I remove the splash option from the grub option and input something like "vga=791" to enable framebuffer, the screen will immediately turn into black and I won't be able to see the boot log. It seems the problem is related not only to X but also to the framebuffer or whatever display model which is different from the default 80x25 command line mode. 

Any suggestions? :confused:

---

### Post by lamborghiniwang on 2007-09-22
Finally found a way to work around the black screen problem. Basically I just boot into the recovery mode, and change "nv" into "vesa" in xorg.conf, and then I can boot into Gnome to configure the wireless network. After the wireless network is on, I installed the updates(including the newest nvidia driver), and then the black screen problem is gone. Although it seems I still have some problem with the framebuffer settings, it seems it only works at the lowest 80x25 mode, any attempts to change it into 1024x768 or higher leads to black screen during boot until gdm is started, and Ctrl-Alt-F1 will also produce black screen.

Anyway, I found that the bluetooth is working now, all I did was
```

$ sudo -i
# echo enable > /proc/acpi/ibm/bluetooth

```
I also found that the gnome bluetooth applet is great, I used it to install my bluetooth mouse, and it is was easier than edit the /etc/default/bluetooth file. (also I found that if I set  HIDD_ENABLED=1, it will produce an error message during boot saying that the bluetooth host can not be found)

---

### Post by bliffle on 2007-09-25
I'm contemplating a T61, so I'm concluding from this string that 7.04 won't work and I've gotta go 7.10, so I might as well wait a couple weeks for the actual release.

Is that about right?

---

### Post by lamborghiniwang on 2007-09-26
> **bliffle said:**
> I'm contemplating a T61, so I'm concluding from this string that 7.04 won't work and I've gotta go 7.10, so I might as well wait a couple weeks for the actual release.

Is that about right?

You can use 7.04, but sound and wireless (only 4965AGN card, I believe 3945ABG card works) won't work automatically.

---

### Post by rybu on 2007-10-07
NVIDIA recently updated their webpage to be a little less obtuse.  This is the first time I've even seen the mention of the type of card the Thinkpad t61p *has*.  So maybe in the not too distant future a proper video driver might exist?

[IMG]http://i117.photobucket.com/albums/o64/configurationspace/nvidia-screen.jpg[/IMG]

Their driver for the Quadro FX card (as opposed to the Quadro FX Mobile) works for most purposes on my laptop, but it *is* buggy and running with Compiz will cause X to crash with the Quadro FX driver.

---

### Post by j0rd on 2007-10-18
Did you guys install x32 or x64 bit versions of ubuntu?

What would you recommend for a guy who looking for less hassles and just wants his machine to work?

---

### Post by rybu on 2007-10-19
> **j0rd said:**
> Did you guys install x32 or x64 bit versions of ubuntu?

What would you recommend for a guy who looking for less hassles and just wants his machine to work?

I installed the 64 bit version, mostly because I'm working on an app which makes significant use of the bigger pipeline. 

I doubt it'll make much of a difference which kernel you install.  Since in the 64-bit version you can install 32-bit compatibility libraries for any 32-bit only code you may need to run.

---

### Post by lamborghiniwang on 2007-10-21
I am running 32bit Gutsy on my T61p. Most of the things are working, except suspend and hibernate, and I also have the IRQ problem for the USB port (two USB on the right hand side stop working if idle for more than 10 minutes, the left one works perfectly though).
Haven't tried 64bits though.

---

### Post by dmz17 on 2007-10-28
etooth is working now, all I did was
```

$ sudo -i
# echo enable > /proc/acpi/ibm/bluetooth

```
I also found that the gnome bluetooth applet is great, I used it to install my bluetooth mouse, and it is was easier than edit the /etc/default/bluetooth file. (also I found that if I set  HIDD_ENABLED=1, it will produce an error message during boot saying that the bluetooth host can not be found)[/QUOTE]

Lucky you! I got the T61p. Bluetooth does not seem to work. Suspend does not work, Everything else (ok, perhaps sound volume controls do not) works.

---

### Post by rybu on 2007-10-28
> **dmz17 said:**
> 
Lucky you! I got the T61p. Bluetooth does not seem to work. Suspend does not work, Everything else (ok, perhaps sound volume controls do not) works.

Bluetooth is working fine on my T61p.  Sound controls, too.

---

### Post by dmz17 on 2007-10-29
SQUOTE=rybu;3656607]Bluetooth is working fine on my T61p.  Sound coGtrols, too.[/QUOTE]
Bluetooth:
Any chance you could post what you did? I have a Samsung cell phone and cannot connect. It worked with OpenSuSE 10.3, but not with anything prior to that (not even Vista Ultimate).

Sound controls:
The keyboard controls work, the sound applet volume slider does not.

BTW:
Have you, by any chance, got suspend to RAM or hibernate working on the box? 

Got Suspend working now. I can live without Bluetooth and sound controls.

Tnx in advance.

---

### Post by arsenix on 2007-10-29
Any of you T61p users try burning a CD?  For some reason it doesn't work on my machine.  Been a few years since I had trouble with cd burning under linux...

  My dmesg fills up with:
[ 4289.524000] end_request: I/O error, dev sr0, sector 0
[ 4289.524000] Buffer I/O error on device sr0, logical block 0

  cdrecord says:
Last chance to quit, starting real write    0 seconds. Operation starts.
cdrecord: WARNING: Drive returns wrong startsec (0) using -150
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 10 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 2A 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 200s
write track pad data: error after 0 bytes
BFree: 1029 K BSize: 1029 K
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 10 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 2A 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 200s
write track data: error after 0 bytes
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

  Anybody else see this issue?  Other CD drive use seems to work just fine...

James

(PS Will create new thread for this issue... wanted to ask T61p specific folks as well)

---

### Post by dmz17 on 2007-10-29
Just put 600MB of digital photos on a CD (not DVD) using Ubuntu 7.10 on a T61p and K3B. It worked just as expected.

Have not tried a ISO image yet but have no reason to believe that it would not work.

Cheers,

Malte

---

### Post by arsenix on 2007-10-29
Hmm.  Interesting.  Do you have the HL-DT-ST GSA-U10n drive like I do?  What BIOS rev are you using?

  Maybe my hardware is pooched...   it does work under Vista (ugh)

James

---

### Post by dmz17 on 2007-10-29
Any way I can figure that out w/o booting and hitting the ThinkvVantage thingie?
(New to Ubuntu, I'm afraid). Confession in order: Switched to Ubuntu, after succesfully installing OpenSuSE 10.3 and promptly trashing KDE when downloading an 'important security update'. Sometimes I just need to use a computer, not tinker with it.

---

### Post by dmz17 on 2007-10-29
OK, I broke down and rebooted. This is from the thinkVantage utility:

BIOS 1.14 (7LET44WW)
Date 2007-06-27 (you can tell it's a fairly new machine)

Controller version 1.06

DVD:

ATAPI CDO: MatshitaDVD-RAM UJ-852-(SM)

I hope this helps,

Malte

---

### Post by arsenix on 2007-10-29
So you do have a different DVD from me...

  In the meantime, I tried burning a disc with "Brasero" and it worked fine with no error messages.  So apparently my cdrecord is the issue.  I don't believe brasero uses cdrecord as a backend... I'll check into it.  Thanks for confirming that it works :)


James

---

### Post by dmz17 on 2007-10-29
I am not surprised. I believe that more often than not, what goes into a PC is what is available/cheapest on the particular day of production.

---

### Post by rybu on 2007-10-31
I've had no problem burning DVDs.  I have both one of the internal DVD CD-RW multi-burners, and an external USB lightscribe DVD CD+RW burner.  Both work fine.

I got the Razer bluetooth mouse in the mail today.  It also works fine, once HIDD_ENABLED=1 is set in /etc/default/bluetooth. Ubuntu remembers the mouse's mac address after a single handshake, so it'll recognise the mouse immediately after it has been turned on. 

Ever since the most recent kernel upgrade (just before the Ubuntu 7.10 RC came out) I've been having strange episodes where my laptop just *shuts down* of its own freewill.  It's strange that all the Ubuntu 7.10 beta distros were more stable than the release, but that seems to be how it's working for me. 

I filled out a bug report several weeks ago, but it goes pretty much unnoticed: [https://bugs.launchpad.net/ubuntu/+bug/152202](https://bugs.launchpad.net/ubuntu/+bug/152202)

---

### Post by brenix on 2007-10-31
Everything seems to be stable on my T61p (burning, video, nvidia 570m). My sound had worked fine until I fiddled with something and now I only have one possible output at a time..Any ideas?

---

### Post by StrangeBrew on 2008-02-12
I just got my T61p 6460-8VU. When I select start and install Ubuntu (7.10) after a few minutes the screen goes blank and the cd stops spinning.

---

### Post by dmz17 on 2008-02-13
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61#Installation_Notes](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61#Installation_Notes)

Might help you. I also seem to remember that there is a certain 'compability' thingie one can switch on/of in the BIOS..

I have the same machine, and 7.10 works very well.

Good luck!

Malte

---

### Post by StrangeBrew on 2008-02-13
I changed the serial ata controller in the bios to run in "capability" mode. All that did was make it run slow enough I could read what was being displayed.  It gets a uevent error no buffer space, then this.
cat: /var/lib/acpi-support/system-manufacturer: no such file or directory
cat: /var/lib/acpi-support/system-product-name: no such file or directory
cat: /var/lib/acpi-support/system-version: no such file or directory
cat:/var/lib/acpi-support/bios-version: no such file or directory

then another error...The display server has been shut down 6 times in the last 90 seconds. It is likely that something bad is going on (no kidding!). Waiting for 2 minutes before trying again on display :0.

---

### Post by uchihaitachi on 2008-02-26
I encounrtered that message when I select safe graphic mode installation.
I'll let the installation hit the error you mention, switch to another console screen (ctr + alt + f1)
Type startx
You should be able to start the livecd from that point onwards. You should be better off from this point.

OOB installation won't get your graphics to work. The most obvious way for it to work is downloading restricted nvidia drivers (a pop up will notify you) and you'll be set from that point on.

---

