---
title: "Asus P8H67-M LE mother board with Azalia HD Audio"
date: 2022-09-01
forum: Hardware
---

### Post by w0h0i6-2ic6ajy-p7k1qa on 2022-09-01
After upgrading to Ubuntu 22.04 I have lost my sound and have tried a couple of the listed fixes and none seem to work.  can anyone out there help me get sound back ?

---

### Post by Yellow Pasque on 2022-09-01
Please run alsa-info, upload, and give the link to your info:
```
sudo alsa-info
```

---

### Post by w0h0i6-2ic6ajy-p7k1qa on 2022-09-02
[IMG]https://ubuntuforums.org/text/plain;base64,[/IMG] I am not sure of how to link this info but I did try to include them.

---

### Post by w0h0i6-2ic6ajy-p7k1qa on 2022-09-02
richard@richard-Linux:~$ sudo alsa-info
[sudo] password for richard: 
ALSA Information Script v 0.5.1
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  aplay
  amixer
  alsactl
  rpm, dpkg
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See '/usr/sbin/alsa-info --help' for command line options.

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] :

---

### Post by Yellow Pasque on 2022-09-02
You're supposed to upload the info and give the link. Try it again with this command to automate it:
```
sudo alsa-info --upload
```

---

### Post by w0h0i6-2ic6ajy-p7k1qa on 2022-09-02
ahhh i see now.  I have done the upload

---

### Post by Yellow Pasque on 2022-09-02
And the link?

---

### Post by w0h0i6-2ic6ajy-p7k1qa on 2022-09-05
[http://alsa-project.org/db/?f=f782ef763fd74557f9d533fd235152ef7beb854a](http://alsa-project.org/db/?f=f782ef763fd74557f9d533fd235152ef7beb854a)

Ok another learning thing.  Hope this is what is needed :-)

---

### Post by Yellow Pasque on 2022-09-05
```
!!Sound Servers on this system
!!----------------------------

PipeWire:
      Installed - Yes (/usr/bin/pipewire)
      Running - Yes

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No
```

Pulseaudio is not running. That is problematic unless you've configured your system to use pipewire for audio. Did you configure this system to run pipewire?

---

### Post by w0h0i6-2ic6ajy-p7k1qa on 2022-09-05
yes because I had found some info on the internet that said to use pipewire

---

### Post by &amp;KyT$0P# on 2022-09-05
How did you set up Pipewire for audio?
What version of Pipewire are you using?

---

### Post by w0h0i6-2ic6ajy-p7k1qa on 2022-09-13
the pipewire version was newest version 0.357.r4

I have since removed pipewire and trying to get sound to work from beginning and it still does not work.

---

