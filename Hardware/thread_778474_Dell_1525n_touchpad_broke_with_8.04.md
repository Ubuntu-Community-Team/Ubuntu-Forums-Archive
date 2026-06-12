---
title: "Dell 1525n touchpad broke with 8.04"
date: 2008-05-02
forum: Hardware
---

### Post by tylersontag on 2008-05-02
A week ago i upgraded to 8.04 on my Dell Inspirion 1525.  I was quite pleased initially, alot of the video problems stemming from the embedded video card were fixed.  Videos played, my screensavers worked correctly.  As i said, i was happy i could enjoy some of the prettier screensavers.

I was watching TV and hadn't used the top in a while, i look over and flocks is running, i stared for a moments, its quite mezmerizing.  THhen my screen froze, black with a multi-colored static.  When i rebooted my touchpad wasn't working.  i looked for some info but found nothing.  i went out that night, when i got back it was working again.  Alas the next morning it wasn't working and ive been on a USB mouse ever since.

I talked with dell, ran some diagnostics and determined its not hardware related.  He had me try to rebuild my xorg with "sudo dpkg-reconfigure xserver-xorg" but it didn't help, and whats more, apparently it doesn't function the same as the previous build, or at least not on mine.

I was alerted to a similar but with 8.04 regarding the touchpad, [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173411](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173411) but thats only regard to the side scroll bar not working.  i've found this: [https://answers.launchpad.net/ubuntu/+question/31505](https://answers.launchpad.net/ubuntu/+question/31505) which seems to be the same problem.   Any ideas?

---

### Post by subzero316 on 2008-05-02
Are you sure you installed the correct video driver???

---

### Post by clw3388 on 2008-05-02
I too am having this issue.. mine is on a xps 1530 of Dells.
It worked fine in v7 but not so on v8...I did have a gsynaptics app installed that helped in v7 but when removed and reinstalled on v8 and it throws errors when you try and open the program about the Option "SHMConfig" "true" listing in my /etc/X11/xorg.conf file even though it is already set to true.. i reset it and also tried other options such as "on" and "false" and "no". It works better on "false" or "no" but is realy slow to respond to movments...takes 5 minutes to get from one side of the screen to the other.. lol.. 

One other note.. this was an upgrade.. I also downloaded the live cd and when booted off it the touchpad is broke as well...

Seems silly that they broke it .. upgrades are supposed to work better not worse than what they are intended to replace... I'll know better next time to stick with the tried and true.. It also broke my biometric with thinkfinger.. Very dissapointing.. 


If i come across a fix i'll try and post it here as well...

---

