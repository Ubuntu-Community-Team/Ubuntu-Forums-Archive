---
title: "Dell XPS 1530 - 7.10 or 8.04?"
date: 2008-04-29
forum: Hardware
---

### Post by mailforbiz on 2008-04-29
I still have issues with 7.10 and am wondering if I should upgrade to 8.04 or should try to fix the issues in 7.10.

My major issues currently are :

Internal/External mic: tried out all the links that were mentioned in one of the other posts but no-can-do. Installing the backports did no good. I don't have EITHER INTERNAL OR EXTERNAL MIC working. Pretty frustrating as I want to use Ubuntu exclusively but need to use skype for work. Sound worked out of the box

Hibernate:
It seems to go into hibernation but on wakeup, the screen never wakes up though i hear the HD and the fans. I end up turning power off using the power button and rebooting
Suspend: Same as above

Dell travel mouse: Bluetooth works, front/back buttons and side scroll not working

Webcam: low priority but would be great if worked

Any pointers/suggestions? Thanks in advance!!

---

### Post by jespdj on 2008-04-29
Try 8.04. It works great on my M1530. See the link in my signature below.

---

### Post by mailforbiz on 2008-04-29
Thanks, jespdj. Is a new install a better way to go? If thats the case, what are some of the things I should be wary of. I have Vista-Gutsy dual boot and my Ubuntu partitions are 

/
/home
/tmp
swap

Will I be able to reinstall just the root w/o any problems ? Its been a while since I tried an upgrade and I don't know how sophisticated/stable the process is now but I want to make sure everything goes as smoothly as possible. 

Thanks!

---

### Post by mailforbiz on 2008-04-29
Tried the 8.04 live CD and am seeing improvement. The wireless doesn't work but I have to enable the Broadcom driver and hopefully it'll then work (dunno if I can enable using the LiveCD; where will it save the firmware?). The mic works but it has to be configured. Hibernate/suspend still seems broken. I am tempted to just go ahead and reinstall. [B][I]Can someone please confirm that just reinstalling on the root partition will do the trick? 
[/I][/B]
Thanks in advance for all your help!

---

### Post by mailforbiz on 2008-04-29
Well, I took the plunge and did an Upgrade to Hardy from the Update manager (my system was already up-to-date). 

The problems:

*wireless doesn't work now. I have Broadcom BCM4312 chip which I'd got to work in Gutsy with the b43-fwcutter restricted driver. 

*microphone doesn't work (worked with the LiveCD)

I am searching on the forums and I'm kind of confused. Some folks are saying wireless works out of the box and some seem to suggest it works with ndiswrapper after some harakiri. I am relatively new to all this stuff and would appreciate help. It took me a few days of trying before someone told me to use the restricted driver to get wireless working in Gutsy and lo! here we go again - I'm kind of disappointed -  one step forward, two steps backward.

If it helps, I would like to do a clean install but I'm not sure how to reinstall just the root. When I tried, partition mgr didn't show any of my existing partitions on the disk. It showed the entire disk as partitionable. Can someone please, please help me?


Thanks in advance!

---

### Post by mailforbiz on 2008-04-30
Well, I was able to make the wireless work by uninstalling and reinstalling the fwcutter driver in Synaptics. But sound/mic still was a problem. So I decided to do a clean reinstall. Thats when I discovered that my partition table has been truly messed up by Dell Mediadirect. So I'm going through the ordeal of completely wiping out the disk and putting Vista Ubuntu dual boot all over again (but w/o Dells hidden partitions). Will update when done.

---

