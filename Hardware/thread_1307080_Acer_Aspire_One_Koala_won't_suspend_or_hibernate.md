---
title: "Acer Aspire One Koala won't suspend or hibernate"
date: 2009-10-30
forum: Hardware
---

### Post by chris.willis on 2009-10-30
Hi there, I recently did a fresh install of Koala 9.10 and found my Acer Aspire One doesn't suspend or go into hibernation when I shut the lid, and when I click the option in my log out ... restart ... shut down menu in the top right corner. It worked in 9.04. Now, instead of suspending or hibernating, the screen fades to a dark grey, and won't resume - I have to turn the computer off. Any ideas what I could do, as I would like it to suspend when I close the lid.

---

### Post by samstag on 2009-10-31
same here! In addition the battery/wall plug detection does not work in gnome power monitor. Otherwise the Koala release gives great overall responsiveness and graphics performance. Audio is great too! Hope the Ubuntu team figures those 2 not unimportant bugs out

---

### Post by kevinsickles on 2009-10-31
Ditto same problem

---

### Post by Toddy on 2009-10-31
I have an AOA 150 and closing the lid seems to put me in suspend. So does Fn-F4. This is on a fresh install of 9.10.

---

### Post by jeffster1970 on 2009-10-31
Same here - can't suspend or get a battery reading without a restart (while not having it plugged in)

I had the RC of 9.10 and had no issues - they occured with the final release.

---

### Post by Richard Mathie on 2009-11-03
same here, Acer One L110 Netbook remix 9.10 karmic,
suspend with power button results in frozen screen
shutting lid (should result in suspend) results in greayed screen, i.e. not off
power manager dosent detect removal of ac power and continues to report 100% battery till battery dead :lolflag: 

a briefe view of the log messages showes nothing

syslog:
```
Nov  3 21:11:15 honolulu acerfand: Set fan Off
Nov  3 21:11:15 honolulu kernel: [ 1338.076143] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] 20090521 evregion-424
Nov  3 21:11:15 honolulu kernel: [ 1338.076190] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.BAT1._BST] (Node f7012b70), AE_TIME
Nov  3 21:11:15 honolulu kernel: [ 1338.076297] ACPI Exception: AE_TIME, Evaluating _BST 20090521 battery-385
Nov  3 21:11:36 honolulu anacron[4523]: Anacron 2.3 started on 2009-11-03
Nov  3 21:11:36 honolulu anacron[4523]: Normal exit (0 jobs run)
Nov  3 21:11:36 honolulu kernel: [ 1358.379993] CPU0 attaching NULL sched-domain.
Nov  3 21:11:36 honolulu kernel: [ 1358.380005] CPU1 attaching NULL sched-domain.
Nov  3 21:11:36 honolulu kernel: [ 1358.400296] CPU0 attaching sched-domain:
Nov  3 21:11:36 honolulu kernel: [ 1358.400313]  domain 0: span 0-1 level SIBLING
Nov  3 21:11:36 honolulu kernel: [ 1358.400326]   groups: 0 1
Nov  3 21:11:36 honolulu kernel: [ 1358.400348] CPU1 attaching sched-domain:
Nov  3 21:11:36 honolulu kernel: [ 1358.400358]  domain 0: span 0-1 level SIBLING
Nov  3 21:11:36 honolulu kernel: [ 1358.400370]   groups: 1 0
Nov  3 21:11:36 honolulu NetworkManager: <info>  Sleeping...
Nov  3 21:11:36 honolulu NetworkManager: <info>  (eth0): now unmanaged
Nov  3 21:11:36 honolulu NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
Nov  3 21:11:36 honolulu NetworkManager: <info>  (eth0): cleaning up...
Nov  3 21:11:36 honolulu NetworkManager: <info>  (eth0): taking down device.
Nov  3 21:11:36 honolulu NetworkManager: <info>  (wlan0): now unmanaged
Nov  3 21:11:36 honolulu NetworkManager: <info>  (wlan0): device state change: 3 -> 1 (reason 37)
Nov  3 21:11:36 honolulu NetworkManager: <info>  (wlan0): cleaning up...
Nov  3 21:11:36 honolulu NetworkManager: <info>  (wlan0): taking down device.
```

its not always the netmanager thats last to speak, is there perhaps  a script somewhere which exicutes the final suspend comand and isnt fully exicuting?

other people are also experiencing this:
[http://ubuntuforums.org/showthread.php?t=1309440](http://ubuntuforums.org/showthread.php?t=1309440)
[http://ubuntuforums.org/showthread.php?t=1312918](http://ubuntuforums.org/showthread.php?t=1312918)
[http://ubuntuforums.org/showthread.php?t=1306521](http://ubuntuforums.org/showthread.php?t=1306521)

also the pm-suspend.log, thinks its done its job....
```

Initial commandline parameters: 
Tue Nov  3 21:11:35 GMT 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-none 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux honolulu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10272  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
arc4                    1660  2 
snd_rawmidi            22208  1 snd_seq_midi
ecb                     2524  2 
acerhdf                 8116  0 
mmc_block              10592  2 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                56180  0 
serio_raw               5280  0 
ath5k                 124260  0 
mac80211              181236  1 ath5k
ath                     8060  1 ath5k
lp                      8964  0 
sdhci_pci               7100  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci                  17472  1 sdhci_pci
cfg80211               93052  3 ath5k,mac80211,ath
soundcore               7264  1 snd
jmb38x_ms               9600  0 
memstick               10072  1 jmb38x_ms
led_class               4096  2 ath5k,sdhci
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
r8169                  32064  0 
mii                     5212  1 r8169
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
             total       used       free     shared    buffers     cached
Mem:       1532380     625432     906948          0     266932     190632
-/+ buffers/cache:     167868    1364512
Swap:            0          0          0
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
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Tue Nov  3 21:11:36 GMT 2009: performing suspend

```

---

### Post by Richard Mathie on 2009-11-03
i can now confirm that unmounting the right hand sd media card befor suspending/opening closing lid, results in successful suspend. the power manager still wont recognise when i pull out ac power though

```

sudo umount /dev/mmcblk0p1

```

---

### Post by Richard Mathie on 2009-11-04
apparently ther is a fix
[https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/424877](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/424877)

```

/etc/default/grub

```

then edit the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp.pciehp_force=1"

```
then
```

update-grub

```
```

sudo apt-get install linux-backports-modules-karmic

```

however i cant get it to work

and acording to
[https://help.ubuntu.com/community/AspireOne/Ubuntu9.10](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10)
> 
Suspend and hibernate seem both to be working without a hiccough. [Edit: (28/09) a recent upgrade seems to have broken suspend/resume with a flurry of bug-reports and me-toos on launchpad.]

---

### Post by Richard Mathie on 2009-11-04
I did this as a temporary fix. added a hook in /ect/pm/sleep.d/11_mmc_mounts

```

#!/bin/sh
# mmcard must be mounted or unmounted before suspend | hibinate
case "$1" in
 hibernate|suspend)
  umount /dev/mmcblk0p1
  ;;
 thaw|resume)
  mount /dev/mmcblk0p1
  ;;
 *) exit 0
  ;;
esac

```

make it exicutable
```

sudo chmod +x /ect/pm/sleep.d/11_mmc_mounts

```

(where /dev/mmc*) is the mount point of your sd card

end of problem, though perhaps i should be smarter about running through mm cards, and cards which wont unmount

---

### Post by chris.willis on 2009-11-06
I reinstalled, same issue. Although I did notice on the LiveCD (LiveUSB) it goes into suspend mode. After installing, same problem. Will wait for the clever people at Ubuntu.

---

### Post by TheTilde on 2009-11-06
A11OL prout user here. :-)
same problem :-(

---

### Post by pjalegria on 2009-11-06
110L, after suspend/resume i cant open anything...

---

### Post by jawaho on 2009-11-07
Same problem with my aa1 110l. 
Hopefully this issue will be handled soon! Until then I'm considering to restore my jaunty backup. Karmic is so buggy, it's a shame! Empathy freezes when clicking on Contacts Menu, Webcam isn't recognized, OpenOffice Writer crashes spontaneously ... I'm afraid of what's next!

---

### Post by chris.willis on 2009-11-07
I don't have that many problems ... just hibernate/suspend, although the radio switch to turn wireless on/off is annoying as I have to reboot every time I use it.

---

### Post by DaiLaughing on 2009-11-13
For me 9.10 suspend is fine until I put a flash card into the left slot (haven't tried the right-hand one).  Without card the laptop suspends.  With it there is some "disk" activity then everything locks and will not free up when the lid opens.  The laptop also gets very hot and uses battery quickly.

I have repeated this twice with the same results.  System is up-to-date.

---

### Post by asphixmx on 2009-11-22
Problem solved, same as Richard. You have to make a script that umounts the left SD card, then it suspends/hibernates normally. Place this script in /etc/pm/sleep.d/

For expample, I did:

sudo gedit /etc/pm/sleep.d/umount_sd

Then I copied this:

#!/bin/sh
# mmcard must be mounted or unmounted before suspend | hibernate
case "$1" in
 hibernate|suspend)
  umount /dev/mmcblk0p1
  ;;
 thaw|resume)
  mount /dev/mmcblk0p1
  ;;
 *) exit 0
  ;;
esac

Save & exit. Then made the script executable:

sudo chmod +x /etc/pm/sleep.d/umount_sd

Done. When the AA1 goes suspend or hibernate, the script is executed, umount the left sd then continues with the suspend or hibernate task.

---

### Post by pjalegria on 2009-11-22
Not working... when i do SUSPEND it goes to screensaver...

---

### Post by blackest_knight on 2009-11-29
It might be worth updating the bios version 3309 improves the card support I think it may change the device id also.

I got my first successful suspend after flashing.

---

### Post by pwebster25 on 2009-12-20
I just ran an update on my AAO D150 from Jaunty. My problem is similar but different.  When we disconnect power cord it shows a battery monitor in the tray and then immediately goes to sleep.  We have changed the settings in the powermanager but to no avail.  It won't stay awake on battery power.  When we power it back up on battery power it wakes up and then immediately goes back to sleep.

---

### Post by libssd on 2010-05-20
Here's a solution for the D150: 

[http://ubuntuforums.org/showthread.php?t=1316780&highlight=d150]("http://ubuntuforums.org/showthread.php?t=1316780&highlight=d150")

---

### Post by Richard Mathie on 2012-01-07
Here is an update for anyone still running into these problems.

In the latest version of Ubuntu (or any other flavour of Linux) Circa kernel 2.6.36 , the pm utils workaround from before should still work, however you will find it will fail if you are using the SD card as /home or any other root file system. Since 2.6.36 there has been a kernel boot option which allows you to set the MMC as non removable, prior to that you had to compile your kernel with the CONFIG_MMC_UNSAFE_RESUME = Y which was APITA. 

basically with your favourite editor
```
sudo vim /etc/defaults/grub
```
and modify the line starting GRUB_CMDLINE_LINUX_DEFAULT = 
and add the option mmc_core.removable=0
```
GRUB_CMDLINE_LINUX_DEFAULT="noop quiet splash mmc_core.removable=0"
```
then update the grub
```
sudo update-grub
```

and remove the hook from the /usr/lib/pm-utils/sleep.d/010_unmountSD.sh or whatever it was you put there (be sure to back it up). If you left it there the machine would still try to unmount home fail, and so fail to suspend. 

A better option would be for unmountSD.sh to check if the mmc's were being treated as non removable (cat /sys/module/mmc_core/perameters/removable) and if they were  being treated as non removable only unmount devises not listed in the fstab.

when I get round to that I will post the new script...

Ric

p.s. when the SD cards are being treated as non removable DO NOT remove the SD when suspended, and don't do anything silly like swap it out for a different card.

---

