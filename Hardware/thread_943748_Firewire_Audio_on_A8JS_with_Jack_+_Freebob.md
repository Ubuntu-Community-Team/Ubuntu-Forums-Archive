---
title: "Firewire Audio on A8JS with Jack + Freebob"
date: 2008-10-10
forum: Hardware
---

### Post by martron88 on 2008-10-10
I've owned an Edirol FA-101 audio interface for 2 years now and had never really been successful in getting to work on various versions of linux.  Usually too unstable with lots of XRuns.  So, I finally set my mind to getting this working and I've made some, but not complete progress.

There is 1 primary problem with my set up (which I found out in this process).  The Ricoh chipset for firewire in my A8JS just isn't suitable for low-latency audio recording.  

I've been doing this debugging using Ubuntu Studio Intrepid Beta amd64 with the real-time kernel.

So, after much reading online.  It was suggested that disabling the dvd drive (in windows) improves the firewire performance.  So, I set out to find how to do that on linux.

I used ```
lspci -v -t
``` to find the drive.  Then scanned through lsmod to find the cd-driver which is apparently "sr_mod".

So, I made a shellscript called jack-start.sh and ran ```
chmod 755 jack-start.sh
``` to make it executable.

```

#!/bin/bash
#jack-start.sh
artsshell -q terminate 
sudo modprobe -r sr_mod

```

I copied the artsshell command from qjackctl's startup commands.  "modprobe -r sr_mod" removes the dvd-rom driver from the modules.  You can re-activate by running ```
sudo modprobe sr_mod
```.

I run this script in terminal so that I can type in my sudo password.  Then I start jackd through qjackctl.

Removing the DVD drive did greatly enhance jack's ability to run without XRuns, but they were still occuring and it still felt unstable.  So after more reading I realized that the SD card reader is also a Ricoh device and could be a culprit.  So, I popped out the SD card.  This also improved things a great deal.  For a while I fiddled around trying to disable the SD device outright just like I did with the DVD-rom but I couldn't find anything in lsmod other than ricoh_mmc which didn't do much when I removed it.

So, now I have jack running pretty well.  1 Xrun over 10 minutes while playing through Mixxx.  This still isn't good enough but it's way better than when I started.  The main problem, however is that after an indeterminate time (within 15 minutes), my laptop will lock up and freeze and I'll have to hard reset.

More troubleshooting on that.  Running ```
cat /proc/interrupts
``` I saw that the ieee1394 (firewire) chip is on the same irq as a number of usb ports.  So, I unplugged all unnecessary usb devices and jack again seems to be just a little bit more stable.  I'm not getting hard freezes anymore.

What I do get after running for 5 to 15 minutes (still testing with Mixxx) is jack just crashes for some reason.  It's a soft crash and I can start jack right back up again.  At least I'm not losing all my info and hard resetting anymore.  But, like I said, definitely not stable enough for real use yet.

I feel like I'm so close to making this work within reasonable bounds.  Does anyone have any tips?  Maybe ways to disable the other ricoh devices without disabling the firewire?  BIOS is not an option.

Here's the latest output from my last jackd testing session (I did nothing to spur the 'shutdown notification'):

```
15:36:06.827 JACK is starting...
15:36:06.828 /usr/bin/jackd -R -p128 -dfreebob -r48000 -p1024 -n3 -D
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
15:36:06.853 JACK was started with PID=20902.
loading driver ..
SSE2 detected
Freebob using Firewire port 0, node -1
15:36:07.777 ALSA connection graph change.
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
15:36:07.856 ALSA connection change.
15:36:11.879 Server configuration saved to "/home/martron/.jackdrc".
15:36:11.882 Statistics reset.
15:36:11.912 Client activated.
15:36:11.918 JACK connection change.
15:36:11.924 JACK connection graph change.
SSE2 detected
15:36:19.609 JACK connection graph change.
15:36:21.587 ALSA connection graph change.
15:36:21.738 ALSA connection change.
15:36:28.130 JACK connection graph change.
15:36:28.150 JACK connection change.
LibFreeBoB ERR: Dropped packets on connection 1
15:37:00.262 XRUN callback (1).
**15:43:16.370 Shutdown notification.**
15:43:16.377 JACK is stopping...
**15:43:16.390 JACK is being forced...**
**cannot complete execution of the processing graph (Success)**
zombified - calling shutdown handler
15:43:16.393 ALSA connection graph change.
15:43:16.393 JACK has crashed.
15:43:16.476 ALSA connection change.
15:43:16.590 JACK was stopped successfully.
```


Thanks

---

### Post by martron88 on 2008-10-10
Here's my output of lsmod, lspci and cat /proc/interrupts for anyone interested.


```
$lsmod
dv1394                 28016  0 
vfat                   20992  0 
fat                    62896  1 vfat
af_packet              28544  4 
binfmt_misc            18828  1 
bridge                 65448  0 
bnep                   22656  2 
rfcomm                 50592  4 
l2cap                  31360  16 bnep,rfcomm
ppdev                  16776  0 
acpi_cpufreq           16656  1 
cpufreq_userspace      13444  0 
cpufreq_powersave      10496  0 
cpufreq_conservative    16520  0 
cpufreq_ondemand       16656  1 
cpufreq_stats          14912  0 
freq_table             13952  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    22288  0 
sbshc                  14592  1 sbs
container              12416  0 
sbp2                   32396  0 
raw1394                35472  4 
parport_pc             43816  0 
lp                     20548  0 
parport                50316  3 ppdev,parport_pc,lp
loop                   26508  0 
ipv6                  324328  10 
usb_storage            89664  0 
libusual               31144  1 usb_storage
joydev                 20608  0 
snd_hda_intel         470328  2 
snd_pcm_oss            52352  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                97032  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11652  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
arc4                   10368  2 
snd_rawmidi            33536  1 snd_seq_midi
ecb                    11520  2 
gspca                 666192  0 
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
crypto_blkcipher       27908  1 ecb
snd_seq                66976  14 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
compat_ioctl32         18304  1 gspca
hci_usb                24732  0 
videodev               44032  2 gspca,compat_ioctl32
psmouse                51356  0 
usbhid                 39904  0 
sdhci                  25860  0 
v4l1_compat            24452  1 videodev
bluetooth              68452  6 bnep,rfcomm,l2cap,hci_usb
serio_raw              14596  0 
hid                    57280  1 usbhid
snd_timer              33672  2 snd_pcm,snd_seq
iwl3945               110324  0 
mmc_core               62320  1 sdhci
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              254208  1 iwl3945
cfg80211               37520  2 iwl3945,mac80211
snd                    79048  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               20992  0 
iTCO_vendor_support    12548  1 iTCO_wdt
soundcore              17184  1 snd
shpchp                 42656  0 
snd_page_alloc         17808  2 snd_hda_intel,snd_pcm
intel_agp              38384  0 
pci_hotplug            39736  1 shpchp
video                  28692  0 
output                 12160  1 video
battery                21128  0 
ac                     13576  0 
asus_laptop            27868  0 
led_class              13192  2 iwl3945,asus_laptop
button                 15904  0 
evdev                  19968  54 
ext3                  148112  2 
jbd                    63144  1 ext3
mbcache                17920  1 ext3
sg                     45456  0 
sd_mod                 37456  4 
ata_generic            14340  0 
pata_acpi              13568  0 
ata_piix               28932  3 
libata                193984  3 ata_generic,pata_acpi,ata_piix
scsi_mod              181528  5 sbp2,usb_storage,sg,sd_mod,libata
dock                   18640  1 libata
ohci1394               41268  3 dv1394
ieee1394              112088  4 dv1394,sbp2,raw1394,ohci1394
ehci_hcd               48140  0 
r8169                  38404  0 
uhci_hcd               33696  0 
usbcore               172056  8 usb_storage,libusual,gspca,hci_usb,usbhid,ehci_hcd,uhci_hcd
thermal                27168  0 
processor              48572  4 acpi_cpufreq,thermal
fan                    13448  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
uvesafb                37800  0 
cn                     17324  1 uvesafb

```

```
$ lspci -v -t
-[0000:00]-+-00.0  Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
           +-01.0-[0000:01]----00.0  nVidia Corporation GeForce Go 7700
           +-1b.0  Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller
           +-1c.0-[0000:02]----00.0  Intel Corporation PRO/Wireless 3945ABG Network Connection
           +-1c.2-[0000:03]----00.0  Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller
           +-1c.3-[0000:04-05]--
           +-1d.0  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller
           +-1e.0-[0000:06]--+-00.0  Ricoh Co Ltd R5C832 IEEE 1394 Controller
           |                 +-00.1  Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
           |                 +-00.2  Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter
           |                 \-00.3  Ricoh Co Ltd xD-Picture Card Controller
           +-1f.0  Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge
           \-1f.2  Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller
```


```
$ cat /proc/interrupts 
           CPU0       CPU1       
  0:        538          0    XT-PIC-XT        timer
  1:         20          0    XT-PIC-XT        i8042
  2:          0          0    XT-PIC-XT        cascade
  3:          1          0    XT-PIC-XT      
  4:      56816          0    XT-PIC-XT        HDA Intel
  5:    3108167          0    XT-PIC-XT        uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, ohci1394, mmc0
  6:     195757          0    XT-PIC-XT        uhci_hcd:usb1, ehci_hcd:usb5
  8:          1          0    XT-PIC-XT        rtc0
  9:     178527          0    XT-PIC-XT        acpi
 12:       1848          0    XT-PIC-XT        i8042
 14:      61152          0    XT-PIC-XT        ata_piix
 15:      97990          0    XT-PIC-XT        ata_piix
2298:     376148          0   PCI-MSI-edge      iwl3945
2299:          0          0   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:   36242615   38467922   Local timer interrupts
RES:    1503022    2215044   Rescheduling interrupts
CAL:        430        795   function call interrupts
TLB:       7724       8469   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
SPU:          0          0   Spurious interrupts
ERR:          0

```

---

### Post by martron88 on 2008-10-10
Adding the cpufrequency applet to gnome and setting it to 'performance' has helped out a bunch.  Ardour seems to be running quite well though I haven't tested extensively.

I get the feeling that Mixxx has been the cause of some of these crashes.  Maybe.  We'll see how long this no-Xrun deal will last. (only about 20 mins so far).

---

### Post by martron88 on 2008-10-12
Hmm... Well mixx ended up crashing yesterday so I started investigating ffado.  I went to [https://bugs.launchpad.net/gutsy-backports/+bug/246894](https://bugs.launchpad.net/gutsy-backports/+bug/246894) and installed the packages (found in hardy).  Although ffado didn't work when I tried it, freebob seems to.  I installed a new version of jack-control and jackd.

So, I've been running mixxx for half an hour now without any xruns, lockups or jack crashes.  Feels a lot better and more stable.  Let's hope this keeps up.

---

### Post by martron88 on 2008-10-12
So Mixxx has been running reliably with freebob and jack for the past three hours :)    This leads me to believe that the updated version of Jack has somehow fixed the issue I was having.  I still disable the DVD drive before running jack for added stability.

The versions I've got running now are
```

jackd, libjack0, libjack0.100.0-0: 1.8+svn2885ubuntu2
mixxx: 1.6.0~beta3-2ubuntu1
libffado0: 2.0-beta6-0ubuntu1.ppa1

```
Which I downloaded by adding the repository mentioned in [https://bugs.launchpad.net/gutsy-backports/+bug/246894](https://bugs.launchpad.net/gutsy-backports/+bug/246894)
Had to add the Hardy repository even though I'm running intrepid.  Worked fine.

This is on an Asus a8js laptop running Ubuntustudio with an Edirol FA-101.

Also, I realize that I'm just talking to myself but I would have liked to read this post when I first tried to get this working.  Also, I'll probably have to refer to it again whenever I redo my system...

---

### Post by Acksys on 2008-10-19
It's okay to talk to yourself when someone needs to hear what you have to say later!

Wondering if you have any updates on using the FA-101 with Ubuntu? The device looks great, and I'm considering purchasing one, but I want to make sure I can use it cross-platform.

---

### Post by martron88 on 2008-10-19
I used it last night to dj a house party (wanted to test this out).  It worked fine with only 1 xrun which I never actually heard.

The freebob and ffado drivers seem to be getting better for the FA-101 so it is a viable interface to use.  However, I would recommend having the Texas Instruments chipset for the firewire on your system since the Ricoh chipset really doesn't seem to cut it all that well.  Unfortunately, most laptops don't have the TI chipset.

---

