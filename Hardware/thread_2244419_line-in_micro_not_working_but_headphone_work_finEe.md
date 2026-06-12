---
title: "line-in micro not working but headphone work finEe?"
date: 2014-09-16
forum: Hardware
---

### Post by Dinh_Quoc_Han on 2014-09-16
Pleaze help me. line-in micro not working but headphone work fine.
I used to use Windows XP, 7. It's working fine. But I try Install Ubuntu 14.04.1, More device working well, but source input not work, My laptop have 1 input 2in1 headphone and micro. pleaze help me.
p/s: My Englist is very bad

---

### Post by Yellow Pasque on 2014-09-16
Please give a lin to your audio information: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Dinh_Quoc_Han on 2014-09-16
```
.sh && bash alsa-info.sh
--2014-09-16 17:57:32--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org (www.alsa-project.org)... 77.48.224.243
Connecting to www.alsa-project.org (www.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-utils.git;a=blob_plain;hb=refs/heads/build;f=alsa-info/alsa-info.sh [following]
--2014-09-16 17:57:34--  http://git.alsa-project.org/?p=alsa-utils.git;a=blob_plain;hb=refs/heads/build;f=alsa-info/alsa-info.sh
Resolving git.alsa-project.org (git.alsa-project.org)... 77.48.224.243
Connecting to git.alsa-project.org (git.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2014-09-16 17:57:36 ERROR 404: Not Found.

```

?

---

### Post by Dinh_Quoc_Han on 2014-09-16
i cant get my infomation device. can you help me?

---

### Post by Dinh_Quoc_Han on 2014-09-16
> **Temüjin said:**
> Please give a lin to your audio information: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

My ALSA information is located at [http://www.alsa-project.org/db/?f=1481d6c276ad74143191e466ea762eb115d9f84a](http://www.alsa-project.org/db/?f=1481d6c276ad74143191e466ea762eb115d9f84a)
please help me !

---

### Post by Dinh_Quoc_Han on 2014-09-17
please every one help me

---

### Post by QIII on 2014-09-17
Hello.

Please remember that the community is world-wide and that our members live in all time zones.  You cannot reasonably expect people to always be on hand when you are awake.  Neither can you reasonably expect an answer at a moment's notice.

We used to have a rule that you could not bump your threads any more often than 24 hours.  We have relaxed that.  However, your repeated bumping is verging on abuse of the new rules.

Please be patient and wait for an answer.  You already had one -- from a very knowledgeable member -- who may be back to continue if you will refrain from impatience.

Thanks.

---

### Post by Dinh_Quoc_Han on 2014-09-17
I am sorry. I wait for answer !

---

### Post by Yellow Pasque on 2014-09-19
The first thing to try is the latest driver: 

```
cd ~/
sudo apt-get install dkms
wget https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201409161916%7Eubuntu14.04.1_all.deb
sudo dpkg -i oem-audio-hda-daily-dkms_0.201409161916~ubuntu14.04.1_all.deb
```

Reboot and check the line-in.

---

### Post by Dinh_Quoc_Han on 2014-09-21
> **Temüjin said:**
> The first thing to try is the latest driver: 

```
cd ~/
sudo apt-get install dkms
wget https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201409161916%7Eubuntu14.04.1_all.deb
sudo dpkg -i oem-audio-hda-daily-dkms_0.201409161916~ubuntu14.04.1_all.deb
```

Reboot and check the line-in.

Not working bro!

---

### Post by Yellow Pasque on 2014-09-21
I may have overlooked something in your information:
```
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 22 [71%] [-1.50dB] [off]
  Front Right: Playback 22 [71%] [-1.50dB] [off]
```

You may need to enable the microphone in alsamixer (using spacebar). Command:
```
alsamixer
```

---

### Post by Dinh_Quoc_Han on 2014-09-21
[IMG]http://i.imgur.com/NdUCafx.png[/IMG]
I dont know to enable :(

---

### Post by Yellow Pasque on 2014-09-21
Go to the one that says 'Mic' and press the 'M' key to unmute.

---

### Post by Dinh_Quoc_Han on 2014-09-22
> **Temüjin said:**
> Go to the one that says 'Mic' and press the 'M' key to unmute.

It's not working pro, my headphone very noisy while press "M" at 'Mic'

---

### Post by Yellow Pasque on 2014-09-22
At this point, I suggest filing a bug report. Make sure the mic is unmuted before you do. This will also gather your updated ALSA information:
```
ubuntu-bug audio
```

---

