---
title: "Dell XPS m1330 with Ubuntu 7.10"
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by Mr. Johnson on 2007-10-06
Hi :)

I'm curious about how Ubuntu 7.10 will work on the Dell XPS m1330 laptop, do anyone know?
What kind of issiues might I've experience? Maybe problems with the webcam on m1330, etc?
One thing too, will the Ubuntu 7.10 be laptop friendly (I'm thinking of batteri life; options, etc).

If you have any experience or knowledge of informartion, please do share.
Thank you for your time.

Cheers :KS

---

### Post by neo.patrix on 2007-10-06
Well if you could please give your hardware cofiguration, like Videcard, Soundcard, etc. I
have Dell Inspirion 6400, it does have some problems with Graphics.

---

### Post by Mr. Johnson on 2007-10-06
> **neo.patrix said:**
> Well if you could please give your hardware cofiguration, like Videcard, Soundcard, etc. I
have Dell Inspirion 6400, it does have some problems with Graphics.

If you checked my signature at my first post, you would see! :)
About the soundcard, I could not find anything about it. But yeah, it's the basic soundcard you get with the m1330, so...

---

### Post by Mr. Johnson on 2007-10-08
Oh well, it's only few days before I get my Dell XPS m1330 so I'll give a feedback on how it works with Ubuntu 7.10 very soon. :)

---

### Post by jespdj on 2007-10-08
Me too - my m1330 has been shipped and will be here in a few days \\:D/

For more info on Linux on the m1330 have a look here:
[http://forum.notebookreview.com/forumdisplay.php?f=1029](http://forum.notebookreview.com/forumdisplay.php?f=1029)

---

### Post by LML on 2007-10-08
Thank you for this!
I'm really looking forward to read about your experiences!!!

---

### Post by IgnatiusReilly on 2007-10-09
I have recently decided to move to Linux because of Vista bugs (It is still really unstable)
After some time spent trying to install the 7.04 without success, following a suggestion I installed Ubuntu 7.10beta on my Dell XPS M1330 a few days ago. 
I am really a newbie with Linux and Ubuntu Linux, but I am really surprised that almost everything works fine (wireless, webcam, CD, sound,).
I am experiencing some problems only with the internal microphone and with the hibernation process. The microphone does not record any sound and the hibernation process turns out to be a one way process (Computer got asleep forever...)
 don't know if it is just my fault cause I don't have yet enough experience
Could anyone give me some suggestion?

Thanks a lot.

---

### Post by Mr. Johnson on 2007-10-10
> **IgnatiusReilly said:**
> I have recently decided to move to Linux because of Vista bugs (It is still really unstable)
After some time spent trying to install the 7.04 without success, following a suggestion I installed Ubuntu 7.10beta on my Dell XPS M1330 a few days ago. 
I am really a newbie with Linux and Ubuntu Linux, but I am really surprised that almost everything works fine (wireless, webcam, CD, sound,).
I am experiencing some problems only with the internal microphone and with the hibernation process. The microphone does not record any sound and the hibernation process turns out to be a one way process (Computer got asleep forever...)
 don't know if it is just my fault cause I don't have yet enough experience
Could anyone give me some suggestion?

Thanks a lot.

First of all I want to thank you for sharing your experience, and I'm happy too hear that wireless, webcam, sound works fine! :) As for your questions, my Dell XPS m1330 will arrive today so I can say more after that. But I hope someone else can give you any suggestions too.

Cheers :KS

---

### Post by Mr. Johnson on 2007-10-10
I'm on my Dell XPS m1330 now in Vista because as I try Ubuntu 7.10 and I find wireless network I try to connect with the password and all that I use in Vista that works.

But in Ubuntu 7.10 it just use all day long trying to connect without getting there. :confused:

What now?
I need to connect to the Internet. And I am i no position to have a wire connected to my laptop, only wireless here.

---

### Post by LML on 2007-10-10
Are you using WPA or WPA2 encryption? In that case I guess you'll need wpasupplicant. Or simply stack down to WEP for the meantime

---

### Post by Mr. Johnson on 2007-10-10
> **LML said:**
> Are you using WPA or WPA2 encryption? In that case I guess you'll need wpasupplicant. Or simply stack down to WEP for the meantime
It's WEP (open) and it works with Vista, but not in Ubuntu 7.10 when I try, do I have to install it first? Because I should get connected simply when I use Ubuntu 7.10 from the DVDROM. Because no point of me installing it, if I can't connect to the Internet for updates, etc.

---

### Post by LML on 2007-10-10
sry, i dont know that. i would try to get a wired connection for the installing process.
(In my case, i allways used a wired connection first, because wlan never worked out of the box...)

Do you have this n-WLAN card in use?

kind regards.

---

### Post by Mr. Johnson on 2007-10-10
Now it works, yes! Going to install Ubuntu 7.10 and do the updates, later!

---

### Post by jespdj on 2007-10-10
> **IgnatiusReilly said:**
> I am really a newbie with Linux and Ubuntu Linux, but I am really surprised that almost everything works fine (wireless, webcam, CD, sound,).
Good to hear that. I'm surprised that even the webcam works fine, I've tried getting a webcam (not the M1330 webcam) to work on Ubuntu some time ago and it was very hard and didn't work. It seems that most webcams are poorly supported because the manufacturers use proprietary protocols, so it's difficult to write Linux drivers for webcams.
> **IgnatiusReilly said:**
> I am experiencing some problems only with the internal microphone and with the hibernation process. The microphone does not record any sound and the hibernation process turns out to be a one way process (Computer got asleep forever...)
I think that is a [known bug](https://bugs.launchpad.net/dell/+bug/147682) in Ubuntu 7.10 Beta. It is in the [list of bugs to solve for 7.10 Release Candidate](https://launchpad.net/ubuntu/+milestone/ubuntu-7.10-rc). According to the bug report, a fix is available, so let's hope the fix is included in the final release of 7.10 next week.

---

### Post by Mr. Johnson on 2007-10-12
Ok, I think I got a problem. I'm not sure.

But as I use Rhythmbox musicplayer and I listen to few songs I get this noise, like the speakers are exploded? Kinda... Even when I plug my headphones in but if I listen to a song on full volume on like YouTube, there is no noise at all.

What can be the problem?

---

### Post by regmee on 2007-10-17
I had problems installing 7.04 ubuntu and so I had gutsy gibbon (tribe 5) installed instead.
I din't have any problem with wireless. 

below are the problems that I have faced and instead of running after 'em I thought of waiting for the 7.10 release (that's tomorrow ... yippieeeee .. :-) 

a) audio .. only through the second head-phone slot.
b) Desktop does not streach fully to the right end of the screen. I tried playing with the nividia drivers and had to install the system thrice :(( ....... but finally learnt to get the X-server re-configured that din't make me install for the fourth time. 
c) Din't try out the WebCam stuff.
d) I can make calls thro' skype but the person on the other side can't hear what i speak :P 
Seems like Microphone is not configured well to grab my speech .. :) 
e) Wireless is working too good. Never faced any problems with it so far. 

will try to discover more once I get the release tomorrow :) 

Have fun guys !!! 

- Regmee.

---

### Post by tuaranoi on 2007-10-18
hi guys,

i have a laptop in office with ubuntu 7.10 install, 

1. i have hibernation problem, cannot wake up.
2. projector displayed, but with separate screen not working properly.
3. network sometime will hang and need to restart PC.

:confused:

---

### Post by xl_cheese on 2007-10-18
Internal mic patch here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963)

These systems will now be included with preinstalled ubuntu in a few weeks...  Maybe others, but I'm not sure.

I just started working at IDT which bought the sigmatel audio codec group.

---

### Post by Oxymeron on 2007-10-19
anyone got cpu-scaling up and running?

mine seems messed up or not working.

i'm using the acpi_cpufreq module combined with cpufreqd.

---

### Post by kswenson on 2007-10-20
Just to summarize...
   almost everything works without configuration in 7.10.

doesn't work:
  - internal mic (plug-in mic works though)
see -  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963)
         [https://bugs.launchpad.net/dell/+bug/147682](https://bugs.launchpad.net/dell/+bug/147682)
  - hibernate (but suspend works half the time)

does work:
  - suspend to memory
     (UPDATE: see [this thread]("http://ubuntuforums.org/showthread.php?p=4247400#post4247400") for info on getting  it to wake well every time) 
     (also see the "If you have sound issues after restore" message below)
  - sound
  - plug-in mic
  - 3d acceleration (compiz-fusion is nice but some operations use CPU)
  - dvd/cd read/write
  - blue media buttons (including screen brightness buttons)
  - SD/MMC - MS/Pro card reader
  - power consumption control (gnome power management)
  - remote control
  - cpu speed control (i use emifreq-applet, does anyone know a better one?)
  - projector (note: change the System->Preferences->"Screen Resolution" first to that of your projector, then use Sys->Admin->"Screens and Graphics")
  - internal camera (with ekiga anyway)

MY SETUP:
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
WLED scree with 0.3 Mpixel webcam

---

### Post by natuan on 2007-10-20
I have problem with internal mic too and also my wireless card doesn't work (without configuration in 7.10)
EDIT: I have a broadcom 1390 wireless card

---

### Post by gertin on 2007-10-20
Has anyone gotten the webcam to work with mplayer?
The following won't work: (taken from [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam))

```
martin@xps:~$ mplayer tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: Laptop Integrated Webcam
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
FPS not specified in the header or invalid, use the -fps option.
No stream found.

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.

Exiting... (End of file)
```

Camorama won't work either. It claims it can't open /dev/video0.
Everytime mplayer or Camorama tries to use the webcam, a blue light blinks on the top of the monitor, right next to the webcam.

---

### Post by jespdj on 2007-10-20
Note that the XPS M1330 comes with one of two different webcams: if you have the CCFL screen, it has a 2.0 Mpixel webcam, if you have the WLED screen, it has a 0.3 Mpixel webcam.

I have a WLED screen and the webcam does not work either. Ubuntu recognises the webcam, and I do have a device /dev/video0, but it doesn't work, I have the same problems:
> Camorama won't work either. It claims it can't open /dev/video0.
Everytime mplayer or Camorama tries to use the webcam, a blue light blinks on the top of the monitor, right next to the webcam.

---

### Post by gertin on 2007-10-20
> **jespdj said:**
> Note that the XPS M1330 comes with one of two different webcams: if you have the CCFL screen, it has a 2.0 Mpixel webcam, if you have the WLED screen, it has a 0.3 Mpixel webcam.

I have a WLED screen and the webcam does not work either. Ubuntu recognises the webcam, and I do have a device /dev/video0, but it doesn't work, I have the same problems:
I have the WLED screen too and if you try using the webcam in Ekiga, it should work (it did for me). Now I'm just wondering which options Ekiga passes to the V4L2 driver, that mplayer doesn't. They use the same driver, so I'm guessing it should work with mplayer too.

---

### Post by broken_symmetry on 2007-10-20
Howdy all,

I am trying to set up beryl on my m1330, and I just cannot get it to work.

It worked a few builds before the official gutsy release, and an update broke it.

Right now I cannot even get the nvidia proprietary drivers running....I have the nvidia card of course.

Has anyone else had this problem and can anyone give me any hints? I am hoping to get compiz-fusion running on my 1330 again.

Thanks,

NM

---

### Post by rhonaldmoses on 2007-10-21
Hi,

Ubuntu 7.10 works perfect in DELL XPS M1330, however if you wish to retain Vista, MediaDirect (you better retain this coz your laptop gets messed up if you press MediaDirect key without having MediaDirect installed), follow the link below:

[http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html](http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html)

---

### Post by paulten on 2007-10-21
Hi all.

I bought the m1330 about two weeks ago. This is by far the most linux friendly laptop I've had.
Hibernate and suspend works (however sound does not work after restore, still working on that) webcam works, remote works... all out of box.

Really nice to find this post, I have one annoying problem which I explained in a post here :
[http://ubuntuforums.org/showthread.php?t=584790&highlight=ticks](http://ubuntuforums.org/showthread.php?t=584790&highlight=ticks)

The harddrive made strange ticks or clicks every time the hdd spins up or down. It was solved.

---

### Post by LML on 2007-10-21
Hi!
I'am thinking of buying this laptop, but i've still a few questions. So could you please help me with this?

-how good is compz-fusion working together with emerald? (nvidia)
-Is there a cpu-state / fan-speed throttling problem with the T7250 cpu?
-Is it possible to use Media Direct and ubuntu without a windows vista installation?

Thanks a lot!!

---

### Post by saracen on 2007-10-23
**If you have sound issues after restore:**
> 

Install linux-backports-modules-2.6.22-14-generic and run the following script:

#!/bin/sh
## Fix for audio failure after Suspend and Hibernate
cat > /etc/acpi/resume.d/99-restore-volume.sh << EOF
#!/bin/sh
amixer sget Master|grep "Mono:" | while read m p v j
do
   amixer sset Master 0
   amixer sset Master \$v
done
EOF
chown root.root /etc/acpi/resume.d/99-restore-volume.sh
chmod a+x /etc/acpi/resume.d/99-restore-volume.sh


---

### Post by regmee on 2007-10-27
Thanks **saracen  **

That helped fix my sound problem after hybernation. :) 
I still have problems with the Mic. Well I am not so confident to apply the patch in the source [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963) 
I fear I might screw up my system again. :( Have done it several times already.
I hope there will be an update coming up sooner on the Mic thingie.

My volume control touch-buttons won't work though :( .. I am using the volume controller applet everytime music goes too loud.  anyone with a solution ?

--
Regmee

---

### Post by youngerpants on 2007-10-27
I've just tried running the patch for the microphone using the command " patch -p1 < stac9228_dmux_mixer_ubuntu.patch "

Unfortunately I got an error back;

can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Only in linux-source-2.6.22/sound/pci/hda: hda_codec.c.orig
|diff -ur linux-source-2.6.22.orig/sound/pci/hda/patch_sigmatel.c linux-source-2.6.22/sound/pci/hda/patch_sigmatel.c
|--- linux-source-2.6.22.orig/sound/pci/hda/patch_sigmatel.c    2007-10-17 23:23:31.000000000 -0400
|+++ linux-source-2.6.22/sound/pci/hda/patch_sigmatel.c 2007-10-24 00:07:12.000000000 -0400
--------------------------
File to patch:



Oh, incidentally, the webcam works through aMSN as well as Ekiga

---

### Post by robert@debian on 2007-11-13
Well I've got the same problem with the microphone as you guys.
Has anyone solved the problem by now?

@youngerpants 
Have you encountered any sound input (external Input) or output problems since
you've tried to patch the kernel?
I don't like to mess up my system for no good.

---

### Post by jespdj on 2007-11-21
There is a patch available to make the internal microphone work.
See [bug #147682](https://bugs.launchpad.net/dell/+bug/147682).

About the webcam: It seems that the built-in webcam is only supported by V4L2, not by V4L. Camorama uses V4L and doesn't work. The webcam works without problems with other programs such as Cheese, Ekiga and Skype 2.0 Beta.

---

### Post by cendant on 2007-11-28
Did anyone manage to run Gutsy LiveCD on XPS 1330?

I get a message about a low-than-usual resolution, after that the CD hangs the system

---

### Post by LML on 2007-11-28
Have you tried to set the correct resolution by pressing F2 (or what ever it was...)? What about safe mode?

---

### Post by robert@debian on 2007-11-29
Thanks alot jespdj. Now everything just works fine :guitar:

---

### Post by FrankVdb on 2007-12-05
I bought the XPS M1330 as well. In contrast to the Latitude and Inspiron laptops, Dell would not supply the M1330 without an OS so they shoved me Vista down my throat.

I made a fuss and got a 70 € discount on the Belgian price. Needless to say, I was so happy to see Gutsy trash everything pre-installed on my brand-new, gorgeously looking laptop (it's got the crimson cover). In other words: the install went flawless. Apart from the mike and the webcam, which I haven't tested yet, everything just works. Wonderful.

The only thing I am struggling with, is the sleep mode. It just doesn't work. Same goes for the pause mode or whatever it's called in English (I'm using the Dutch version).

Any ideas?

---

### Post by visionofarun on 2007-12-05
Its not been a pleasant experience for me with Ubuntu on M1330. Ubuntu installation hung up once. 
If i try to enable the compiz-fusion effects, it says, "Desktop effects could not be enabled" :( 
Mine is Intel Graphics Media Accelerator X3100. Wireless card is not working..

This is my configuration. Can any one help please?

```
 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

---

### Post by FrankVdb on 2007-12-07
Apparently, you don't have a real graphics card on your system. I think it is just a chip that uses RAM memory to produce video. As a result, you may experience lag when using Compiz on your system.

My configuration - probably a little bit higher-end than yours - has a GeForce 8 series card. All of the standard Compiz Fusion stuff that comes with Gutsy works flawlessly on it. Actually, I'm amazed. 

Have a look on
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2301&DwnldID=13815&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2301&DwnldID=13815&strOSs=39&OSFullName=Linux*&lang=eng)
for Intel drivers for Linux.

---

### Post by kswenson on 2007-12-09
Thanks for the sound fix saracen...
   it seems as though pressing mute now losses the state of the sound before; unmute just restores to 0 volume level.
I don't think this happened before.  Do you have an idea why this is happening?

---

### Post by bcrom on 2007-12-16
To fix the touch sensitive volume buttons open System->Preferences->Sound and under Default Mixer Tracks, select SigmaTel STAC9228 (OSS Mixer) or whatever you OSS mixer is.    Make sure your Sound Capture is still set as ALSA, or your mic may not work.  

Let me know if this helps.

---

### Post by yesint on 2007-12-28
Dear All,
I'm playing with Kubuntu on xps1330 and have found few very annoing problems. Could you please help me to fix them.
1) Brightness can not be adjusted by Fnc+up/down. The only way to adjust brightness, which I found, is from the power-saving applet. This is very inconvenient. Is this also the case in Gnome or this bug is KDE-specific? How can I fix this?
2) Compiz is unstable and there are a lot of problems: wrong number of virtual desctops, broken cube effect, applets are jumping out of the tray randomly, etc. Is this a general problem with compiz in Kubuntu, or this is specific to xps1330? Is there any guide to fix compiz in Kubuntu?

Thanks!

Semen

---

### Post by bcrom on 2007-12-28
1) On my XPS m1330 I have no problem adjusting the brightness with function keys in gnome.  However, after about five minutes it will readjust to whatever you set it to in power settings.  

2) There is a bug in Compiz on number of virtual desktops.  Sometimes you must select one more or one less than the number of desktops you want.  Play with it until it's right.  

As to your other problems--I've never experienced them in Gnome.  Good luck!

---

### Post by yesint on 2007-12-29
Yet another problem: the wireless card works, but can't connect. The same card with the same driver and the same settings (as far as I can see) connects immediately in Mandriva 2008. Weird. 
I'm switching to Mandriva now because there too many problems in Kubuntu 7.10. I will probably try again with the next version.

---

### Post by jespdj on 2007-12-29
Which wireless card do you have in your M1330? The Intel 3945 as well as the 4965 should work without problems.

Sometimes you have to be patient to get wireless working. A few days ago I was at my dad, who has just bought a WiFi router. My brother was there too with his MacBook. When we booted our computers at the same time, the router refused to connect one of the laptops because it thought it was being attacked with a DOS (denial of service) attack... (found this in the log of the router).

If you have that kind of problem, then switching to another Linux distro is obviously not going to help.

---

### Post by yesint on 2007-12-30
I have Intel card. The problem with wireless is really weird. I type the password and it freezes at "57% determining IP...". After 2-3 minuts it shows password form again. I've tryed 5-6 times and it doesn't work. In Mandriva 2008 it connects perfectly from the first attempt.
What is interesting is that it doesn't work also in Fedora 8, which seems to have the same network applet as Kubuntu. In Mandriva the network applet looks very different, but I don't know if this is the reason. 
The wireless "just works" in Mabdriva but not in Kubuntu. However, the webcam works in Kubuntu but not in Mandriva. Since the webcam is useless without connection anyway  I had to switch to Mandriva...

---

### Post by yesint on 2008-01-03
> **yesint said:**
> I have Intel card. The problem with wireless is really weird. I type the password and it freezes at "57% determining IP...". After 2-3 minuts it shows password form again. I've tryed 5-6 times and it doesn't work. In Mandriva 2008 it connects perfectly from the first attempt.
What is interesting is that it doesn't work also in Fedora 8, which seems to have the same network applet as Kubuntu. In Mandriva the network applet looks very different, but I don't know if this is the reason. 
The wireless "just works" in Mabdriva but not in Kubuntu. However, the webcam works in Kubuntu but not in Mandriva. Since the webcam is useless without connection anyway  I had to switch to Mandriva...

Ok, this is finally fixed by installing wifi-radar. The default network applet doesn't work.

---

### Post by vaxen on 2008-01-05
have you gotten the brightness up+down working on kubuntu?

The virtual desktop is a compiz+kde pager bug. They just don't play well together.

---

### Post by yesint on 2008-01-07
No, the up/down brightness control doesn't work in kubuntu. In ubuntu it is working, but there is a bug which resets it to the BIOS values each ~5 min or so...

---

### Post by GU1330 on 2008-01-18
Hello, I'm a new member of the Forum, and I want to say that is very usefull.

I have installed Kubuntu Gutsy in my new Dell XPS m1330 and I had the same problem that JESIN has with the brightness control (FN up/down arrows) and Compiz. To solve these problems I found the solutions in another place, but I don't remember where:

1. For brightness control:

Adding:

blacklist video 

to the end of /etc/modprobe.d/blacklist and reboot.

That was the solution in my case. I hope this will be helpfull.


2. For the problem installing Compiz, you have to install first the Nvidia drivers:

follow this guide:
[http://doc.ubuntu-fr.org/nvidia](http://doc.ubuntu-fr.org/nvidia)

and  for the installation of Compiz, follow this guide:
[http://doc.ubuntu-fr.org/compiz_fusion](http://doc.ubuntu-fr.org/compiz_fusion)

I know, is not English, but is the best way to install Compiz.

If you need any help, please let me know.

---

