---
title: "Dell Inspiron 1525 Sound Problem"
date: 2008-10-20
forum: Hardware
---

### Post by jameselliot on 2008-10-20
Hi All,

The sound on my dell laptop was working fine until I did an update today.  The following files were updated:

[COLOR="DarkRed"][FONT="Courier New"]Commit Log for Mon Oct 20 08:55:34 2008


Upgraded the following packages:
hal-info (20080508+git20080601-0ubuntu0.8.04) to 20081001-0ubuntu1~hardy1
jockey-common (0.3.3-0ubuntu8) to 0.3.3-0ubuntu8.1
jockey-gtk (0.3.3-0ubuntu8) to 0.3.3-0ubuntu8.1
kdelibs-data (4:3.5.9-0ubuntu7.1) to 4:3.5.10-0ubuntu1~hardy1
kdelibs4c2a (4:3.5.9-0ubuntu7.1) to 4:3.5.10-0ubuntu1~hardy1
kfilereplace (4:3.5.9-0ubuntu1) to 4:3.5.10-0ubuntu1~hardy1
klinkstatus (4:3.5.9-0ubuntu1) to 4:3.5.10-0ubuntu1~hardy1
kommander (4:3.5.9-0ubuntu1) to 4:3.5.10-0ubuntu1~hardy1
libarts1c2a (1.5.9-0ubuntu2) to 1.5.10-0ubuntu1~hardy1
libartsc0 (1.5.9-0ubuntu2) to 1.5.10-0ubuntu1~hardy1
libcvsservice0 (4:3.5.9-0ubuntu1) to 4:3.5.10-0ubuntu1~hardy1
libnautilus-extension1 (1:2.22.3-0ubuntu2) to 1:2.22.5.1-0ubuntu1
linux-backports-modules-hardy (2.6.24.19.21) to 2.6.24.21.23
linux-backports-modules-hardy-generic (2.6.24.19.21) to 2.6.24.21.23
linux-generic (2.6.24.19.21) to 2.6.24.21.23
linux-headers-generic (2.6.24.19.21) to 2.6.24.21.23
linux-image-generic (2.6.24.19.21) to 2.6.24.21.23
linux-restricted-modules-common (2.6.24.13-19.45) to 2.6.24.14-21.51
linux-restricted-modules-generic (2.6.24.19.21) to 2.6.24.21.23
nautilus (1:2.22.3-0ubuntu2) to 1:2.22.5.1-0ubuntu1
nautilus-data (1:2.22.3-0ubuntu2) to 1:2.22.5.1-0ubuntu1
quanta (4:3.5.9-0ubuntu1) to 4:3.5.10-0ubuntu1~hardy1
quanta-data (4:3.5.9-0ubuntu1) to 4:3.5.10-0ubuntu1~hardy1
sun-java6-bin (6-06-0ubuntu1) to 6-07-3ubuntu2
sun-java6-jre (6-06-0ubuntu1) to 6-07-3ubuntu2
sun-java6-plugin (6-06-0ubuntu1) to 6-07-3ubuntu2
tzdata (2008e-1ubuntu0.8.04) to 2008g-0ubuntu0.8.04

Installed the following packages:
linux-backports-modules-2.6.24-21-generic (2.6.24-21.27)
linux-headers-2.6.24-21 (2.6.24-21.42)
linux-headers-2.6.24-21-generic (2.6.24-21.42)
linux-image-2.6.24-21-generic (2.6.24-21.42)
linux-restricted-modules-2.6.24-21-generic (2.6.24.14-21.51)
linux-ubuntu-modules-2.6.24-21-generic (2.6.24-21.32)
[/FONT][/COLOR]

I have followed the guide here
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
in an attempt to fix the problem.  I have tried compiling the hda_intel driver.  The driver was compiled successfully but I got errors again when trying to probe the module.

The errors I am getting are:

[COLOR="DarkRed"][FONT="Courier New"]$ sudo modprobe snd_hda_intel
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.24-21-generic/updates/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-21-generic/updates/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/FONT][/COLOR]

Where dmesg says:
[COLOR="DarkRed"][FONT="Courier New"]
[  155.734722] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[  155.734783] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[  155.736368] snd_hda_intel: Unknown symbol snd_hda_bus_new
[  155.736491] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[  155.736555] snd_hda_intel: Unknown symbol snd_hda_codec_new
[  155.736680] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[  155.736942] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[  155.737056] snd_hda_intel: Unknown symbol snd_hda_suspend
[  155.737165] snd_hda_intel: Unknown symbol snd_hda_codec_remove_notify_all
[  155.737292] snd_hda_intel: Unknown symbol snd_hda_resume
[  155.737390] snd_hda_intel: Unknown symbol snd_hda_build_controls
[  767.222014] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[  767.222077] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[  767.223779] snd_hda_intel: Unknown symbol snd_hda_bus_new
[  767.223903] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[  767.223966] snd_hda_intel: Unknown symbol snd_hda_codec_new
[  767.224092] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[  767.224355] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[  767.224469] snd_hda_intel: Unknown symbol snd_hda_suspend
[  767.224578] snd_hda_intel: Unknown symbol snd_hda_codec_remove_notify_all
[  767.224706] snd_hda_intel: Unknown symbol snd_hda_resume
[  767.224804] snd_hda_intel: Unknown symbol snd_hda_build_controls
[/FONT][/COLOR]

Plus..

[COLOR="DarkRed"][FONT="Courier New"]~$ aplay -l
aplay: device_list:205: no soundcards found...[/FONT][/COLOR]

and...

[COLOR="DarkRed"][FONT="Courier New"]$ sudo lspci -v
[/FONT][/COLOR]

contains 

[COLOR="DarkRed"][FONT="Courier New"]00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Unknown device 022f
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0[/FONT][/COLOR]


I'm running ubuntu 8.04.

Any help/pointers/ideas will be gratefully received.

Thanks for reading...

James.

---

### Post by anubhavrocks on 2008-10-20
Most probably it isn't a driver problem.Can you just use the original driver that came with the distro and run

 ```
gstreamer-properties
```

Here try ALSA as the default output plugin.
Also remember to un mute the audio device just in case ;)

---

### Post by squaregoldfish on 2008-10-21
It seems there's a problem with the new kernel. A lot of people (me included) have simply uninstalled the new and reverted to the previous one.

See [this thread]("http://ubuntuforums.org/showthread.php?t=948302") for details.

Steve.

---

### Post by jameselliot on 2008-10-21
> **squaregoldfish said:**
> It seems there's a problem with the new kernel. A lot of people (me included) have simply uninstalled the new and reverted to the previous one.

See [this thread]("http://ubuntuforums.org/showthread.php?t=948302") for details.

Steve.

Bingo!!  Thanks for the pointer.. I have sound again.. horrah!

I followed this guide for removing the new kernel because it updates the grub menu for you.

[http://ubuntuforums.org/showpost.php?p=5112848&postcount=3](http://ubuntuforums.org/showpost.php?p=5112848&postcount=3)

---

### Post by amplexus on 2008-10-21
I had the same problem, and Bobnutfield's posts on this thread solved it for me. 

[http://ubuntuforums.org/showthread.php?t=948553](http://ubuntuforums.org/showthread.php?t=948553)

---

