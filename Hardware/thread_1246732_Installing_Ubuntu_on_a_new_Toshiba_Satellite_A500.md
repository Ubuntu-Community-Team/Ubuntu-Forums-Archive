---
title: "Installing Ubuntu on a new Toshiba Satellite A500"
date: 2009-08-22
forum: Hardware
---

### Post by myk02k on 2009-08-22
Long story short, last night my 2 1/2 year, $2200 HP dv9000 faced its last hardware failure--this time coming from its video card.  I could've attempted to swap out the GPU but I've already spent way too much time and money repairing stuff on it already.  One failure always led to another on that thing.

So today I picked up a brand new Toshiba Satellite A500.  My laptop before the disappointing HP dv9000 was a Toshiba and lasted for over 8 years with no problems whatsoever.  The Satellite A500 was just released about last month ago and I am impressed with its looks.  The back-lighting and sleek design definitely gave Toshiba a needed facelift.  As for performance, there is plenty.

So after staring at Windows Vista on my screen for a whole 5 minutes, making sure all of the hardware worked out of the box, I popped in the Jaunty Jackalope.  Norton Antivirus blocked the CD from running and labelled the CD a "security threat".  How ironic.  So I installed the Ubuntu CD at boot and everything seems A-OK so far.  All hardware seems to be responding properly and I am in the midst of getting 3d support out of my ATI Radeon graphics card.  I see that there are no previous posts about this laptop, so here is a start for us Satellite A500 Ubuntu users.  I'll keep my fingers crossed that everything continues as smoothly as it has...

---

### Post by myk02k on 2009-08-22
I just installed the ATI/AMD proprietary FGLRX graphics driver.  I now have 3d support.  :-D

---

### Post by JoshStrobl on 2009-08-22
I installed Ubuntu on my Satellite L305 and everything went fine. I recommend you install Gnome ALSA Mixer and Miro Internet TV. I love Miro because all the shows I've watched I have been able to download.

Something else I recommend is first tackle the video/audio playback for online videos, if such problem occurs.

---

### Post by myk02k on 2009-08-23
The native volume control should do, but I will be checking into what Miro is all about.  Thanks.

So far the features that I figure will be of concern for A500 users to get working is this advertised eco-friendly software that is offered in Windows.  I have no idea what purpose it serves or what it does, all I know is that the multimedia button is on permanent off mode in Ubuntu.  

Second is the multitouch mouse pad, where you could zoom in with finger motions in Windows.  I still need to find a Linux-equivalent piece of software for that.  

Third is the use of LightFlash, which from what it sounds like I could use the software with no problems in WINE.  Is there really nobody else out there with the Satellite A500 running Ubuntu?

---

### Post by myk02k on 2009-08-28
I have experienced a few system hangs, so I figured I'd post the last system hang message from /var/log/messages and see if anyone could point me in the right direction to get this fixed.

Aug 28 08:16:38 mike-laptop kernel: [  104.224704] npviewer.bin[4071]: segfault at f5573030 ip 00000000f78c69e0 sp 00000000ffd94184 error 4 in libpthread-2.9.so[f78bf000+15000]

---

### Post by aix on 2009-09-07
hi!!  First, sorry for my english, I have a new Toshiba Satellite A500 and i want installing ubuntu but when run ubuntu whith liveCD (32 bits) the sound don't work.For this reason I am afraid to install ubuntu.  Other question, what installing ubuntu 32 bits or is better 64 bits?  thanks   > **myk02k said:**
> The native volume control should do, but I will be checking into what Miro is all about.  Thanks.

So far the features that I figure will be of concern for A500 users to get working is this advertised eco-friendly software that is offered in Windows.  I have no idea what purpose it serves or what it does, all I know is that the multimedia button is on permanent off mode in Ubuntu.  

Second is the multitouch mouse pad, where you could zoom in with finger motions in Windows.  I still need to find a Linux-equivalent piece of software for that.  

Third is the use of LightFlash, which from what it sounds like I could use the software with no problems in WINE.  Is there really nobody else out there with the Satellite A500 running Ubuntu?

---

### Post by myk02k on 2009-09-08
> **aix said:**
> hi!!  First, sorry for my english, I have a new Toshiba Satellite A500 and i want installing ubuntu but when run ubuntu whith liveCD (32 bits) the sound don't work.For this reason I am afraid to install ubuntu.  Other question, what installing ubuntu 32 bits or is better 64 bits?  thanks


What is the exact Satellite A500 model that you have?  I have the A505-S6965 model and have no issues with sound using Ubuntu Jaunty 64 bit installed to the hard drive.  You are best installing a 64 bit operating system if you have more than 3 GB RAM.  32 bit operating systems cannot use anymore than about 3 GB RAM.

---

### Post by myk02k on 2009-09-08
I would also like to know if there is anybody out there who has experimented with the different ATI Radeon drivers that are available for the ATI Mobility Radeon HD 4570 video card.  The default open source driver that Ubuntu uses does not support 3d, yet the proprietary fglrx driver available in the "Restricted Drivers" seems to be very buggy (horrible video playback, black flickering in firefox, compiz segfaults, random restarts, etc).  What are my solutions?  

Again, this video card is used in the Toshiba Satellite A505-S6965 model.

---

### Post by typiCAL_ on 2009-09-13
hi myk02k,

I was recently able to get a hold of a copy of linuxmint 7, which i understand is built on jaunty, so i'm testing it on my A500 ST5602, which also uses the Radeon HD 4570.  Unfortunately on AMD/ATI's website there's no luck of finding a driver specifically for it.

I live on a mountain in central america, and my internet's a 3G usb modem (in other words, crap), so i won't be able to download and test as fast as I'd like to, but I'll definitely let you know if I can figure something out.

---

### Post by aix on 2009-09-14
Hi!! first thanks very much. Well i have A500 140. Finally, I have installed ubuntu 9.04 64 bits... wifi OK, sound OK,  but now Windows Vista don't run. In the grub i can choose start windows vista, but if i choose this option run ubuntu, and if choose ubuntu run ubuntu also.   I only resize windows vista partition  original disk:  1.5 GB oculted partition the rest GB  Windos vista (ntfs) 230 GB DAta (ntfs)   final disk:  1.5 GB oculted partition 50 GB  Windos vista (ntfs) 2 GB  swap 50 GB / (ext4) the rest  /home (ext4) 230 GB DAta (ntfs)  The data of windows vista partition is OK, because only resize this partition, and i can see all folders,  "program files" etc..     the file of grub menu.lst: title		Windows Vista (loader) root		(hda0,1) savedefault makeactive chainloader	+1   uff.. i don't know how repair this :(   sorry for my english and thanks  > **myk02k said:**
> What is the exact Satellite A500 model that you have?  I have the A505-S6965 model and have no issues with sound using Ubuntu Jaunty 64 bit installed to the hard drive.  You are best installing a 64 bit operating system if you have more than 3 GB RAM.  32 bit operating systems cannot use anymore than about 3 GB RAM.

---

### Post by aix on 2009-09-15
Problem solved. Thank you very much everybody. I think the MBR failed. I've solved this  whith this rescue tool: "Microsoft Diagnostics and Recovery Toolset 6.0.0".  Now run fine the two systems either from the grub,  ubuntu 9.04 and windows vista.  But Bluethooth do not work in Ubuntu :(   I think is for this bug:  [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982)  But i don't know.  Thanks for all.

---

### Post by typiCAL_ on 2009-09-15
After a few headaches trying to get it to work, I was able to install the latest ATI/AMD driver (ati-driver-installer-9-9-x86.x86_64.run) from their website and so far, 3D is working smoothly, I get about 1600 fps with glxgears.  I also don't seem to be having any problems with video playback or anything else really it seems to be very smooth overall.

I have however noticed the occasional system hang which seems to be happenning after logging out and restarting X.

Last line in /var/log/messages after logging out:
```
Sep 15 10:51:10 mint kernel: [  109.500064] Clocksource tsc unstable (delta = -413063673 ns)
```I'm curious if anyone has had the same luck with the proprietary closed source fglrx drivers from ATI/AMD?

---

### Post by aix on 2009-09-15
Hi!! problem solved, bluethooth work fine on toshiba satellite A500 141.

In this link i find the solution:
[http://lamaquinadiferencial.wordpress.com/2009/06/10/no-funciona-el-bluetooth-en-toshiba-satellite-en-debianubuntu/](http://lamaquinadiferencial.wordpress.com/2009/06/10/no-funciona-el-bluetooth-en-toshiba-satellite-en-debianubuntu/)



> **aix said:**
> Problem solved. Thank you very much everybody. I think the MBR failed. I've solved this  whith this rescue tool: "Microsoft Diagnostics and Recovery Toolset 6.0.0".  Now run fine the two systems either from the grub,  ubuntu 9.04 and windows vista.  But Bluethooth do not work in Ubuntu :(   I think is for this bug:  [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982)  But i don't know.  Thanks for all.

---

### Post by typiCAL_ on 2009-09-16
so just to post a little update, i have the latest catalyst 9.9 driver from ATI/AMD installed and everything is working just fine for the most part.  desktop compositing works fine, i run doom3 windowed mode at about 60fps on ultra-high.

the only issues i've found so far are the following:
  
[LIST]
[*]HDMI output (audio & video) doesn't seem to be working at all, setting any changes to the displays in the CCC ends in a segmentation fault
[*]when running Steam in wine, none of my source games (e.g. HL2, CS:S, DOD:S, etc) will work when they get to rendering actual 3D, which I believe to be an ATI/FGLRX problem, not wine. ([thread here]("http://ubuntuforums.org/showthread.php?p=7959072"))
[*]The fingerprint scanner is not supported by neither fprint or thinkfinger
```

lsusb | grep AuthenTec
Bus 004 Device 002: ID 08ff:2550 AuthenTec, Inc.
```
[*]so far i have been unable to use any of the toshiba modules to configure any of the toshiba settings (e.g. hotkeys, fan speed, etc)
[/LIST]
again this is on an A500-ST5602 with a Radeon HD 4570

---

### Post by myk02k on 2009-09-16
> **aix said:**
> Problem solved. Thank you very much everybody. I think the MBR failed. I've solved this  whith this rescue tool: "Microsoft Diagnostics and Recovery Toolset 6.0.0".  Now run fine the two systems either from the grub,  ubuntu 9.04 and windows vista.  But Bluethooth do not work in Ubuntu :(   I think is for this bug:  [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982)  But i don't know.  Thanks for all.

SuperGRUB is an easy bootable CD that will repair Windows MBR and GRUB for issues like this.  It's how I repaired my Windows MBR when I switched over to GRUB.  Burn an image CD and hold onto it because you may need it again if you ever need to reinstall or run into GRUB failure.

I don't think we have Bluetooth, do we?

---

### Post by myk02k on 2009-09-16
> **typiCAL_ said:**
> so just to post a little update, i have the latest catalyst 9.9 driver from ATI/AMD installed and everything is working just fine for the most part.  desktop compositing works fine, i run doom3 windowed mode at about 60fps on ultra-high.

the only issues i've found so far are the following:
  
[LIST]
[*]HDMI output (audio & video) doesn't seem to be working at all, setting any changes to the displays in the CCC ends in a segmentation fault
[*]when running Steam in wine, none of my source games (e.g. HL2, CS:S, DOD:S, etc) will work when they get to rendering actual 3D, which I believe to be an ATI/FGLRX problem, not wine. ([thread here]("http://ubuntuforums.org/showthread.php?p=7959072"))
[*]The fingerprint scanner is not supported by neither fprint or thinkfinger
```

lsusb | grep AuthenTec
Bus 004 Device 002: ID 08ff:2550 AuthenTec, Inc.
```
[*]so far i have been unable to use any of the toshiba modules to configure any of the toshiba settings (e.g. hotkeys, fan speed, etc)
[/LIST]
again this is on an A500-ST5602 with a Radeon HD 4570

The Radeon HD 4570 is not being so friendly to me with the FGLRX drivers.  At times, the system fails to halt because a program refuses to halt (does not happen with VESA driver).  I am also getting black flickering in Firefox, seem to have some errors with flash playback, and cannot seem to iron out issues using advanced graphics while playing video.

---

### Post by typiCAL_ on 2009-09-16
> **myk02k said:**
> The Radeon HD 4570 is not being so friendly to me with the FGLRX drivers.  At times, the system fails to halt because a program refuses to halt (does not happen with VESA driver).  I am also getting black flickering in Firefox, seem to have some errors with flash playback, and cannot seem to iron out issues using advanced graphics while playing video.

Are you using the fglrx drivers from the "Hardware Drivers" utility, or did you download the latest catalyst from the ATI/AMD website?  When I tried the "Restricted Drivers" I couldn't even get X to start.  Actually my machine would halt and crash, and I would have to do a cold reboot every time until I reverted back to the open source drives installed by jaunty, which of course didn't have 3d support and were terribly slow.

If you haven't tried so, I'd recommend downloading the latest drivers from the ATI/AMD website.  They are a pain to setup (or at least were for me), but they seem to do the job well for the most part, unfortunately Steam's source games don't like them :|

---

### Post by typiCAL_ on 2009-09-16
> **myk02k said:**
> I don't think we have Bluetooth, do we?

From my understanding, none of the pre-configured A500 models come with Bluetooth.  So if you have Bluetooth you should know because you put it there ;)

---

### Post by vhenry on 2009-10-01
I had the same failure on an HP dv9330us and just received my Toshiba Satellite A500-ST5601.

I'd like to take the leap and install 64bit Jaunty. My apps are mainly Bluefish, Netbeans, Gimp, and OpenOffice. Any known issues with these? Also, are the flash issues I've read about resolved?

The fingerprint reader is a nice feature, is there any software that I can use under Ubuntu to manage it?

---

### Post by typiCAL_ on 2009-10-01
> **vhenry said:**
> I had the same failure on an HP dv9330us and just received my Toshiba Satellite A500-ST5601.

I'd like to take the leap and install 64bit Jaunty. My apps are mainly Bluefish, Netbeans, Gimp, and OpenOffice. Any known issues with these? Also, are the flash issues I've read about resolved?

The fingerprint reader is a nice feature, is there any software that I can use under Ubuntu to manage it?


From the model number I'm assuming you ordered this from toshibadirect.com right?  If you haven't customized it at all (e.g. gpu upgrade), you should expect things to go VERY smoothly on your laptop.  You won't suffer from the ATI problem obviously as yours is Intel-based.

All-in-all, I'm found the 64-bit build to run extremely well.  My only real issues have related to ATI problems.  I haven't noticed any flash problems at all on my end at least.  No problems with Bluefish, anything Eclipse based, Gimp or OO.  Runs like a beast!!

If you have the exact same fingerprint reader that I do (judging by your model I think you do), then it wont work unfortunately.  I've tried all the different hacks and mods out there but no dice :(

Although not all Satellite models use the same fp hardware though, so you may get yours working.

---

### Post by vhenry on 2009-10-01
Yep, ordered from Toshibadirect.com, no config changes. Bummed about the fingerprint reader, but maybe that will change. Someone's bound to tinker around and get it working in time. I'm going to boot with LiveCD and see if we have the same hardware.

Thanks

---

### Post by typiCAL_ on 2009-10-02
Well back to the topic of Steam games, I posted a few days back that my ATI card was causing the problems with games crashing.  It seems that upgrading wine to version 1.1.30 allows the games to work fine.

Although the ATI driver is still crap unfortunately.. the system freezes whenever the X server is reset (e.g. control+alt+backspace, or logout/in), blackspots randomly in firefox, and overall performance isn't near what it should be :\

---

### Post by almikul on 2009-10-02
Folks,

Has anyone of you had a heating problem with your A500s? I bought an M505, and everything works fine except for fans. They don't turn on in Jaunty and neither in Karmic beta. The temp in Ubuntu rises to 60+ degrees while in Vista it is kept under 40. Sorry for hijacking this thread, but it seems nobody else has Satellite M505.

Thanks

---

### Post by myk02k on 2009-10-02
> **typiCAL_ said:**
> Although the ATI driver is still crap unfortunately.. the system freezes whenever the X server is reset (e.g. control+alt+backspace, or logout/in), blackspots randomly in firefox, and overall performance isn't near what it should be :\

Firefox flickers black when scrolling at times for me.  It also has issues coming out of hibernation from time to time.

---

### Post by typiCAL_ on 2009-10-05
> **myk02k said:**
> Firefox flickers black when scrolling at times for me.  It also has issues coming out of hibernation from time to time.

sounds pretty similar to the way mine acts, so are you using the driver from ATI/AMD's website?  that's the one i have, and while things work, it really lacks stability needs some serious improvement, and i hate the fact that i still have vista installed but unfortunately i still need it :|

---

### Post by myk02k on 2009-10-06
> **typiCAL_ said:**
> sounds pretty similar to the way mine acts, so are you using the driver from ATI/AMD's website?  that's the one i have, and while things work, it really lacks stability needs some serious improvement, and i hate the fact that i still have vista installed but unfortunately i still need it :|

The open-source drivers work fine, but no 3d acceleration.  I turn off the advanced graphics if I'm working on something important and don't need the stress of a system lock.  That's enough stability to delete Vista for me.

I am using the driver from ATI.  ATI really needs to start resolving these issues because my HP laptop's NVIDIA card worked flawless before it fried and there's no doubt in my head that there are serious issues with this one layer of software.  I went from a shoddy laptop to an unstable video driver.  :(

---

### Post by typiCAL_ on 2009-10-07
> **myk02k said:**
> my HP laptop's NVIDIA card worked flawless before it fried and there's no doubt in my head that there are serious issues with this one layer of software.  I went from a shoddy laptop to an unstable video driver.  :(

yeah nVIDIA has always done a pretty good job as far as support for linux.. i have a 7300 GS in my desktop that does a better job than my HD 4570 right now.. and i'm not joking.. hopefully ATI wakes up soon enough :|

---

### Post by myk02k on 2009-10-07
I also wanted to add to the list of issues that I believe is caused by fglrx is a 2-3 second lag in maximizing-unmaximizing.  If you hit the "show desktop button" once to bring front all windows and again to maximize, you will see what i mean.  There is about a 2-3 second delay before the windows are brought back.

I have also re-enabled CTRL-ALT-BACKSPACE to restart X.  The computer refuses to restart X and hangs 100% of the time.

Are there alternative drivers for our cards that support 3D/compiz?

---

### Post by typiCAL_ on 2009-10-09
> **myk02k said:**
> I also wanted to add to the list of issues that I believe is caused by fglrx is a 2-3 second lag in maximizing-unmaximizing.  If you hit the "show desktop button" once to bring front all windows and again to maximize, you will see what i mean.  There is about a 2-3 second delay before the windows are brought back.

I have also re-enabled CTRL-ALT-BACKSPACE to restart X.  The computer refuses to restart X and hangs 100% of the time.

Are there alternative drivers for our cards that support 3D/compiz?

In my setup my "show desktop" has the windows fly off to the corner which i noticed was smoother so I don't notice the delay, but before I noticed that as well.

And yes there is an issue restarting X for some reason it refuses to reinitiate the fglrx driver. Issuing CTRL-ALT-F1,etc to switch VT's and returning to the desktop via CTRL-ALT-F7 has no problem at all, but actually stopping X and restarting it always fails.

I've tried forcing the 'radeon' and 'radeonhd' driver.  No dice with either, they both completely fail to load.

---

### Post by vhenry on 2009-10-10
Anybody having any problems with suspend and/or hibernate on the A500?

(my hp was in suspend mode when the screen went black and died, so I have irrational, yet lingering fears over using) :confused:

---

### Post by feed_sparky on 2009-10-12
I have a Toshiba a505-s6970 and I am using the 9.9 driver from ATI ( I also have the HD 4570) and it runs perfect, no FF flickering or anything like that. I can play steam games perfectly.

---

### Post by myk02k on 2009-10-13
> **feed_sparky said:**
> I have a Toshiba a505-s6970 and I am using the 9.9 driver from ATI ( I also have the HD 4570) and it runs perfect, no FF flickering or anything like that. I can play steam games perfectly.

Are there any changes you have made to Xorg or any other settings?

What distro of Ubuntu are you using?

Where did you download your driver?

Do you have compiz enabled?

---

### Post by feed_sparky on 2009-10-13
> **myk02k said:**
> Are there any changes you have made to Xorg or any other settings?

What distro of Ubuntu are you using?

Where did you download your driver?

Do you have compiz enabled?

I downloaded the 9.9 driver from ATI's website, Installed using automatic settings, restarted, ran aticonfig, and that was it. No modifications, I gots wobbly windows and everything. I will admit games do run better with no visual effects (once in a while Urban Terror would act funny with "extra" visual effects). I have been running 9.04 64 bit for about 2 weeks now with no problems, 9.10 won't play nice with ATI's 9.9 drivers.

---

### Post by tyk on 2009-10-14
> **feed_sparky said:**
> I downloaded the 9.9 driver from ATI's website, Installed using automatic settings, restarted, ran aticonfig, and that was it. No modifications, I gots wobbly windows and everything. I will admit games do run better with no visual effects (once in a while Urban Terror would act funny with "extra" visual effects). I have been running 9.04 64 bit for about 2 weeks now with no problems, 9.10 won't play nice with ATI's 9.9 drivers.

You lucky bugger :)

but... you sure you don't have an onboard hd3200 which got picked up by the fglrx. It happened to me (on an asus though) and i was prematurely gleeful. you tried glxinfo or lspci? don't wanna spoil your fun but i gotta know.. getting frustrated with having all the videocard (the hd4570) and not being able to use it...
My best.

---

### Post by feed_sparky on 2009-10-14
glxinfo reports ```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 2.1.8918

```

lspci reports ```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

```

---

### Post by myk02k on 2009-10-14
> **feed_sparky said:**
> glxinfo reports ```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 2.1.8918

```

lspci reports ```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

```

Thanks.  Once I give the fglrx drivers a shot again I'll see if mine matches.  I've been relying on the Jaunty default drivers lately since they appear more stable.

A few more odd system hangs here.  The last one froze the screen to where I was unable to switch to a console.  The caps lock button was also blinking on and off.  I was forced to restart but got lazy and didn't find why it crashed from /var/log/messages.  I'll see if there's a way to retrieve my errors out of all the compressed files, maybe by upgrading "deskbar-applet" who knows.  

I also noticed that the num key was inoperable. I found a fix [here]("http://nancib.wordpress.com/2008/03/17/fixing-the-borked-numeric-keypad-in-ubuntu-hardy/").  Could someone please confirm this exists with someone else out there?  That may require a bug report.

---

### Post by tyk on 2009-10-15
> **feed_sparky said:**
> glxinfo reports ```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 2.1.8918

```

lspci reports ```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

```

Thanks. It seems like you got it right. And just by standard procedure.. Wow. I'm gonna try this one more time.
Cheers.

btw what's your kernel? thanks again.

---

### Post by myk02k on 2009-10-15
Computer shutdown on me early this morning.  Log from /var/log/messages attached.

```
Oct 15 04:47:49 mike-laptop kernel: [25842.758843] ACPI: Critical trip point
Oct 15 04:47:50 mike-laptop kernel: [25842.890416] ACPI: Critical trip point
Oct 15 04:47:55 mike-laptop kernel: [25847.844792] ACPI: Transitioning device [FAN] to D3
Oct 15 04:47:55 mike-laptop kernel: [25847.844798] ACPI: Unable to turn cooling device [ffff88013f815720] 'off'
Oct 15 04:47:55 mike-laptop kernel: [25847.981029] ACPI: Transitioning device [FAN] to D3
Oct 15 04:47:55 mike-laptop kernel: [25847.981033] ACPI: Unable to turn cooling device [ffff88013f815720] 'off'
Oct 15 04:47:55 mike-laptop bonobo-activation-server (mike-22257): could not associate with desktop session: Failed to connect to socket /tmp/dbus-iE7CQl5PkF: Connection refused
Oct 15 04:48:02 mike-laptop exiting on signal 15
```

---

### Post by myk02k on 2009-10-15
> **feed_sparky said:**
> glxinfo reports ```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 2.1.8918

```

lspci reports ```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

```

my glxinfo matches

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 1.4 (2.1.8918)

```

& lspci

```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

```

To clarify things I am running the newest Catalyst driver from their website.  I am running kernel 2.6.28-15-generic


I'm currently watching the newest South Park episode with Flash and npviewer.bin is, according to top, using 32% CPU.  My RAM monitor applet is reporting 50% in use by programs but the RAM #'s don't add up on top.  Npviewer.bin acts up only with the fglrx drivers.

---

### Post by feed_sparky on 2009-10-15
I am running kernel 2.6.28-15 as well. My Num Lock works just fine, the only real problem I have is my brightness keys seem to stop working whenever they feel like it. I haven't had a system crash, yet... blinking caps lock is usually a kernel panic I believe.

---

### Post by feed_sparky on 2009-10-15
> **myk02k said:**
> 

I'm currently watching the newest South Park episode with Flash and npviewer.bin is, according to top, using 32% CPU.  My RAM monitor applet is reporting 50% in use by programs but the RAM #'s don't add up on top.  Npviewer.bin acts up only with the fglrx drivers.

I just watched the same episode in flash and I had 18-22% cpu and around 11% Ram usage in system monitor (npviewer is 2.7 of that).

---

### Post by myk02k on 2009-10-16
Well my last post inadvertently pointed out another issue; my fan never turns off.  Google has no answers, although I see people with the Toshiba M300s are having the same issues.

---

### Post by tyk on 2009-10-16
> **myk02k said:**
> my glxinfo matches

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 1.4 (2.1.8918)

```

& lspci

```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

```

To clarify things I am running the newest Catalyst driver from their website.  I am running kernel 2.6.28-15-generic


I'm currently watching the newest South Park episode with Flash and npviewer.bin is, according to top, using 32% CPU.  My RAM monitor applet is reporting 50% in use by programs but the RAM #'s don't add up on top.  Npviewer.bin acts up only with the fglrx drivers.

Thanks myk02k and feed_sparky. I am running 2.6.28-11 right now. Maybe the upgrade will help. Will keep posted.
Cheers.

---

### Post by feed_sparky on 2009-10-16
> **myk02k said:**
> Well my last post inadvertently pointed out another issue; my fan never turns off.  Google has no answers, although I see people with the Toshiba M300s are having the same issues.

Hmmm, my fan behaves the way it should... I can't believe there is that much hardware difference between the 6965 and the 6970... Toshiba had a BIOS update for the a505/500 series. My BIOS version is 1.60

---

### Post by feed_sparky on 2009-10-16
> **tyk said:**
> Thanks myk02k and feed_sparky. I am running 2.6.28-11 right now. Maybe the upgrade will help. Will keep posted.
Cheers.

If yo do the upgrade you will have to reinstall the ATI driver again, I had to anyways, maybe it will be different for you. 

I usually upgrade all the way before I try any installs.

---

### Post by gbrethen on 2009-10-17
does anyone have 3d and compiz working in ubuntu 9.10?  I have an A505-6965 with the ati hd4570.  Everything works fine in 9.04.  I am using the catalyst 9.9 as well.  Just wondering if its going to work in the 9.10 ubuntu?

---

### Post by myk02k on 2009-10-17
> **gbrethen said:**
> does anyone have 3d and compiz working in ubuntu 9.10?  I have an A505-6965 with the ati hd4570.  Everything works fine in 9.04.  I am using the catalyst 9.9 as well.  Just wondering if its going to work in the 9.10 ubuntu?

I'm waiting upon it's official release.  Hopefully Karmic will come with some fixes.

---

### Post by feed_sparky on 2009-10-17
> **gbrethen said:**
> does anyone have 3d and compiz working in ubuntu 9.10?  I have an A505-6965 with the ati hd4570.  Everything works fine in 9.04.  I am using the catalyst 9.9 as well.  Just wondering if its going to work in the 9.10 ubuntu?

I tried 9.10 and kept getting the garbled screen after restarting x. I'll try again after the official release.

---

### Post by myk02k on 2009-10-18
Anyone get multitouch support setup for their mouse?

For any of you who may need to know [how to get Labelflash working]("http://howtopenguin.blogspot.com/2008/05/how-to-install-lightscribe-software-on.html").  You should be able to fix the broken link by replacing it with the new version #, "lightscribe-1.18.8.1"

---

### Post by tyk on 2009-10-21
I finally got the hd4570 working on my lappy. At least on my machine the problem was that it was a hybrid card and I needed to switch to the 4570 permanently. made a thread about it [_here_]("http://ubuntuforums.org/showthread.php?t=1295105").
Cheers.

---

### Post by myk02k on 2009-10-21
> **aix said:**
> Hi!! first thanks very much. Well i have A500 140. Finally, I have installed ubuntu 9.04 64 bits... wifi OK, sound OK,  but now Windows Vista don't run. In the grub i can choose start windows vista, but if i choose this option run ubuntu, and if choose ubuntu run ubuntu also.   I only resize windows vista partition  original disk:  1.5 GB oculted partition the rest GB  Windos vista (ntfs) 230 GB DAta (ntfs)   final disk:  1.5 GB oculted partition 50 GB  Windos vista (ntfs) 2 GB  swap 50 GB / (ext4) the rest  /home (ext4) 230 GB DAta (ntfs)  The data of windows vista partition is OK, because only resize this partition, and i can see all folders,  "program files" etc..     the file of grub menu.lst: title		Windows Vista (loader) root		(hda0,1) savedefault makeactive chainloader	+1   uff.. i don't know how repair this :(   sorry for my english and thanks

Let me rephrase your problem so we can understand clearly.  You have your computer dual-booting Vista and Ubuntu using GRUB as your boot-loader.  Ubuntu runs fine, but Windows Vista will not load.  

A common error is that Windows fails to load the Master Boot Record after GRUB is installed.  Is this your error?  Please specify what it is that prevents Vista from working.

---

### Post by feed_sparky on 2009-10-24
Anyone tried the new 9.10 driver yet?

---

### Post by myk02k on 2009-10-25
I'm tempted, but scared.  Maybe after I get some deadlined paperwork complete for classes.

---

### Post by myk02k on 2009-10-25
On another thought, we only have 4 days until Karmic Koala is released.  I figure I'll upgrade to the newest distro first, make sure everything works fine, then upgrade the ATI drivers.  HOPEFULLY everything goes smoothly.

---

### Post by myk02k on 2009-10-25
I just had yet another unexpected shut-down.  This time, I was unfortunate enough to have litigation paperwork that took me about an hour to compile sitting in GEdit.  All is lost.  Can someone please tell me how I can figure out what is triggering these unusual shut-downs?

---

### Post by feed_sparky on 2009-10-25
The new ATI 9.10 drivers play nice with Ubuntu 9.10rc, just finished installing and so far so good. I will report back if I run into any problems.

---

### Post by myk02k on 2009-10-25
> **feed_sparky said:**
> The new ATI 9.10 drivers play nice with Ubuntu 9.10rc, just finished installing and so far so good. I will report back if I run into any problems.

CTRL-ALT-backspace should change all that (unless you haven't re-enabled this command)

---

### Post by feed_sparky on 2009-10-25
> **myk02k said:**
> CTRL-ALT-backspace should change all that (unless you haven't re-enabled this command)

I restarted X and everything is still fine, I installed it without X from the command line. I get about 2000fps with glxgears.

Are you not having the same results?

---

### Post by myk02k on 2009-10-25
Back again.  My computer screen just bugged out for like the dozenth time in this fashion.  Attached is a screenshot.  Note:  the little black boxes were added to censure out personal documents that were opened at the time of the screenshot.

***A NOTE TO ALL A500/A505 INTERESTED BUYERS***
I would like to recommend to any Ubuntu users interested in buying the A500/A505 to go for the latest NVIDIA card Toshiba is offering for our notebooks.  If I were to do it all over again, I wouldn't hesitate purchasing the A505 with the NVIDIA cards they just began offering.  NVIDIA has a MUCH higher quality driver and I would not be surprised if you do not face ANY of these problems that we are describing on this thread.  I ran my NVIDIA GPU flawlessly on my previous Linux notebook.  I cannot comment on the Intel chipset; however, from my knowledge it's always better to go dedicated GPU memory for increased performance at the cost of battery life.  Intel's integrated memory GPU has reviews stating that it fails to run 3d games that are almost 2 years old now.  Unless you require 4+ hours of battery life, it would be a shame if you couldn't experience the beauty of compiz-fusion in Linux in all its glory.

---

### Post by feed_sparky on 2009-10-25
> **myk02k said:**
> Back again.  My computer screen just bugged out for like the dozenth time in this fashion.  Attached is a screenshot.  Note:  the little black boxes were added to censure out personal documents that were opened at the time of the screenshot.

***A NOTE TO ALL A500/A505 INTERESTED BUYERS***
I would like to recommend to any Ubuntu users interested in buying the A500/A505 to go for the latest NVIDIA card Toshiba is offering for our notebooks.  If I were to do it all over again, I wouldn't hesitate purchasing the A505 with the NVIDIA cards they just began offering.  NVIDIA has a MUCH higher quality driver and I would not be surprised if you do not face ANY of these problems that we are describing on this thread.  I ran my NVIDIA GPU flawlessly on my previous Linux notebook.  I cannot comment on the Intel chipset; however, from my knowledge it's always better to go dedicated GPU memory for increased performance at the cost of battery life.  Intel's integrated memory GPU has reviews stating that it fails to run 3d games that are almost 2 years old now.  Unless you require 4+ hours of battery life, it would be a shame if you couldn't experience the beauty of compiz-fusion in Linux in all its glory.

Are you using a clean install? I am not having any of the problems you are and we almost have the same hardware...

---

### Post by myk02k on 2009-10-25
> **feed_sparky said:**
> Are you using a clean install? I am not having any of the problems you are and we almost have the same hardware...

I haven't tried Karmic & Catalyst 9.10 yet, so we don't match configuration at the moment.  When we do, I'll be sure to do a clean install.

---

### Post by myk02k on 2009-10-28
Regarding my statement about my recommendations, I recently saw a post that the Intel chipsets run much better with the Karmic Koala 9.10 upgrade.  Sorry, no idea what serial numbers they all are.

---

### Post by vhenry on 2009-11-02
Anyone followed the kramic upgrade option in synaptic? Having just gotten my laptop (a500-st5601) functioning the way I want, I'm hesitant to screw it all up. I'd rather not do a clean install if I don't have to.

The only difference I think in hardware from other folks on this thread, is that I have Intel graphics.

---

### Post by phillw on 2009-11-08
> **vhenry said:**
> Anyone followed the kramic upgrade option in synaptic? Having just gotten my laptop (a500-st5601) functioning the way I want, I'm hesitant to screw it all up. I'd rather not do a clean install if I don't have to.

The only difference I think in hardware from other folks on this thread, is that I have Intel graphics.


There is no requirement to upgrade, if your system works okay with 9.04, do not break something. IMHO, I'd follow the track in my blog about 9.10 -- Basically, try the LiveCD version and make sure you don't have 'issues'. If you do have problems with 9.10 and your system, as the tosh laptops have different bits inside them, dependent if the there is a 'y' in the day. Do, please, ensure 9.10 is happy with your system.

Phill.

---

### Post by myk02k on 2009-11-08
Just did a clean install for Ubuntu 9.10 and the newest ATI Catalyst driver.  So far so good.  :p

---

### Post by vhenry on 2009-11-09
Tried Karmic with Live CD a few times, everything works, usb, flash, video,etc. Not one hiccup. Only prob. is, if I follow the upgrade path, I don't get grub2 or ext 4 - and I'm not sure if I need either. At some point, will support for ext3 and legacy grub go away?

On another note, having moved to Ubuntu earlier this year, didn't know it was better to have home on a separate partition. Do you think its better that I repartition (currently have Vista & Ubuntu partitions)? If so, is there a way to do this painlessly and how do I point the OS to the new home partition after I set it up?

---

### Post by myk02k on 2009-11-10
> **vhenry said:**
> Tried Karmic with Live CD a few times, everything works, usb, flash, video,etc. Not one hiccup. Only prob. is, if I follow the upgrade path, I don't get grub2 or ext 4 - and I'm not sure if I need either. At some point, will support for ext3 and legacy grub go away?

I just did a clean install and recommend you should as well.  I'm almost sure you can upgrade to ext4 with any live CD using gparted, but I'm not sure what you could do to upgrade grub.  Ext4 seems to have slightly better performance than ext3.  Start-up also seems noticeably faster from Jaunty to Karmic.  

> **vhenry said:**
> On another note, having moved to Ubuntu earlier this year, didn't know it was better to have home on a separate partition. Do you think its better that I repartition (currently have Vista & Ubuntu partitions)? If so, is there a way to do this painlessly and how do I point the OS to the new home partition after I set it up?

A quick Google search came up with this [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome").  Use at your own risk.  I couldn't find an answer whether there are gains to a separate home partition and if you find out, please let me know.

---

### Post by Vaphell on 2009-11-10
advantages of separate home are clear - when you want to reinstall system because it fubared hard or when you want to do an upgrade to a newer version you don't need to back anything up. You just assign your home partition as /home during the installation, uncheck formatting and all your personal stuff and configurations are in place already. You won't need to tweak anything when the installation is complete.
Of course there can be some incompatibilities  (different versions of software can have different configs) but it's nothing deleting config dir to get fresh one won't solve.

---

### Post by myk02k on 2009-11-10
2 new issues

1 - Dim control and lcd power management dim no longer function
2 - Flash issues with controlling buttons exist  [https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all]("https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all")

---

### Post by myk02k on 2009-11-10
The dim issue must have been resolved with my most recent update because it now works.  The Flash issue has been fixed with the work-around posted in the bug report.  All is good.  The errors I witnessed in Jaunty seemed to have all disappeared thus far.

> **myk02k said:**
> 2 new issues

1 - Dim control and lcd power management dim no longer function
2 - Flash issues with controlling buttons exist  [https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all]("https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all")

---

### Post by SimonErich on 2010-01-16
Hello guys

I also bought the A500 and I am still trying to get multitouch to work on Ubuntu.
synclient recognizes only 1 finger.

Has anyone found a solution for "real" multitouch support for the A500 in Ubuntu ?

---

### Post by myk02k on 2010-01-16
I personally have not bothered to hunt for packages because last I read, Lucid Lynx will support multi-touch pads out of the box (releasing in June I believe).

> **SimonErich said:**
> Hello guys

I also bought the A500 and I am still trying to get multitouch to work on Ubuntu.
synclient recognizes only 1 finger.

Has anyone found a solution for "real" multitouch support for the A500 in Ubuntu ?

---

### Post by myk02k on 2010-01-28
[http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/](http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/)

Multitouch support

---

### Post by myk02k on 2010-01-28
My function buttons no longer work after returning from a suspended session.  For instance, I cannot dim my screen after returning from suspension.  Is anyone else experiencing this problem?

---

### Post by SimonErich on 2010-01-28
Hello @myk02k

i already found similar instructions, but I don't want to emulate multitouch support, when I have a multitouch capable touchpad.
I want to use real mouse gestures, 2, 3 finger actions, ...

---

### Post by c00lwaterz on 2010-04-03
do anyone of you (toshiba user) experience overheat or high temperature while using linux?

I use ubuntu 9.1, ubuntu 10.04 beta, linux mint 8, freebsd 8, eAR OS, Debian 5.04, and other linux distros.

All of these Linux (32bit) gave me same issues (high temp). I don't know how to fix. I have searched so much in google and forums. But no luck. I am afraid it might burn. My toshiba is new. I bought it couple of months ago.after buying, I tried ubuntu but it has high temp. I tried many time (fresh install). I try also no updating after installation. Until now with high temp issue.

im using toshiba m900 core 2 duo 2.2ghz, 3gb memory.

Any help is appreciated in advance.

Thanks

---

### Post by SimonErich on 2010-04-06
Hi @c00lwaterz

I'm using a Toshiba A500 and I'm not experiencing any problems with temp. I use Ubuntu 9.04.

---

### Post by Forastan on 2010-04-06
I tried to test 9.10 on a new Toshiba Satellite E205, and after the language choice, all I get is a black screen - Failure.   I haven't tried any other versions of Ubuntu on this machine - it is worth the trouble?

Disk works on older laptops.  Satellite works fine with Windows 7.  It has an Intel i5 core.  I have no clues from the load as to why it quits in the middle.:confused:

---

### Post by c00lwaterz on 2010-04-07
i don't have any idea why my laptop produce more heat than other toshiba owners (using linux). My machine is m900 and I don't know if other people use same model as mine get high temperature? if not then it's only my laptop has problem.:(

---

### Post by myk02k on 2010-05-02
I just did a clean install of Lucid Lynx.  It works great, and no longer requires the ATI fglrx drivers in order to use compiz!

---

### Post by typiCAL_ on 2010-05-06
> **myk02k said:**
> I just did a clean install of Lucid Lynx.  It works great, and no longer requires the ATI fglrx drivers in order to use compiz!

I've been playing with Lucid Lynx on my A500 since Beta 1, upgrades and fresh installs of both Ubuntu and Kubuntu, and I must say I have no complaints.  Everything works OOB!! (except fingerprint scanner still has no support :frown:)

Actually, I tried getting the fglrx drivers from Ubuntu's repos, and noticed a significant DECREASE in performance, especially in VLC (lines during playback, delayed picture when switching into fullscreen).
Right now I'm using a fresh install of Kubuntu with the default drivers and video works flawlessly!

---

