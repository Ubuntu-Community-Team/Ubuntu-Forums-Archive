---
title: "Bluetooth Issues - 14.04 Based releases"
date: 2014-05-23
forum: Hardware
---

### Post by Allan_Christean on 2014-05-23
I have now installed lubuntu 14.04, xubuntu 14.04, and Mint 17 Mate edition RC on two separate computers, with two separate usb bluetooth adapters. On all three installed, I cannot get "blueman" to navigate and connect an audio sink to my bluetooth stereo headset. All three behave exactly the same - it will pair, say I can have "headset" service, but not the audio sink - it just says "failed to connect", "connot connect to stream" even though it is paired. I've searched all over for help with this - and there is quite a silence out there on this issue - what am I doing wrong? I'm not sure how to clarify the issue, but I've toyed around with all the different settings in blueman; I've deleted and re-paired with my headset I don't know how many times now. There simply is no option to output audio to the headset.

In Ubuntu 13.10 or Mint 16 Cinnamon... no issues at all. It simply pairs and connects and is immediately available as an audio output option under sound settings. Piece of cake. Not so easy with 14.04. Please help!!!

---

### Post by Allan_Christean on 2014-05-24
I've now tried to connect an external bluetooth speaker, in addition to the stereo headset. Still the same issue that I can't remedy. If anyone has any suggestions I'd sure appreciate it. I cannot link any bluetooth audio device as an output option in any of the 14.04 based releases I've tried as I noted above.

---

### Post by Allan_Christean on 2014-05-26
So, I discovered that when searching for A2DP this is not only my issue... at least there are numerous others out there with the same "kind" of issue with blueman and previous releases of Ubuntu variants. I've tried all sorts of tweaks to pulseaudio settings (following other threads), installed all kinds of options from the software manager relating to bluetooth and pulseaudio to no avail. Most of the fixes are years old, and it appears that enough has changed with pulseaudio or Blueman to make those fixes not even relevant any more. This is crazy, am I really the only guy who has this kind of a serious issue with xfce, lxde, and mate? WTH? I have two older computers, which run Windows 7 fine, the exact same hardware. Cinnamon, KDE, and Ubuntu+Unity run sloooow but run bluetooth audio sink to my devices without a hitch - same d*mn hardware! The aforementioned lightweight DE variants are excellent at everything else BUT I can't use bluetooth. This is a deal killer for me, and maddening. 

I've now tried two totally different stereo bluetooth headsets (borrowed one) and a Braven bluetooth speaker. None of them will work - cannot connect as an audio sink A2DP and have it listed as an output option. 

Is there a way to remove everything associated with Blueman and use whatever is default in Ubuntu+Unity or Cinnamon installs? Is that what is called Bluez? What about Bazaar? I've broken the bluetooth now twice trying all kinds of tweak necessitating a reinstall of xubuntu - I even tried 13.10 with the same issue. I guess I get to wait until this is really fixed somewhere down the road or I get better hardware to run one of the other options. Stupid.

---

### Post by vasa1 on 2014-05-26
I hope at least one of the many Xubuntu users drop by to help you. I don't know anything about Bluetooth but I find it a bit "hit-and-miss" on Lubuntu 14.04 when I try to send and receive small files to and from my cheapo Android phone (GT-S7562).

---

### Post by editor-mushtaqbhat on 2015-01-01
Had a similar problem. I seemed to have however overlooked the one option in bluetooth device settings. There should be one for "Audio Profile" The default is off. Set it to AD2P.
If it does not work, try the command: pulseaudio -k first in terminal. After that choose your device in bluetooth device manager window and click "refresh services" and then reconnect via Audio Profiles and not Set Up! 
The Setup has a default setting for headsets. Leave it unchanged. This has worked for me. 
Looking around the forums, I have not been able to find a resolution for the problem completely though. I still have to use the command: pulseaudio -k  at each log in. 
The older issues are related to missing bluez profiles for pulse audio to use. That issue seems to have been resolved, since the blueman configuration does show an option for Audio Profiles. You may have however other issues related to your hardware.

---

### Post by astrodarwin on 2015-02-02
It worked for me with pulseaudio -k, thanks a lot.

---

### Post by astrodarwin on 2015-02-02
I forgot to say that first you must install the bluetooth module (sudo apt-get install pulseaudio-module-bluetooth) and then execute pulseaudio -k with your local user (not sudo).
But there's another problem, when you disconnect or turn off the bluetooth device, audio crashes, and the only way to reconnect is restarting the pc (restarting pulseaudio doesn't work).

---

