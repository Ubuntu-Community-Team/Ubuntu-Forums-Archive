---
title: "Suspend and Hibernate Problem"
date: 2009-05-11
forum: Hardware
---

### Post by charmsen on 2009-05-11
Like many others I have a suspend and hibernate problem. After suspending, the screen cuts to black and then I get a flashing cursor in the upper left hand corner. There is no way to get the system back without a hard reboot. 

I have a Gateway MT6705 with 2 gigs of RAM. I started using Ubuntu at 8.1 and had the problem with that version. I have now upgraded to 9.04 and still have the problem. I have tried a number of the suggested fixes with no success.  Does anyone else out there use a Gateway MT6705 and been able to solve this problem?  If so I would love to know how you fixed this. Thanks

Craig

---

### Post by Mantrasong on 2009-05-11
Does the problem occur while suspending, or while resuming. If it's while suspending, have you checked your swap?

Try running these commands
```
cat /proc/swaps
swapon -s
```

And post the output.

---

### Post by charmsen on 2009-05-13
Thanks for your input. Here is my Swap info:

Filename				Type		Size	Used	Priority
/dev/sda3                               partition	6142968	0	-1


I find it very strange that the "used" always come up "0". Is there anyway to test if the system is actually using the swap drive?

---

### Post by Mantrasong on 2009-05-20
Sorry for taking so long to respond. The 0 used probably means that your computer never needs to use swap, as opposed to ram. How much ram do you have installed?

Also, could you go through [this post](http://ubuntuforums.org/showpost.php?p=7242180&postcount=4) and gather the information suggested there?

---

### Post by DLG102282 on 2009-05-20
WHat version of Ubuntu are you running?

---

### Post by charmsen on 2009-05-23
I am running Ubuntu 9.04 and I have 2 gig of RAM.

---

### Post by sean_worker on 2009-05-26
I believe I have this problem too, on a Thinkpad x61.

```
$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	4192892	2592	-1
$ uname -a
Linux ralfe 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009 i686 GNU/Linux
$
```

Suspend works fine, and while hibernate appears to succeed, when I start the machine, it does not restore.
In both cases I see a message about "deleting an empty queue" when entering the state.  The message is still there, briefly, when returning from suspend.
(It doesn't work with the generic kernel either.)

---

### Post by sean_worker on 2009-05-27
actually, I think the message is more like:
"killing requests to empty queue"

---

### Post by jbslaw on 2009-06-06
I have the same problem.  My Toshiba A205 suspends to a blank screen with a blinking white line cursor in the upper left portion of the screen.  It is locked up hard, requiring the power button to be held 5 seconds to force the power off. 

Swap is on.  It isn't being used.

The logs all look normal.  The pm-suspend log looks fine:

Initial commandline parameters: --quirk-s3-bios
--quirk-s3-mode
Sat Jun  6 10:37:11 CDT 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux gustav 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
arc4                    9856  2 
ecb                    10752  2 
snd_hda_intel         435636  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
rtl8187                53376  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
mac80211              217208  1 rtl8187
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6           10240  1 rtl8187
psmouse                61972  0 
snd                    62628  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              34108  1 
iTCO_wdt               19108  0 
cfg80211               38032  2 rtl8187,mac80211
serio_raw              13316  0 
pcspkr                 10496  0 
soundcore              15200  1 snd
agpgart                42696  3 drm,intel_agp
iTCO_vendor_support    11652  1 iTCO_wdt
video                  25360  0 
input_polldev          11912  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
output                 11008  1 video
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
             total       used       free     shared    buffers     cached
Mem:       2052676    1003104    1049572          0      83424     557980
-/+ buffers/cache:     361700    1690976
Swap:      3903784          0    3903784
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/usr/lib/pm-utils/sleep.d/45iwlist suspend suspend: /sbin/iwlist
not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90chvt suspend suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/etc/pm/sleep.d/99laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 3
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Sat Jun  6 10:37:13 CDT 2009: performing suspend

If I could get this machine to suspend and resume, Jaunty would be running perfectly.

---

