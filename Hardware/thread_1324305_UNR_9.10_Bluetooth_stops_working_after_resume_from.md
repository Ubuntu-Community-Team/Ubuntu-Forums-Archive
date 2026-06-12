---
title: "UNR 9.10 Bluetooth stops working after resume from suspend"
date: 2009-11-12
forum: Hardware
---

### Post by outdoorsman14 on 2009-11-12
Hello, new user to Ubuntu Netbook Remix and had a question about resuming from suspend. I have a Toshiba NB205 netbook and I have the classic issues that come with it being installed with Ubuntu, no bluetooth and no speaker output. I was able to get my bluetooth to work with the omnibook-source code, but only when I boot it up. After I suspend it and resume from the suspend my bluetooth goes away. i was able to get it to work by modifying the /etc/modules file with the line 'omnibook ectype=14', is there another file that gets accessed on resume that I could add that line to for it to work after a suspend? I only worry about it, because I have my computer go to sleep after a certain period of time to conserve battery life and if I want to use my bluetooth mouse afterwards I have to restart my computer. Any help would be great.

On a side note, if anyone knows how to get the internal speaker to work, that would be a plus. the headphone jack works and the internal mic works, just no sound out of the speaker. I had found some patches, but could not get them to work properly. It's not a very big deal since the speaker is crap anyways, but it would be nice to have the full functionality of the computer.

---

### Post by outdoorsman14 on 2009-11-24
Bump, anyone have any ideas?

---

### Post by chauser on 2010-05-01
With UNR 10.4 and the omnibook module installed (and working) I also had the problem that bluetooth was not working after suspend. Searching for more info about the omnibook module I found this gem[INDENT][FONT=Courier New]echo 1 > /proc/omnibook/bluetooth[/FONT]
[/INDENT]will turn on the bluetooth hardware so that it can again be controlled by the bluetooth app on the system menu. Note that this needs to be done as root.

(I wouldn't be surprised if [INDENT]     echo 1 > /proc/omnibook/wifi
[/INDENT]would also work to turn on the wireless on this if it has been turned off in Windows before booting linux -- a problem that some have complained about -- but I have not tested it.)

---

