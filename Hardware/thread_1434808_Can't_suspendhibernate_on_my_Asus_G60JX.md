---
title: "Can't suspend/hibernate on my Asus G60JX"
date: 2010-03-20
forum: Hardware
---

### Post by CHUCKYCHUCK on 2010-03-20
Hi !

I've just bought a new laptop, an Asus G60JX-JX040V :

Intel Core i5 430M
4 GB RAM
Nvidia GTS 360M

It works great with Ubuntu, except that i can't suspend or hibernate.
For suspending : the screen becomes black, the hard driver powers off, but the laptop doesn't power off : there is a blinking white dash on a black screen ...
Then i'm forced to power off by pushing the power button.

For hibernating : the computer can't power off either ..
I'm then forced to power off by pushing the power button, but during the next reboot, there is a message "waking up ..." during ubuntu's boot, but the waking up doesn't work.
Forced to reboot manually then i can boot Ubuntu ...

I don't where is the problem, i even totally uninstalled the Nvidia binary drivers, it didn't work either, so i guess it's not related to my video card.
I also deactivated the Bluetooth applet ( in Gnome ).

Here is the output in the /var/log/pm-suspend : 

for suspending :
```
Initial commandline parameters: 
Sat Mar 20 23:42:21 CET 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux chucky-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3740  2 
nls_cp437               5372  2 
vfat                   10716  2 
fat                    51452  1 vfat
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
snd_hda_codec_realtek   203328  1 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
iwlagn                109084  0 
iwlcore               112796  1 iwlagn
snd_seq_midi            6464  0 
mac80211              181140  2 iwlagn,iwlcore
iptable_filter          3100  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ip_tables              11692  1 iptable_filter
uvcvideo               59080  0 
x_tables               16544  1 ip_tables
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 10240  0 
btusb                  11856  2 
nvidia               9586440  40 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0 
serio_raw               5280  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
cfg80211               93052  3 iwlagn,iwlcore,mac80211
atl1c                  30880  0 
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
asus_laptop            17400  0 
led_class               4096  3 iwlcore,sdhci,asus_laptop
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
usb_storage            52768  5 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
intel_agp              27676  0 
agpgart                34988  2 nvidia,intel_agp
video                  19380  0 
output                  2780  1 video
             total       used       free     shared    buffers     cached
Mem:       3603748     701524    2902224          0      51868     299968
-/+ buffers/cache:     349688    3254060
Swap:      9767480          0    9767480
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/etc/pm/sleep.d/10_grub-common suspend suspend: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Sat Mar 20 23:42:24 CET 2010: performing suspend
```

for hibernating :

```
Initial commandline parameters: 
Sat Mar 20 23:13:06 CET 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux chucky-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3740  2 
nls_cp437               5372  2 
vfat                   10716  2 
fat                    51452  1 vfat
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
joydev                 10240  0 
snd_hda_codec_realtek   203328  1 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
iwlagn                109084  0 
snd_mixer_oss          16028  1 snd_pcm_oss
iwlcore               112796  1 iwlagn
mac80211              181140  2 iwlagn,iwlcore
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
uvcvideo               59080  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
iptable_filter          3100  0 
snd_timer              22276  2 snd_pcm,snd_seq
btusb                  11856  2 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
cfg80211               93052  3 iwlagn,iwlcore,mac80211
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
psmouse                56500  0 
serio_raw               5280  0 
atl1c                  30880  0 
asus_laptop            17400  0 
led_class               4096  3 iwlcore,sdhci,asus_laptop
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
ohci1394               29900  0 
usb_storage            52768  5 
ieee1394               86596  1 ohci1394
intel_agp              27676  0 
video                  19380  0 
output                  2780  1 video
agpgart                34988  1 intel_agp
             total       used       free     shared    buffers     cached
Mem:       3603748     414348    3189400          0      51188     178724
-/+ buffers/cache:     184436    3419312
Swap:      9767480          0    9767480
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Sat Mar 20 23:13:07 CET 2010: performing hibernate
```

i can't see anything suspicious, so i really don't know where to look to find a solution ..

Thanks

---

### Post by Djalmahal on 2010-03-22
Hi,

I tried to boot this computer in a BestBuy with Ubuntu 9.10 from a USB Stick, suspending worked, hibernating obviously not as (I think) there wasn't enough space on the USB Stick to save he RAM. Sorry that I can't tell you more, maybe you want to see if you can just make it work from a USB Stick, so as to ell you it's technically possibly.

Andreas

---

### Post by mnjm97 on 2010-04-22
I have the same notebook running 10.04 b2

same results...

both suspend and hibernate seem to freeze just before powerdown.

any progress in this???

none of the fixes I found work for this notebook.

---

### Post by CHUCKYCHUCK on 2010-04-22
no i haven't found anything since ..

---

### Post by greeble on 2010-05-07
I too have the same laptop running 9.10 and can't suspend. I tried updating to the newest BIOS and that didn't help. Has there been any developments?

---

### Post by John Dias on 2010-05-10
Hi folks,
I have an ASUS N71 and had the same problem with the default configuration. The issue is with the USB 2.0 builtin controller (ehci). You can fix by unloading ehci from kernel before suspend/hibernate. 
Take a look in this tread and see what happens:
[http://ubuntuforums.org/showthread.php?p=9261807](http://ubuntuforums.org/showthread.php?p=9261807)

P.S.:
1. You don't have to bother about xhci, since you dont have this module loaded. 
2. Don't forget to make the script executable:
sudo chmod +x "/etc/pm/sleep.d/20_custom-ehci_hcd"

---

### Post by greeble on 2010-05-13
> **John Dias said:**
> Hi folks,
I have an ASUS N71 and had the same problem with the default configuration. The issue is with the USB 2.0 builtin controller (ehci). You can fix by unloading ehci from kernel before suspend/hibernate. 
Take a look in this tread and see what happens:
[http://ubuntuforums.org/showthread.php?p=9261807](http://ubuntuforums.org/showthread.php?p=9261807)

P.S.:
1. You don't have to bother about xhci, since you dont have this module loaded. 
2. Don't forget to make the script executable:
sudo chmod +x "/etc/pm/sleep.d/20_custom-ehci_hcd"

Hey it worked! Thanks man! Only strange issue is that the keyboard backlight seems to flash while its suspending but thats a small thing. (Might look into how to disable it if it seems to drain the battery too much)

---

