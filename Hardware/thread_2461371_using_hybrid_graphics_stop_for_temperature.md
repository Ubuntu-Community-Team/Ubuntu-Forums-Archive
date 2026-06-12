---
title: "using hybrid graphics stop for temperature"
date: 2021-04-29
forum: Hardware
---

### Post by laponatty on 2021-04-29
I have just donwgraded my system to xfce as suggested by many user to have a lighter system, but this not save me in any way!

I have the same problems found with mate and gnome, so is not about resources used by the system, but the driver instead!

I have installed 390 adn 340 from apt, "additional driver" and even downloaded from nvidia site.

But the most frustrating thing is that alla works in windows 10!!!!!!! So is not about fans, dust or termal paste! And many linux user, just suggest me to buy a new laptop, that for me is almost unacceptable reply from a "linux's point of view"

These are some hardware infos:
[IMG]https://i.stack.imgur.com/TMwrS.png[/IMG]


if I run nvidia-settings and i try to switch form the options, i have these results:

[LIST=1]
[*]ON DEMAND= pc works untill i have very few thins opens; When starts to ask for resuoruce--->termal; 
[*]PERFOMANCE MODE= same as above; 
[*]INTEL POWER SAVE MODE= The system works a little bit better, but i've severl erros: 
[/LIST]

[LIST]
[*=3]f I select Intel, when i reboot ive this error: > [INDENT] sudo nvidia-settings

 ERROR: NVIDIA driver is not loaded

 ERROR: Unable to load info from any available system

 (nvidia-settings:2418): GLib-GObject-CRITICAL **: 14:00:44.099: g_object_unref: assertion 'G_IS_OBJECT (object)' failed ** Message: 14:00:44.106: PRIME: No offloading required. Abort ** Message: 14:00:44.106: PRIME: is it supported? no

 [/INDENT]
 
[*=3] "additional drivers" is empty; 
[*=3]Nvidia-settings looks like: [IMG]https://i.stack.imgur.com/4Zi2K.png[/IMG] 
[/LIST]

---

