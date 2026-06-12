---
title: "Medion Akoya E5312"
date: 2008-08-06
forum: Hardware
---

### Post by Dorrax on 2008-08-06
I just purchased a Medion Akoya E5312 and wiped Vista for Ubuntu. I have never used Ubuntu before, so I have a couple problems. I can't use wireless or hear any sound. I've read several threads on sound issues and can't solve it, and I have yet to address the wireless problems at all.


Here is what I get after running the aplay -l script:

X@X-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
X@X-laptop:~$ 

Does anyone have any experience with this soundcard? I'm not even sure what the name of the soundcard is...

---

### Post by JackDeth on 2008-08-07
I just bought the same system for the same purpose. Well, it's actually for my wife. I'm trying to encourage her to switch to open source (most especially Ubuntu) and have had the exact same problems. Needless to say, she is not impressed so far.  :(

I did, however, get the wireless working after working on it for several days. While Gnome was installed as the default GUI, I also installed KDE so she would have a choice upon bootup. I also installed all the wireless Gnome and KDE tools I could find. I found RutilT WLAN Manager to be useful. What it really came down to, though, was making sure I had the correct network settings in Network in the Administration menu to make the connection work.


I cannot, however, get the sound to work at all. By all rights, everything should work. It all appears to be detected, but sound simply will not play.

lspci shows 01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller.

To find out which model soudcard the computer says it had, I ran the following:
cat /proc/asound/card0/codec#* | grep Codec

It told me it was a SigmaTel ID 7698. I cannot find any drivers anywhere for this.

Does anyone know what we can do about this? I dunno about you but I'm completely new to this and I'm desperate for an answer.


TRS


> **Dorrax said:**
> I just purchased a Medion Akoya E5312 and wiped Vista for Ubuntu. I have never used Ubuntu before, so I have a couple problems. I can't use wireless or hear any sound. I've read several threads on sound issues and can't solve it, and I have yet to address the wireless problems at all.


Here is what I get after running the aplay -l script:

X@X-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
X@X-laptop:~$ 

Does anyone have any experience with this soundcard? I'm not even sure what the name of the soundcard is...

---

### Post by JackDeth on 2008-08-07
Oh yeah, there's also a driver for the wireless at [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html). Try installing that.

---

### Post by Dorrax on 2008-08-11
Bumping this because it's still not fixed.

---

### Post by Dorrax on 2008-08-12
I got sound to work by following instructions here:

[http://ubuntuforums.org/showthread.php?t=780961&highlight=sigmatel](http://ubuntuforums.org/showthread.php?t=780961&highlight=sigmatel)

---

