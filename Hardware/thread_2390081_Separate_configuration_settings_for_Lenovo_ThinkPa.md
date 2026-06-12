---
title: "Separate configuration settings for Lenovo ThinkPad TrackPoint and TouchPad"
date: 2018-04-25
forum: Hardware
---

### Post by ward388 on 2018-04-25
Hi,

I want to configure the TrackPoint (little round red trackstick above the B-key) of my Lenovo ThinkPad T450.
But I want to leave the configuration settings of my TouchPad unchanged.

In KDE > Settings > Input, no special TrackPoint settings are shown, only Touchpad settings.

Is it possible to have separate configuration settings for the Touchpad and TrackPoint?
How to configure Lenovo ThinkPad TrackPoint independent of the Touchpad settings?

I'm using Kubuntu 16.04 LTS. 
Since I just installed my machine, I'm willing to switch to another version if it is possible over there.

Thanks!

---

### Post by tinylagarto on 2018-04-26
I have a T400 but I use Xfce. Though in the touchpad settings I can access both, the touchpad and the trackpoint because in the settings is a dropdown menu. Is there something similar in KDE? Just switch from Synaptics Touchpad to IBM TrackPoint and you can configure them separately.

---

### Post by mircsicz on 2018-04-27
You might wanna try what "xinput list" returns... If that see's two different devices you might configure them independently using X config

---

### Post by ward388 on 2018-04-28
Thnx!

Unfortunately I can't find separate configuration options in Kubuntu KDE for the touchpad and trackpoint. (If somebody does know where that option is in Kubuntu KDE, please send a screenshot with an arrow where I need to look :-))

But xinput list does return two different devices :-)

```

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=14   [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                     id=15   [slave  pointer  (2)]

```

How can I start X Config or where can I find the X Config file which I need to edit?

---

