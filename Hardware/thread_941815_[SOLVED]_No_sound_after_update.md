---
title: "[SOLVED] No sound after update"
date: 2008-10-08
forum: Hardware
---

### Post by Lurchicus on 2008-10-08
Hi,

I have a Dell Inspiron E1705 that I have set up to dual boot Windows XP and Ubuntu 8.04. When I ran an update (System -> Administration -> Update Manager). After the update and a reboot, the sound stopped working (the speaker icon on the upper bar has a small red x next to it). The sound worked before the update and still works fine under Windows XP. Any suggestions?

```
p:~$ uname -a
Linux danr-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```

I believe this is my audio card (":~$ sudo lspci -v")

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Unknown device 01cd
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0
```

I'm still pretty much a noob with Ubuntu and it's been several years since I've done much with Linux.

---

### Post by Yellow Pasque on 2008-10-08
IIRC, this is known to happen with kernel updates. Try reinstalling alsa-base.
```
sudo apt-get reinstall alsa-base
```

---

### Post by Lurchicus on 2008-10-08
Hi Temüjin,

I tried the command suggested but...

```
danr@danr-laptop:~$ sudo apt-get reinstall alsa-base
[sudo] password for danr: 
E: Invalid operation reinstall
danr@danr-laptop:~$ 

```

---

### Post by Yellow Pasque on 2008-10-08
Err, sorry
```
sudo aptitude reinstall alsa-base
```

---

### Post by Lurchicus on 2008-10-08
Hi Temüjin,

Thanks... the command ran just fine... I rebooted after but still no sound.

I don't know if this would help, but when I double click the volume control I get the following message:

   No volume control GStreamer plugins and/or devices found.

When I go into System -> Preferences (all items are set to ALSA) and click on the Test button I get this:

   audiotestsrc wave=sine freq=512 !
   audioconvert ! audioresample ! gconfaudiosinc:
   Could not open audio device for playback.

I tried the other options in Sound Preferences and saw the same results except that settings other than ALSA also added "Invalid Argument" the the same error message.

---

### Post by Yellow Pasque on 2008-10-08
Is the driver for your sound card loaded? The following command should return a line with driver=snd-hda-intel
```
sudo lshw -C multimedia | grep driver
```

---

### Post by Lurchicus on 2008-10-08
Hi again Temüjin,

I didn't get any output from the command so I ran it without the grep filter and got this:

```
danr@danr-laptop:~$ sudo lshw -C multimedia | grep driver
[sudo] password for danr: 
danr@danr-laptop:~$ sudo lshw -C multimedia
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

I don't see anything relating to a driver there... not that I have much of an idea of what I'm looking for.

---

### Post by Yellow Pasque on 2008-10-08
```
sudo modprobe snd_hda_intel
```
If that works, add snd_hda_intel to /etc/modules:
```
gksudo gedit /etc/modules
```

---

### Post by Lurchicus on 2008-10-08
```
danr@danr-laptop:~$ sudo modprobe snd_hda_intel
[sudo] password for danr: 
FATAL: Module snd_hda_intel not found.
danr@danr-laptop:~$ 

```

And the mystery deepens... :)

---

### Post by Yellow Pasque on 2008-10-08
Try this: [https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel](https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel)

If that doesn't work, there is a script that builds the latest version of ALSA for you. [http://ubuntuforums.org/showpost.php?p=5792918&postcount=104](http://ubuntuforums.org/showpost.php?p=5792918&postcount=104)

---

### Post by Lurchicus on 2008-10-12
Hi Temüjin,

I still haven't had a chance to try this. I'll let you know how it works out in the next couple of days.

---

### Post by steveneddy on 2008-10-14
I'm having issues with sound after today's updates.

I updated through Update Manager.

New kernel in this update.

output of uname -a

```
2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
```

it says I don't have the gstreamer plugins but I look in synaptic and I see the gstreamer stuff installed.

---

### Post by Lurchicus on 2008-10-15
Hi Temüjin,

Woot! Success!

This statement:

```
sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic
```

from your first link "https://help.ubuntu.com/community/SoundTroubleshooting#Getting the ALSA drivers from a *fresh* kernel" did the trick!

Thank you very much!

---

