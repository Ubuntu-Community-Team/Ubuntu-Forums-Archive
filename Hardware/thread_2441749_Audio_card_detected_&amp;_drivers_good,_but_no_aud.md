---
title: "Audio card detected &amp; drivers good, but no audio (Ubuntu 20.04)"
date: 2020-04-26
forum: Hardware
---

### Post by srv666 on 2020-04-26
Details:

- HP All-in-One
- AMD Family 17H drivers (detected correctly)
- Driver installed correctly
- No sound however

- Good sound on USB Headset and HDMI out
- Good sound on 3.5mm jack

---

### Post by TheFu on 2020-04-26
Please post the exact device and exact driver including version used.

I'm a little confused.  If the 3.5mm jack connects to speakers and the USB headset is a headset and the HDMI connects to a TV or Receiver, is there somewhere else you'd expect the sound to come from that isn't listed?

A few commands to get audio device/driver information:
```
lspci -vk |perl -lne 'print if /Audio/ .. /^[\w]*$/'
sudo lshw -C multimedia

```

---

### Post by srv666 on 2020-04-26
Hello,

I meant to say that there is no sound coming from the integrated PC speakers (B&O). Everything else works.

It does detect the speakers, but there is just no sound. The one having the issue is Family 17h

```
*-multimedia:0            
       description: Audio device
       product: Raven/Raven2/Fenghuang HDMI/DP Audio Controller
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0.1
       bus info: pci@0000:03:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:57 memory:fe788000-fe78bfff
  *-usb:0
       description: Audio device
       product: Plantronics C725
       vendor: Plantronics
       physical id: 1
       bus info: usb@1:3.1
       version: 1.35
       serial: 63A66D945C98684F9163A19DD9251BEE
       capabilities: usb-2.00 audio-control
       configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
  *-usb
       description: Video
       product: HP 2.0MP High Definition Webcam
       vendor: DHJPF019ICA2AB
       physical id: 1
       bus info: usb@3:1
       version: 0.08
       serial: 200901010001
       capabilities: usb-2.01
       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
  *-multimedia:1
       description: Audio device
       product: Family 17h (Models 10h-1fh) HD Audio Controller
       vendor: Advanced Micro Devices, Inc. [AMD]
       physical id: 0.6
       bus info: pci@0000:03:00.6
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:56 memory:fe780000-fe787fff
```

---

### Post by srv666 on 2020-04-27
Might it have something to do with UEFI? That's the option I selected. It did give me problems with the WiFi, but I was able to fix it by reinstalling the driver and following some instructions on how to correct it for EUFI and it works now.  I haven't been able to get the speakers to work though.  Speakers work great on another PC I installed 20.04 on (Acer).

---

### Post by slickymaster on 2020-04-27
*Thread moved to **Hardware**.*

---

### Post by CelticWarrior on 2020-04-27
No, whatever the problem is, UEFI has nothing to do with it. Unless... You installed Ubuntu in Legacy ("BIOS") mode which is absolutely NOT recommended and sometimes (rarely but still...) creates hardware detection/initialization problems.

Your hardware should work, it's certified: [https://certification.ubuntu.com/catalog/component/1022:15e3](https://certification.ubuntu.com/catalog/component/1022:15e3)

make sure it isn't disabled in UEFI ("BIOS") or otherwise muted in alsamixer.

---

### Post by srv666 on 2020-04-28
Yes, I saw that page, which is so weird.  It is for sure not muted and not Bios mode either. 

What is the command to reinstall this driver?  I would appreciate your help on this matter.

---

### Post by P-I H on 2020-04-28
Have you checked settings in alsamixer.

---

### Post by TheFu on 2020-04-28
Doubtful that reinstalling the driver will help.  But if you figure out the package name, then
```
sudo apt install --reinstall {insert-name-of-package} 
```
is the way. Don't include the {}.  How-to find packages when you know a filename: 
    [https://askubuntu.com/questions/481/how-do-i-find-the-package-that-provides-a-file](https://askubuntu.com/questions/481/how-do-i-find-the-package-that-provides-a-file)

First, be certain your system is fully patched:```

sudo apt update
sudo apt dist-upgrade
```
if those commands create any errors, fix them first.  if you installed in the last few days, the upgrade probably won't find much, but best to be sure.

---

### Post by srv666 on 2020-04-28
Yes everything looks good here, I even disabled auto mute. Still no sound, only some popping noises.

---

### Post by srv666 on 2020-04-28
WHAT IN THE WORLD??? If I change to bluetooth audio (JBL speaker) or earbuds, then come back to audio from my integrated speakers, THEN I have audio. After a reboot however, there is no audio on the integrated speakers once again :-(. So the speakers DO work, it's just a matter of finding what is causing them to die or not remain on...

---

### Post by TheFu on 2020-04-28
> **srv666 said:**
> WHAT IN THE WORLD??? If I change to bluetooth audio (JBL speaker) or earbuds, then come back to audio from my integrated speakers, THEN I have audio. After a reboot however, there is no audio on the integrated speakers once again :-(. So the speakers DO work, it's just a matter of finding what is causing them to die or not remain on...

I would guess that pulseaudio has decided that non-internal devices should get priority.  Pulse does 1 thing really well, it assumes that whatever device you just plugged into the system is the one you want to use.  That is problematic if you want to use the built-in speakers, since those are effectively never disconnected and cannot be "plugged in" to get Pulse Audio's attention.

Something you might try .... let me search these forums ... 
[https://ubuntuforums.org/showthread.php?t=2439232&p=13941459#post13941459](https://ubuntuforums.org/showthread.php?t=2439232&p=13941459#post13941459)  that post is about a webcam, but the pulseaudio stuff applied to the audio parts should work.  The stuff about **pavcontrol** is what matters.

I'm certain there is a CLI way to accomplish the same stuff, but pulseaudio seems to be the cruise-ship of capabilities when most of us want a little ski boat.

---

### Post by Yellow Pasque on 2020-04-28
You can probably run a command at startup to specify the default sink. You don't need to run the list-sink command every time. That is just to determine the name of the sink.
```
pactl list sinks
pactl set-default-sink <sinkname>
```

---

### Post by TheFu on 2020-04-29
Think **pactl list sinks** is the command, be careful. _No dash_ in the **pactl**, but there is in the **pacmd**.
```

$ pactl list sinks |egrep 'Name:|Description:'
        Name: **alsa_output.pci-0000_0a_00.3.analog-stereo**
        Description: HD-Audio Generic Analog Stereo
```

```
$ pactl set-default-sink alsa_output.pci-0000_0a_00.3.analog-stereo
```
worked.  Who, exactly, would know that long string is required?

For sources (i.e. microphones), something similar works:
```

$ pactl list sources |egrep 'Name:|Description:'
        Name: alsa_output.pci-0000_0a_00.3.analog-stereo.monitor
        Description: Monitor of HD-Audio Generic Analog Stereo
        Name: **alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo**
        Description: HD Pro Webcam C920 Analog Stereo

$ pactl set-default-source  alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo
```

If you don't need the Description, the 
```
$ pactl list short sources
4       alsa_output.pci-0000_0a_00.3.analog-stereo.monitor      module-alsa-card.cs16le 2ch 48000Hz        SUSPENDED
5       **alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo**        module-alsa-card.c s16le 2ch 32000Hz       SUSPENDED
```
can be useful.

---

### Post by srv666 on 2020-04-29
I have no issue at all with the mics, integrated mic and headset mic work really well. Still no solution to the speaker issue though, so weird.

---

### Post by Yellow Pasque on 2020-04-29
> **srv666 said:**
> I have no issue at all with the mics, integrated mic and headset mic work really well. Still no solution to the speaker issue though, so weird.

So did you try the solution in my previous post or not? Did it not work?

---

### Post by srv666 on 2020-04-29
No solution as of yet.  If any of you have a PayPal account, I am willing to pay for support from someone qualified.  Everything else works perfect and I even converted 20.04 to my daily driver, but no sound from the integrated speakers yet, just popping sounds every now and then.

---

### Post by TheFu on 2020-04-30
> **Yellow Pasque said:**
> So did you try the solution in my previous post or not? Did it not work?

Exactly, we need to see the command output to help. It makes things clear and we don't have to assume anything.
Please.

---

### Post by srv666 on 2020-04-30
It shows exactly that same window, nothing else. Please let me know if there is something I'm missing.

---

### Post by TheFu on 2020-04-30
> **srv666 said:**
> It shows exactly that same window, nothing else. Please let me know if there is something I'm missing.

[LIST=1]
[*]Open a terminal.
[*]Run this command: 
```
  pactl list sources |egrep 'Name:|Description:'
```
[*]Post the results here. Please use code tags, as I've done above, multiple times.
[/LIST]

Thanks.

---

### Post by srv666 on 2020-04-30
> **TheFu said:**
> 
[LIST=1]
[*]Open a terminal.
[*]Run this command: 
```
  pactl list sources |egrep 'Name:|Description:'
```
[*]Post the results here. Please use code tags, as I've done above, multiple times.
[/LIST]

Thanks.
```
pactl list sources |egrep 'Name:|Description:'
	Name: alsa_output.usb-Plantronics_Plantronics_C725_63A66D945C98684F9163A19DD9251BEE-00.analog-stereo.monitor
	Description: Monitor of Plantronics C725 Analog Stereo
	Name: alsa_input.usb-Plantronics_Plantronics_C725_63A66D945C98684F9163A19DD9251BEE-00.analog-stereo
	Description: Plantronics C725 Analog Stereo
	Name: alsa_output.pci-0000_03_00.6.analog-stereo.monitor
	Description: Monitor of Family 17h (Models 10h-1fh) HD Audio Controller Analog Stereo
	Name: alsa_input.pci-0000_03_00.6.analog-stereo
	Description: Family 17h (Models 10h-1fh) HD Audio Controller Analog Stereo
```

---

### Post by srv666 on 2020-05-02
Now I'm starting to get loud popping sounds on the speakers. Happens about every minute now.  They work great on Windows 10 however. Any ideas?

---

### Post by TheFu on 2020-05-02
Only to review post #14 above, setup a "sink" and any "source" you need.

**source** = input .... like a microphone.
**sink** = output ... like speakers.

Sorry. That's all I got.  You can do that using **pavucontrol**, but that GUI is a mess with far too many tiny options to get wrong.

---

### Post by srv666 on 2020-05-08
Can a Kernel update help perhaps? I see 5.6 is now out and has new cool features.

---

### Post by srv666 on 2020-06-16
PROBLEM FINALLY SOLVED!

See below:

- open terminal and enter

sudo nano /etc/modprobe.d/blacklist.conf

go to the end of the file and enter the two lines below:

#fix for hp-pavilion aio 27 xa0013ng
blacklist snd_hda_codec_realtek

Then reboot and you will be all set.

---

### Post by TheFu on 2020-06-16
Ah ... more realtek crap. Avoid whenever possible, especially NICs.

---

### Post by Yellow Pasque on 2020-06-17
Please mark the thread SOLVED (Thread Tools menu above first post)

> **TheFu said:**
> Ah ... more realtek crap. Avoid whenever possible, especially NICs.

*Shrug* I've never had issues with Realtek LAN (wireless is a different story).
As for avoiding Realtek for onboard audio, good luck with that...

---

