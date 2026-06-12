---
title: "Magic Mouse and Multitouch on 11.10"
date: 2011-12-16
forum: Hardware
---

### Post by vaguely_clear on 2011-12-16
I am reluctant to post this question, because I feel like my issue is probably covered in detail somewhere and I just can't find it. That said, I've been searching myself in circles for about an hour, so I think it's time to post:

I just installed 11.10 earlier this week, and paired my Magic Mouse today. Shouldn't I have some basic multitouch functionality out of the box?

The internet seems to suggest that I should, but nothing on my end. The mouse has basic functionality, including scrolling, but nothing beyond that. Relevant info:

1. Ubuntu 11.10 on older AMD x64

2. To get "natural scrolling" working, I did the .Xmodmap thing a few days ago: [http://maketecheasier.com/reverse-mouse-scrolling-direction-in-ubuntu/2011/09/16](http://maketecheasier.com/reverse-mouse-scrolling-direction-in-ubuntu/2011/09/16). Perhaps this is causing an issue?

3. The Magic Mouse is connected via a D-Link USB dongle. Surely that's not causing an issue?


Suggestions would be greatly appreciated. I am a relative n00b, but I can follow instructions well, if there is something I could do to provide more info.

---

### Post by vaguely_clear on 2011-12-17
I tried setting .Xmodmap back to it's default and logging in again, no dice.

---

### Post by vaguely_clear on 2011-12-17
Following instructions found here: [https://wiki.ubuntu.com/Multitouch/AppleMagicMouse](https://wiki.ubuntu.com/Multitouch/AppleMagicMouse) I tried:
```
lsmod | grep magic
```

Which returned:
```
hid_magicmouse         17938  0 
hid                    95463  3 hid_magicmouse,hidp,usbhid

```

I also ran:
```
sudo lsinput
```

Which returned, among other things:
```
/dev/input/event8
   bustype : BUS_BLUETOOTH
   vendor  : 0x5ac
   product : 0x30d
   version : 774
   name    : "matt’s mouse #1"
   phys    : "00:17:9A:2A:F2:62"
   uniq    : "28:CF:DA:BC:45:BB"
   bits ev : EV_SYN EV_KEY EV_REL EV_ABS EV_MSC
```


I intended to take my new found device name and set up PyMT as per the instructions on this page, but it links to a PyMT page which apparently doesn't exist yet: [https://wiki.ubuntu.com/PyMT](https://wiki.ubuntu.com/PyMT) 

Back at a stand still.

---

### Post by vaguely_clear on 2011-12-17
I also just ran:
```
sudo apt-get install utouch
```

thinking maybe it hadn't been installed for whatever reason. It seemed to install fine, but no progress.

---

### Post by vaguely_clear on 2011-12-18
Well, I did a clean install of 11.10 (my previous install was pretty young, anyway) but it didn't help. Still without multitouch.

Anybody?

---

### Post by vaguely_clear on 2011-12-19
Well, I've been using Gnome Shell today and really loving it, but I would still prefer Unity if I could get multitouch working.

Something occurred to me this evening - should this thread be in the Apple Users forum? I'm running on amd64, but if it needs to be moved, mods, please do so!

Perhaps I'll get some traffic over there. :/

---

