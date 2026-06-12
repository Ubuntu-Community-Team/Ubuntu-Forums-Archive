---
title: "No sound, New install, IBM X31"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by jfitzmyer on 2008-01-19
New user, here.

Somewhat tricky to install without a CD. Works fine but no sound.

I haven't been able to find any info on getting it going. 

Can anyone help point me in the right direction?

Thanks!

Joe

---

### Post by linuxwizard on 2008-01-19
Look through this, may help find something on sound issues and a fix.

[http://www.thinkwiki.org/wiki/Category:X31](http://www.thinkwiki.org/wiki/Category:X31)

---

### Post by Yellow Pasque on 2008-01-19
It's an ADI1981 codec, so according to my handy guide ([http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)), you shoud try adding the following line: 
"options snd-hda-intel model=thinkpad"  (without the quotes) into the /etc/modprobe.d/alsa-base file

Also try model=basic or model=3stack if that doesn't work.

---

### Post by jfitzmyer on 2008-01-20
Thanks for the reply!

I had some problems. Running

joe@ubuntu:~$ cat /proc/asound/card0/codec#* | grep Codec

gave me:

cat: /proc/asound/card0/codec#*: No such file or directory

running:

joe@ubuntu:~$ aplay -l

gives:

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Not seeing  I82801DBICH in the listing on [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)
I remembered seeing on the alsamixer screen that my sound card was an Intel 82801DB-ICH4 with chip AD1981B.

So I tried editing /etc/modprobe.d/alsa-base

with:

options snd-hda-intel model=thinkpad
options snd-hda-intel model=basic
options snd-hda-intel model=3stack
options snd-hda-intel model=hp
options snd-hda-intel model=toshiba
and
options snd-hda-intel model=auto

rebooting after editing each line.

Nothing worked! 

So now I'm stumped. Is AD1981B the same as AD1981?

I'd appreciate any other suggestions.

Thanks!

Joe

---

