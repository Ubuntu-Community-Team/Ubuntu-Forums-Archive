---
title: "Fujitsu Siemens si1520 - suspend problems"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by deNniZ on 2006-09-06
Hi,

I have a FSC si1520 laptop, everything worked out of the Box with kubuntu except suspend to RAM and suspend to Disk.

If i go to suspend to RAM the laptop gpes to sleep but when waked up nothing happens the screen stays black even on runlevel 1 it does that.

Suspend to Disk only works once (after that it doesn't even power off) and gets really buggy with my WLAN (after resume WLAN doesn't really work)

Here are some Specs:

Intel Core duo 1.83 ghz
kernel 2.6.15-686-smp
chipset intel ICH7
Graphics Intel GMA945
2gb of RAM
WLAN ipw3945

if u need any more information pls ask.

---

### Post by jogege on 2006-09-09
Sorry I cant help you but what are your impressions of this laptop? Would you recommend it for someone to buy? I am trying to make up my mind between this and an Asus A8.

---

### Post by deNniZ on 2006-09-09
Hi, I have this laptop now for 2 weeks and I really enjoy it. It's small and fast. What I don't like is the glare panel, I prefer bright panels which the mac books have.

Ubuntu worked here really out of the box with some small issues, like wrong resolution and no smp kernel but that's minor things. What really annoys me is the fact that suspend doesn't really work, well suspend to disk now works but suspend to ram doesn't.

I like this notebook, but for fact it's my first laptop, so I can't really compare it to any other laptop.

---

### Post by jogege on 2006-09-09
I really like the form factor as well. I did go into a store on Tottenham court road in London last week to have a feel for it.Looks pretty good and I might just end up buying one.

Only reason am holding back is the 2 years Warranty on Asus and the 3 years C&R warranty on a Rock Pegasus 330 is also very tempting.

Hope you are able to resolve the suspend issue and regarding smp, are you using a 686 kernel?

---

### Post by ubuntu_demon on 2006-09-09
here's another thread about the same laptop :
[http://www.ubuntuforums.org/showthread.php?t=208957](http://www.ubuntuforums.org/showthread.php?t=208957)

I'm also searching for a good laptop to buy :
[http://ubuntuforums.org/showthread.php?t=247158](http://ubuntuforums.org/showthread.php?t=247158)

---

### Post by ubuntu_demon on 2006-09-09
Try this to sovle your suspend problems and let us know whether it worked :

[http://www.amilo-forum.com/topic,148,56249cae16aac0c9b0b06939b151bbf4,-amilo-si-1520.html#631](http://www.amilo-forum.com/topic,148,56249cae16aac0c9b0b06939b151bbf4,-amilo-si-1520.html#631)

it's a post from this thread :
[http://www.amilo-forum.com/topic,148,-amilo-si-1520.html](http://www.amilo-forum.com/topic,148,-amilo-si-1520.html)

---

### Post by xyz on 2006-09-09
I've just tried this script to suspend my Toshiba Satellite A40 and it works fine.
**Manolis Tzanidakis**, the author seems to say that it should work on any laptop!
Let us know...
[http://www.linux.com/article.pl?sid=06/05/24/1716222](http://www.linux.com/article.pl?sid=06/05/24/1716222)

---

### Post by deNniZ on 2006-09-09
> I've just tried this script to suspend my Toshiba Satellite A40 and it works fine.
Manolis Tzanidakis, the author seems to say that it should work on any laptop!
Let us know...
[http://www.linux.com/article.pl?sid=06/05/24/1716222](http://www.linux.com/article.pl?sid=06/05/24/1716222)

this works at first but then i realised my rootfs is umounted and I only can use things which are stored in ram right now.

remounting with mount / -o rw or mount / -o remount,rw end up in mounting Read-Only then when I do ls . it works if I do ls -l I get Bus error. Anyone got an Idea? Seems to be my SATA modules that forked up. Ah and sound doesn't work after resume too. Maybe I will make a short video with my camcorder for u to get an Idea.

---

### Post by deNniZ on 2006-09-09
> Try this to sovle your suspend problems and let us know whether it worked :

[http://www.amilo-forum.com/topic,148...-1520.html#631](http://www.amilo-forum.com/topic,148...-1520.html#631)

it's a post from this thread :
[http://www.amilo-forum.com/topic,148...o-si-1520.html](http://www.amilo-forum.com/topic,148...o-si-1520.html)

I think he means STD which works for me too.

Only STR forks up, I want it working!!11 :-)

Thanks for ur help and research ;-)

---

### Post by deNniZ on 2006-09-09
> **deNniZ said:**
> this works at first but then i realised my rootfs is umounted and I only can use things which are stored in ram right now.

remounting with mount / -o rw or mount / -o remount,rw end up in mounting Read-Only then when I do ls . it works if I do ls -l I get Bus error. Anyone got an Idea? Seems to be my SATA modules that forked up. Ah and sound doesn't work after resume too. Maybe I will make a short video with my camcorder for u to get an Idea.

Ok I found out why, the FSC has a Bios Option which reads:

SATA Mode: -> Enhanced or Compatibility if u set to Compatibility everything works out of the box. Is there any laptop forum where I can write down all "tricks and tweaks" for this specific notebook?

And btw. for all searching for a Notebook where everything works nearly out of the box the FSC si1520 could be your choice. :-)

---

### Post by ubuntu_demon on 2006-09-10
> **deNniZ said:**
> Ok I found out why, the FSC has a Bios Option which reads:

SATA Mode: -> Enhanced or Compatibility if u set to Compatibility everything works out of the box. Is there any laptop forum where I can write down all "tricks and tweaks" for this specific notebook?

And btw. for all searching for a Notebook where everything works nearly out of the box the FSC si1520 could be your choice. :-)
Great.

Maybe you can elaborate on this and write a detailed guide of the few steps you have done to make everything work :)

---

### Post by elvstone on 2007-01-04
I would also very much like to know how you got both STR and STD to work on this laptop. I just got this laptop yesterday. I can't get either to work. I got STR working once yesterday, but now it's no longer working (the keyboard stopped working after resume).

I have the SATA mode setting set to Compatibility.

Best regards,
Aron Stansvik

PS. I have the ipw3945 wifi driver loaded, maybe that could be a problem? DS.

---

### Post by deNniZ on 2007-01-11
Well I used Ubuntu where it didn't work and in Kubuntu it works perfectly, don't ask me why ;-)

I prefer kubuntu anyway.

---

### Post by backup on 2007-12-21
I'm having this problem too. Has anybody gotten the FSC Amilo Si 1520 to suspend correctly with Ubuntu Gutsy?

It's the only black mark on an otherwise great combo...

---

