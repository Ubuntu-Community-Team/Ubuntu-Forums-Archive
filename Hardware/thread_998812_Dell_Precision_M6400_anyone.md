---
title: "Dell Precision M6400 anyone ?"
date: 2008-12-01
forum: Hardware
---

### Post by aurelieng on 2008-12-01
Dear all,

I wonder if some of you here are lucky enough to have a Dell Precision M6400 running Ubuntu 8.04 or 8.10. I am particularly interested by your feedbacks about general hardware support, RAID, wireless, suspend/hibernate, etc...

Cheers,

Aurelien.

---

### Post by JDahl on 2008-12-06
I have one running Ubuntu 8.10 64bit.  Running on AC power, it 
seems to work perfectly,  but on battery power it often crashes
soon after X login.

I've successfully tested the following:
Nvidia 177 drivers
Wifi
sound
brightness adjustment from function keys
dual monitors

---

### Post by aurelieng on 2008-12-06
Thank you for your reply :) Strange X problem... I would bee curious to see the logs, if any.

You did not try to use the built-in RAID controller or suspend/hibernate ?

---

### Post by JDahl on 2008-12-06
I just checked: suspend/hibernate also seems to work,  and even restores
wifi connectivity.

I haven't tested raid.

I only had the machine for a few days, but so far I am very happy with it;
the important things all work without special configuration,  and by far it's
the fastest computer I've had.

---

### Post by aurelieng on 2008-12-08
I am really interested by this machine. Since I don't really have many hours to spend trying to make it work properly, I would like to gather as many information as possible :-) Could you please post the output of the following commands ? :)

```
sudo lspci; sudo lshw;
```

Thanks a lot :-)

---

### Post by nemarona on 2008-12-08
I'm curious about the 32-bit/64-bit choice. I understand 32-bit systems have problems with RAM > 3 GB or so; is this the reason for going with 64-bit? Are there any issues associated with this choice?

---

### Post by aurelieng on 2008-12-08
@nemarona: you should have a look at this: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by aurelieng on 2008-12-09
@JDahl: I read on [http://forum.notebookreview.com/showthread.php?t=303226](http://forum.notebookreview.com/showthread.php?t=303226) that a lot of users are reporting instabilities and BSOD using Windows, mostly linked to the graphic card/driver. Are you facing stability issues with Ubuntu ?

Aurel, very curious :)

---

### Post by vicbrother on 2008-12-16
Hello to all,

I have a M6400 too. I installed Ubuntu yesterday and it works with webcam and sound. But I have three problems:

1. Hibernate/Suspend: My RGB LED is black after waking up. 

2. My microphone doesn't work (I think I must configure it).

3. I have after installation 1920x1200, but after a reboot 1280x1024 only. Is there a nVidia-Driver for the 3700M?

Greetings from Hamburg
Vic

---

### Post by aurelieng on 2008-12-16
1. Is this problem solved by switching back to tty1, then back to X (i.e. Crtl+Alt+F1, Crtl+Alt+F7) ?

2. No idea

3. NVIDIA support : from [here]("http://forum.notebookreview.com/showthread.php?t=329970"), it seems that it should works with 177.82 or 180.11 (Beta).

Also, could you post the output of ```
sudo lspci; sudo lshw;
```
Cheers from Lausanne,

Aurelien.

---

### Post by yodi13 on 2008-12-30
> **aurelieng said:**
> Thank you for your reply :) Strange X problem... I would bee curious to see the logs, if any.

You did not try to use the built-in RAID controller or suspend/hibernate ?
I tried it but during installation Ubuntu 8.10 only detects individual disks. It did not detect the raid1 volume I had.
I was using Ubuntu8.10 desktop 64 bit so I wonder if the Raid controller is present in the server one ... I just posted a question on that.
Cheers

---

### Post by vicbrother on 2008-12-30
What did you mean? You can't see your RAID1? In my opinion you should see one disk - the other is the raid-disk. Do you use the dmraid-tools?

I have no time for a new installation of linux on my notebook, so I have put my 8-year-old-debian on a virtualbox-disk and run it under Vista. Thats fast enough for me :)

---

### Post by garet jax on 2009-04-07
> **aurelieng said:**
> Dear all,

I wonder if some of you here are lucky enough to have a Dell Precision M6400 running Ubuntu 8.04 or 8.10. I am particularly interested by your feedbacks about general hardware support, RAID, wireless, suspend/hibernate, etc...

Cheers,

Aurelien.
Ditto.
I am evaluating the M6400 to run Ubuntu, and I was wondering if someone got bad surprises with respect to stability and heat dissipation.

@aurelieng, you also have the M6400 ?

@JDahl, you managed to figure out the X problems ?

Thanks !

---

### Post by aurelieng on 2009-04-08
I recieved mine yesterday. QX9300, 4Go RAM, FX2700M, 2x320Go. No big trouble so far, but I'm still migrating my data from my previous laptop (8.04) to this one (8.10). I'm almost one release late for the sake of reliability, and will keep you informed in this thread.

Cheers,

Aurelien.

---

### Post by garet jax on 2009-04-27
Ok, I received mine Friday 24th.

P8600 (2.6GHz), 4GB DDR3 RAM, 1x320GB, nVidia FX2700, 17" LED RGB 1920x1200 with integrated camera, no fingerprint reader (below my lspci).

I installed Jaunty 9.04 x86_64 from an USB stick, and everything I tried works out of the box, and by that I mean:

[LIST]
[*]CPU frequency throttling
[*]Wifi (Intel 5300) network
[*]All special keys (display luminosity, keyboard luminosity, calc button, sound buttons)
[*]Sound
[*]Suspend/Resume and Hibernate/Resume (with binary nVidia driver)
[*]SD camera card reader
[*]Bluetooth
[/LIST]

Jaunty installs by default with the open source nVidia driver, which only gives 1280x800 resolution; installing the binary driver (version 180.44) gives full screen resolution.

Once done that I tried suspend/resume, which works fine. The only scaring thing is that suspending and hibernating ends with a "tuk" noise, similar to an exploded capacitor :shock:
I was scared, but resume went fine and no damages reported (I carefully sniffed the keyboard to check if a capacitor was really exploded).

Skype 32-bit works (sound and video) after configuring the sound in Skype itself.

I use it mainly for Java development, and first impressions is that this machine is really fast.

Slight disappointments for:
[LIST]
[*]AC adapter: it's huge and heavy, cannot believe how big it is
[*]Italian Keyboard: the Delete, Home, End, PgUp and PgDown buttons are IMHO too small and badly positioned (easy to push the wrong key). It's a shame as those keys are heavily used by a developer (at least by me). Maybe I'll get used to them, but the initial feeling is not comfortable.
[*]Fans: they start way too often (see below)
[/LIST]

I hoped the machine would not heat too much and that the fans would stay quite most of the semi-idle time (like just surfing the internet).
However, the fans kick in at around 46C to stop at 34C. I think this range is very conservative, and probably the machine can have a temperature equilibrium at around 50C.
I tried to modify this behavior with both i8k and dellfand to no avail: it seems that the BIOS kicks in anyway overlapping either i8k or dellfand configuration. 
For example, I got a situation where the BIOS said "fans on" and i8k said "fans on at this temperature ? fans off!", and so on with hichup-ing fans that every second started and stopped.
I ended up disabling both i8k and dellfand because it seems the BIOS is not configurable (at least found no configuration entries for the fans) or overridable.
Anyone that knows how to modify the BIOS settings for the fans, please speak up.
The fans are very efficient though, and reduce from 46C to 34C in less than a minute, albeit a bit too noisy for my taste. That's why I'd prefer to reduce the rate they start by increasing the temperature they start (without frying the laptop).
GPU temperature stays at 40-50C.

Regarding the 17" display, it's really wide, and had to modify the DPI from 96 to 104 to get a more comfortable font size. This of course breaks some application that uses fixed layouts (e.g. GMail). Also subpixel smoothing on this display is not perfect: you can see vertical colored lines for a white text on a black background, especially when seen from a distance of around 1m.
In general the colors are more "saturated" (forgive my ignorance on the terminology) than in normal LCDs (in my experience): they are more vivid. 
Seems to me that my color settings are good (i.e. colors are correctly displayed, no confusions between greens and yellows, etc.), but any advice on how I can check if the colors are correctly configured will be greatly appreciated.

I think I will appreciate more this laptop as the time passes, but I had high expectations for fans and display which are not matched.  

I was worried by Linux compatibility, but everything works out of the box (at least in Jaunty), and that is just great.

My lspci:
```

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX 2700M (rev a1)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection

```

---

### Post by garet jax on 2009-05-22
After days of utilization, I found another glitch of this laptop: the sound randomly stops working.

From my searches on the internet, it looks like it's a driver problem, and it can be worked around by issuing this command:

```
$ sudo alsa force-reload
```

My sound system is as follows:
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

$ lspci -vvv
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 0251
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at f6ffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I did not play with the various suggestions of adding parameters to the sound driver, because the information looked to me very fragmented and not clear enough or controversial.

I guess I will wait and hope the driver will be fixed (if it's indeed a driver problem, which is not clear, although looks like it is).

Battery lasts more than 3 hours and recharges faster than I expected, and I got used to the keyboard, so I am starting to enjoy this laptop.

Any comment is welcome. Do you also experience audio suddenly stop working ?
Aurelien, does the sound work ok on 8.10, or you migrated to 9.04 meanwhile ?

---

### Post by aurelieng on 2009-05-22
The sound was OK in 8.10, but broken with 9.04. This is likely to be a kernel problem, and I'm using the 8.10 kernel meanwhile. See [https://bugs.launchpad.net/ubuntu/+bug/362444](https://bugs.launchpad.net/ubuntu/+bug/362444) for more informations :)

---

### Post by josephhand on 2009-10-08
Ok.. so let me get this out now... I have never gotten any version of linux operationsl... :-(  I am a uhh... erm... windows person. Sorry.
 
So here it the interesting thing... I loaded Windows Server 2008 64Bit on this M6400 beast. I had the jerky sound issues... 
 
Then I loaded Windows 7 and the sound sounds great... except it just stops working... Just like on Ubuntu...
 
I do not think it is the drivers... I think we all seem to have a case of bad audio components. 
 
Thoughts?
 
joe

---

### Post by josephhand on 2009-10-08
I got an update... talked wtih Dell. Not great news for Ubuntu... but... maybe there is a matching driver out there for you guys... 
 
I was told to download and install the "Intel Matrix Storage Manager" driver. I know what your thinking... I asked that very question... and was told this fixes the issue. Givving it a try,
 
thanks,
joe
 
 
> **josephhand said:**
> Ok.. so let me get this out now... I have never gotten any version of linux operationsl... :-( I am a uhh... erm... windows person. Sorry.
 
So here it the interesting thing... I loaded Windows Server 2008 64Bit on this M6400 beast. I had the jerky sound issues... 
 
Then I loaded Windows 7 and the sound sounds great... except it just stops working... Just like on Ubuntu...
 
I do not think it is the drivers... I think we all seem to have a case of bad audio components. 
 
Thoughts?
 
joe

---

### Post by garet jax on 2009-10-09
> **josephhand said:**
> I got an update... talked with Dell. Not great news for Ubuntu... but... maybe there is a matching driver out there for you guys... 
 
I was told to download and install the "Intel Matrix Storage Manager" driver. I know what your thinking... I asked that very question... and was told this fixes the issue. Giving it a try.


Let us know anyway (certainly installing a SATA driver to fix sound problems seems strange) :???:
The strange thing is that force-reload ALSA makes the sound come back, so looks like a software issue.

Ubuntu 9.10 will finally ship an up-to-date version of ALSA, so I will try it and report here how it goes.

---

### Post by therico on 2009-10-15
Thought I'd chip in as the owner of a Precision M6400 with Ubuntu 9.04 (and 8.10) for 6 months. For the most part it works - 64-bit, sound, wireless, VPN, dual-array microphone and even the webcam (zero configuration with Skype) etc. There were a couple of issues:

1) Sound suddenly dropped out around June, fixed by adding 'options snd-hda-intel model-laptop' to the top of /etc/modprobe.d/alsa-base.conf. Then restart sound with pulseaudio -k && sudo alsa force-reload && pulseaudio -D (ignore the warning about the pulse-rt group).

2) If the laptop is exposed to very bright sunlight (shining behind you) the automatic brightness system can go a bit haywire, with no obvious way to override it as it's in hardware. I'm not sure if Windows has software to do this. This is pretty rare though.

The audio can take a bit of messing around. Be sure to check that things aren't magically muting themselves in the pulseaudio settings (pavucontrol) and the gnome Volume Control. Under Volume Control / Options tab, you can change the Digital Input Source between Analog Inputs and Digital Mic 1 (or change Input source to Front Mic instead of Mic) to change between the red microphone jack and the dual array microphone above the screen. Btw, under Sound options, all inputs+outputs are set to 'PulseAudio Sound Server' and Skype is using the 'pulse' driver too.

Other things --
I haven't personally had any fan problems.
You have the option to buy a slimline AC adapter, it's still quite absurd but perhaps half as big, and flatter.
The battery life is really good for this model, especially given the size of the thing!

---

### Post by garet jax on 2009-11-09
I re-installed Karmic Koala from scratch, mainly to get the ext4 improvements.

The overall impression is that Karmic works better than Jaunty; sound glitches seems to be gone, and suspend/resume (a usual suspect for being broken in every release ;)) works for me.

I don't use Compiz effects because of [this bug]("https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/290339"), which only appears to me with Compiz effects enabled, but they do work fine.

Karmic looks much snappier than Jaunty in almost everything; I don't have any benchmark, but just feels snappier. I guess it's mostly because of ext4.

Before updating to Karmic, I also updated the BIOS, which Dell prepared for Linux as well; updating the BIOS is a breeze.

I installed Skype 2.1.0.47 native 64-bit (without need for ia32libs), and works like a charm.

I thought I would share my upgrade, if you were interested.

Cheers

---

### Post by jlavezzo on 2010-03-30
I've been using a work-supplied M6400 since December.

Three cheers for Ubuntu!  I'm running 9.10 32bit.

I have been very impressed with how well everything works, Suspend, auto-dimming the screen, second monitor via displayport cable using the Nvidia configuration tool, Compiz, it's all great. (the only problem with suspend is that the battery doesn't last more than a few hours, so no suspend when unplugged except for driving to the coffee shop.)

Considering no one else on the web has reported this as a Linux problem, I'm going to assume that the Wifi problems I'm having are hardware related.  After about a month, the wifi started dropping out occasionally. Sometimes switching off the switch on the side of the machine and switching it back on after a moment would make it re-initialize wifi and I'd be back in business. But that has worked more infrequently. Typically I have to power off the whole system to get wifi back.  Today all networking shut down and I had to reboot to get it back.

Before I deal with the corporate hassle (Dell and my employer) I'm going to test if my windows VM running in Virtual Box is contributing to the problem.

---

### Post by garet jax on 2010-04-25
I have updated to Lucid Lynx over the weekend, few days before the official release.
The update went smooth, and everything works fine: suspend/resume, integrated camera, sound, Compiz, wifi, Skype, VirtualBox, etc.

No big differences from Karmic Koala regarding perceived snappiness, not much even in the boot time, though I have not clocked it. 
It was probably already quite fast for me in Karmic.

Cheers

---

### Post by garet jax on 2010-10-26
I have updated to Maverick Meerkat, and again no issues at all.

The sound problems (sometimes the sound just stopped working, and I had to reboot) seems to be solved by adding this to [FONT="Lucida Console"]/etc/modprobe.d/alsa-base.conf[/FONT]:

[FONT="Lucida Console"]options snd-hda-intel model=dell-m4-1[/FONT]

Since I added it, the sound never failed on me again.

---

### Post by garet jax on 2010-12-15
For the record, the sound still fails on me randomly, but I think it is due to Skype. When the sound disappears, it is always when I chat in Skype (which I have configured to emit short sounds when I send and when I receive a message).

I found no way to restart the sound via command line by interacting with pulseaudio or alsa, but I discovered today that by suspending the session and by re-activating it I get the sound back.

---

