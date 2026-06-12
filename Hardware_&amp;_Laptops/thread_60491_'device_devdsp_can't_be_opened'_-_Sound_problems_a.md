---
title: "'device /dev/dsp can't be opened' - Sound problems after installation."
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by LinuxLove on 2005-08-28
```

Sound server information message:

Error while initializing the sound driver:

device /dev/dsp can't be opened (No such file or directory)

The sound server will continue, using the null output device.

```

Absolutely no sound.

I'm not quite sure on specifics, but I believe I have a Realtek sound card (Btw, can anyone help on how I can check what kind of sound card I have?).

Help is appreciated.

---

### Post by joshmachine on 2005-08-28
Disclaimer:
I am running Hoary so menu items may be slightly different.

First check if indeed the file is not there.
If it is follow the advice below. If it is not, please post that it is not present as well as the output of "lspci" (see below).

 To see what you have in terms of harware, I would open up a terminal and run the
 
 "lspci" command.  This will show all of the hardware that is connected through the "PCI" Bus (i.e. sound cards etc). 
 
 If you can't figure out all the gobbledy-gook just post it to this thread.


If the file is there read on ...

I've seen similar errors when users haven't been added to the "audio" group. Since esd runs as your user, if you don't have the correct permissions, neither does it.

You can either use the command line:

$ groups

and verify that "audio" is in the list

or use the gui tool

System > Administration > Users and Groups

Select yourself and click on "Properties"

Select the "User Priveleges" tab and verify that the checkbox next to "Use audio devices"
is selected.

Cheers,
Josh

---

### Post by cheepgeek on 2005-08-28
My sound card is present. See attached output.

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] (rev 47)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
0000:00:07.3 Host bridge: VIA Technologies, Inc. VT82C586B ACPI (rev 10)
0000:00:11.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:13.0 Multimedia audio controller: Creative Labs SB Audigy LS
0000:00:14.0 USB Controller: OPTi Inc. 82C861 (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

also it appears that I have permission to access it. Do you have any other suggestions?
 
                                                                                                 Thanks,Jeff

---

### Post by LinuxLove on 2005-08-28
I should also mention that sound in Windows works perfectly.

Anyway, I couldn't find a "Multimedia Audio Controller."

```
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev
 04)
0000:00:02.0 VGA compatible controller: Intel Corp. 82915G Express Chipset Famil
y Graphics Controller (rev 04)
0000:00:02.1 Display controller: Intel Corp. 82915G Express Chipset Family Graph
ics Controller (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definiti
on Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp
ress Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB
 UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB                                             UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB                                             UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB                                             UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB                                            2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridg                                            e (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE                                             Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller                                             (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contro                                            ller (rev 03)
0000:02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control                                            ler (rev 80)
0000:02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C                                            /8139C+ (rev 10)
0000:02:04.0 Communication controller: Lucent Microelectronics V.92 56K WinModem                                             (rev 03)

```

"Audio" was also in the group list.
--------------------------------------------------------
EDIT: Sorry, but I just noticed I posted this in the wrong section of the forums. If any admin can move this topic to "Hoary 5.04 Kubuntu (KDE)" that would be great.

Thanks and sorry.

---

### Post by NiceGuy on 2005-09-01
Hi, it seems you are not alone with your problem, my system (and many others) appears to be doing the same. After trawling google for hours and trying different methods (none of which worked for me) I managed to fix the problem on my system with stunning ease!

I have a logitech 'communicate' webcam (usb), and for reasons better known to its self, (k)ubuntu was trying to use that as a sound card! I turned of the pc, unplugged it, restarted and hey presto - we have sound!!

So my next question - how can I stop my system getting confused so I can use my webcam again!?  ](*,) 

But at least I have sound!!  \\:D/ 

This may not be what is causing your problem but you never know - hope this helps,

Mark B-)

---

### Post by LinuxLove on 2005-09-01
[QUOTE=NiceGuy]Hi, it seems you are not alone with your problem, my system (and many others) appears to be doing the same. After trawling google for hours and trying different methods (none of which worked for me) I managed to fix the problem on my system with stunning ease!

I have a logitech 'communicate' webcam (usb), and for reasons better known to its self, (k)ubuntu was trying to use that as a sound card! I turned of the pc, unplugged it, restarted and hey presto - we have sound!!

So my next question - how can I stop my system getting confused so I can use my webcam again!?  ](*,) 

But at least I have sound!!  \\:D/ 

This may not be what is causing your problem but you never know - hope this helps,

Mark B-)[/QUOTE]

I just tried this with my webcam, and the sound still is not working; but I guess its possible that Kubuntu is thinking something thats not my sound card is. However some things I can't unplug, like the keyboard and mouse, so I'd rather find the answer to your question.

Thanks a lot for the reply. I'm sure someone (or us :)) will be able to solve this problem eventually.

---

### Post by NiceGuy on 2005-09-02
Well there is one way to be sure(ish) what your pc is trying to use as a sound card - type:

```
alsamixer
```

in to the console - that should bring up a screen which will tell you what your sound card is and allow you to change volume etc., thats how I found out about my webcam because it said my card was 'webcam' and my chip was 'usb'  :grin: 

If it is correctly detecting your sound card, try changing the volume levels (esp. the ones which are set to 0 if there are any). I don't know if will help but apparently that fixed someones sound problems on a random forum I read.

Mark B-)

---

### Post by NiceGuy on 2005-09-02
I've just had another thought...

The way I understand it (but I'm probably wrong so don't take it as gospel), is that in KDE sound is handled by a system called the aRts (analog Real time synthesizer) engine which then passes the sound on to one of a number of different sound system (which provide drivers for various soundcards). The most commonly used of these is ALSA (Advanced Linux Sound Architecture) but others include OSS (open sound system) and one or two others. 

Firstly I suggest you try going to Control Center > Sound & Multimedia > Sound System, Hardware tab, and change the audio device from auto detect to ALSA (which is probably to what it is using anyway) and then click apply, which should restart your sound system. If you recieve the same error message as you did before (ie. the one about "device /dev/dsp can't be opened (No such file or directory)" then try changing the audo device to OSS and click apply again to restart the sound system. If this works then it was probably a problem with ALSA (which you may need to fix but I wouldn't really know how to do it - I'm a linux newbie to!), if you get the same error message then is possibly a problem with aRts. 

In my case, when I tried to play sounds, aRts (or at least I think it was aRts) was telling ALSA (and OSS) that my soundcard was my webcam. However, DVD's played in Kaffine etc. are more commonly handled an engine called xine, not aRts. In my case, xine got it right and told OSS to use my sound card (not my webcam) and so I was able to hear the sound on dvd's. If you don't have a dvd player on your pc (but have amaroK installed) , try this: 

Open Kynaptic (or Synaptic if you use that) and search for 'amarok-engines' and install it (you may need to have extra repositorys enables: see [the Unoffical Ubuntu starter guide](http://www.ubuntuguide.org/#extrarepositories) ). Then open amaroK and go to  'settings > configure amaroK > engine' and change it from aRts to xine, click ok and try playing something in amaroK. If you still have no luck you could try going back to the engine window and scrolling down the xine page which (should have appeared in the engine window) to 'select audio device name' and try selecting another name (eg. dev/dsp or dev/sound/dsp or whatever options are there).

If you can get sound working in this fashon then it shows that its aRts that is getting confused, un-confusing it however, is another matter!  ](*,) 

Hope this helps,

Mark B-)

---

### Post by LinuxLove on 2005-09-04
On Auto the error message was "   device /dev/dsp can't be opened (No such file or directory) ", but on ALSA the error message was " device: default can't be opened for playback" Nothing else worked.

---

### Post by JaceWindu on 2006-08-16
If you're having the USB issue (or would like to check if you're having the USB issue) you can fix or check this from GNOME (and possibly KDE) by clicking on System -> Preferences -> Sound.  Once in there check the default sound card, if it's incorrect change it to the correct one and close the window.  I had to restart X after this (Ctrl + Alt + Backspace) for the changes to take affect.

EDIT:  This only fixed some problems I was having with programs that seemingly knew my sound device.  I was still having issues with programs trying to access /dev/dsp.  After a little experimenting (you can type *mplayer path_to_music_file/music_file 1> /dev/**###*** replacing **###** with a device in /dev (as another side you can find all the devices that audio has permissions for with the command *ls -l /dev/ | grep audio*)). I discovered that /dev/mixer would output the sound perfectly.  Working on getting /dev/mixer to be default for programs

---

