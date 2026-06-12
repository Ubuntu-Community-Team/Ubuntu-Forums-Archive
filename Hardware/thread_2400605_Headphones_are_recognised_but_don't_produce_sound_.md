---
title: "Headphones are recognised but don't produce sound - Ubuntu 18.04"
date: 2018-09-07
forum: Hardware
---

### Post by limok on 2018-09-07
This seems to be an often repeated question, but none of the answers on AskUbuntu worked for me.

I recently installed Ubuntu 18.04 in dual-boot with Windows 10; my machine is an HP Spectre x360, from 2016/2017. My speakers and headphone work fine on Windows 10, On Ubuntu 18.04, the in-built speakers also work without a problem (though they are quieter than on Windows). However, when I plug in my headphones, they seem to be recognised, but they never produce any sound. I have two pairs of headphones for which I tried this.

I went through this AskUbuntu thread, and tried the answers one by one, none worked: [https://askubuntu.com/questions/132440/headphone-jack-not-working](https://askubuntu.com/questions/132440/headphone-jack-not-working)

When I plug them in and go on Settings -> Sound, I see it switch from "Speakers - Built-in Audio" to "Headphones - Built-in Audio".

Output of lspci:

```
$ lspci | grep Audio
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
```

In anticipation of extra information, based on a previous post, I also ran that ALSA script which uploads all my config info:


```
$ bash alsa-info.sh
ALSA Information Script v 0.4.64
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=e0c2213d62d3e74006024d0a5511655c21ac3e1f

Please inform the person helping you.


```

Additionally, I don't know if it's visible from that alsa-info upload, but I already made some minor changes to my config files while following the AskUbuntu suggestions.

---

### Post by Yellow Pasque on 2018-09-07
There's a long discussion here, but my head's spinning trying to make sense of it all, especially because some of the reports conflict. [https://bugzilla.kernel.org/show_bug.cgi?id=189331](https://bugzilla.kernel.org/show_bug.cgi?id=189331)

---

### Post by limok on 2018-09-08
That's interesting, the reports started in 11/2016. I actually had this same laptop back then, running Ubuntu 14.04, and I remember having several hardware problems in the beginning, possibly including the sound. However, I managed to fix them all somehow. Since then I wiped my SSD and updated to Ubuntu 18.04, and now it doesn't work.

Although that bug report is about speakers for the parts I read. I'll try and look into that a bit, like I said I thought my speakers seemed a lot quieter on linux than on Windows, but it may be that I had the same problem they describe, with only the front speakers working, and I didn't notice.

UPDATE: yes, not all the speakers work either. However, it seems a bit mixed up: when testing in Sound settings, it only has options for "Front Left" and "Front Right" speakers, however, the speakers that produce the sound are the ones at the back (on the bottom of the chassis). Now I think about it, even with Ubuntu 14.04, the top speakers never produced sound, which is why I actually thought the grill on the speakers was for ventilation and not for sound.

@Temujin: the reports seem to conflict, but it seems to depend on the exact model. I have a i7/16GB/1TB model, and the other two guys with the same model have the same problem (that their headphone jack also doesn't work). I'm trying to read through it but most of it is over my head.

---

