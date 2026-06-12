---
title: "Hello from new guy with a question"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by abbacan on 2005-12-29
I'm not sure if this is the proper place to ask this or not. There seems to be some pretty strict rules here. Oh, Hi everybody.

I've been playing with various Linux distros (none of which have been Debian based) for several years so I can't use the newby section. I haven't switched to Ubuntu yet so I can't post to Gnome or KDE threads. I don't have any installation problems, configuration problems or any "How to's" or "FAQ's" I just have a simple basic question.

If I install Ubuntu can I install programs from my Debian Sarge cd's?

I live in a rural area and can only get very slow (26 Kbps) dial-up so down loading anything is out of the question.

Thanks

---

### Post by dbeckham32 on 2005-12-29
I belive you can. You'll have to add the CD to your list of respositories in Ubuntu. They are stored in the /etc/apt/sources.list file. A CD entry in that file might look like this (edit the CD name to match):

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

Alternatively, use Synaptic to add the CD to your list of respositories.

When you're finished, don't forget to run:

$ sudo apt-get update

---

