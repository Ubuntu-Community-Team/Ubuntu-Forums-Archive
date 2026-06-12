---
title: "How to hibernate?"
date: 2011-02-01
forum: Hardware
---

### Post by bilkay on 2011-02-01
I'm not asking how to get the hibernate feature to work, I'm asking how it is invoked. I can get the laptop to hibernate by the command "sudo hibernate" - which means I can only invoke it from a terminal and have to supply a password. Clicking the "Hibernate" button causes the laptop to shut down, but not hibernate - nothing showing progress of image being saved, nothing in /var/log/hibernate.log, and nothing but normal boot on restart.

This is 10.04.1 and migrated from WUBI.

---

### Post by bilkay on 2011-02-02
?

---

### Post by gordintoronto on 2011-02-02
Do you have a swap file which is larger than your RAM? That's where you hibernate to.

---

### Post by bilkay on 2011-02-03
> **gordintoronto said:**
> Do you have a swap file which is larger than your RAM? That's where you hibernate to.
As I said, I can get the laptop to hibernate by the command "sudo hibernate." I want to know what USER command is invoked when a USER clicks on "Hibernate" - or takes some action like closing the laptop lid.

The "sudo hibernate" command works as expected: I see the progress of the image being saved, then the laptop shuts down. On startup, the image is restored and all is well. The hibernate log file (/var/log/hibernate.log) shows the hibernation.

When I click on a "Hibernate" button (e.g. from Shutdown applet), the laptop shuts down with no evidence of an image being saved. The hibernate log file gets no entries, and subsequent startup doesn't restore the previous condition.

---

### Post by bilkay on 2011-02-04
?

---

### Post by bilkay on 2011-02-05
Everything I've been able to find on the net on the subject is years old and doesn't seem relevant. If someone could just tell me what they do to hibernate their laptop (e.g., close the lid, click something, etc.) and anything else they had to do, beyond getting hibernation to work, it would at least be a start.** I CAN GET MY LAPTOP TO HIBERNATE!** My problem is that a user who isn't a sudoer can't because the only way I know of to invoke hibernate is the command "sudo hibernate" from a terminal.

---

### Post by bilkay on 2011-02-05
This is what's in /var/log/pm-suspend.log after clicking the gnome "Hibernate" button in the shutdown menu. 

```
Sat Feb  5 12:02:51 EST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux Laptop 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
ath9k                 306138  0 
mac80211              205402  1 ath9k
autofs4                22715  2 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
fbcon                  35102  73 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_intelhdmi     9559  1 
snd_hda_codec_realtek   216061  1 
snd_hda_intel          20799  2 
arc4                    1153  2 
i915                  287458  3 
snd_hda_codec          87096  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5668  1 snd_hda_codec
snd_pcm_oss            34603  0 
snd_mixer_oss          13929  1 snd_pcm_oss
snd_pcm                71646  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1498  0 
snd_seq_oss            27626  0 
snd_seq_midi            4621  0 
snd_rawmidi            19141  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                48042  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              18710  2 snd_pcm,snd_seq
snd_seq_device          6052  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29329  1 i915
psmouse                63245  0 
ath                     7611  1 ath9k
snd                    56687  19 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               3978  0 
drm                   162409  4 i915,drm_kms_helper
intel_agp              24375  2 i915
cfg80211              126528  3 ath9k,mac80211,ath
led_class               2864  1 ath9k
soundcore               6620  1 snd
snd_page_alloc          7140  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67064  1 usbhid
usb_storage            39553  0 
r8169                  34108  0 
mii                     4381  1 r8169
ahci                   32200  2 
             total       used       free     shared    buffers     cached
Mem:       3027380    1904004    1123376          0     708516     735084
-/+ buffers/cache:     460404    2566976
Swap:      3145720          0    3145720
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Sat Feb  5 12:02:52 EST 2011: performing hibernate
```

When I click "Hibernate," the lock screen comes up, and then after a delay, the laptop shuts down. From the above entries, it appears as if hibernation was achieved. But on restart, it's a normal startup. Hibernating with the "sudo hibernate" command resumes the previous state as expected.

---

### Post by bcbc on 2011-02-05
What does the syslog say on the restart? Are there any PM: messages that show errors (cat /var/log/syslog | grep 'PM:'). How does this compare to sudo hibernate?

Also:
cat /etc/fstab
sudo blkid
cat /etc/initramfs-tools/conf.d/resume

machine brand/model as well?

---

### Post by bilkay on 2011-02-05
> **bcbc said:**
> What does the syslog say on the restart? Are there any PM: messages that show errors (cat /var/log/syslog | grep 'PM:'). How does this compare to sudo hibernate?

Also:
cat /etc/fstab
sudo blkid
cat /etc/initramfs-tools/conf.d/resume

machine brand/model as well?

HP G62
Thanks for replying!

This seems relevant from syslog:
```
...
Feb  5 15:00:10 Laptop kernel: [    0.388681] PM: Checking image partition UUID=e42b5082-99ef-4740-a1e1-4f45af8de261
Feb  5 15:00:10 Laptop kernel: [    0.408956] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Feb  5 15:00:10 Laptop kernel: [    0.453478] ACPI: Battery Slot [BAT0] (battery present)
Feb  5 15:00:10 Laptop kernel: [    0.659187] isapnp: No Plug & Play device found
Feb  5 15:00:10 Laptop kernel: [    0.659207] PM: Resume from disk failed.
...
```The "image partition" is actually a swap file and the file's offset is noted in:

/etc/default/grub
 /etc/uswsusp.conf
/etc/initramfs-tools/conf.d/resume

```
$ cat /etc/initramfs-tools/conf.d/resume
resume=UUID=e42b5082-99ef-4740-a1e1-4f45af8de261 resume_offset=86016
``````
$ cat /etc/uswsusp.conf
resume device = /dev/sda4
...
resume offset = 86016
``````
$ grep UUID /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=e42b5082-99ef-4740-a1e1-4f45af8de261 resume_offset=86016"
```

---

### Post by bcbc on 2011-02-05
Ah, the swap file hibernation! I remember now we talked about this one before. Sorry - I have no idea about this. Did you post a query in that howto thread and get any response? Probably there are two distinct hibernate methods and you're using the 'legacy' one.

It's great that you have it working though. Why don't you just add a launcher to your panel that runs "sudo hibernate" and keep using it that way?

---

### Post by bilkay on 2011-02-05
> **bcbc said:**
> Ah, the swap file hibernation! I remember now we talked about this one before. Sorry - I have no idea about this. Did you post a query in that howto thread and get any response? Probably there are two distinct hibernate methods and you're using the 'legacy' one.

It's great that you have it working though. Why don't you just add a launcher to your panel that runs "sudo hibernate" and keep using it that way?
Again, thanks!

I really don't like the way it is now for two reasons:

1. I'd have to give sudoer authority to everyone using it, and
2. It resumes with no password - not exactly secure.

I'd rather not have to make a partition. I've had some bad experience with gparted.

Oh, well!

---

