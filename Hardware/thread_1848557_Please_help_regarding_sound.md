---
title: "Please help regarding sound"
date: 2011-09-22
forum: Hardware
---

### Post by stefanjhill on 2011-09-22
Hi,

I have an older Packard Bell laptop that it seems has a SiS SI7012 AD1888 onboard sound card.  I have searched the Ubuntu forums high and low and have just ended up more confused than when I started.

Could some kind soul please tell me in plain English if this sound card works on any version of Ubuntu?  I have the same problem that many have indicated, that is the card seems to work and is detected by the OS, with the pulseaudio playback meter shows playback (speaker-test and a youtube vid), but no sound emits from the speakers.  alsamixer shows nothing is muted.

Any help clearing this up would be greatly appreciated.  Note the sound worked fine under Windows XP, but this computer is being used by my partners older parents and we don't trust Windows for security reasons...

I just want to know if we are looking at a new laptop or not.

Regards,
   Stefan.

---

### Post by aura7 on 2011-09-22
Check this out

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

---

### Post by stefanjhill on 2011-09-23
Thanks for the link.  Unfortunately my problem isn't the installation of drivers, Ubuntu 10.04LTS detects and reports the sound chip correctly.  The disconnect is that the sound seems to be generated (pulseaudio playback monitor shows this) but no sound is being sent to the speakers?  This problem has been report from what I see all the way back to 5.04.  The threads all mention numerous ideas but in my hunts all the threads lead to nothing concrete, sort of vague rumors.

For example from the supplied link;
  alias snd-card-0 snd-intel8x0
&
  alias snd-card-0 snd-hda-intel
Both can't be correct for the modules.conf file can they?

By Unbuntu-Fu isn't the strongest, meaning I have never compiled a kernel in my life.  If someone has solved this issue and has a step-by-step guide not based on prior Linux knowledge I would gladly promise by first born.

Many thanks in advance and sorry for being so lame,
   Stefan.

---

### Post by .... on 2011-09-23
The device in question is not an HDA codec. It is AC97 (intel 8x0). Unfortunately, I don't know too much about troubleshooting these old chips. The best I can do is give you relevant documentation and encourage you to play around with different options in alsa-base.conf. 
See the snd-intel8x0 and AC97 quirk options here:  [http://git.alsa-project.org/?p=alsa-kernel.git;a=blob_plain;f=Documentation/sound/alsa/ALSA-Configuration.txt;hb=HEAD](http://git.alsa-project.org/?p=alsa-kernel.git;a=blob_plain;f=Documentation/sound/alsa/ALSA-Configuration.txt;hb=HEAD)

This command will help you quickly try different options without restarting each time:
```
sudo /usr/sbin/alsa force-reload
```Good luck.

---

### Post by stefanjhill on 2011-09-23
Thanks for the clear advice.  Most appreciated.

Regards,
   Stefan.

---

