---
title: "HDMI issues"
date: 2014-12-31
forum: Hardware
---

### Post by supercabbageuk on 2014-12-31
I have a Ubuntu 14.04.1 installation running on a AMD A4-5300 AMU paired with a Gigabyte F2A88XN-WIFI, built the whole thing a couple of days ago and I'm using it as a media server running Plex, SickRage and Couch Potato. So far so good, however I noticed that it doesn't boot with HDMI plugged into a TV, it gets as far as the Ubuntu loading screen (the 5 dots) then seems to hang. I can't SSH into the machine either at this point either. I used an old monitor connected via DVI to get install everything (which worked fine, no issues with it not booting) but as it sits next to my HDTV I'd really like to be able to get them working together so I can run a Genesis/Megadrive emulator and the like. 

I'm pretty familiar with Ubuntu, I've used the server edition nearly every working day for the last 3 years or so but I'm really struggling here.

Thanks for any help :).

---

### Post by Gustaf_Alhll on 2014-12-31
Have you tried VGA, or any other adapter?
If that works, try booting up the computer without the HDMI-adapter attached and once you reach the login screen/desktop, connect the HDMI to your TV-Screen/Computer (Depending on what you disconnected).
The next thing you should try is a different screen (Monitor or TV, doesn't matter). It could be the drivers failing.

---

### Post by supercabbageuk on 2014-12-31
I tried DVI on the monitor which worked fine, unfortunately I can't test the HDTVs VGA port as my motherboard doesn't have VGA out. If I boot using DVI, then connect HDMI I get a garbled display (white background, lots of distorted black blocks on top of the white) on both displays, then it becomes unresponsive via SSH. Is there a command I can run or flag I can set to make Ubuntu detect and install drivers for its displays on boot?

---

### Post by iceman30ad on 2014-12-31
had the same issue, steps i took were reinstalled connected to dvi. installed the propitary drivers and dkms (sp? but you know what im meaning) then connected dmi and rebooted

---

### Post by supercabbageuk on 2015-01-01
> **iceman30ad said:**
> had the same issue, steps i took were reinstalled connected to dvi. installed the propitary drivers and dkms (sp? but you know what im meaning) then connected dmi and rebooted

Thanks, this did the trick.

[LIST]
[*]Powered down
[*]Booted with DVI monitor
[*]Installed proprietary drivers
[*]Powered down
[*]Booted with both DVI and HDMI monitors connected
[*]Success
[/LIST]

---

