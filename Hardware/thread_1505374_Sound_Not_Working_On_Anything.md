---
title: "Sound Not Working On Anything?"
date: 2010-06-09
forum: Hardware
---

### Post by w0Rm210 on 2010-06-09
I've read multiple posts on this but for some reason on my compaq presario 64-bit of course Lucid Lynx installed and no matter what i play youtube videos or videos through the main video player or songs on rythembox nothing happens. Help?

---

### Post by w0Rm210 on 2010-06-09
> **rickymaccullum said:**
> What OS are you running on? What type of connection from your soundcard are you using? SPDIF? What types of source sound files are you using? Wave/MP3, MIDI, DVD? After your drivers are installed if you look in Device manager does everything appear to be okay?


Ubuntu 10.04. Just the main speakers. No clue. And yes

---

### Post by lidex on 2010-06-09
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by w0Rm210 on 2010-06-09
Ok it's a compaq presario CQ61 and it's a laptop, here's the outcome

anthony@H:~$ uname -a
Linux H 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

anthony@H:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

anthony@H:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

anthony@H:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B2X5

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

---

### Post by lidex on 2010-06-09
Follow the alsa-upgrade link in my sig to get version 1.0.23

---

### Post by w0Rm210 on 2010-06-09
> **lidex said:**
> Follow the alsa-upgrade link in my sig to get version 1.0.23

Thanks i'll try it, i really appriciate it because i'm a youtuber and i like to hear my own videos...

---

### Post by w0Rm210 on 2010-06-09
Worked THANKS!

---

### Post by lidex on 2010-06-09
You're welcome! Please mark the thread as solved using 'Thread Tools' up top. Enjoy.

---

