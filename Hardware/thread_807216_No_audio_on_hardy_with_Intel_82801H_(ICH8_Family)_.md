---
title: "No audio on hardy with Intel 82801H (ICH8 Family) HD Audio Controller (rev"
date: 2008-05-25
forum: Hardware
---

### Post by tuxfire on 2008-05-25
this is the lspci output:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


thanks

---

### Post by Zorael on 2008-05-26
See [http://ubuntuforums.org/showpost.php?p=5017453&postcount=2](http://ubuntuforums.org/showpost.php?p=5017453&postcount=2) and check if anything applies.

---

### Post by tuxfire on 2008-05-27
nothing is changed. Need to try oss thanks anyway

---

### Post by tuxfire on 2008-05-28
i can hear audio now with oss but volume is low... 

better than nothing... :(

oss is obsolete i suppose :(

the strange thing is that my card is recognized with an ALC883 chipset but the first method doesn't work (I've added options snd-hda-intel model=acer or options snd-hda-intel model=acer-aspire to /etc/modprobe.d/alsa-base)

I have an acer 6920G-814G32Bn

thanks anyway :)

---

### Post by komputes on 2009-01-23
Testing out Jaunty Alpha 3 and I have the same issue with the following hardware:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

No sound output. works properly in Hardy/Intrepid.

---

### Post by BuddyJones on 2009-08-08
Thanks Zorael, I was having the same issue with an unrecognised audio out (internal laptop speakers were working, just not my external system) and adding **'model=vaio'** worked on my sony(kubuntu jaunty).

Headache fading...

---

