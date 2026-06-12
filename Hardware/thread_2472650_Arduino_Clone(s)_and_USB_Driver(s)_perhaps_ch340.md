---
title: "Arduino Clone(s) and USB Driver(s) perhaps ch340"
date: 2022-03-07
forum: Hardware
---

### Post by patrickworth on 2022-03-07
Hi All,

I've been searching the net for weeks now and haven't seen anything definitive yet.

My scenario is that i had a bunch of adafruit and elegoo arduino clones and they were working prior to my 20.04 upgrade. Then a few weeks/months ago i dusted off some of my robotics projects with my students and found that the Elegoos were not even being scene as a usb device and the others were giving me *intermittent* (i have all of permissions set up correctly and pure arduino Unos continued to work correctly.) 

I found a few references to some kind of linux kernel bug re: the ch340/ch341 drivers and perhaps the upstream changes were not carried through to ubuntu oem.

I keep my system up to date and after the last update or two and finishing up projects I returned back to this. I found that all of the issues i was having are resolved now with arduino and adafruit boards. However, my elegoo Uno R3 clone is still not recognized at all as usb. Aka, no activity in dmesg and not seen by lsusb. So, i am kind of guessing that there were some kinds of changes to usb drivers that fixed a lot but wondering if something was missed.

I was just wondering if there is a none issue/work around. I got a bunch of them for my robotics team and i'd like to be able to use them. I had thoughts of seeing if that issue remains with 21.xx; thinking that maybe upstream change(s) may have been incorporated.

I can post a whatever config set up i have if anyone has seen this at all. I am sure this is not priority on anyone's list but wondering if everyone using Ubuntu should avoid Elegoo Uno clones.

**Linux -Precision-3560 5.14.0-1024-oem #26-Ubuntu SMP Thu Feb 17 14:35:50 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux**

---

