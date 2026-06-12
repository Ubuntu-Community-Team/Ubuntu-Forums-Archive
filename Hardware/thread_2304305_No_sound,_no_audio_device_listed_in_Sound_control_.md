---
title: "No sound, no audio device listed in Sound control under output"
date: 2015-11-25
forum: Hardware
---

### Post by mark-bobak on 2015-11-25
Hi,

I recently installed Ubuntu 15.10 on an HP 550-a114 desktop, and I don't have any sound.

Further, under the sound control panel, under the output tab, there is no device listed.  

Help?

alssa-info output is here:
[http://www.alsa-project.org/db/?f=4d7ceda2e2eafe6089a03fd7c851aae7c33de25d](http://www.alsa-project.org/db/?f=4d7ceda2e2eafe6089a03fd7c851aae7c33de25d)

-Mark

---

### Post by bodyeuh on 2015-11-27
have you checked the preferences - Additional Drivers? maybe your desktop has third party drivers issue.

---

### Post by fleenots on 2015-11-27
I have exactly the same problem even though I am using a different desktop and Ubuntu 14.04.

the alsa-info output:

 [http://www.alsa-project.org/db/?f=1c01a15615b2f4394e1462e295cd4a3880df2811](http://www.alsa-project.org/db/?f=1c01a15615b2f4394e1462e295cd4a3880df2811)

---

### Post by Yellow Pasque on 2015-11-27
> **fleenots said:**
> I have exactly the same problem even though I am using a different desktop and Ubuntu 14.04.

Is it a Z170 chipset mobo? You've got that same "failed to add i915_bpo component master" error that I've been seeing from Z170 owners on a 3.19 kernel. Luckily, it's been fixed upstream and it's easy to upgrade: [http://ubuntuforums.org/showthread.php?t=2296136&p=13361578#post13361578](http://ubuntuforums.org/showthread.php?t=2296136&p=13361578#post13361578)

---

### Post by Yellow Pasque on 2015-11-27
> **mark-bobak said:**
> Further, under the sound control panel, under the output tab, there is no device listed.  Help?

I don't see anything in the alsa info indicating your device is not detected. Maybe your issue is on the pulseaudio level: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by fleenots on 2015-11-28
> **Temüjin said:**
> I don't see anything in the alsa info indicating your device is not detected. Maybe your issue is on the pulseaudio level: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

It is a z170 chipset mobo.
I've tried what you suggested and now the devices show in the sound  control panel. But I still don't have any sound from any of those  devices.

---

### Post by fleenots on 2015-11-28
> **Temüjin said:**
> I don't see anything in the alsa info indicating your device is not detected. Maybe your issue is on the pulseaudio level: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)


Some of the error messages in the pulseaudio log file. On top of these there are a number of failed 

(   0.010|   0.000) I: [pulseaudio] (alsa-lib)parser.c: error: could not parse configuration for card HDA NVidia
(   0.010|   0.000) I: [pulseaudio] (alsa-lib)main.c: error: failed to import HDA NVidia use case configuration -2
(   1.558|   0.000) I: [pulseaudio] (alsa-lib)parser.c: error: could not parse configuration for card USB Device 0x46d:0x825
(   1.558|   0.000) I: [pulseaudio] (alsa-lib)main.c: error: failed to import USB Device 0x46d:0x825 use case configuration -2
(   3.492|   0.000) I: [pulseaudio] (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
(   3.492|   0.000) I: [pulseaudio] (alsa-lib)conf.c: Evaluate error: No such file or directory
(   3.503|   0.000) I: [pulseaudio] (alsa-lib)parser.c: error: could not parse configuration for card HDA Intel PCH
(   3.503|   0.000) I: [pulseaudio] (alsa-lib)main.c: error: failed to import HDA Intel PCH use case configuration -2
(   0.012|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:1: No such file or directory
(   0.015|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device front:1: No such file or directory
(   0.015|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:1: No such file or directory
(   0.015|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:1: No such file or directory
(   0.015|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:1: No such file or directory
(   0.015|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device front:1: No such file or directory
(   0.015|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:1: No such file or directory
(   0.015|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround40:1: No such file or directory
(   0.016|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround41:1: No such file or directory
(   0.016|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround50:1: No such file or directory
(   0.016|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround51:1: No such file or directory
(   0.016|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:1: No such file or directory
(   0.016|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:1: No such file or directory
(   0.016|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:1: No such file or directory
(   0.016|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:1: No such file or directory
(   0.016|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device dca:1: No such file or directory
(   3.491|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:2: No such file or directory
(   3.491|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device front:2: No such file or directory
(   3.491|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:2: No such file or directory
(   3.491|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround40:2: No such file or directory
(   3.492|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround41:2: No such file or directory
(   3.492|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround50:2: No such file or directory
(   3.492|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround51:2: No such file or directory
(   3.492|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:2: No such file or directory
(   3.492|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:2: No such file or directory
(   3.492|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:2: No such file or directory
(   3.492|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:2: No such file or directory
(   3.492|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device dca:2: No such file or directory
(   3.492|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:2: No such file or directory
(   3.506|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
(   3.583|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   3.583|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   3.583|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device dca:0: No such file or directory
(   3.584|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
(   3.584|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
(   3.584|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: No such file or directory
(   3.584|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: No such file or directory
(   3.585|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: No such file or directory
(   3.585|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: No such file or directory
(   3.585|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
(   3.585|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory

On top of these there are a number of failed processes

(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
(   0.010|   0.000) I: [pulseaudio] (alsa-lib)main.c: error: failed to import HDA NVidia use case configuration -2
(   0.012|   0.001) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D0c' failed (-2)
(   0.015|   0.002) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D0c' failed (-2)
(   0.015|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D0c' failed (-2)
(   0.015|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D1c' failed (-2)
(   0.015|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D0p' failed (-2)
(   0.015|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D0p' failed (-2)
(   0.015|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D0p' failed (-2)
(   0.015|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D0p' failed (-2)
(   0.016|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D0p' failed (-2)
(   0.016|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D0p' failed (-2)
(   0.016|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D0p' failed (-2)
(   0.016|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D0p' failed (-2)
(   0.016|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D1p' failed (-2)
(   1.558|   0.000) I: [pulseaudio] (alsa-lib)main.c: error: failed to import USB Device 0x46d:0x825 use case configuration -2
(   3.485|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' failed.
(   3.485|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' failed.
(   3.486|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' failed.
(   3.486|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' failed.
(   3.486|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' failed.
(   3.486|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' failed.
(   3.487|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(2) failed: Invalid argument
(   3.487|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(2) failed: Invalid argument
(   3.488|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(2) failed: Invalid argument
(   3.488|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(2) failed: Invalid argument
(   3.488|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(2) failed: Invalid argument
(   3.489|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(2) failed: Invalid argument
(   3.489|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(2) failed: Invalid argument
(   3.489|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(2) failed: Invalid argument
(   3.489|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   3.490|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   3.490|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   3.490|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   3.490|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(2) failed: Invalid argument
(   3.491|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(2) failed: Invalid argument
(   3.491|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(2) failed: Invalid argument
(   3.491|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(2) failed: Invalid argument
(   3.491|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC2D0p' failed (-2)
(   3.491|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC2D0p' failed (-2)
(   3.491|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC2D0p' failed (-2)
(   3.491|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC2D0p' failed (-2)
(   3.492|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC2D0p' failed (-2)
(   3.492|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC2D0p' failed (-2)
(   3.492|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC2D0p' failed (-2)
(   3.492|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC2D0p' failed (-2)
(   3.492|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC2D0p' failed (-2)
(   3.503|   0.000) I: [pulseaudio] (alsa-lib)main.c: error: failed to import HDA Intel PCH use case configuration -2
(   3.503|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   3.504|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   3.504|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   3.504|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   3.505|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' failed.
(   3.506|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' failed.
(   3.506|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' failed.
(   3.506|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' failed.
(   3.506|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' failed.
(   3.506|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' failed.
(   3.506|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
(   3.506|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   3.506|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   3.506|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   3.507|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   3.508|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Desktop Speaker' failed.
(   3.508|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' failed.
(   3.573|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   3.574|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   3.574|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   3.574|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   3.584|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
(   3.584|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
(   3.584|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D7p' failed (-2)
(   3.584|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D7p' failed (-2)
(   3.585|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D8p' failed (-2)
(   3.585|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D8p' failed (-2)
(   3.585|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D9p' failed (-2)
(   3.585|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D9p' failed (-2)

---

### Post by oldefoxx on 2016-03-03
I have as simular problem.  I'm on a HP K073ca Laptop  with an Intel cpu and chipset in it.  The sound was working through the built-in speaker  in earlier releases in Ubuntu, but now no devices are detected for audio output.  I'm on the latest release of Ubuntu 15.10 with latest updates.  Trying to follow one of the leads above, i decided to see if I could locate a pulseaudio.log and check what it contained.  I could not find it.   Then I looked for a log that had either "pulse" or 'audio' in it.  Could not find that either.  Deciding such a log would have the letters 'p', 'a', and the word 'log' in it, I tried this command:   sudo find / -type f -iname p*a*log* |tee 0; less 0.  No match in terms of what I sought.  I trimmed off /home and /media entries and the first attachment shows you all that is left:

Hmm.  Sorry about that.  The Attachment Manager is really screwed up.  It says it will delete an attachment if it is not used in 1 hour, but it's still holding files I posted many months afo.  18 in fact.  It won't.' let me delete any, and it wont let me add more,  It won't even sort the ones I have.  I have no cancel, quit, or exit option, and If I try to click Done, it demands I use a previously uploaded file or add more files, which it won't accept.  In other words... well, I won't resort to those words.

So, I guess I will have to insert the 0 file's contents into this post.  I hope it is not too long.  I see nothing related to pulse audio in it, but that was in a fast scroll through.  I don't really know what to look for, where it should be, and what I should check next. By the way, this flaw, and possibly others, has killed my ability to use VirtualBox with clients.  They are promised audio service in their settings, and of course it;s not there for them either.  I could maybe disable sound for them, but I'd rather get back to ubuntu as it was and should be,  How is it that this problem has surfaced like this?  Very strange indeed.

Excuse me, here it comes:
```
/var/log/pm-powersave.log
/var/log/pm-powersave.log.1
/var/log/pm-powersave.log.2.gz
/var/log/cups/page_log
/var/log/upstart/procps-static-network-up.log.1.gz
/var/log/upstart/procps-static-network-up.log.6.gz
/var/log/upstart/procps-virtual-filesystems.log.1.gz
/var/log/upstart/procps-virtual-filesystems.log.7.gz
/var/log/upstart/procps-virtual-filesystems.log.4.gz
/var/log/upstart/procps-static-network-up.log.2.gz
/var/log/upstart/procps-virtual-filesystems.log.3.gz
/var/log/upstart/procps-virtual-filesystems.log.2.gz
/var/log/upstart/procps-static-network-up.log.4.gz
/var/log/upstart/procps-virtual-filesystems.log.6.gz
/var/log/upstart/procps-static-network-up.log.3.gz
/var/log/upstart/plymouth-ready-started.log.1.gz
/var/log/upstart/procps-static-network-up.log.7.gz
/var/log/upstart/procps-static-network-up.log.5.gz
/var/log/upstart/procps-virtual-filesystems.log.5.gz
/lib/x86_64-linux-gnu/security/pam_nologin.so
/lib/x86_64-linux-gnu/security/pam_lastlog.so
/lib/x86_64-linux-gnu/security/pam_loginuid.so
/usr/share/rhythmbox/podcast-add-dialog.ui
/usr/share/app-install/desktop/pathological:pathological.desktop
/usr/share/app-install/icons/pyhoca_x2go-logo-ubuntu.svg
/usr/share/unity-control-center/ui/printers/ppd-selection-dialog.ui
/usr/share/transmission/web/javascript/prefs-dialog.js
/usr/share/hplip/ui4/printdialog.py
/usr/share/hplip/ui4/printsettingsdialog_base.py
/usr/share/hplip/ui4/pqdiagdialog.py
/usr/share/hplip/ui4/__pycache__/plugindialog.cpython-34.pyc
/usr/share/hplip/ui4/__pycache__/printtestpagedialog.cpython-34.pyc
/usr/share/hplip/ui4/__pycache__/printtestpagedialog_base.cpython-34.pyc
/usr/share/hplip/ui4/__pycache__/printsettingsdialog_base.cpython-34.pyc
/usr/share/hplip/ui4/__pycache__/plugindialog_base.cpython-34.pyc
/usr/share/hplip/ui4/__pycache__/pqdiagdialog_base.cpython-34.pyc
/usr/share/hplip/ui4/__pycache__/printdialog_base.cpython-34.pyc
/usr/share/hplip/ui4/__pycache__/pqdiagdialog.cpython-34.pyc
/usr/share/hplip/ui4/__pycache__/pluginlicensedialog_base.cpython-34.pyc
/usr/share/hplip/ui4/__pycache__/printdialog.cpython-34.pyc
/usr/share/hplip/ui4/__pycache__/pluginlicensedialog.cpython-34.pyc
/usr/share/hplip/ui4/__pycache__/printsettingsdialog.cpython-34.pyc
/usr/share/hplip/ui4/pqdiagdialog_base.py
/usr/share/hplip/ui4/pluginlicensedialog_base.py
/usr/share/hplip/ui4/printdialog_base.py
/usr/share/hplip/ui4/printtestpagedialog.py
/usr/share/hplip/ui4/plugindialog_base.py
/usr/share/hplip/ui4/plugindialog.py
/usr/share/hplip/ui4/pluginlicensedialog.py
/usr/share/hplip/ui4/printsettingsdialog.py
/usr/share/hplip/ui4/printtestpagedialog_base.py
/usr/share/locale-langpack/en_GB/LC_MESSAGES/Parse-DebianChangelog.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/Parse-DebianChangelog-Pod.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/Parse-DebianChangelog.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/Parse-DebianChangelog-Pod.mo
/usr/share/system-config-printer/ui/PrinterPropertiesDialog.ui
/usr/share/shutter/resources/icons/drawing_tool/objects/Tango icon library/Apps/preferences-desktop-assistive-technology.svg
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-dialog.svg
/usr/share/man/de/man3/Parse::DebianChangelog::Entry.3pm.gz
/usr/share/man/de/man3/Parse::DebianChangelog::ChangesFilters.3pm.gz
/usr/share/man/man1/parsechangelog.1p.gz
/usr/share/man/man3/Parse::DebianChangelog.3pm.gz
/usr/share/man/man3/Parse::DebianChangelog::Util.3pm.gz
/usr/share/man/man3/Parse::DebianChangelog::Entry.3pm.gz
/usr/share/man/man3/Parse::DebianChangelog::ChangesFilters.3pm.gz
/usr/share/man/man8/pam_nologin.8.gz
/usr/share/man/man8/pam_lastlog.8.gz
/usr/share/man/man8/pam_loginuid.8.gz
/usr/share/webbrowser-app/PromptDialog.qml
/usr/share/webbrowser-app/ProxyAuthenticationDialog.qml
/usr/share/debhelper/autoscripts/postrm-xmlcatalog
/usr/share/debhelper/autoscripts/prerm-xmlcatalog
/usr/share/debhelper/autoscripts/postinst-xmlcatalog
/usr/bin/parsechangelog
/usr/lib/x86_64-linux-gnu/perl5/5.20/Gnome2/PasswordDialog.pod
/usr/lib/libreoffice/share/config/soffice.cfg/filter/ui/pdfoptionsdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/swriter/ui/picturedialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/swriter/ui/paradialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/swriter/ui/previewzoomdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/swriter/ui/printmonitordialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/swriter/ui/printmergedialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/scalc/ui/pivottablelayoutdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/scalc/ui/paradialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/scalc/ui/pivotfilterdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/scalc/ui/pivotfielddialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/scalc/ui/printareasdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/scalc/ui/paratemplatedialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/scalc/ui/pagetemplatedialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/simpress/ui/presentationdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/simpress/ui/publishingdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/schart/ui/paradialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/dbreport/ui/pagenumberdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/modules/dbreport/ui/pagedialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/svt/ui/printersetupdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/sfx/ui/printeroptionsdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/dbaccess/ui/parametersdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/vcl/ui/printprogressdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/vcl/ui/printdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/vcl/ui/printerpropertiesdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/cui/ui/positionsizedialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/cui/ui/percentdialog.ui
/usr/lib/libreoffice/share/config/soffice.cfg/cui/ui/posterdialog.ui
/usr/lib/scribes/GenericPlugins/PluginSaveDialog.pyc
/usr/lib/scribes/GenericPlugins/PluginSaveDialog.py
/usr/lib/python2.7/dist-packages/ubuntu-sso-client/ubuntu_sso/qt/proxy_dialog.py
/usr/lib/python2.7/dist-packages/ubuntu-sso-client/ubuntu_sso/qt/ui/proxy_credentials_dialog_ui.py
/usr/lib/python2.7/dist-packages/ubuntu-sso-client/ubuntu_sso/qt/ui/proxy_credentials_dialog_ui.pyc
/usr/lib/python2.7/dist-packages/ubuntu-sso-client/ubuntu_sso/qt/proxy_dialog.pyc
```

---

