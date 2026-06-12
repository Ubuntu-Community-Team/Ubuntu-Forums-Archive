---
title: "after suspend GRUB fails"
date: 2012-01-10
forum: Hardware
---

### Post by p3tris on 2012-01-10
Hi,

I installed ubuntu 11.10 on my new eeepc 1215B. Everything works fine except the suspend. When I suspend, my netbook never wakes up. At some point I'm forced to shut if by force. After that, grub is gone: After the bios splash all I get is a blinking cursor. I can fix this by using a live usb and boot-repair.

It happened 3 times consecutively.

The log from last try...

```
Initial commandline parameters: 
Wed Jan 11 00:37:41 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux p3tris-eeepc 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
joydev                 17693  0 
eeepc_wmi              12826  0 
asus_wmi               20035  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
arc4                   12529  2 
ath9k                 127538  0 
mac80211              462092  1 ath9k
psmouse                73882  0 
snd_hda_codec_realtek   330769  1 
serio_raw              13166  0 
k10temp                13166  0 
ath9k_common           13839  1 ath9k
sp5100_tco             13791  0 
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
snd_hda_codec_hdmi     32040  1 
i2c_piix4              13301  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
cfg80211              199587  3 ath9k,mac80211,ath
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                3101156  103 
snd                    68266  14 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17540  1 
video                  19412  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  1 asus_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
atl1c                  41643  0 
libahci                26861  1 ahci
             total       used       free     shared    buffers     cached
Mem:       1648984    1586192      62792          0       3888     146636
-/+ buffers/cache:    1435668     213316
Swap:      2440188      37124    2403064

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Jan 11 00:38:07 CET 2012: performing suspend
```

---

### Post by bluexrider on 2012-01-10
Take a look [HERE]("http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html")

Fix for laptops suspend and hibernation problems

---

### Post by p3tris on 2012-01-11
hi; thanks for the quick answer. s2disk works fine! the s2ram no...

I get:
p3tris@p3tris-eeepc:~$ sudo s2ram
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "ASUSTeK Computer INC."
    sys_product  = "1215B"
    sys_version  = "x.x"
    bios_version = "0503"

---

### Post by Sidius on 2012-01-16
> **p3tris said:**
> hi; thanks for the quick answer. s2disk works fine! the s2ram no...

I get:
p3tris@p3tris-eeepc:~$ sudo s2ram
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "ASUSTeK Computer INC."
    sys_product  = "1215B"
    sys_version  = "x.x"
    bios_version = "0503"
You should add -f option, so the final command will look like:

sudo s2ram -f

---

### Post by p3tris on 2012-01-16
Hi, thanks for the answer. I tried almost everything out there. Nothing works.. I guess I'll wait for the next ubuntu version to see if things get better.

I tried all suggestion out there... This one worked better -> [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug) but still with bugs. It goes to standby and resume fine, but, if I reboot I don't get grub. Just a black screen. To start I need to remove and re-insert the battery. Then it boots fine.

All the rest didn't work...

---

### Post by Sidius on 2012-01-16
> **p3tris said:**
> Hi, thanks for the answer. I tried almost everything out there. Nothing works.. I guess I'll wait for the next ubuntu version to see if things get better.

I tried all suggestion out there... This one worked better -> [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug) but still with bugs. It goes to standby and resume fine, but, if I reboot I don't get grub. Just a black screen. To start I need to remove and re-insert the battery. Then it boots fine.

All the rest didn't work...
Have you used script from your link without any changes? If so, could you post the result of this command:

ls /sys/bus/pci/drivers


Thanks in advance.

---

### Post by p3tris on 2012-01-16
sorry for the delay. Didn't have my netbook with me:

p3tris@p3tris-eeepc:~$ ls /sys/bus/pci/drivers
agpgart-intel  ahci	   ata_generic	ath9k  ehci_hcd   HDA Intel  ioapic   langwell_gpio  parport_pc  pata_sis  pdc_adma	serial
agpgart-via    asiliantfb  ata_piix	atl1c  fglrx_pci  imsttfb    k10temp  ohci_hcd	     pata_acpi	 pcieport  piix4_smbus	uhci_hcd

---

### Post by rfugger on 2012-07-25
If you remove the power and battery for a few seconds, you will be able to reboot just fine.

[http://ubuntuforums.org/showthread.php?t=1791456](http://ubuntuforums.org/showthread.php?t=1791456)
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=asus+1215b+suspend](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=asus+1215b+suspend)

---

### Post by p3tris on 2012-07-26
> **rfugger said:**
> If you remove the power and battery for a few seconds, you will be able to reboot just fine.

[http://ubuntuforums.org/showthread.php?t=1791456](http://ubuntuforums.org/showthread.php?t=1791456)
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=asus+1215b+suspend](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=asus+1215b+suspend)

Yeap, I figured that out... I had an old phone that was getting stuck and I had to do that, I remembered the old times :p

Anyway, it's strange because after all this time, suspend still doesn't work properly..

---

