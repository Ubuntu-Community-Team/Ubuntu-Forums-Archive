---
title: "Can't make laptop sleep."
date: 2011-01-31
forum: Hardware
---

### Post by jarg on 2011-01-31
I've recently upgraded to 10.10 and sleep is now broken on my laptop (Lenovo ThinkPad w500).

If I close the lid the sleep LED blinks some then stops. If I hit fn+f4 (the sleep button) it trys to sleep then just acts like it was locked.

While searching for a solution I found a suggestion that if "sudo s2ram" made it sleep I could replace parts of a script with that. But in my case sudo s2ram didn't work, it acted like the other two time, trys to sleep then fails.

Any ideas? This is a pretty big issue because I drag my laptop through 6-8 straight hours of lectures everyday and today I have no idea how long it was on in my bag being jostled around.

---

### Post by squenson on 2011-01-31
What happens when you use the menu option System > Shut Down > Suspend?

---

### Post by jarg on 2011-01-31
Same thing, it tries, then it fails. It does show me a terminal that the bottom line is a login prompt, before that it says, checking battery state. The terminal doesn't last long enough before it goes to the gnome locked screen, screen.

---

### Post by SaintDanBert on 2011-02-02
I continue fighting troubles suspend-to-ram (*buntu says "suspend"; I say "sleep") and suspend-to-disk (*buntu says "hibernate") and the corresponding "resume" (restart from "suspend") and "thaw" (restart from "hibernate").  That said, here are things to do.
[list=1]
[*]have a swap [highlight]partition[/highlight] that is **larger than** physical ram by 1Mb(my number).
[*]unmount any file systems that are mounted USB or flash drives
[*]remove any media installed to a built-in SD, MMC, MemStick etc reader
[*]unload drivers for any USB-connected devices
[*]unload drivers for other devices (mostly older wireless and video) with known issues with suspending or resuming.
[/list]
... whew! There are ways to do much of this automatically when you request sleep or hibernate.

"Hibernate" saves the system state and then does a real shutdown power off.

"Sleep" saves system state and idles everything leaving power on
and often some LED (new moon?) as an indicator.

For these reasons, it is easier to sort out "sleep" and "resume" than it is "hibernate" and "thaw".  (I'm still fighting "thaw" if anyone wants to jump in.)

Bonne chance,
~~~ 0;-Dan

---

### Post by jarg on 2011-02-02
> **SaintDanBert said:**
> [list=1]
[*]have a swap [highlight]partition[/highlight] that is **larger than** physical ram by 1Mb(my number).
[*]unmount any file systems that are mounted USB or flash drives
[*]remove any media installed to a built-in SD, MMC, MemStick etc reader
[*]unload drivers for any USB-connected devices
[*]unload drivers for other devices (mostly older wireless and video) with known issues with suspending or resuming.
[/list]

[list]
[*]Swap = 5.6 GiB, Memory = 3.8 GiB.
[*]I unplug everything first and it still won't sleep.
[*]I unplug my usb dongled mouse first and it still won't sleep.
[*]Only thing I can think about is the built in trackpoint and touchpad (disabled normally).
[*]I don't believe any of my hardware is old (the computer is 2 years old) and I have had sleep working on previous Ubuntu installs on this same computer.
[/list]

BTW, hibernate doesn't work either, it flashes to a terminal that says "snapshotting system" or something like that (too fast to read clearly) and then goes to a locked screen.

---

### Post by SaintDanBert on 2011-02-03
> **jarg said:**
> [list]
[*]Swap = 5.6 GiB, Memory = 3.8 GiB.
[*]I unplug everything first and it still won't sleep.
[*]I unplug my usb dongled mouse first and it still won't sleep.
[*]Only thing I can think about is the built in trackpoint and touchpad (disabled normally).
[*]I don't believe any of my hardware is old (the computer is 2 years old) and I have had sleep working on previous Ubuntu installs on this same computer.
[/list]

BTW, hibernate doesn't work either, it flashes to a terminal that says "snapshotting system" or something like that (too fast to read clearly) and then goes to a locked screen.

Again, "hibernate" is more troublesome than "sleep" because you must restart after a power-off that resets the hardware.

You likely have hardware whose driver is a culprit. You need to unload the modules for that hardware during "suspend-to" processing. Do it manually to see if it helps then configure the automatic unload.

~~~ 0;-Dan

---

### Post by jarg on 2011-02-03
```

$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
rfcomm                 33811  4 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190647  2 vboxnetadp,vboxnetflt
parport_pc             26378  0 
ppdev                   5556  0 
joydev                  8767  0 
snd_hda_codec_conexant    30003  1 
arc4                    1165  2 
snd_hda_intel          22267  4 
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  3 snd_hda_intel,snd_hda_codec
thinkpad_acpi          67659  0 
iwlagn                179815  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
pcmcia                 36037  0 
iwlcore               127479  1 iwlagn
i915                  295915  4 
psmouse                59033  0 
mac80211              231959  2 iwlagn,iwlcore
r852                    9600  0 
sm_common               3285  1 r852
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           21710  0 
pcmcia_rsrc            11142  1 yenta_socket
drm_kms_helper         30200  1 i915
snd                    49038  17 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   168764  4 i915,drm_kms_helper
usbhid                 36978  0 
nand                   34905  2 r852,sm_common
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit            5168  1 i915
lp                      7342  0 
nand_ids                2903  1 nand
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
hid                    67742  1 usbhid
video                  18712  1 i915
nvram                   6342  1 thinkpad_acpi
btusb                  11001  2 
uvcvideo               55911  0 
nand_ecc                3938  1 nand
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
parport                31492  3 parport_pc,ppdev,lp
videodev               43098  1 uvcvideo
mtd                    18877  2 sm_common,nand
v4l1_compat            13359  2 uvcvideo,videodev
cfg80211              144694  3 iwlagn,iwlcore,mac80211
tpm_tis                 7658  0 
tpm                    13741  1 tpm_tis
intel_agp              26926  2 i915
tpm_bios                5310  1 tpm
agpgart                32075  2 drm,intel_agp
output                  1883  1 video
firewire_ohci          21554  0 
ahci                   19198  2 
sdhci_pci               6339  0 
sdhci                  15954  1 sdhci_pci
firewire_core          46675  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
led_class               2633  2 thinkpad_acpi,sdhci
e1000e                133436  0 
libahci                21792  1 ahci

```

Any suggestions on what could be the problem one, or how to find out?

---

### Post by jarg on 2011-02-06
Bump.

Any suggestions?

---

### Post by jarg on 2011-02-07
After some more digging I found an obscure bug on launchpad ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627275](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627275)) with a solution.

Running
```

sudo rmmod tpm_tis

```
allows me to sleep.

Now I am wondering, what is tpm_tis and is it necessary to have loaded to begin with? Or can I safely blacklist it in "/etc/modprobe.d/blacklist.conf"?

---

### Post by SaintDanBert on 2011-02-11
add this module into **/etc/pm/config.d/unload_modules.sh**.
When you request susupend-to-*, power-manager will automatically remove that module on the way down.  On restart, if some part of your hardware wants that module, it gets reloaded for you.

Create the file with any text editor and make it executable.
You will need root permissions to add it into /etc/pm tree.
My file looks like this:
```

[highlight]#!/bin/bash[/highlight]
#++
#  TITLE:  unload_modules.sh
#
#  DESCRIPTION:
#  [per KB #2543] Sometimes, certain modules fail to reload properly on
#  suspend or hibernate.
#  
#  Common ones are wireless modules such as 'ath9k.' To have power
#  management remove these on suspend, use the SUSPEND_MODULES settings
#  in /etc/pm/config.d/unload_modules with each module to unload
#  separate with a space (see KB #2375, "Editing files as the super user").
#
#  For example:
#       SUSPEND_MODULES="kvm ath9k"
#
#  This will make power-management unload the 'kvm' and 'ath9k' modules
#  on suspend or hibernate and it will reinsert the modules back
#  into the kernel on resume.
#
#  "The files in /etc/pm/config.d/* are evaluated in C sort order.  
#  These files can be provided by individual packages outside of
#  pm-utils, and contain globally available configuration settings
#  for pm-utils and the [various] hooks."
#
#  PROGRAMMER NOTES:
#  23-DEC-2010/sta ... ??? NEED_CLOCK_SYNC seems to abort "resume"
#  09-DEC-2010/sta ... refer to /usr/lib/pm-utils/defaults for details
#  09-DEC-2010/sta ... refer to /usr/share/doc/pm-utils/* for background
#  09-DEC-2010/sta ... created per Landscape KnowledgeBase #2543 
#--

#
#=== which modules do we unload?
#..... not exported so these settings must be "sourced"
[highlight]SUSPEND_MODULES="usb_storage iwlagn"[/highlight]

# EOF -- unload_modules.sh

```
The highlighted lines are the working parts.

~~~ 0;-Dan

---

