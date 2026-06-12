---
title: "Using abnormal amount of memory and 2 Xorg?"
date: 2008-07-29
forum: General Help
---

### Post by Qrikko on 2008-07-29
Hi, and thanks for the interest..

Well first of all I haven't re-installed/formate my "/home" partition in a while, might be related to this but to be honest I have to much to do to have time for this right now. So I thought I could cry out for some help.

_The problem:_
It started a while ago now, I think around when ATI's drivers went version 8-5 or so (could be even back to 8-3 or 8-4) and I haven't had the time to really address this so what I did was put another 512mb ram and look happy. Though that is a very temporary solution.

What is happening is that I feel like a lot of "unneeded" memory is used, when I do a fresh restart of the OS it uses what I would consider normal (some few % of memory) but after a little use (like after starting Firefox or so) it tick up to around 36% in use by programs, and 42% in use by cache. and as you see if this is added up I end in a glorious 78% memory being used by default. Abnormal isn't it?

If I CTRL+ALT+Backspace (i.e. restart X) it has the same usage and it's only the full restart that seem to help this problem for a short while, and I would like to get this out of the way.

for your connivance I made this screens:

1) 2 XOrg processes?
[IMG]http://i54.photobucket.com/albums/g110/Qrikko/Linux/2_xorg.png[/IMG] 

2) The system info:
[IMG]http://i54.photobucket.com/albums/g110/Qrikko/Linux/system.png[/IMG]

3) Used resources:
[IMG]http://i54.photobucket.com/albums/g110/Qrikko/Linux/resources.png[/IMG]

4) My partition table:
[IMG]http://i54.photobucket.com/albums/g110/Qrikko/Linux/filesystems.png[/IMG]

*problems that may be related:*
First of all, the picture (1) show that there seem to be a second XOrg process running, could this be something to investigate?

Second, I feel that the problem could be related to the ATI graphics card drivers, and to add to this hypothesis this is some example from a *"cat /var/log/Xorg.0.log | grep WW"*
```

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
...
(WW) AIGLX: 3D driver claims to not support visual 0x72
(WW) Configured Mouse: No Device specified, looking for one...

```
*(where the ... is more like 20 or so entities of the AIGLX warning)*

_Finnish_
Well it's all I have right now, sorry to write so much about it, I hope that someone that know a little more then me feel compelled to have a look at the information and if there is some more info I should provide to help you help me please feel free to say it.

If I had the time to back up work and so on and just wipe the /home for a complete reinstall of the OS I would just do it but I haven't had a formate of /home since.. at lest feisty and my whole idea of keeping /home in one partition is to not need to formate it.

Big thanks for bearing with me.
*OBS! xorg.conf and Xorg.0.log in attachements*

---

