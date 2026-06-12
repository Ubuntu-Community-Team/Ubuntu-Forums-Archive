---
title: "HP DV7-4177CA Laptop Subwoofer not Playing Sound in Ubuntu 10.04.2 LTS 64-Bit"
date: 2011-03-31
forum: Hardware
---

### Post by A_Brick on 2011-03-31
Hello
There is an issue that has gotten annoying.
My laptop plays sound fairly nicely, however the subwoofer does not play anything!
Now i am a complete linux noob, so any help on this would be greatly apprectiated.
I have the beats audio on this system if that helps at all.
TIA

---

### Post by lidex on 2011-04-02
Have a look here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio)

---

### Post by A_Brick on 2011-04-03
Thank you, I will give this a go tomorrow.

---

### Post by Daniel Libonati on 2011-06-14
I got it working, after a long search I've found this on a HP forum:

[http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/quot-Beats-Audio-quot-Linux-HP-Envy-17/m-p/617837#M60631](http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/quot-Beats-Audio-quot-Linux-HP-Envy-17/m-p/617837#M60631)

Basically you only have to open alsa-base.conf:

sudo gedit /etc/modprobe.d/alsa-base.conf

..and add the following line:

options snd-hda-intel model=ref

Save. Reboot.

---

