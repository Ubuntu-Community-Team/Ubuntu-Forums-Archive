---
title: "T410 muted speakers problem (Conexant CX20585)"
date: 2019-04-12
forum: Hardware
---

### Post by germo969 on 2019-04-12
Speakers are muted by default, headphones work out-of-box. Computer beeps while starting up and in BIOS-mode only. This problem has been documented since 12.04. I can hear them power down immediately Xubuntu is loaded. Also if I use hda-verb to power them on, i can hear it disable after 3 sec.
**Previous threads: **

[LIST=1]
[*][https://ubuntuforums.org/showthread.php?t=2211531&page=2&highlight=T410+speaker](https://ubuntuforums.org/showthread.php?t=2211531&page=2&highlight=T410+speaker)
[*][https://ubuntuforums.org/showthread.php?t=2195514&highlight=cx20585](https://ubuntuforums.org/showthread.php?t=2195514&highlight=cx20585)
[*][https://ubuntuforums.org/showthread.php?t=2335566&highlight=cx20585](https://ubuntuforums.org/showthread.php?t=2335566&highlight=cx20585)
[/LIST]
**Expired bug report: **

[LIST=1]
[*][https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1445596](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1445596)
[*][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1589756](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1589756)
[*][full list of bug-reports related to it]("https://launchpad.net/ubuntu/+bugs?field.searchtext=CX20585&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")
[/LIST]
[**Here is my Alsa output**]("http://alsa-project.org/db/?f=eff0ff34d79730aa8a559418b320d1bd56b528ea")

**Problem seems to be related to this part:**
```

Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x901701f0: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D3, actual=D3
``` 

As stated in other threads speakers can be enabled by
```

hda-verb /dev/snd/hwC0D0 0x1f SET_POWER_STATE 0

```
for some it works few minutes, for me only 3 seconds. Previously it had W10 and speakers worked without problems. _**Being inexperienced to come up with solution myself, I therefore ask does anyone know how to get speakers work permanently?**_ It seems there are also lot of bug reports and I doubt another one is needed to copy old ones.

**Related to this problem:**
[https://superuser.com/questions/567255/thinkpad-speaker-turns-mute-linux-codec-issue](https://superuser.com/questions/567255/thinkpad-speaker-turns-mute-linux-codec-issue)
[https://lists.gt.net/linux/kernel/1745623](https://lists.gt.net/linux/kernel/1745623)
[https://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg28769.html](https://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg28769.html)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1445596](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1445596)
[https://forums.lenovo.com/t5/ThinkPad-T400-T500-and-newer-T/T410-sound-not-working-anymore-What-can-i-do/td-p/1062775](https://forums.lenovo.com/t5/ThinkPad-T400-T500-and-newer-T/T410-sound-not-working-anymore-What-can-i-do/td-p/1062775)
[https://bugzilla.redhat.com/show_bug.cgi?id=967985](https://bugzilla.redhat.com/show_bug.cgi?id=967985)

---

### Post by Yellow Pasque on 2019-04-13
Have you tried this?:
```
options snd_hda_intel power_save_controller=N power_save=0
```

---

### Post by germo969 on 2019-04-14
Added into /etc/modprobe.d/alsa-base.conf did not resolve the problem.
```
[COLOR=#000000][FONT=&amp]options snd-hda-intel power_save_controller=N power_save=0[/FONT][/COLOR]
```

Under /sys/module/snd_hda_intel/parameters/ are
power_save 0
power_save controller N

[Full alsa-base.conf via pastebin]("https://pastebin.com/XNp7BAN4")
I have only added the last line, others are set by machine default

I can still hear the cracking sound when I start the laptop. Speakers are disabled by default.
```
[COLOR=#000000][FONT=&amp]hda-verb /dev/snd/hwC0D0 0x1f SET_POWER_STATE 0[/FONT][/COLOR]
```
Still allows to enable speakers for 3-seconds.

---

