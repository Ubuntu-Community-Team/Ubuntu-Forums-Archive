---
title: "HP Pavillion DV4-1225DX issues / fix thread"
date: 2009-02-24
forum: Hardware
---

### Post by ryofire on 2009-02-24
It took 2 weeks to install Ubuntu Intrepid to my liking on my HP laptop, and I know theres a few more 1225 DX users out there suffering from the same issues so heres my issue, fix, and, compatibility report. 

If you have the same laptop, and have your own suggestions or issues feel free to reply. 

Default specs (mostly stolen from best buy :p )

HP Pavilion DV4-1225DX[LIST]
[*]AMD Turion™ X2 RM-72 Dual-Core Mobile Processor
[*]4GB DDR2 memory
[*]Multiformat DVD±RW/CD-RW drive with double-layer support and lightscribe
[*]14.1" WXGA high-definition widescreen display
[*]250GB SATA hard drive (5400 rpm)
[*]ATI RADEON HD 3200 graphics RS780M (shared memory, HDMI output)
[*]5-in-1 digital media reader
[*]Expansion port 3 (nobody actually uses this thing)
[*]2 USB 2.0 ports + 1 USB/ESATA port
[*]built in (802.11b/g BCM4312 rev 01 chipset)
[*]Default OS Vista Home Premium 64bit
[/LIST]

Ubuntu install notes.
 [LIST]
[*]A bios update is available. If your going to overwrite vista you should probably install this first. (it's not life or death, but might help somebody)
[*]  Gparted refused to resize my windows partition, when I installed with an 8.04 live cd. (I updated immediately to intrepid after install). If you have this issue and want to dual boot you may need to shrink the vista partition within windows using disc manager.
[/LIST]
Known Issues after install. 
[LIST]
[*]  No sound except out of headphones. (no sound through internal speakers)
[INDENT]
lspci -v output (for anyone that cares)

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
Subsystem: Hewlett-Packard Company Unknown device 30fb
Flags: bus master, slow devsel, latency 64, IRQ 16
Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
  [INDENT]FIX: add the line
```
options snd-hda-intel model=dell-m4-1
```
to the file
/etc/modprobe.d/alsa-base
[/INDENT]
*This fix works, but seems to have issues with sound quality and volume control. If someone stumbles upon a better solution let me know. It took over 1/2 a week for me to find this fix so I'm just happy that there is one.
[/INDENT]
[*]  Keyboard and touch pad lock up on return from suspend and hibernate.
[INDENT][INDENT]Fix: add
```
 i8042.reset
```
to the end of the kernel line in grub. You can also add it to the default options line if you want it automaticly added whenever grub is updated to a new kernel if you like.
example of updated Kernal line (in case your not clear)
```
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=88b99fce-0f2b-421d-9071-5974649671ce ro quiet splash i8042.reset
```
[/INDENT]
*this fixes the listed problem, but there seems to be another more intermittent issue with returning from hibernate, but as long as I have suspend I don't care.
[/INDENT]
[*]  Many 3d games output pure junk to the screen when using the restricted driver.
[INDENT]This only seems to effect openGL games like Open Arena, Alien Arena, and Warzone 2100
[INDENT]Fix: Radeon HD 3200 has documented issues with the ATI driver version used by Intrepid. The only solution is to compile and install the newest catalyst drivers (if you dare)
[click here for instructions on how to compile the ATI drivers for ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu")[/INDENT]
*This hardware also has known issues with mythbuntu, but i don't use that software so I don't know if this will fix it. 
[/INDENT]
[*]Kernel panics aka system lockup immediately upon connecting to certain encrypted networks.
[INDENT] This affects my university's WPA-2 enterprise network(PEAP, MSCHAPV2). This is a part of a larger issue with Ubuntu 8.10 and network manager, downgrading or upgrading network manager MIGHT fix this, but only intrepid seems to have CDMA (cricket wireless internet) support so neither are an option for me.
[/INDENT]
[/LIST]
Credits: (sites I found these fixes on)

[LIST]
[*][http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
[*][http://yourenotabowler.blogspot.com/2009/01/sound-warz.html](http://yourenotabowler.blogspot.com/2009/01/sound-warz.html)
[*][http://ubuntuforums.org/showthread.php?t=1047284&page=2](http://ubuntuforums.org/showthread.php?t=1047284&page=2)
[/LIST]

---

### Post by MD Sane on 2009-03-02
Dude thanks! a bunch i have a month looking for a solution work great with my dv4-1220 tks! :P

---

### Post by jstalnak on 2009-03-03
There is a fix, albeit incomplete for your speaker sound issue. See:

[http://ubuntuforums.org/showthread.php?t=1073090&highlight=jstalnak](http://ubuntuforums.org/showthread.php?t=1073090&highlight=jstalnak)

When I implemented this, my internal speakers now work, but the headphone jack no longer works and the maximum volume seems to me a bit low.  But the speakers do work.

---

### Post by ryofire on 2009-03-05
New issue and I think it's related to those lousy broadcom drivers again. Sometimes network manager seems to crash looooooong after returning from suspend (like 6 hrs later this time), but it only seems to happen when i use suspend. Well It's more of an annoyance than an issue since I can always restart it in the terminal with sudo NetworkManager .

---

### Post by NazarXG on 2009-03-05
Hei guys,

ryofire i got the exact laptop from bestbuy :D but my sound issue is not resolved though.

Your solution, gives me sound through internal speakers but doesn't respond to headphone jack being plugged in, it will keep playing via internal speakers. (model=dell-m4-1).

Then i tried model=hp-dv5, this gives me sound on headphones but not through internal speakers. Just to note, to begin with, i had no sound at all. Under device control i have HDA ATI SB (alsa mixer).

any suggestions?

---

### Post by ryofire on 2009-03-15
I'm as perplexed as you are. Make sure you get the same results as I do when you type ```
lspci -v
``` in the terminal.

If your still having problems you can try popping in the 9.04 livecd. I'm not sugesting you install an alpha release, but if it works off the livecd you know an upgrade after next month is in order.

---

### Post by crazyMochi on 2009-03-28
The following steps will enable sound on the internal speakers for the HP dv4-1225dx

sudo gedit /etc/modprobe.d/alsa-base

Add the following lines:

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 

perform sudo reboot after saving your changes


Thank you, NaplesBill, for your posting on this fix!

---

### Post by ryofire on 2009-04-06
I can confirm that NaplesBill's/CrazyMochi's fix works the same as the one I've already listed.

Also I was reading bugfixes online, and it looks like the kernel panic on issue with BCM4312 has been fixed with a new broadcom patch. The fix has been applied to Ubuntu restricted extras for Jaunty and Hardy. No update for Intrepid yet, but the priority for the issue is high and the fix is already known so I can only hope that the fix will be here soon.

---

### Post by ryofire on 2009-04-14
I've been having serious issues with the media (quicklaunch, quickplay whatever) buttons on my laptop ever since the middle of a game of a game of wesnoth yesterday. This isn't a Linux issue since I'm having the same problem in windows. 

Hp's reaction is to fool around with windows when this is obviously a bios or a hardware issue. Well forget them then I'll buy from one of the many other wonderful vendors out there next time i need a laptop. 

But for now my laptops volume keeps changing costantly and my media buttons don't work at all.

---

### Post by NazarXG on 2009-05-12
dell-m4-1 will fix the internal speaker, though the internal mic will not function. on the other hand, with hp-dv5, the internal speaker will not function but headphones and internal mic will. so depends on what you need more.

---

### Post by ryofire on 2009-05-24
> **NazarXG said:**
> dell-m4-1 will fix the internal speaker, though the internal mic will not function. on the other hand, with hp-dv5, the internal speaker will not function but headphones and internal mic will. so depends on what you need more.

The dell-m4-1 fix is still necessary in jaunty, but now the mic does work. Also the default ati restricted drivers work well enough. I'm finding a few too many stability issues with it though. Here's a quick list.

General instability and slowness with firefox plugins.
Skype works great... until it inevitably crashes.
Warzone 2100 keeps minimizing on me at somewhat regular intervals.
Warzone's sound occasionally acts really strange when the program is loaded it turns to static for a few seconds.

---

### Post by fabiosl on 2009-06-17
Hey all...
How about the video issue, have you got a right driver for it?
I tried some free-drivers and the proprietary one.
The proprietary works, but I don´t know why, when I open applications like Totem or when I open 5, 6 or 7 windows, the system slows down. 
I tried ¨radeonhd¨ and ¨radeon¨ drivers too, but they did not work for me.

One point to note too is that the System Monitor shows that the processor is being strongly used with those visual effects, what should not happen. I don´t know if it´s true, but i´ve read somewhere that it does have something to do with the new X server.

Wireless seems fine to me. :D

How about the webcam, have any of you succeded with it?
And about the remote control?

Anybody have installed Ubuntu 8.10 in this laptop? Experiences in older versions? =//
Help plzz....

---

### Post by fabiosl on 2009-08-06
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)
Keep the Video driver up-to-date... worked for me. :D

---

### Post by fabiosl on 2009-08-07
The audio stuff can be fixed (in hardy 8.04) by adding this two lines into /etc/modprobe.d/alsa-base :

```

options snd-hda-intel enable_msi=1
options snd-hda-intel model=dell-m4-2

```
I'm trying now to fix the Remote Control, does anyone can help? =/

---

### Post by ryofire on 2009-09-05
Another possible audio fix.
[URL="https://answers.launchpad.net/ubuntu/+source/kdebase-runtime/+question/69975"]
https://answers.launchpad.net/ubuntu/+source/kdebase-runtime/+question/69975[/URL]

I'll try it out after I get my laptop back from a warranty back-light replacement.


As far as the remote goes I never even bothered to try it. I guess I should look for the thing just in case I can find the time to play with it.


Also I plan on testing out Karmic before it get's released. Expect a cleaned up streamlined post on that subject come October.

---

### Post by ryofire on 2009-10-11
Bad news guys. Your on your own for Karmic.

My laptop isn't charging. It's either the power adapter or laptop itself (no light, won't work without battery, etc etc). This is actually my third serious hardware problem with this machine. I hope this time they just blame the motherboard and replace the whole thing....

well time to back up the whole hard drive...

---

### Post by ryofire on 2009-11-05
I've got 9.10 up and running now. I'll give more detail later, but for anyone out there thinking about upgrading heres my experience so far.

Sound works great out of the box (headphones untested). Wireless is broke out of box but I have it working.

The restricted drivers manager is useless. That said the manufacturers for both video and wireless have surprisingly good documentation.

grab the video driver from
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")

compile the wifi driver from
[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

### Post by Ckoryom on 2010-01-23
Confirmed It Works!!! Thank you , My system can go into suspend mode now without freezing!!! 

I have an HP laptop dv4 1225dx

---

### Post by lordsusanoo on 2010-02-03
Im running Karmic Koala too but my "integrated Microphone Array" isnt picked up by Ubuntu....it works fine in windows though. I have good output through speakers (have not tested the headphones)

My lspci -v output

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: ATI Technologies Inc RS780 Azalia controller
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

Also...im running 64 bit...so i dont know why that says 32

---

### Post by topcoder on 2010-02-04
I have quite the opposite problem: My integrated mic array is detected, but external mic does not work. Funny thing is that sometimes, my integrated mic array also stops working in Ubuntu, and does not work until I restart.
As for the 32 bit thing, I too am not very sure. I too use 64 bit Karmic, and my system shows 64 bit in some places and 32 bit in other places. My "lspci -v" output is:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at 92500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: ATI Technologies Inc RS780 Azalia controller
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at 92410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by ryofire on 2010-02-25
I had a problem with the fn key "sticking" or working "backwards" (I had to hold it down to type normally). If anyone else gets this problem it's an easy fix. Hold down fn and numlk together and it should fix itself. Source [http://en.kioskea.net/forum/affich-64792-laptop-function-key-problem](http://en.kioskea.net/forum/affich-64792-laptop-function-key-problem) 

Anyhow I found another issue. It wont accept my password when I return from  standby.

---

### Post by topcoder on 2010-02-28
> **ryofire said:**
> Anyhow I found another issue. It wont accept my password when I return from  standby.

By not accepting password, do you mean that your keyboard and/or mouse does not work when you resume from standby? If yes, did you try ssh from another machine on the network. If you find that the computer works through ssh, I think that the fix mentioned here, in the first post should help. Well, at least it worked for me in jaunty. In karmic, I had no such issues, luckily.

---

### Post by ganjarie on 2010-06-26
How about the webcam for dv4-1225dx. How can I install it? is there any manuals and software needed?

---

### Post by Katty2008 on 2010-07-18
I'm running xubuntu since my HP didn't seem to get along with ubuntu. I had sound in my speakers when I wanted that and had sound in my headphones when I want that. Now, after I updated the other day, there is no sound in my headphone, but it was play through my speakers no matter what...Any idea on what I should do??

---

### Post by Applelnx on 2010-07-26
Hi, I'm having trouble with the integrated microphone, I can't make it work. I'm using Ubuntu 10.04, 64 bits. Any chance someone had the same problem and fixed it?

---

### Post by topcoder on 2010-07-27
> **Applelnx said:**
> Hi, I'm having trouble with the integrated microphone, I can't make it work. I'm using Ubuntu 10.04, 64 bits. Any chance someone had the same problem and fixed it?

Same issues here. I am using a Compaq CQ45 laptop. Not only does the integrated microphone not work, I also cannot use an external microphone, or headphones. This issue did not exist with ALSA (Karmic), but came in with pulseaudio. Any way to go back to ALSA, or fix the thing with pulseaudio?

---

### Post by imwithid on 2010-08-16
I don't care too much about the web cam (I never used the one on my desktop either), but the card reader is one thing I can't get working and I use this on my desktop about once a week. Has anyone been able to figure this out?

Also, has anyone any information about external hard drive cases with the powered eSATA/USB combo? The hard drive in this laptop was toast and I don't want to put another one in as this laptop bakes like an oven (I have to use the Thermaltake Massive23 to cool it).

[Edit]
Never mind. Ubuntu Lucid 10.04 seems to support the 4in1 card slot. I would like to see how well the Web Cam works on this laptop.

[Edit #2]
It works! I just installed Cheese and I can only assume that if I install Skype that it will work there as well. Just about everything works.

---

### Post by OthnielGraichen on 2010-08-17
Applelnx:

My friend Rory also has a DV4-1225DX.  His Web cam and sound are working with the dell-m4-1 alsa driver.  Skype works but with no microphone.  I've been studying the forums and have tried hp-dv5 with and without msi_enable=1.  Still no dice.

Do I have to upgrade from Alsa version 21 to the new 23?  Or just wait
for Ubuntu 10.10?  Any simple replies welcome.  I told him to just buy
a better webcam as the built-in one is only .3MP.

---

### Post by imwithid on 2010-08-19
I find the only two persisting problems on this laptop as of Lucid 10.04 are:

1. The microphone (input works for external microphones) and
2. The 5-in-1 card reader requires a reboot with the card inside for it to be detected.

I would like to know if it is possible to somehow kill the lights on the SmartMedia panel as well as the HP logo on the lid. I find the panel most annoying with the bright light always in my periphery, especially when the room gets dark. I'm not prepared to take apart this laptop (I just took apart an old Gateway to see if it was possible to retrofit an SATA hard drive using a 2.5" SATA to PATA converter - it almost worked if it hadn't been for the orientation of the pins).

[EDIT]

The 5-in-1 card reader's ability to detect memory cards depends on the BIOS settings.

If the card reader's power saving feature is ENABLED, then you must reboot the system with the card inserted for it to be detected.

If the card reader's power saving feature is DISABLED, then the card will be detected whenever it is inserted.

This is not much of a power saving feature if the system must be rebooted in order to detect the card. It wastes both time and power.

---

### Post by imwithid on 2010-09-04
I have just installed Lucid 10.04.1 and the microphone problem seems to have gone away. I now have 3 microphones listed in Sound Preferences. I can now fully use Skype without having to plug in an external microphone.

This saves me from having to try upgrading to 10.10. I just want to stick with a single release for more than a few months for once. I haven't stayed with a single release of Ubuntu ever since I got my first taste of Ubuntu with version 6.06.

---

### Post by Applelnx on 2010-12-04
The problem seems to be solved for me. I reinstalled ALSA and PULSEAUDIO, edited **/etc/modprobe.d/alsa-base.conf** and added the following line at the bottom:

```
options snd-hda-intel model=dell-m4-1
``` 

Then, reloaded ALSA, and typed the following in a terminal:

```
killall pulseaudio
sudo alsa force-reload
pulseaudio -D
```

Everything works fine for me now (internal and external microphone,speakers and headphones).

---

### Post by Alex Herron on 2011-01-11
the latest round of updates for Lucid 10.04 (which included kernel 2.6.32-27-generic) broke my microphone(internal and line out) and line out speakers.

i already had alsa-base.conf edited, this has not changed, and i purged reinstalled alsa-base alsa-utils and pulseaudio (also purged reinstalled linux-sound-base, libasound, and the kernel image beforehand)

anyone else experience this on their HP dv4-1225dx after the updates?

---

### Post by Zaelyx on 2011-02-22
Well, the microphone input now randomly stops working. I will load an application, like Exaile or Sound Recorder and the input will just cease to work. I can see 3 different microphones, but no matter the one I choose, the input does NOT work.
I'm running Ubuntu 10.10, kernel 2.6.35-25-generic.

I added the following lines to my /etc/modprobe.d/alsa-utils.conf
```

options snd-hda-intel enable_msi=1
options snd-hda-intel model=dell-m4-1

```

The Microphones all WORK for a small amount of time, but I'm puzzled as to what is killing them off. I get this message every time I force alsa to reload itself.

```

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zaelyx/.gvfs
      Output information may be incomplete.
Terminating processes: 2603lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zaelyx/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zaelyx/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zaelyx/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-atihdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device (failed: modules still loaded: snd-hda-codec-atihdmi snd-hda-codec-idt snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-atihdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

```

Relevant dmesg output:
```

[  149.480274] input: HDA ATI SB Mic at Sep Left Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input16
[  149.480396] input: HDA ATI SB Mic at Ext Right Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input17
[  149.480459] input: HDA ATI SB Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input18
[  149.480521] input: HDA ATI SB HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input19
[  149.480775] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  149.480886] HDA Intel 0000:01:05.1: irq 45 for MSI/MSI-X
[  149.480907] HDA Intel 0000:01:05.1: setting latency timer to 64
[  152.551270] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0001
[  424.582611] HDA Intel 0000:01:05.1: PCI INT B disabled
[  424.683487] HDA Intel 0000:00:14.2: PCI INT A disabled
[  425.161749] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  425.321924] input: HDA ATI SB Mic at Sep Left Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input20
[  425.322290] input: HDA ATI SB Mic at Ext Right Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input21
[  425.322523] input: HDA ATI SB Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input22
[  425.323057] input: HDA ATI SB HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input23
[  425.335456] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  425.335566] HDA Intel 0000:01:05.1: irq 45 for MSI/MSI-X
[  425.335588] HDA Intel 0000:01:05.1: setting latency timer to 64
[  428.401371] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0001
[  542.535878] HDA Intel 0000:01:05.1: PCI INT B disabled
[  542.662551] HDA Intel 0000:00:14.2: PCI INT A disabled
[  542.900599] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  543.040748] input: HDA ATI SB Mic at Sep Left Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input24
[  543.041109] input: HDA ATI SB Mic at Ext Right Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input25
[  543.041341] input: HDA ATI SB Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input26
[  543.041573] input: HDA ATI SB HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input27
[  543.053509] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  543.053636] HDA Intel 0000:01:05.1: irq 45 for MSI/MSI-X
[  543.053658] HDA Intel 0000:01:05.1: setting latency timer to 64
[  546.120073] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0001

```

arecord -l:
```

zaelyx@zaelyx:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```

This is quite irritating, having to reset alsa for who knows why...and it ruins my skype calls as well. Hopefully someone can resolve this issue!

---

### Post by Zaelyx on 2011-03-02
Well, I think I may have solved the issue (by angry deletion.) I have been on Skype for 5 hours and there hasn't been a single hiccup, so I'll go ahead and assume everything is fixed!

What did I do?

I removed pulseaudio. I returned ALSA to the native sound driver for the system, following the instructions here: [http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html](http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html)

We'll see if the solution lasts, but so far its good! ^_^

---

### Post by imwithid on 2011-03-18
Having installed Ubuntu 10.04 several times, I find that the installation can be finicky. By that, I mean that it depends on what you are doing or have plugged in during the Live installation.

For example, if you have your headphones plugged in during installation, you will lose the ability to use the external speakers and this may affect (not sure) your microphone as a result as well.

Also, if you change the brightness during installation, it can be tricky fixing it upon reboot after installation as it remains at full brightness afterwards.

One last quirk is that if you install the restricted drivers for the wireless mini card (the proprietary one that works)  prior to installation via the Live installation, it will  remain intact after reboot, however, if you install it after reboot, you will have to build it or install it while wired via a LAN connection (the former is the easy way; I have not had any success via the CD or installing it via the manually downloaded file kept on a backup external drive).

---

### Post by gideond on 2011-03-31
I've recently installed Ubuntu 10.10 on my DV4-1281 and everything is working great with one exception. It's killing my battery. It seems to charge fine and it seems to have battery consumption comparable to Vista during actual use. However, once I shut it down it continues to drain my battery even when the power is off. I'm assuming something is being kept active here. 

Also is there a way to update the bios from Ubuntu? I do not have a windows partition on this machine anymore.

---

### Post by imwithid on 2011-04-05
> **gideond said:**
> I've recently installed Ubuntu 10.10 on my DV4-1281 and everything is working great with one exception. It's killing my battery. It seems to charge fine and it seems to have battery consumption comparable to Vista during actual use. However, once I shut it down it continues to drain my battery even when the power is off. I'm assuming something is being kept active here. 

Also is there a way to update the bios from Ubuntu? I do not have a windows partition on this machine anymore.

As to your battery issue, something seems wrong, possibly with the hardware. I had a Gateway 450 ROG which made an odd buzzing noise when off (it was barely audible but if you put your ear to the keyboard, you'd hear it) and the battery would drain rapidly when off (about 5-7% per day). In my case, it was not a battery issue as I had 4 different batteries that I was able to use to test the problem.

Unfortunately, there is no way to update the BIOS safely without Vista or 7. I had to bite the bullet and download a copy of Vista just to update the BIOS on my DV4-1225dx (I know that this is illegal but I did not intend on using it for longer than the time it took to install and update the BIOS). Fortunately, I had a spare hard drive via an eSATA cable which made things easier (as I did not want to modify partitions and Vista does not like to use USB external drives).

I hope that helps.

---

### Post by gideond on 2011-04-05
Unfortunately, I've already slapped another drive in it and did a quick install of Win7 to flash the latest BIOS. It didn't seem to help any though. Anyone know if there is a way to test the external ports for active power when the laptop is shutdown? I guess I could try plugging my USB speaker into and see if they light up.

---

### Post by gideond on 2011-04-08
I reinstalled Ubuntu, did my updates and left it alone overnight. No additional configuration. The problem remained the same. I blanked it and put Mint Debian on it instead and no more battery issue. I get a 3-4% loss overnight with Mint, which is about what Vista got. I guess Ubuntu doesn't get along with this laptop.

---

### Post by kamabah on 2011-04-24
> **OthnielGraichen said:**
> Applelnx:

My friend Rory also has a DV4-1225DX.  His Web cam and sound are working with the dell-m4-1 alsa driver.  Skype works but with no microphone.  I've been studying the forums and have tried hp-dv5 with and without msi_enable=1.  Still no dice.

Do I have to upgrade from Alsa version 21 to the new 23?  Or just wait
for Ubuntu 10.10?  Any simple replies welcome.  I told him to just buy
a better webcam as the built-in one is only .3MP.

I have exactly the same problem

---

### Post by Ckoryom on 2011-06-20
This was my solution for my 1225dx!! thank you!! Now I have Headphones and mic working.

> **Applelnx said:**
> The problem seems to be solved for me. I reinstalled ALSA and PULSEAUDIO, edited **/etc/modprobe.d/alsa-base.conf** and added the following line at the bottom:

```
options snd-hda-intel model=dell-m4-1
``` 

Then, reloaded ALSA, and typed the following in a terminal:

```
killall pulseaudio
sudo alsa force-reload
pulseaudio -D
```

Everything works fine for me now (internal and external microphone,speakers and headphones).

---

