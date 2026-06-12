---
title: "Couldn't find linux-ubuntu-modules-2.6.27-9-generic"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by eyal_barouk on 2009-01-19
Hi,
ubuntu 8.10
2.6.27-9-generic
Very new to linux

I am trying to get my sound card to work.

When I type
$ sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic

I get:
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.27-9-generic"

I have installed:
linux-backports-modules-2.6.27-9-generic
linux-restricted-modules-2.6.27-9-generic
linux-restricted-modules-common
linux-restricted-modules-generic

but still get the same "Couldn't find any package" message.

Searching the web didn't help any

Thank you,
Eyal

---

### Post by eyal_barouk on 2009-01-20
To answer my own question:

First, I got it to work!
I would like to share my findings.
My troubles began when I read
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")
Which is not for 8.10 I guess

Currently I have OSS installed
My sound card is M-audio 2496
When I type: 
aplay -l
I get: 
aplay: device_list:215: no soundcards found...

But still the sound works...

When I type: 
find /lib/modules/`uname -r` | grep snd
I get only:
/lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/media/snd-bt-sco.ko

But still the sound works...

OSS have installed all the drivers I needed
After a restart I went to System > prefs > Sound and set all to OSS M-audio
And walla!
I hope this helps anyone...
Eyal

---

