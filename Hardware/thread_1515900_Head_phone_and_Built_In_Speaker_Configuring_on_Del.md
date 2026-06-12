---
title: "Head phone and Built In Speaker Configuring on Dell Studio"
date: 2010-06-23
forum: Hardware
---

### Post by black2blacky on 2010-06-23
[SIZE=2]:popcorn:When the head phone is pluged into the front jack the speaker is still blowing when i finished my ALSA 1.0.23 as mentioned below in my Lap

:KS[/SIZE][> [SIZE=2][http://ubuntuforums.org/showthread.php?p=9498759#post9498759](http://ubuntuforums.org/showthread.php?p=9498759#post9498759)[/SIZE]]("http://ubuntuforums.org/showthread.php?p=9498759#post9498759"):KS

:lolflag: for solving the problem,make a small change,

In terminal, follow the command
> sudo gedit /etc/modprobe.d/alsa-base.conf
In that file ,
addup a line as follows at the last,

> option snd-hda-intel model=dell-studio

---

