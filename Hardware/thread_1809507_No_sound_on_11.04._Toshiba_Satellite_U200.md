---
title: "No sound on 11.04. Toshiba Satellite U200"
date: 2011-07-21
forum: Hardware
---

### Post by Sirocco01 on 2011-07-21
Help guys!!! Hello to everyone who reading this. Need your help.

No sound on Toshiba Satellite U200 running UBUNTU 11.04.

mixer settings

[[IMG]http://img4.imageshack.us/img4/4755/55999611.th.png[/img]](http://imageshack.us/photo/my-images/4/55999611.png/)

**lspci -k**
sirocco@SATELLITE-PRO-U200:~$ lspci -k
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
sirocco@SATELLITE-PRO-U200:~$ ^C
sirocco@SATELLITE-PRO-U200:~$

**uname -a**
sirocco@SATELLITE-PRO-U200:~$ uname -a
Linux SATELLITE-PRO-U200 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux
sirocco@SATELLITE-PRO-U200:~$ ^C
sirocco@SATELLITE-PRO-U200:~$ 

**aplay -l**

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  &#1055;&#1110;&#1076;&#1087;&#1088;&#1080;&#1083;&#1072;&#1076;&#1080;: 1/1
  &#1055;&#1110;&#1076;&#1087;&#1088;&#1080;&#1083;&#1072;&#1076; #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  &#1055;&#1110;&#1076;&#1087;&#1088;&#1080;&#1083;&#1072;&#1076;&#1080;: 1/1
  &#1055;&#1110;&#1076;&#1087;&#1088;&#1080;&#1083;&#1072;&#1076; #0: subdevice #0
sirocco@SATELLITE-PRO-U200:~$ ^C
sirocco@SATELLITE-PRO-U200:~$ 

**cat /proc/asound/version**
Advanced Linux Sound Architecture Driver Version 1.0.23.
sirocco@SATELLITE-PRO-U200:~$ 

**head -n 1 /proc/asound/card*/codec#***
==> /proc/asound/card0/codec#0 <==
Codec: Analog Devices AD1981

==> /proc/asound/card0/codec#1 <==
Codec: LSI Si3054
sirocco@SATELLITE-PRO-U200:~$

---

### Post by lidex on 2011-07-21
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=toshiba" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by lkjoel on 2011-07-21
If the above technique doesn't work, try Sound Troubleshooting in my signature.

---

### Post by Sirocco01 on 2011-07-22
Thank You for supporting me, lidex but this method won't work. {Code:
wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh} 

Oh yes. I hear music in earphones, but VERY-VERY LOW. I don't recognize the music, but i hear sounds seems like miles away from me. My note have hardware volume/mute button

---

### Post by Sirocco01 on 2011-07-22
I did it!!! Everything is allright. I think that's because the hardware volume|mute button (three positioning joystick). I formatted the hard disk, then installed my Windows Vista, then downoaded sound driver for vista and there was no sound too. The music plays, the volume bar i full, but no sound. WTF??? Than i pressed hardware button volume|mute twice and suddenly the music started to play. Then i booted Live CD of Ubuntu 11.04. Hurray - the sound is on now and i can hear it. Then reinstalled UBUNTU as a first OS and the sound is now working properly!!! Thank everyone for patience. You make me happy with such OS. Bye and thanks!!!!!!

---

### Post by johenkel on 2011-11-05
Haha, good for you.
I have a used Toshiba Satellite Laptop and my sound was gone after some updates.

After reading your post I checked that little volume turn knob on the front on the laptop - and - v'oala - IT WORKS.

My kids must have just turned it down.

Thanks for giving me the idea to check !

johenkel

---

