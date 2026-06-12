---
title: "sony vaio microphone"
date: 2010-12-08
forum: Hardware
---

### Post by rgrig on 2010-12-08
My built-in microphone does not work. I am running Ubuntu 10.10 on Sony Vaio VPCS13C5E.

As [suggested on these forums]("http://ubuntuforums.org/showthread.php?t=1335825"), I installed linux-backports-modules-alsa-maverick-generic and appended "options snd-hda-intel model=auto" to /etc/modprobe.d/alsa-base.conf. I also tried the [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") help. Here is my [Alsa info page]("http://www.alsa-project.org/db/?f=1e689890ae64e2c53d86924af103e981f0985e10") and the [ALSA-Configuration.txt]("http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob_plain;f=Documentation/ALSA-Configuration.txt;hb=0c8e73dc82fce0832b7b85bf5a06d9fbfd27a31b") for the version 1.0.23 installed on my computer. At some point, SoundTroubleshooting says I should figure out the codec in the former and look up information about it in the latter. However, the codecs (Realtek ALC275 and Intel IbexPeak HDMI) do not appear in ALSA-Configuration.txt, so it seems I'm stuck.

I'd really like to make the microphone work. Any help is welcome.

---

### Post by stefango on 2010-12-18
Hi rgrig, 
I have the same issue with the same computer, so I can confirm the issue. Unfortunately, I couldn't find any working solution yet. 
:\

---

### Post by rgrig on 2010-12-19
OK, I searched a bit more, and I found what looks like a [workaround]("http://thread.gmane.org/gmane.linux.alsa.devel/70475"). I'll try later today, or tomorrow.

---

