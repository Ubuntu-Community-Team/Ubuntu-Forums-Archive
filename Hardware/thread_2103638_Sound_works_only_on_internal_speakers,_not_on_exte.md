---
title: "Sound works only on internal speakers, not on external"
date: 2013-01-10
forum: Hardware
---

### Post by kenweill on 2013-01-10
Need help.

Before, I watch movies with my laptop. Watch youtube videos via firefox with my laptop. No problem on sound, with internal speakers.

Today, I just hook my external speakers and found out that both movies doesn't produce sound on external speakers. Not even on my headphone.

Sound only works on internal speakers but not on external speakers or headphone.

What else should I install to fix this one?

> 
kenweill@ASUSK55VD:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC270 Analog [ALC270 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



---

### Post by kenweill on 2013-01-24
I can't edit this post and so I'll just reply on my own thread.

Got this fixed with
```
echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
then reboot system.

Found the solution from [http://ubuntuforums.org/showpost.php?p=11418413&postcount=3](http://ubuntuforums.org/showpost.php?p=11418413&postcount=3)

---

### Post by Yellow Pasque on 2013-01-24
That's odd, since 'asus' is not a valid model for that codec.

```
ALC269/270/275/276/280/282
======
  laptop-amic	Laptops with analog-mic input
  laptop-dmic	Laptops with digital-mic input
  alc269-dmic	Enable ALC269(VA) digital mic workaround
  alc271-dmic	Enable ALC271X digital mic workaround
  inv-dmic	Inverted internal mic workaround
  lenovo-dock   Enables docking station I/O for some Lenovos
```
[http://git.alsa-project.org/?p=alsa-kernel.git;a=blob_plain;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD](http://git.alsa-project.org/?p=alsa-kernel.git;a=blob_plain;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD)

---

