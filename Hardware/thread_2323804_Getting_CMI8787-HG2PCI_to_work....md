---
title: "Getting CMI8787-HG2PCI to work..."
date: 2016-05-08
forum: Hardware
---

### Post by Tahiro Hashizume on 2016-05-08
The body of the issue mostly follows that of [my previous post in 2013]("http://ubuntuforums.org/showthread.php?t=2137922"). At the time, I seem to have given up on using the device under Ubuntu after finding that I was not getting anywhere. While being distant from the issue, I had also come to assume that someone else may have already worked on getting this device to work - wrong.

UbuntuStudio 16.04 doesn't list the device in 
```
aplay -l
```
So I decided that I'd work on the issue again. This time, the cause might be the driver, or something else. But for start, let me inform that the device is indeed listed in 
```
lspci
```


Supposing the issue's cause to be the lack of entry or improper implementation in ***oxygen.c***, it means I would have to work on it again like I once attempted to do so just three years ago.


As I have just foud out, there seems to have been a change in the method by which users trying to work on the alsa-driver should now use 
```
bzr branch http://bazaar.launchpad.net/~ubuntu-audio-dev/alsa-driver/ubuntu
```
instead of 
```
apt-get source alsa-driver
```
to get access to the codes.


As I'm not a frequent developer on issues of this kind, brief instructions and procedures on setting up a development environment for adding a new entry to alsa-driver would also be much appreciated.

The PC that I have the device plugged in is *SG31G2* by *Shuttle*.

Thanks in advance.

---

### Post by him610 on 2016-05-08
Welcome back to the Ubuntu forum, Tahiro Hashizume

My Shuttle is a model *SN68S*. It is going on eight years now since I built it - probably my favorite machine.

Were you perhaps aware of this post?
[http://www.phoronix.com/scan.php?page=news_item&px=OTA4MA]("http://www.phoronix.com/scan.php?page=news_item&px=OTA4MA")

I am not an audio guy. If it works, it works; if it doesn't, it doesn't.

---

### Post by Tahiro Hashizume on 2016-05-08
When I do
```
dpkg -l | grep alsa
```
I get
 ```

ii  alsa-base  1.0.25+dfsg-0ubuntu5  all  ALSA driver configuration files
ii  alsa-source  1.0.25+dfsg-0ubuntu5  all  ALSA driver sources

```
so I'm assuming I'm on 1.0.25.

Users of the same sound interface reported some odd behaviour when installing the driver for it under Windows 7 (described [here]("http://ameblo.jp/arimasou16/entry-10984770151.html") in Japanese).
If the issue has something to do with a possibly broken hardware configuration written inside its EEPROM, I'm willing to work on it. In fact, that is more of my thing than messing with source code of kernel modules. It'll well be worth some effort for me since the device has got a decent DAC chip.

---

