---
title: "[SOLVED] Sound problems-Intel 8201I (ICH9 Family) HD Audio"
date: 2008-09-07
forum: Hardware
---

### Post by Jorge_C on 2008-09-07
Hi, I installed Hardy 64 bits in my laptop and even though most things work out of the box, I'm having problems with sound which I haven't been able to solve searching the web.
Things that happen:
The drums sound that plays in the log in screen loops three or four times and then it loops some more times much more quietly, for instance.
Furthermore, if I start playing the .ogg video provided in the examples directory with vlc (totem makes it all worse somehow) video plays fine, but sound starts looping loudly (kind of ta ta ta ta...). Closing vlc doesn't stop the noise and I must restart to stop it. Besides, the volume applet doesn't affect those sounds, muting or setting the volume lower there makes no difference.
The output of aplay -l:
```
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: STAC92xx Digital [STAC92xx Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
```
And lspci -v:
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at df300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```

Thanks in advance.

---

### Post by remu on 2008-09-11
Hey, I'm having the exact same problem. Problem existed on Hardy 64bit, so I installed Intrepid hoping that may fix it, it didn't the problem continued. So I thought maybe it was occurring since I was using 64bit, so I installed 32bit Hardy, but the problem continues.

```
umer@umer-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
umer@umer-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07)
        Subsystem: Hewlett-Packard Company Unknown device 30f7
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Cantiga PCI Express Graphics Port (rev 07) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: 90000000-92ffffff
        Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30f7
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 90e0 [size=32]
        Capabilities: <access denied>

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 90c0 [size=32]
	Capabilities: <access denied>

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at 9f304c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at 9f300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: 9e300000-9f2fffff
	Prefetchable memory behind bridge: 0000000093000000-0000000093ffffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: 9d300000-9e2fffff
	Prefetchable memory behind bridge: 0000000094000000-0000000094ffffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: 9c200000-9d2fffff
	Prefetchable memory behind bridge: 0000000095000000-0000000095ffffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: 9b200000-9c1fffff
	Prefetchable memory behind bridge: 0000000096000000-00000000970fffff
	Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 9a100000-9b1fffff
	Prefetchable memory behind bridge: 0000000097100000-00000000980fffff
	Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 99100000-9a0fffff
	Prefetchable memory behind bridge: 0000000098100000-00000000990fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 90a0 [size=32]
	Capabilities: <access denied>

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 9080 [size=32]
	Capabilities: <access denied>

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 9060 [size=32]
	Capabilities: <access denied>

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 9040 [size=32]
	Capabilities: <access denied>

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at 9f304800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 215
	I/O ports at 9108 [size=8]
	I/O ports at 9114 [size=4]
	I/O ports at 9100 [size=8]
	I/O ports at 9110 [size=4]
	I/O ports at 9020 [size=32]
	Memory at 9f304000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: medium devsel, IRQ 11
	Memory at 9f305000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 9000 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e8 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 92000000 (32-bit, non-prefetchable) [size=16M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	Memory at 90000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 8000 [size=128]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>

04:00.0 Network controller: Intel Corporation Unknown device 4237
	Subsystem: Intel Corporation Unknown device 1211
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 9c200000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, fast devsel, latency 0, IRQ 216
	I/O ports at 3000 [size=256]
	Memory at 96010000 (64-bit, prefetchable) [size=4K]
	Memory at 96000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 96020000 [disabled] [size=64K]
	Capabilities: <access denied>

06:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 9a100300 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

06:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381 (prog-if 01)
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 9a100200 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

06:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 9a100100 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

06:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384
	Subsystem: Hewlett-Packard Company Unknown device 30f7
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 9a100000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

---

### Post by Jorge_C on 2008-09-11
Hi, I also tried Intrepid and even though I have the same sound problems at least I can mute it, more than what I can do with Hardy.
In the meanwhile, I enabled automatic login (not very security wise) and I avoid music/sounds.
Let's see if someone else helps us to solve this annoying issue.

---

### Post by remu on 2008-09-12
Hey,
I think I may have found a solution. Try adding pci=noacpi as a boot option. That solved it for me on my 32bit install, however I had done a whole bunch of other stuff before hand, so I don't know if the boot option alone is enough, or what else needs to be done. I'm going to do a clean install with Hardy 64bit and then see what is neccessary to get this working properly. I'll let you know what I find.

---

### Post by Jorge_C on 2008-09-12
Thank you very much! It works like a charm for me in a clean Hardy 64 install, so I guess that pci=noacpi is enough.
Let me now if it works for you too before I mark the thread as solved, please.

---

### Post by remu on 2008-09-12
Yea, I did a clean install, and that trick works for me as well. Though the startup and login sound are different from before, for some reason, but that might not have anything to do with this. Go ahead and mark it solved!

Edit: Though, the master slider doesn't do anything, I have to open the Alsa Mixer and change the audio level under "Front" to see a change.

---

### Post by Jorge_C on 2008-09-12
I didn't use to hear the startup sound (the one that plays while loading the desktop) and the login sound doesn't "hang" any more, but they don't seem different from my other ubuntu pc's.
I've been playing with alsamixer and in my laptop (an HP Pavilion dv7-1090es) the master slider controls the headphones; Front controls the laptop speakers and PCM controls both. I have tweaked master and front sliders so that they sound in a similar way with alsamixer and set my volume keys to control PCM through System->Preferences->Sound.
By the way, I had to install all updates before pci=noacpi worked.

---

### Post by remu on 2008-09-12
It seems to be all working properly now, thank god!
You were able to get your wireless working, correct? I have the WifiLink 5100, and I was able to get it up and running.

---

### Post by Jorge_C on 2008-09-13
No, my wireless doesn't work. It's a 5100 AGN, too, but according to "lshw -C network" there is no driver in use.
It seems that this card is supported in the 2.6.26 kernel ([http://intellinuxwireless.org/]("http://intellinuxwireless.org/")). I've been thinking about compiling the latest stable vanilla kernel but I've never done that before and since I don't need a working wireless right now I may wait till Intrepid. Though, the kernel thing must be quite instructive.
Anyway, how did you make it work? I'll probably give it a try.

---

### Post by remu on 2008-09-13
I followed theburningor's guide here: [http://ubuntuforums.org/showpost.php?p=5754065&postcount=62](http://ubuntuforums.org/showpost.php?p=5754065&postcount=62). It worked for me, at first I thought it didn't then I realised that I had the wireless turned off, so I pressed the wireless button on the laptop and it worked.

---

### Post by lopata on 2008-09-13
hey people  where i need to put the pci=noacpi   ???

i dont understand

 

the 5100 wireles card is working, everything works well on my hardy but on  lspci -v  its showing an unknowing device x))))

---

### Post by remu on 2008-09-13
You would put it in the kernel line of your GRUB file. Have a read here [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) hopefully that will clear it up for you

---

### Post by lopata on 2008-09-14
i put it , but still no sound x(((

---

### Post by remu on 2008-09-14
hmm, I'm not sure then.

---

### Post by remu on 2008-09-16
I just realised that I cannot control the brightness, either with the keyboard or with the brightness applet. I believe this may have something to do with the pci=noacpi option. Has anyone else encountered this problem or am I alone in this? Does anyone know what to do in fixing it?

---

### Post by Jorge_C on 2008-09-23
I can't control the brightness either, but I think I couldn't before either. Though, I'm sure I could control it when I tried Intrepid. Right now, ubuntu keeps the last brightness set in windows vista.

By the way, whenever I boot into windows, somehow it shuts down the sound card when halting, and later I can't play sounds in ubuntu. The first time I thought I had messed it all up, and I even reinstalled ubuntu, but finally I tried using a live CD and it made sound work again! So right now, if I ever boot into windows, I must use a live CD to get sound working properly. I will test it again because when that happened windows installed some updates and that could have been the problem.
I mean, the laptop has one key that mutes the sound: it works in ubuntu, but in a slightly different way. In windows, when sound is muted it is red, and it becomes white if sound is not muted. In ubuntu, is is always white, no matter whether it is muted or not. If it is red in ubuntu (after having used windows), it won't play any sound and I have to use the live CD, which is able to make the touch button white again. Quite weird...

---

### Post by thomashansen on 2008-09-24
Well, for those who (like me) reached this page and felt soo depressed after the last comment:

For those with a P5E Asus Motherboard, I think I found the main reason for this problem on Ubuntu Hardy 8.04:

The sound works out of the box, IF... you put the accessory sound board in the right slot!!!!

For the sound to work, you must place the soundboard on the FIRST TOP BROWN SLOT, near to the processor slot. Did this, and now the sound is perfect!

I found this info here: [http://alsa.opensrc.org/index.php/TroubleShooting#hda-intel:_no_codecs_found.21](http://alsa.opensrc.org/index.php/TroubleShooting#hda-intel:_no_codecs_found.21)

Good luck!

---

### Post by ohb1knewbie on 2008-09-26
Missed 2nd page of posts please ignore.

---

### Post by WheelsOfSteel on 2008-10-06
The pci=noacpi fixes the sound, but also makes the system boot with only 1 cpu core if running dual core cpu's like me - centrino 2.

---

### Post by remu on 2008-10-06
> **WheelsOfSteel said:**
> The pci=noacpi fixes the sound, but also makes the system boot with only 1 cpu core if running dual core cpu's like me - centrino 2.

Same here, let's hope this works out of the box with Intrepid final, it doesn't work at all with Intrepid Beta though :(

---

### Post by WheelsOfSteel on 2008-10-06
> **remu said:**
> Same here, let's hope this works out of the box with Intrepid final, it doesn't work at all with Intrepid Beta though :(

Yes, screwed my ubuntu upgrading to intrepid today.  No wired network on my pavilion dv7.  Re-installed Hardy and will stay at Hardy until Intrepid is seasoned at least.
I'll have to live with the cpu issue for now.

If anyone knows how to fix the sound and load 2 cores then please let us know.

---

### Post by Jorge_C on 2008-10-06
> **WheelsOfSteel said:**
> The pci=noacpi fixes the sound, but also makes the system boot with only 1 cpu core if running dual core cpu's like me - centrino 2.

Same here.

---

### Post by hvlugger on 2008-10-06
> **remu said:**
> Hey,
I think I may have found a solution. Try adding pci=noacpi as a boot option. That solved it for me on my 32bit install, however I had done a whole bunch of other stuff before hand, so I don't know if the boot option alone is enough, or what else needs to be done. I'm going to do a clean install with Hardy 64bit and then see what is neccessary to get this working properly. I'll let you know what I find.
Have a HP DV4-1041TX notebook, your fix fixed my problem, sound could be better but at least it works now, thanks

---

### Post by AlexH76 on 2008-10-08
I'm on an asus x71a. Tried the pci=noacpi, unfortunately, no luck.
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
```

Also followed instructions in [[COLOR="Navy"]this thread (about specific options to snd-hda-intel)[/COLOR]]("http://ubuntuforums.org/showthread.php?t=616845") but still.. no sound at all.
If there are other options to try, pls let me know.
A.

---

### Post by remu on 2008-10-08
> **AlexH76 said:**
> I'm on an asus x71a. Tried the pci=noacpi, unfortunately, no luck.
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
```

Also followed instructions in [[COLOR="Navy"]this thread (about specific options to snd-hda-intel)[/COLOR]]("http://ubuntuforums.org/showthread.php?t=616845") but still.. no sound at all.
If there are other options to try, pls let me know.
A.

We have different Audio Codecs, but something that may work for you is using the "irqpoll" kernel option. This fixed my sound issues in Intrepid which could not be worked around using the pci=noacpi option, however, irqpoll does cause the touchpad to be a little less responsive.

---

### Post by remu on 2008-10-30
Alright folks, good news! The audio situation is solved for anyone using the IDT 92HD71B7X audio codec. Comes in most HP dv4, dv5, and dv7 laptops. The solution as found here: 
[https://bugs.launchpad.net/ubuntu/+bug/269586](https://bugs.launchpad.net/ubuntu/+bug/269586)

The solution is quite simply.
First:
```
gksu gedit /etc/modprobe.d/alsa-base
```

Then add the following to the end of the file:
```
options snd-hda-intel enable_msi=1
```

For me this worked on a clean install of Intrepid. Also, make sure you remove any kernel options you put in place to get sound working previously, such as noacpi, pci=noacpi, or irqpoll.
Since two of those reduce you down to one core, and the last one screws around with trackpad response.

The above mentioned solution seems to fix all my flaws, and now I seem to have everything I need working on my dv4.

Hope this helped most people.

---

### Post by cloudstrife87 on 2008-10-31
Thanks remu!!! it really solved the sound problem of my Compaq CQ-45 IDT High Definition Audio Codec... :-)

---

### Post by Koufax on 2008-10-31
Having trouble with a DV7, and have tried just about everything listed, including the SOLVED fix here.  The welcome sound plays normally when starting, but after that nothing, and some error messages when changing settings.  Using the latest Intrepid, but I couldn't get it to work under Hardy either.

Update:
Disabling Skype and setting all the drop downs in the sound cp to Pulse has sound working normally.  No dice in Skype, but other than that things appear to be working normally.

---

### Post by kermiac on 2008-11-06
> **remu said:**
> Alright folks, good news! The audio situation is solved for anyone using the IDT 92HD71B7X audio codec. Comes in most HP dv4, dv5, and dv7 laptops. The solution as found here: 
[https://bugs.launchpad.net/ubuntu/+bug/269586](https://bugs.launchpad.net/ubuntu/+bug/269586)

The solution is quite simply.
First:
```
gksu gedit /etc/modprobe.d/alsa-base
```

Then add the following to the end of the file:
```
options snd-hda-intel enable_msi=1
```

SNIP


Thankyou SOOOO much remu! That has fixed all of my audio issues on a HP dv7 laptop! 
You Rock! :guitar:

---

### Post by Jorge_C on 2008-11-08
Thank you very much remu!!

Sound works now, but I have a small issue when muting pcm channel (which controls both the speakers and the headphones) while a sound is being played: the speakers/headphones start making some weird noises. Muting front or headphones or master channel works fine, though. However, I don't want my volume and mute keys to control master channel since it is way too sensitive and a small change makes the sound much higher or lower.

Any ideas about how to stop this small problem?

---

### Post by remu on 2008-11-08
Jorge_C:
If you would like your volume keys to control PCM, then go to System>Pref>Sound. There, at the bottom, choose HDA Intel Mixer (I think its that one, it may be the ALSA Mixer, only one of them gives you PCM) from the dropdown box. Then highlight PCM by clicking on it. Then close the window. Your volume keys should now control PCM.

As for the weird noise issue. I am also having the same problem. I do not know what is wrong. Sorry. If someone has found a fix to that small issue, please let us know. For the time being though, I just mute "Front" when I need to mute.

---

### Post by Jorge_C on 2008-11-08
Thanks remu, but I explained myself quite badly and it was impossible to understand what I really meant, I edited my previous post and now it should be much more clear:
"Thank you very much remu!!

Sound works now, but I have a small issue when muting pcm channel (which controls both the speakers and the headphones) while a sound is being played: the speakers/headphones start making some weird noises. Muting front or headphones or master channel works fine, though. However, I don't want my volume and mute keys to control master channel since it is way too sensitive and a small change makes the sound much higher or lower.

Any ideas about how to stop this small problem?"

---

### Post by remu on 2008-11-08
Well, what you want to do is go to: System>Preferences>Sound
Then, under Default Mixer Tracks: Choose "HDA Intel (Alsa Mixer)" from the Device drop down menu. After that, from the list of channells in that section, you can select the channel that you want to control with your volume keys. I would recommend selecting "PCM" from that list. Just select it by clicking the channel so that it is highlighted. After that, click close. Once you do that, your volume keys should control the channell that you have selected.

---

### Post by Jorge_C on 2008-11-08
I see it isn't clear yet, sorry for my bad English.
I have the same issue as you: when pcm is muted some I get some weird noises, and I'd like to solve that.  If anyone knows how to solve that, please let us know.
And setting my volume keys to control master (since it mutes properly as I said) isn't an option because it's way too sensitive.

---

### Post by remu on 2008-11-08
okay, I get it now, yea, I am having the same problem. For now, what I'm doing is controlling PCM with my volume keys, and then muting master if I need to mute (which I don't do too often).

---

### Post by ariekanarie on 2008-11-09
First of all: Complements to all Ubuntu folks: I have been with Fedora Core for many, many years, but I love my first experience with Ubuntu. On Fedora 9, no way I could not get wireless to work (tried it all, including compiling a specific kernel), but in Ubuntu it works out of the box!

Main problem at this moment is the sound. I have an HP DV7-1090 laptop and from the posts above I was positive that I would be able to make it work. 1,5 week later, I am not sure what to do anymore. When I installed vanilla Ubuntu 8.10, there was a continuous clicking sound in the speaker. The welcome sound and all other sounds were distorted. 

My current setup:
[LIST]
[*]Ubuntu 8.10 - kernel 2.6.27-7-generic
[*]System fully up-to-date, all updates installed
[*]Standard ALSA drivers
[*]Added options snd-hda-intel enable_msi=1 to /etc/modprobe.d/alsa-base 
[*]No additional kernel options (like pci=noacpi)
[/LIST]

Current status: 
when I start the laptop, no greeting sound. After logon, the only sound I hear is the error-beep. The volume icon in the panel shows sound is muted and if I click it, I get the following error message: 
> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.
 
Trying Preferences-Sound and the Test button with Autodetect, I get message:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
The window is now locked and has to be killed forcefully. Same when I select Alsa or Pulseaudio. When I try to change the volume with the white “slider” above the laptop keyboard, I do see the On-screen volume indicator, but I cannot change the volume. The mute button on the laptop is white and does not work. I already did check alsamixer: all volume levels are well up and nothing is muted. 

I noticed that kernel module snd-hda-intel is not loaded  when I start the laptop. When I load this module, the error-beep is now muted too. The mute indicator on the laptop turns to red. Difference is that I can push the test button in Preferences-Sound without any error. But I still hear no sound at all. 

With lspci it shows the soundcard is detected correctly. dmesg does not show sound related errors as far as I can see. In /var/log/messages there are 3 pulseaudio related messages:
> pulseaudio[6046]: ltdl-bind-now.c: Failed to find original dlopen loader. 
pulseaudio[6048]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted 
pulseaudio[5925]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted 


Other things I tried without any success:
[LIST]
[*]Adding pci=noapci to kernel options
[*]Compiling and installing the most recent ALSA drivers as described here: [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)
[*]Added my userid to groups pulse, pulse-access, pulse-rt
[/LIST]

Finally: I made my laptop dual boot with Vista and there it all works fine (grumble, grumble). So I do not think it is a hardware issue. I really hope someone can give some more pointers to solve my sound issues.

---

### Post by ariekanarie on 2008-11-10
Finally figured it out myself: I tried the most recent ALSA drivers and I could not get them off the system. Re-installing all relevant packages did not help. So I a full re-install of Ubuntu and added snd-hda-intel enable_msi=1 to /etc/modprobe.d/alsa-base. Hurray: sound finally worked after a reset :):):)

Sound works in Rhythmbox and flash. Only issue is that in Skype the sound-in is giving problems. That's for another day.

---

### Post by crimzon on 2008-11-19
Confirmed "options snd-hda-intel enable_msi=1" fix worked on Sony Vaio VGN-N250E. THANK YOU SO F-ING MUCH! This has been driving me nuts!:guitar:

---

### Post by einfinger on 2008-12-19
> **remu said:**
> Hey,
I think I may have found a solution. Try adding pci=noacpi as a boot option.



what do you mean by this ? im a total noob so... :P

---

### Post by AlexW573 on 2008-12-20
Thanks a lot remu, your solution ended hours of misery & failed googling :)

Adding that line onto alsa-base completely fixed sound on my new dv7-1020us with a fresh 8.10 install from CD.

---

### Post by josil on 2008-12-25
> **Jorge_C said:**
> I didn't use to hear the startup sound (the one that plays while loading the desktop) and the login sound doesn't "hang" any more, but they don't seem different from my other ubuntu pc's.
I've been playing with alsamixer and in my laptop (an HP Pavilion dv7-1090es) the master slider controls the headphones; Front controls the laptop speakers and PCM controls both. I have tweaked master and front sliders so that they sound in a similar way with alsamixer and set my volume keys to control PCM through System->Preferences->Sound.
By the way, I had to install all updates before pci=noacpi worked.

I have the same problem you had and actually a most similar laptop. How did you install pci=noacpi? Thanks in advance

---

### Post by Jorge_C on 2008-12-25
josil, if you're using Intrepid, the solution is found in post #26 in this thread.

For Hardy, you have to add pci=noacpi as a boot option. More information [here]("https://help.ubuntu.com/community/BootOptions#Change Boot Options Permanently On An Existing Installation"). Take into account that, if you have a dualcore, you'll "lose" one of them

---

### Post by SciatoreItaliano on 2008-12-26
This is a great help. I had an HP Pavilion dv4-1028us with this exact problem and reemu's solution solved it perfectly. This also seems to have solved some other mystery issues with my computer. For example, Pidgin would randomly stop responding. It must have had to do with the sounds when a message was received. Whatever caused the problems, this fixed them, so thanks for the great tip.

---

### Post by SciatoreItaliano on 2008-12-26
This is a great help. I had an HP Pavilion dv4-1028us with this exact problem and remu's solution solved it perfectly. This also seems to have solved some other mystery issues with my computer. For example, Pidgin would randomly stop responding. It must have had to do with the sounds when a message was received. Whatever caused the problems, this fixed them, so thanks for the great tip.

---

### Post by josil on 2009-01-01
> **Jorge_C said:**
> josil, if you're using Intrepid, the solution is found in post #26 in this thread.

For Hardy, you have to add pci=noacpi as a boot option. More information [here]("https://help.ubuntu.com/community/BootOptions#Change Boot Options Permanently On An Existing Installation"). Take into account that, if you have a dualcore, you'll "lose" one of them

Thanks a lot for boot option link. Sound problem solved!

---

### Post by NetProx on 2009-01-23
> **remu said:**
> ]

The solution is quite simply.
First:
```
gksu gedit /etc/modprobe.d/alsa-base
```

Then add the following to the end of the file:
```
options snd-hda-intel enable_msi=1
```



Thanks remu, this solution works just fine for me, I have a dv4-1129 and the audio problem was me sick.

Thanks man!

---

### Post by cecilmoney on 2009-02-28
I'm running an hp pavilion dv3, with the audio codec IDT 92HD71B7X (not positive), and this solution did not help. My headphones still don't work when plugged in, and the main speakers do not mute. 

I'm running Ubuntu 64, btw. 

any advice?

---

### Post by ashthekool on 2009-03-18
Hello everyone,

     remu's solution (post # 46) on [http://ubuntuforums.org/showthread.php?t=912896&page=5](http://ubuntuforums.org/showthread.php?t=912896&page=5) solved the sound issue on my HP dv4-1020us laptop. A big thanks to him. I am now able to play mp3 and other audio files on my ubuntu 8.10 :) . I was initially able to hear the drum beats while login but don't hear it anymore!. 

great going ubuntu forum!
cheers,
Ash

---

### Post by jack_spratt on 2009-04-26
> **ashthekool said:**
> Hello everyone,

     remu's solution (post # 46) on [http://ubuntuforums.org/showthread.php?t=912896&page=5](http://ubuntuforums.org/showthread.php?t=912896&page=5) solved the sound issue on my HP dv4-1020us laptop. A big thanks to him. I am now able to play mp3 and other audio files on my ubuntu 8.10 :) . I was initially able to hear the drum beats while login but don't hear it anymore!. 

great going ubuntu forum!
cheers,
Ash

This solution didnt work for me.

Im using Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03). After upgrade to kubuntu jaunty I have no sound whatsoever.

I really need a solution! Thanks :)

---

### Post by joseinbaraj on 2009-04-27
> **remu said:**
> Hey,
I think I may have found a solution. Try adding pci=noacpi as a boot option. That solved it for me on my 32bit install, however I had done a whole bunch of other stuff before hand, so I don't know if the boot option alone is enough, or what else needs to be done. I'm going to do a clean install with Hardy 64bit and then see what is neccessary to get this working properly. I'll let you know what I find.



Can someone tell me how to add "pci=noacpi" as a boot option

---

### Post by joseinbaraj on 2009-04-27
Can someone tell me how to add "pci=noacpi" as a boot option 

Thanks in advance ....

---

### Post by sbungy on 2009-04-27
Im using Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03). I'm using kubuntu jaunty 64bit and i have try the two solutions in the last post:

FIRST)
I add "pci=noacpi" as a boot option to obtain this new row:
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f844c4df-3dec-47ed-b0b9-4a7099ae44a5 ro quiet splash acpi=force pci=noacpi
i've insert acpi=force also to solve another problem whit system shutdown/restart.
SECOND)
I add 
options snd-hda-intel enable_msi=1
to the file 
/etc/modprobe.d/alsa-base
I have no sound!. 

My curiosity: 
[LEFT] in each post, I read add "options snd-hda-intel enable_msi=1" to the END of file alsa base" but my curiosity is this: My alsa-base file is empty when i open it to make this changes, so after the changes I have in the alsa-base file only one row like: "options snd-hda-intel enable_msi=1".. This is correct? I want to be sure that have not overwrite the alsa-base file during the open process (i use the kate editor on Kubuntu)...



 [/LEFT]

---

### Post by Jorge_C on 2009-04-28
I'm not 100% sure because I haven't installed Jaunty yet, but the file ```
/etc/modprobe.d/alsa-base
``` may now be called ```
/etc/modprobe.d/alsa-base.conf
```
The solutions posted in this thread work (though not perfectly, at least not for me) in Hardy and Intrepid, and they may still work in Jaunty.

You could also try adding 
```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5 
options snd-hda-intel enable_msi=1
```
to the same file.

---

### Post by david.smitty on 2009-04-29
Having similar sound issues with My Elitebook 2530p (HP)
Freshly installed Ubuntu 9.04.

Has anyone installed with this combination of OS and Hardware yet? I have no sound and am going through the similar threads to find answers but have come up with no sound on all attempts so far.

Sound Devices for me:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30e1
    Flags: bus master, fast devsel, latency 0, IRQ 2297
    Memory at 94820000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Pulse Audio is installed and running and it is the most recent version as well.

Any similar stories or solutions to this story are Happily welcomed.

Cheers,
D

---

### Post by joseinbaraj on 2009-04-30
Jorge_C,

i tried the previous post...but no luck ...:(

---

### Post by Rev2010 on 2009-08-29
I know this thread is a bit old but I wanted to say thanks to Remu and the rest of you. Remu's info got the sound problem fixed on a brand new laptop my sister-in-law bought that I was putting Ubuntu on. This saved me from pulling my hair out! Thanks again.

Funny how one text line fixed it all LOL.


Rev.

---

### Post by luckyfox on 2010-01-24
> **remu said:**
> Try adding pci=noacpi as a boot option.

This worked only as a temporary fix.

---

