---
title: "Is Ubuntu really for laptops?"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by lobstaman on 2006-12-08
Greetings,

I have a T60 (2007-65U) and I have been trying for some time to get Ubuntu up and running on it. Getting the basic Dapper or Edgy installation is not a problem but getting more than that has become a source of frustration. 

For example: after a clean Edgy installation the laptop would usually suspend to ram without any problems but ... after getting the lates updates the ability to suspend to ram disappears. After several clean installations and partial updating I think I have identified a couple of updates that seem to cause this.

Another example is xgl: again stating with a clean Dapper installation suspend to ram works but after installing xgl suspend to ram does not work any more. It seems that there are some serious issues with ATI drivers (my system has the ATI x1400) and Ubuntu I have tried several versions, starting from 8.25 up to 8.31. All of them had serious side effects on the behavior of my system.

Based on this experience I decided to try out another distribution so that I would have some kind of a basis for comparison. I installed SUSE 10.1 and starting from the installation SUSE seem to be handling my hardware much better. It recognized my ATI card (including the chipset, something that I never achieved in Edgy/Dapper), as well as the wireless network card. The power management seem to be working perfectly. suspend to ram as well as hibernate work out of the box. In addition, I noticed that my laptop holds about the same time on battery as it would under xp using the Lenovo thinkpad power management. 

I have tried solving these issues for about two weeks now. I believe I have tried a considerable portion of the various tweaks, fixes, reported solutions. None of these got me to a stable solution that I could work with. Most of the solutions I tried has various side efects, the more serious of them is the inability to generate the gnome configuration deamon without getting an error window. 

The only (technical) downside of SUSE I noticed so far is that it is a bit heavier than Ubuntu, which seem to be more agile. Some people have noted that SUSE is "bloated" compared to Ubuntu -- I agree with that to some extent. 

I have been using Ubintu on Desktops and will continue to do so, and I would really like to use Ubuntu as much as I can on laptops. But, right now it seems to me that it is not really geared towards more recent laptops (T60 in my case) without some serious tweaking, which might work (and even be stable) in some cases and and might not in others.

I have to emphasize that I am not arguing that SUSE is better or that encourage people to use it. I think that Ubuntu is an amazing distribution and phenomenon. What I would like to point out is that at least based on my experience, using Ubuntu on more recent laptops has become a serious problem, especially since the support for basic functionalities such as suspend to ram and recent video cards is lacking and even lagging behind other distributions. Since more laptops are being sold every year, it seems to me that good laptop support will become essential for the long term survival of any distribution. Just some food for thought ....

---

### Post by K.Mandla on 2006-12-08
A valid point, and one most people would agree to, so long as the crux of your post is that newer hardware doesn't fare as well as older machinery, in the grand scheme of things.

However, I think by and large it's going to depend on the manufacturer, the part, the laptop ... and a lot of other factors.

---

### Post by nmincone on 2006-12-21
[Search this thread for clues...]("http://ubuntuforums.org/showthread.php?t=284994")
This is a real problem that needs real solutions. Supporting hardware for suspend/hibernation is tricky business and could use some polishing in Linux. There's no magic bullet (at the moment).

---

### Post by magian on 2006-12-21
I do not know what exact laptop hardware components you are using, but in my experience (HP, Dell, Toshiba, Sony), Ubuntu and SLED10 are the only two distros with decent laptop support.  AND I have never gotten SLED10 to hibernate correctly, yet Ubuntu does.  I can say that Ubuntu 6.06/6.10 are the best choice for laptops in the Linux space at the moment.  YMMV.:-|

---

### Post by darkhatter on 2006-12-21
I've had the same results which is why I use Suse now, but they are suppose to be "fixing this" with the new release, not sure how much they can solve into one cd

---

### Post by fredj on 2006-12-21
I think it depends on which chips you have in your laptop. I have a Samsung Q35 and
Ubuntu seems to work well on this, better than Suse with regard to power management,
suspending etc.

---

### Post by nmincone on 2006-12-22
"Linux for Human Beings" means that it should just work out of the box- it still needs work, regardless of chip sets and what-nots.
Now, I'm referring to the Ubuntu distro, the rest of the Linux world can go fend for themselves. Laptops are a big part of the installed base, and growing each year as mentioned.

---

### Post by Mimsy on 2006-12-22
> **nmincone said:**
> "Linux for Human Beings" means that it should just work out of the box- it still needs work, regardless of chip sets and what-nots.

Has there ever been an operating system that did?

*graphic mental image of the hours spent searching for ethernet adapter drivers every f-ing time Windows needs to be reinstalled* ](*,) 

/Mimsy

---

### Post by Daveski on 2006-12-22
> **nmincone said:**
> "Linux for Human Beings" means that it should just work out of the box- it still needs work...

Sure does. If it were perfect there would be very little community.
Seriously though, ubuntu does actually function in general and on an enormous variation of hardware. My take on the "Linux for Human Beings" rather than for "geeks" means that the average user can start to use Linux rather than getting frustrated at just getting it installed.

---

### Post by nmincone on 2006-12-23
Ubuntu is definitely one of the more user-friendly distros, but as I commented, it could still use a little more work.

---

### Post by k1001001 on 2006-12-23
I agree that Ubuntu is very user-friendly. I had used Windows all of my life up until September, when XP decided it didn't want to work on my computer anymore. I didn't have a recovery CD, nor did anyone I know. Luckily enough, I lived in a dorm with a Linux guru, and he installed Ubuntu on my computer. I had no problems figuring out how it worked. Getting used to the terminal was a stretch, but it wasn't that bad.

I think in order for Ubuntu to be good for laptops though, wireless connectivity to WPA-encrypted networks out of the box is crucial. There might be some commercial reasons as to why it hasn't been supported so far, but it was a very large headache for me after several failed attempts to get it going. Depending on what type of laptop you have, it varies as to whether you actually have to use ndiswrapper, wpa_supplicant, or what type of installation method you can follow to get your wireless up and going. This was very confusing to me. Under XP, connecting to any wireless network only involved a few clicks.

Maybe laptops need their own version/sub-distro to cater to their different needs?

---

### Post by riven0 on 2006-12-23
I guess it depends on the laptop. I just installed Edgy on my Thinkpad R60 and I didn't have a problem except with the sleep function. Everything else works 'out of the box'.

---

### Post by scrooge_74 on 2006-12-23
I casually read this today and it pertains to the problems we all have with video and wireless drivers.  It no so much a Linux thing, but a manufactures don't want to play with Linux

[http://www.thejemreport.com/mambo/content/view/293/](http://www.thejemreport.com/mambo/content/view/293/)

---

### Post by k1001001 on 2006-12-24
> **scrooge_74 said:**
> I casually read this today and it pertains to the problems we all have with video and wireless drivers.  It no so much a Linux thing, but a manufactures don't want to play with Linux

[http://www.thejemreport.com/mambo/content/view/293/](http://www.thejemreport.com/mambo/content/view/293/)
Funny that I have an Ralink integrated wireless card, but when I was attempting to get it to work with WPA networks (took 2 weeks to finally figure it out), Ralink seemed to be the hardest to get going. It did work out of the box with unsecured and WEP networks, but WPA was a completely different story. Anyways, I think they have a good attitude toward free operating systems.

---

### Post by nrKist on 2006-12-31
Well, I'm feeling lucky after hearing all of these horror stories. Installed 6.10 on my Toshiba Satellite L25-S1194 and everything has worked straight out of the gate. Sound works, DVD works, wifi, touchpad, display, everything. I guess I don't know about sleep, but I've never had a need for it so I've never used it in any OS.

edit: I just remembered that since I don't have dial-up, I don't know if the modem works. Might be a problem for some, but not for me.

---

### Post by bobpur on 2006-12-31
I just posted about a video driver issue I've got with an old IBM Thinkpad 390E. That is the only problem it's got.
It's about 6 or 7 years old with a 4.33 gb drive and 64 mb RAM. I used Damn Small Linux with no problems. I added another 128 mb and installed Xubuntu. It works great (except for the video driver).
I've read several reviews of linux and laptops. It's just like Desktops; Some work right out of the box and some don't.

---

