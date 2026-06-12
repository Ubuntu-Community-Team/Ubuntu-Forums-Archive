---
title: "Sound problems ubuntu 10.04 on hp dv6748us laptop"
date: 2013-06-09
forum: Hardware
---

### Post by Llewxam on 2013-06-09
greetings all.

been using ubuntu 10.04 for a long while now and haven't had any problems until two days ago i lost all sound on this laptop. i've followed and tried all kinds of forum posts and guides on this subject and none have helped out. running aplay -l i get this
```
aplay: device_list:252: no soundcards found...
```
other prompts such as cat /proc/asound print out this: 
```
head: cannot open `/proc/asound/card0/codec*' for reading: No such file or directory
```
alsamixer prints this: 
```
cannot open mixer: No such file or directory
```

this particular model has the touch controls at top (quick play / dvd / previous track / play/pause / next track / stop / mute / vol down vol up) when i used to tap on the mute button it would change light colors now it doesn't anymore. 
i upgraded alsa with the [ALSA Upgrade Script]("http://ubuntuforums.org/showthread.php?t=1681577") and still nothing. last but not least, running alsa force-reload prints out this:
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/maxadiel/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/maxadiel/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
```

any help will be greatly appreciated. don't have any more information to give on the sound card hardware as it is because i never actually looked into that before. all i got is out of virtual box listing ICH AC97.

---

### Post by ahallubuntu on 2013-06-09
~

---

### Post by Llewxam on 2013-06-09
yea forgot to add that, live cd for 10.04 and sound didn't work. might have to burn and re-try with a latest flavor or a different distro (only other one i got is backtrack). need to find the .isos first though. so far, no, live cd didn't work.

---

### Post by ahallubuntu on 2013-06-09
~

---

### Post by Llewxam on 2013-06-10
alright well, neither backtrack livecd or ubuntu 12.04 live cd worked in bringing out any sound. still had dummy output stereo on preferences and the same no devices found with aplay. this is really starting to frustrate me ](*,)!
also ran alsa-info so attached to this post is the result of that if anyone with better understanding or knowledge can help me. please.

---

### Post by Llewxam on 2013-06-10
adding to this, found that by running gnome-alsamixer from terminal i could access the mixer and i get this output:

```
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default

(gnome-alsamixer:2779): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault
```

as a side note: is there some possible way to see a log of the boot and shutdown prompts? in a flash i saw something about sound files being ignored.

---

### Post by GrimReaperAxeKick on 2013-06-10
I remember having this same exact problem with 12.10. I remember that the sound was eventually restored after I re-installed Ubuntu because of an unrelated reason. So my prior experience would lead me to believe that this is strictly a software problem. 

Your headphone output will still work, though, so you can still listen to audio while you are finding a solution. 


Sorry that I can't be of further assistance.

---

### Post by Llewxam on 2013-06-10
actually tried that after reading your post. not working either. i'm at a total standstill now.

---

### Post by Llewxam on 2013-06-10
bit more info while i continue to find the cause of my sound issues. a boot log printed this little tid bit out:
```
fsck from util-linux-ng 2.17.2
udevd[396]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:9


udevd[396]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:9


udevd[396]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:10


udevd[396]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:10


udevd[396]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:12


udevd[396]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:12


udevd[396]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:13


udevd[396]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:13


udevd[396]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:15


udevd[396]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:15


udevd[396]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:16


udevd[396]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:16
```
anybody got any ideas what may be causing this or what it means? :confused:

---

### Post by GrimReaperAxeKick on 2013-06-11
> **Llewxam said:**
> actually tried that after reading your post. not working either. i'm at a total standstill now.

Wow, very strange. Try booting up Puppy linux in live mode (or any other minimalist linux that won't bother your data consumption) to see if you've got any sound. If it has no sound, then I would call hardware issue, as a non functioning headphone jack is suspicious and points toward a hardware issue.

Alternatively, if you have Windows, you could boot into Windows to check the sound.


Puppy linux: [http://www.puppylinux.org/](http://www.puppylinux.org/) - 100 mb

Tiny Core Linux: [http://distro.ibiblio.org/tinycorelinux/](http://distro.ibiblio.org/tinycorelinux/) - 12 mb

Downloading, installing and booting into live mode to test the sound should take no longer 20 minutes if you have a good internet connection.

---

### Post by Llewxam on 2013-06-11
no luck with either puppy or tiny core either. really starting to believe this is a hardware malfunction. all i got left is to find a way to run windows somehow without partitioning my hard drive.

---

### Post by SeijiSensei on 2013-06-11
I lost the sound output via the headphone jack on an older Dell laptop last year.  I opted to buy a $20 [USB sound card]("http://www.tigerdirect.com/applications/category/category_slc.asp?Recs=30&Nav=|c:4261|&Sort=4") to fix the problem.

---

### Post by Llewxam on 2013-06-13
well, desperate times and all that, i downloaded a version of win7 (:-&) that runs from usb and used that. even then the sound card was not recognized. so yea it is a hardware problem... :(

---

