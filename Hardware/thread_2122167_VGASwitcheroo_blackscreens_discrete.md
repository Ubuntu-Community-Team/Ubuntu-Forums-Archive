---
title: "VGASwitcheroo blackscreens discrete"
date: 2013-03-04
forum: Hardware
---

### Post by Diskdoc on 2013-03-04
On Quantal 12.10 64-bit I have vgaswitcheroo set up nicely with permissions and things. Booting up my Acer TimelineX 3820T the situation is

> diskdoc@sector7:~$ cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:02:00.0
2:DIS-Audio:+:Off:0000:02:00.1

and I try to do

> 
echo ON > /sys/kernel/debug/vgaswitcheroo/switch


or

> echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch

and my screen goes black. I can still do ctrl+alt+f2 and ctrl+alt+del after which I can quickly see a few FB messaged swoshing by before reboot.

What's up with that, anyone else had the same?

---

### Post by Diskdoc on 2013-03-04
[Found the bug!]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1077675")

---

