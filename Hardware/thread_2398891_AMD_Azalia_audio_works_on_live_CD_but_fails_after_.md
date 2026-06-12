---
title: "AMD Azalia audio works on live CD but fails after installation (18.04)"
date: 2018-08-18
forum: Hardware
---

### Post by mariusz2 on 2018-08-18
I had a really terrible experience where I was running 16.04, upgraded to 18.04 using the update manager (it was offered to me), and a whole bunch of errors about "app-launch" appeared, updater ignored them, at the end decided "the system is now in an inconsistent state" and simply rebooted. Well.. actually it did not boot at all anymore. Any attempts to fix it broke it even more. So I reinstalled it completly.

My sound worked perfectly on the live CD. However, as soon as I installed the OS, audio does not work anymore. Going into sound settings, the only output it offers me is "Dummy Output". Here's some useful information:

```

mariusz@mariusz-pc:~$ aplay -l
aplay: device_list:270: no soundcards found...
mariusz@mariusz-pc:~$ lspci | grep Audio
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
04:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)



```

I am really angry after spending a whole day trying to fix Ubuntu when back in the day it worked out of the box, and now it's completly unstable and I keep running into issues (especially if the issues are caused by simply upgrading!)

As I said, the sound worked on the Live CD (technically a live USB), but now that it's installed, it does not. Why? What can I do to fix it?

EDIT: lspci also shows no driver loaded for the audio device (no kernel module), and "snd_hda_intel" (which I'm pretty sure would be the correct driver) is not laoded at all and I have no idea how to load or even install it.

---

### Post by Yellow Pasque on 2018-08-18
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by mariusz2 on 2018-08-18
```

mariusz@mariusz-pc:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2018-08-19 00:38:40--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org (www.alsa-project.org)... 77.48.224.243
Connecting to www.alsa-project.org (www.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-utils.git;a=blob_plain;f=alsa-info/alsa-info.sh [following]
--2018-08-19 00:38:40--  http://git.alsa-project.org/?p=alsa-utils.git;a=blob_plain;f=alsa-info/alsa-info.sh
Resolving git.alsa-project.org (git.alsa-project.org)... 77.48.224.243
Connecting to git.alsa-project.org (git.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-sh]
Saving to: ‘alsa-info.sh’


alsa-info.sh            [ <=>                ]  28.03K  --.-KB/s    in 0.03s   


2018-08-19 00:38:40 (833 KB/s) - ‘alsa-info.sh’ saved [28707]


ALSA Information Script v 0.4.64
--------------------------------


This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.


  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)


See 'alsa-info.sh --help' for command line options.


cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
lspci: Unable to load libkmod resources: error -12
cat: /proc/asound/modules: No such file or directory
ls: cannot access '/dev/snd/*': No such file or directory
grep: /proc/asound/cards: No such file or directory
/usr/sbin/alsactl: save_state:1595: No soundcards found...
cat: /tmp/alsa-info.4sxZ5jP1R2/alsactl.tmp: No such file or directory
Automatically upload ALSA information to www.alsa-project.org? [y/N] : 

```

---

### Post by Yellow Pasque on 2018-08-18
Well, that failed spectacularly. Let's try something easier. Can you get the output of:
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|snd[_-]|sound|hda.codec|hda.intel'
```

---

### Post by mariusz2 on 2018-08-19
```

mariusz@mariusz-pc:~$ dmesg | grep -C1 -E 'ALSA|HDA|HDMI|snd[_-]|sound|hda.codec|hda.intel'
[   11.191292] audit: type=1400 audit(1534631116.491:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc//sanitized_helper" pid=363 comm="apparmor_parser"
[   11.742264] snd_hda_core: loading out-of-tree module taints kernel.
[   11.742327] snd_hda_core: module verification failed: signature and/or required key missing - tainting kernel
[   11.742372] snd_hda_core: Unknown symbol snd_pcm_add_chmap_ctls (err 0)
[   11.742388] snd_hda_core: Unknown symbol snd_sgbuf_get_chunk_size (err 0)
[   11.742463] snd_hda_core: Unknown symbol snd_pcm_format_width (err 0)
[   11.768377] snd_hda_core: Unknown symbol snd_pcm_add_chmap_ctls (err 0)
[   11.768394] snd_hda_core: Unknown symbol snd_sgbuf_get_chunk_size (err 0)
[   11.768469] snd_hda_core: Unknown symbol snd_pcm_format_width (err 0)
[   11.833429] r8169 0000:01:00.0 enp1s0: renamed from eth0
[   12.145550] snd_hda_core: Unknown symbol snd_pcm_add_chmap_ctls (err 0)
[   12.145567] snd_hda_core: Unknown symbol snd_sgbuf_get_chunk_size (err 0)
[   12.145644] snd_hda_core: Unknown symbol snd_pcm_format_width (err 0)
[   15.644296] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready

```

---

### Post by mariusz2 on 2018-08-19
UPDATE: after reinstalling linux-image, suddenly the audio works (snd_hda_core was loaded), but now, Ethernet stopped working!!!!!

What is wrong with ubuntu being so unstable in the last 2 or 3 years?!

I don't have ifconfig installed and can't install it due to lack of connection, and lspci shows no driver loaded for my ethernet controller. What now???

---

### Post by Yellow Pasque on 2018-08-19
It looks like the module in question (snd-hda-core) may be corrupted. I would reinstall the kernel (and reboot):
```
apt-get install --reinstall linux-image-`uname -r`
```

---

### Post by Yellow Pasque on 2018-08-19
I see I typed too slowly. I have no idea about your ethernet problem. Maybe look through dmesg again. It may be another corrupt module file.
If files are getting corrupted, which sounds like a distinct possibility based on your first post, then it's most likely a hardware issue.

---

### Post by mariusz2 on 2018-08-19
No, nothing is corrupted, and dmesg does not mention any ethernet drivers whatsoever (in fact, I have 2 slightly different versions of the kernel under /lib/modules and the newer one lacks a lot of network drivers that the older has.... Hmmm).

It is not a hardware issue, other people have experienced similar problems with that audio card on the same version of ubuntu. I got the idea to reinstall the kernel image because I googled the exact error that came up. Everything also works on the Live CD, and in 16.04, and on Windows, so no, it's not a hardware issue, it's a bug in ubuntu (of which I encountered a lot in the last 2 or 3 years).

The ethernet card is RTL8111/8168/8411. how do i install the drivers for this one?

EDIT: Booting into the older kernel (4.15.0-29-generic), both the ethernet AND audio work, but... all color on the screen is slightly off with some weird minor artefacts ???
EDIT 2: ALSO, on -29, the ethernet driver in use is "r8169"... but somehow, on -32 (the defualt one), the driver IS there, but refuses to detect the ethernet controller ???? (even if manually loaded by "modprobe -i r8169"). Again, my hardware successfully supports everything other than ubuntu 18.04 so it's not a hardware issue.
EDIT 3: Sorry, the 32 kernel does not have r8169 installed at all. How do I install that?
UPDATE: The graphics artefacts in -29 only happen in Google Chrome??? What is going on, why can't ubuntu just work the way it used to, i'm having issue after issue after issue after issue after making the grave mistake of accepting the upgrade to 18.04 which was never tested by the looks of it

UPDATE 2: After installing the package linux-modules-extra-`uname -r` for the -32 version, Ethernet works. But now THAT has visual artefacts in chrome. Why?

OK, forcing Chrome to use the sRGB profile instead of "Default" fixed the issue. So to be safe, how do I make sure that sRGB is used in the whole system? Or is that a chrome bug?

---

### Post by leomilrib on 2018-09-18
I am experiencing similar problems since I updated from 16.04 to 18.04.

I'm using Xubuntu and my sound card is Intel though:
```

$ lspci | grep Audio
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)

```

In my case the WiFi was working fine, but the ethernet was failing to connect. After some research I found this answer on [AskUbuntu]("https://askubuntu.com/a/1043584/585194"), which suggests installing the r8168 instead of r8169 that I had already installed on mine machine.

Although it didn't work at first (even restarting and manually loading it), funny enough after I reinstalled the kernel (linux-image-4.15.0-34-generic) it went back working and using the r8168 driver.

I'm still experiencing weird instability with audio... my microphone doesn't work at all with Chrome and sometimes it seems PulseAudio crashes and restarts when I try to use the mic with FireFox or other applications... also always starting (and restarting) with volume level on 100%, which is extremely annoying...

I hope this at least helps with your network for now.


[LIST]
[*]Update: okay... I think I found what was causing all the instability with my audio. When I was on 16.04 I had installed the *pulseaudio-equalizer* which is not supported anymore, and although I had purged it after the update, it still continued causing problems cuz I didn't remove the *~/config/pulse* directory. Removing it and restarting PulseAudio finally fixed it for me:
[/LIST]
[INDENT]```

rm -r ~/config/pulse
pulseaudio -k
pulseaudio --start

```
[/INDENT]
[INDENT] Not sure if this applies on your case, but worth checking. =)
[/INDENT]

Oh yeah, [this was the thread]("https://ubuntuforums.org/showthread.php?p=9833992#post9833992") that helped me to permanently remove the *PulseAudio *configurations.

---

