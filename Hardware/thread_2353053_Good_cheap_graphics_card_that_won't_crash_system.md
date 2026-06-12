---
title: "Good cheap graphics card that won't crash system"
date: 2017-02-18
forum: Hardware
---

### Post by anewbie on 2017-02-18
I have a sandy bridge system (2500K); and while the HD 2000 graphics are more than adequate for my needs; the latest update (16.04.2) is causing my system to crash when using parole (to watch videos). 
-
Not 100% sure but i think this likely related to graphic drivers since 16.04 and 16.04.1 both crashed when I used vlc.
-
So the question: is there a good amd or nvidia graphic card that is cheap and at least as fast as the hd 2000 (which is pretty slow). I ahve a 27 inch monitor (1440p) and use the system for web browsing and watching videos. 

Not sure it matters but I run xfce4 not unity interface (I have ubuntu NOT xubuntu).

---

### Post by Autodave on 2017-02-18
Nvidia is the way to go right now. Drivers are in the repositories and I have never had a problem with them. Look around: decent 1G or 2G cards on Amazon and many other places for way less than $100 and 1 gig cards less than $50.

---

### Post by DuckHook on 2017-02-18
> **anewbie said:**
> …Not sure it matters but I run xfce4 not unity interface (I have ubuntu NOT xubuntu).That may be your problem right there. Mixing desktops sometimes leads to wonky behaviour because you are also mixing config files not meant for each other. The driver may not be the culprit at all. Don't take this as a certainty, but rather, as the educated guess that it is.

If I were you, I would run your machine from a LiveUSB of Xubuntu for a lengthy time (days&#8213;not hours) to see if the problem goes away. If it does, then back up your data and do a pristine install of Xubuntu.

If you are happy with the current video performance, then it seems a shame to spring for another video card before testing to see if the problem is not just system misconfiguration. I have an old computer running Xubuntu on a HD 2400 and it works just fine. OTOH, the HD 2000 series *is* getting long-in-the-tooth, so you may want to replace it anyway. However, it is advisable to still go through the process above because new HW is not likely to solve a misconfigured system.

It is also a good idea to check your logs to see if anything is recorded before the system crashes. Especially kern.log and syslog.

---

### Post by DuckHook on 2017-02-18
Also, check to see if you are getting proper cooling. Are all fans running? Especially the one on the video card? What are component temps? Have you installed lm-sensors? Is the PSU as old as the video card? If so, is it outputting unreliable power? Make sure you stress the system while running LiveUSB by installing and using VLC and Parole.

---

### Post by anewbie on 2017-02-18
It is a hard crash; nothing in syslog or kern.log. I don't want xubuntu; I want xfce4. Unfortunately xubuntu adds other crap that i dislike. Are you suggesting I have to run unity to avoid kernel crashes ?

> **DuckHook said:**
> That may be your problem right there. Mixing desktops sometimes leads to wonky behaviour because you are also mixing config files not meant for each other. The driver may not be the culprit at all. Don't take this as a certainty, but rather, as the educated guess that it is.

If I were you, I would run your machine from a LiveUSB of Xubuntu for a lengthy time (days&#8213;not hours) to see if the problem goes away. If it does, then back up your data and do a pristine install of Xubuntu.

If you are happy with the current video performance, then it seems a shame to spring for another video card before testing to see if the problem is not just system misconfiguration. I have an old computer running Xubuntu on a HD 2400 and it works just fine. OTOH, the HD 2000 series *is* getting long-in-the-tooth, so you may want to replace it anyway. However, it is advisable to still go through the process above because new HW is not likely to solve a misconfigured system.

It is also a good idea to check your logs to see if anything is recorded before the system crashes. Especially kern.log and syslog.

The processor is running fairly cool; around 50c under load; 28c most of the time. Ok not perfectly cool but well within spec. Also the memory has been tested for parity error. Note that these tools (vlc for example) worked perfectly under 14.04; they broke iwth 16.04 upgrade. I used to use mpv exclusively but it can't handle h.264 very well so i switch to parole which works fine.

I can run all four cores 48 hours with no crashes using 31GB of ram (I have 32). It is only these video stuff that is caushing crashes and as i noted it was fine under 14.0.4; this problem started with 16.04. With 16.04.1 i could run parole fine. Now with last week upgrade to 16.04.2 parole started causing system crashes.

The video card i currently have is built into the cpu; the psu was replaced 2 years ago when the fan died on the original and it was being replaced under warranty. 

> **DuckHook said:**
> Also, check to see if you are getting proper cooling. Are all fans running? Especially the one on the video card? What are component temps? Have you installed lm-sensors? Is the PSU as old as the video card? If so, is it outputting unreliable power? Make sure you stress the system while running LiveUSB by installing and using VLC and Parole.

Actually I just realized that I added usb dac the same evening I upgraded to 16.04.2 (from 16.04.1) and each time the system halted there was audio clipping so I'm removing the USB dac to see if that solved the problem.

---

### Post by DuckHook on 2017-02-18
> **anewbie said:**
> &#8230;Are you suggesting I have to run unity to avoid kernel crashes ?There's no need to run Unity if you don't like it. But in such cases, it's my practice to install a non-GUI flavour like the server edition or mini.iso, then install only xfce. If you want the convenience of lightdm, you can then also install only that. You will get much closer to that "pristine" environment that would seem to be your goal with none of the unused Unity cruft hanging around, possibly interfering with xfce. It's not running one DE or the other that causes problems, but conflicts that sometimes arise from mixing multiple ones. And keep in mind that my guess may not be the problem at all. It's just part of the process of elimination that one must go through to crack problems of this sort.
> The processor is running fairly cool; around 50c under load; 28c most of the time. Ok not perfectly cool but well within spec. Also the memory has been tested for parity error.&#8230;which eliminates overheating as a concern.> &#8230;the psu was replaced 2 years ago&#8230;so PSU s/b OK too.
>  Note that these tools&#8230;worked perfectly under 14.04; they broke iwth 16.04 upgrade&#8230;It is only these video stuff that is caushing crashes&#8230;this problem started with 16.04.This points to either a kernel that is incompatible or a corrupted upgrade.> With 16.04.1 i could run parole fine. Now with last week upgrade to 16.04.2 parole started causing system crashes.When booting, go into GRUB advanced mode and try using an older kernel. Not 4.8. Try one of the older 4.4 or even further back if you still have them.> &#8230;I added usb dac the same evening I upgraded to 16.04.2 (from 16.04.1) and each time the system halted there was audio clipping so I'm removing the USB dac to see if that solved the problem.Let us know if this solves your issues. Also, I still recommend running for a period using Xubuntu LiveUSB&#8213;not because you will install it&#8213;but to see if a pure Xubuntu environment makes the problem go away.

As sheer guesswork it may be that something got corrupted as part of your upgrade process. With systems that have been upgraded many times, this is sometimes just as problematic as mixing DEs.

---

### Post by anewbie on 2017-02-18
> **DuckHook said:**
> 

As sheer guesswork it may be that something got corrupted as part of your upgrade process. With systems that have been upgraded many times, this is sometimes just as problematic as mixing DEs.
-
My method of upgrading from 14.04.x to 16.0.4 was to install 16.04 on a new system disk and then replace system disks. I actually did this in case i had to 'downgrade'. All data is (/home et all) is kept on a different set of disks.

---

### Post by DuckHook on 2017-02-18
> **anewbie said:**
> -
My method of upgrading from 14.04.x to 16.0.4 was to install 16.04 on a new system disk and then replace system disks. I actually did this in case i had to 'downgrade'. All data is (/home et all) is kept on a different set of disks.…for someone calling him/her/self "anewbie" you sure don't behave like one. These are impressive practices&#8213;all. ;)

---

### Post by SeijiSensei on 2017-02-19
I have one of these [https://www.newegg.com/Product/Product.aspx?Item=N82E16814127870](https://www.newegg.com/Product/Product.aspx?Item=N82E16814127870) which costs $100.  It works fine with Linux and Windows including support for the Windows games I play which are most RPGs from Steam, GOG, or EA.  To install the proprietary driver, I just run
```
sudo apt-get install nvidia-current
```

For cheap, sub-$50 options look here: [https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600030348&IsNodeId=1&bop=And&Order=PRICE&PageSize=60](https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600030348&IsNodeId=1&bop=And&Order=PRICE&PageSize=60).  This looks like a strong contender: [https://www.newegg.com/Product/Product.aspx?Item=9SIA1N83WZ4129](https://www.newegg.com/Product/Product.aspx?Item=9SIA1N83WZ4129)

---

### Post by Yellow Pasque on 2017-02-19
> the latest update (16.04.2) is causing my system to crash when using parole (to watch videos).

Did you update to the newer (4.8.x) kernel and X stack included with 16.04.2 ?

> Note that these tools (vlc for example) worked perfectly under 14.04; they broke iwth 16.04 upgrade. I used to use mpv exclusively but it can't handle h.264 very well so i switch to parole which works fine.

I would suspect something is wrong with VA-API on your GPU. Have you tried forcing software rendering to see if that behaves the same? mpv always worked well with h.264 for me for whatever card/driver I was using, but then I've always stuck to vdpau output.

> is there a good amd or nvidia graphic card that is cheap and at least as fast..
A lot of folks seem to like the RadeonHD 6450. I've personally used a RadeonHD 4550 and a GeForce 8400GS for cheap (and passively cooled) video playback cards.

---

### Post by mörgæs on 2017-02-20
> **anewbie said:**
> HD 2000 graphics...

Am I correct assuming that you refer to Intel HD 2000, not AMD HD 2000?

---

### Post by gordintoronto on 2017-02-20
One of the cards on Seiji's list is this one: [https://www.newegg.com/Product/Product.aspx?Item=N82E16814126089](https://www.newegg.com/Product/Product.aspx?Item=N82E16814126089) 

It would be my choice if I lived in a relatively dust-free environment.

---

### Post by anewbie on 2017-02-28
Hum I made an update but it was lost. Yes I am using a sandy bridge 2500k without graphic card so intel hd 2000. I did an update to 16.04.2; so I presume that would include all updates provided by 16.04.2. I was on 16.04.1. Without the DAC the crash rate is much lower; so far approx once in 3 to 4 days.  Not sure why I said 4.8; the kernel is 4.4.0-64.

---

### Post by mörgæs on 2017-02-28
Have you tried a live boot of 16.10 or 17.04 (beta) for comparison?

---

### Post by anewbie on 2017-03-03
The issue is too hard to reproduce on demand; but i'm leaning towards a dead lock in the new xserver or video driver. I'm not sure what actually runs in kernel mode and what runs in user mode. I'm pretty sure the driver itself runs in kernel mode. The reason I think it is in the video and a deadlock is i notice repeatedly that for example bringing a window on top of the video window is more likely to cause the freeze then just sitting there letting the video play. The video is set to x11/Xshm/xv mode which I believe uses hardware support for playing the video (software mode that mpv uses seems to stutter).

---

