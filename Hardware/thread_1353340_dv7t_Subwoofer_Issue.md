---
title: "dv7t Subwoofer Issue"
date: 2009-12-12
forum: Hardware
---

### Post by Lancelot59 on 2009-12-12
I know several people have this issue as well. The subwoofer on my machine isn't working. I haven't gotten anything useful from HP. My guess is that ubuntu simply can't see the sub. Is there a way to make it detect/use it in parallel with the main speakers?

---

### Post by P4man on 2010-04-27
Might help to give some basic and more verbose info. Not everyone can bothered to look up what "dv7t" actually is nor guess what ubuntu version you are running or what, if anything, you already tried.

Anyway, lets see the output of ```
lspci
``` and ```
aplay -l
```

---

### Post by Lancelot59 on 2010-04-27
dv7t is the model of the laptop I'm on.

Here's the PCI info:
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

```

and the second set of info.
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

---

### Post by P4man on 2010-04-27
my bad, try this:

```
aplay -L
```

(uppercase L)

---

### Post by Lancelot59 on 2010-04-27
Here we are then:
```

front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server

```

---

### Post by P4man on 2010-04-27
that all looks healthy to me.

Play some music, and in your terminal, run

```
alsamixer
```

Use the tab key to move between playback and recording, arrow keys to navigate left right, and up down keys to adjust the levels. M key to mute/unmute (escape to quit). See if you can get it working, it might just be one of the mixer (for your sub) being muted.

---

### Post by Lancelot59 on 2010-04-27
In windows the sub is listed as the "PC Speaker" under volume control. PC Beep was muted so I turned it up to full. I was playing some music through totem and it wasn't using the sub. Then I tried closing a window of FF I had opened with some tabs in it to get that warning noise, and it was using the sub.

I put my fingers over the sub and I'm feeling just the slightest bit of air moving. A stethoscope confirmed this. It's working I guess, just not enough to actually make a difference.

Also I can't turn the volume up too high, otherwise it makes parts of the laptop body resonate when the music reaches the right note...I really should've just gotten a macbook pro and removed OSx.

Anyhow, what I determined the drivers in windows do is only put the mid/high range sounds out through the main speakers, and pipe the bass channels to the sub. I wonder how we could set something like that up using ALSA.

Also, what is the command to restart the drivers? They usually seize and die when I open audacity.

---

### Post by lidex on 2010-04-27
Try this. Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1  

```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. Keep an eye out for 'LFE'.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

### Post by Lancelot59 on 2010-04-27
I'm on a dv7 though. I guess I can try running it with dv5 in there first.

---

### Post by lidex on 2010-04-27
> **Lancelot59 said:**
> I'm on a dv7 though. I guess I can try running it with dv5 in there first.

Doesn't matter / same configuration. Dv7 is not a valid option.

---

### Post by Lancelot59 on 2010-04-27
Nothing, the sub is just sitting there. Unless it's just doing so little I can't hear it. Does ALSA have an equaliser program? Totem sure doesn't have one, and VLC is acting up.

For output I have Internal Audio 1 Output/1 Input Analog Stereo Duplex selected. Under the sound preferences I just have a list of different modes for the sound card. Like the one above.

---

### Post by lidex on 2010-04-28
Did you go into alsamixer? Can you post the output of these terminal commands for me please:
```
uname -a
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```

---

### Post by Lancelot59 on 2010-04-28
Yes, I went into alsamixer. I set the PCBeep volume to full because the sub registers as PC Speaker in windows

Output:
I edited out my computer's name
```

Linux MYMACHINENAME 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

``````

Advanced Linux Sound Architecture Driver Version 1.0.20.

``````

==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD71B7X

==> /proc/asound/card0/codec#2 <==
Codec: Nvidia MCP78 HDMI

```I'm looking at the alsa-tools-gui. How is it?

---

### Post by lidex on 2010-04-28
I would suggest upgrading alsa. Click the alsa-upgrade-script link in my sig.

---

### Post by Lancelot59 on 2010-04-28
I'll do that in the morning. It's bed time now. Although I have to ask, why is this not in the repository?

---

### Post by P4man on 2010-04-28
> **Lancelot59 said:**
> I'll do that in the morning. It's bed time now. Although I have to ask, why is this not in the repository?
Its ubuntu's release philosophy to keep apps and packages stable for 6 montns and only provide security and bug fixes, no new versions. You can read more about there here:
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Anyway, it might be in the repo, try this:

```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

reboot and see if it helps.

---

### Post by Lancelot59 on 2010-04-28
Well that definately got it working. But now it's too loud. XD

For whatever reason I can't adjust the volume of the bass speaker in the mixer, and it's completely overpowering the tweeters now. :/

---

### Post by Lancelot59 on 2010-04-28
Well that definately got it working. But now it's too loud. XD

For whatever reason I can't adjust the volume of the bass speaker in the mixer, and it's completely overpowering the tweeters now. :/ Is there a way to adjust the bass gain? Or how about an equaliser? That would be much better.

Also, the damn laptop body is resonating at higher amplitudes. Serves me right for not getting an apple machine. A solid chunk of metal wouldn't resonate as easily.

---

### Post by P4man on 2010-04-28
Have you tried ajusting the sliders in alsamixer now, after installing that package? try that first. Try them all, but I think its one of the LFE ones.

As for a system wide equalizer, well, lets just say there are long and heated debates about that. Its not in there out of the box, but its possible if you want, have a look here:
[http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)

---

### Post by Lancelot59 on 2010-04-28
Why would there be a debate over it? It would be incredibly useful!

Also, there is no LFE option in alsamixer[SIZE=1]. This is what I have on output:

Master
Headphon      
Bass Spe 
PCM 
         Mic Jack
IEC958        
IEC958 D       
IEC958 P 
     IEC958 1         
Beep         
Speaker    

I've never gotten a LADSPA plugin before. I'll try installing it and see how it goes.

EDIT: It's working for now, but it's still off. It would be ideal if I could process the audio going to the tweeters/sub separately. But this is definitely an improvement.  Tuning the speakers is gonna take a while though. It's functional though. If ALSA was to implement processing for each device, or each channel even separately that would be wonderful. Now all I need to do is glue some parts of the body so it doesn't resonate! So annoying...
    [/SIZE]

---

### Post by P4man on 2010-04-29
> **Lancelot59 said:**
> W
Also, there is no LFE option in alsamixer[SIZE=1]. This is what I have on output:

Master
Headphon      
**Bass Spe **
PCM 
Mic Jack
IEC958        
IEC958 D       
IEC958 P 
     IEC958 1         
Beep         
Speaker    

And changing the "bass spe" slider makes no difference?

---

### Post by Lancelot59 on 2010-04-29
There is no slider for the bass speaker.

Also when I shutdown or restart the sub emits this very startling loud noise...not good. Can I make a script that automatically mutes it?

---

### Post by lidex on 2010-04-29
Try out some different model options in your alsa-base.conf. Replace 'model=hp-dv5' with 'model=dell-m4-1' and reboot. One more to try is 'model=dell-m4-2' (no quotes).

---

### Post by Lancelot59 on 2010-04-29
How would changing it to a completely unrelated model help? Do they all use the same chipset?

Also, about the massive pop that the sub emits when the machine starts to shut down, is there anything we can do about that?

---

### Post by lidex on 2010-04-29
> **Lancelot59 said:**
> How would changing it to a completely unrelated model help? Do they all use the same chipset?

Also, about the massive pop that the sub emits when the machine starts to shut down, is there anything we can do about that?

Yeah, same chipset.
You might try disabling (remove or comment out) power management option line in alsa-base.conf for the pop.

---

### Post by Lancelot59 on 2010-04-29
Where would that be? Is it the one I highlighted with bold? Also, should I upgrade to the latest version of ubuntu before trying this?

```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
**options snd-hda-intel power_save=10 power_save_controller=N**

# OPTIONS ADDED BY USER
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1

```

---

### Post by lidex on 2010-04-29
Yes, that's the one.
An upgrade could help.

---

### Post by Lancelot59 on 2010-04-29
Alright, I'll upgrade to the latest kernel and see how it performs.

---

### Post by opethfan89 on 2010-04-29
Lancelot,

I also own a dv7 laptop and had this **exact same problem**. For me, it was sound playing ONLY out of subwoofer and not speakers, but there was no terrible resonance problem.

Anyways, I am attaching a text file with the notes I wrote to myself about how to fix audio. I hope that they work for you and sorry if any of the spacing doesn't make sense, I had to convert the spacing over from Ubuntu to Windows.

Cheers,
Opethfan89

---

### Post by lidex on 2010-04-29
These are the actual options I have in my alsa-base.conf on my Dv7t running jaunty x64 with alsa 1.0.21. Codec is IDT 92HD75B3X5.
I had to upgrade alsa and add options to get any sound at all.
```
options snd-hda-intel model=3stack-6ch enable=yes
options snd-hda-intel position_fix=1 enable=yes
options snd-hda-intel enable_msi=1

```

---

### Post by Lancelot59 on 2010-04-30
Well I upgraded to the new build...eww. This new art style is REALLY ugly... Everything has gone all purple and yucky. One I get this working, step two is to find a way to get the old icons and boot screen back. This is just awful on so many levels. My eyes bleed! 

Plus I'm pretty sure I messed up Lirc when I was prompted to pick something...not that I had it working in the first place. Have you guys managed to get the HP remote to work?

During the upgrade it presented me with some changes it was going to make to the alsaconfig file:

```

--- /etc/modprobe.d/alsa-base.conf    2010-04-29 11:58:20.437335345 -0700
+++ /etc/modprobe.d/alsa-base.conf.dpkg-new    2010-01-28 16:01:27.000000000 -0800
@@ -38,9 +38,3 @@
 options snd-cmipci mpu_port=0x330 fm_port=0x388
 # Keep snd-pcsp from being loaded as first soundcard
 options snd-pcsp index=-2
-# Power down HDA controllers after 10 idle seconds
-options snd-hda-intel power_save=10 power_save_controller=N
-
-# OPTIONS ADDED BY USER
-options snd-hda-intel model=hp-dv5
-options snd-hda-intel enable_msi=1

```So should I just put

```

-# OPTIONS ADDED BY USER
-options snd-hda-intel model=hp-dv5
-options snd-hda-intel enable_msi=1

```back in? I'll have to try those suggestions with the different model/what you did in listed in that text file in the morning. It'll wake someone up right now.

---

### Post by opethfan89 on 2010-04-30
> **Lancelot59 said:**
> Have you guys managed to get the HP remote to work?


My remote actually works on my laptop with 9.10 installed, believe it or not. I didn't do any special configuration at all.

Also, I **still** have the same issue with the loud popping noise at shutdown, did upgrading fix it for you?

I just installed 10.04 in a virtual machine so we'll see how it performs, although I won't know until I actually install it.

Did any of the notes I had written down help you lancelot?



Opethfan89

---

### Post by Lancelot59 on 2010-04-30
Weird. Well I'm wishing I hadn't upgraded now...this just looks ugly. Is there a way to downgrade to the last build? Please say yes.

I'll also need to work on that remote once I'm back in Karmic (if I can get there D: ). The power buttons and such worked, but nothing else.

I haven't restarted yet so I can't be sure (I'll restart and let you know how it turns out).

I haven't had a chance to try them out yet, what with my rash upgrading yesterday. I'll monkey with them once I determine if I can get back to Karmic.

EDIT: It did stop, but I had also muted the PC Beep in the alsamixer, and it might have stopped before upgrading. Try muting that first. Although it could be due to the fact that my sub no longer works.

It appears I must reinstall to get my beloved Karmic back. Serves me right...I'll be back on later.

---

### Post by Lancelot59 on 2010-05-01
Alright, I'm back in Karmic. Oddly enough that loud pop when shutting down went away. Hooray! I think it was related to muting the PC beep.

Thanks for all the help. It seems functional now. I think we would make a proper tutorial sticky for all HP users on DVx models.

I've been trying to add a custom preset into the equalizer, but have had no success thus far. Also, with the EQ enabled, everything gets a bit of static to it. It spikes when I adjust the computer's volume. :/

---

### Post by opethfan89 on 2010-05-02
> **Lancelot59 said:**
> Thanks for all the help. It seems functional now. I think we would make a proper tutorial sticky for all HP users on DVx models.

Already done, check [here]("http://ubuntuforums.org/showthread.php?t=1073090").

Glad to see most of your stuff is fixed, but unfortunately it seems hardware support will never be perfect until vendors openly allow drivers for linux to be developed.

Regards,
Opethfan89

---

### Post by Lancelot59 on 2010-05-02
It's a pity. If only there was a company that developed open hardware...

Also, those instructions list a different set of steps. I had to alter the config file.

---

### Post by opethfan89 on 2010-05-03
> **Lancelot59 said:**
> It's a pity. If only there was a company that developed open hardware...

Also, those instructions list a different set of steps. I had to alter the config file.

Of course you have to alter the config file, those steps are not all-inclusive, but they **are** specific to owners of HP dvX laptops, so something is at least better than nothing.

And some companies HAVE, at least, cooperated with Linux for better hardware support. Like in 10.04, nVidia has released their proprietary driver for better Linux compatibility, and Dell already ships computers with Ubuntu pre-installed. But thats a topci for another, more relevant, thread.

---

### Post by Lancelot59 on 2010-05-04
That it is. Well I might as well mark this as solved. Thanks for the help everyone!

---

