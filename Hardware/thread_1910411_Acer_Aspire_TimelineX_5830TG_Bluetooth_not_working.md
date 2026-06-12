---
title: "Acer Aspire TimelineX 5830TG Bluetooth not working in Precise 12.04"
date: 2012-01-17
forum: Hardware
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-01-17
I've been trying to get Bluetooth to work on my machine for over a month now, without success. I set up my Ubuntu 12.04 installation following this thread:

[djcp's blog]("http://blogs.law.harvard.edu/djcp/2011/11/kubuntu-11-10-on-the-acer-aspire-timelinex-4830tg-6450/")

I don't think anything mentioned there could cause a problem with bt, but I'm mentioning it just in case.

Here are some of resources I tried to use since then, which have failed to resolve the problem:

[LIST]
[*][ArchLinux Acer TimelineX]("https://wiki.archlinux.org/index.php/Acer_TimelineX#Bluetooth")
[*][Ubuntu Forums :: [SOLVED] Acer 4820 TimelineX bt problem]("http://ubuntuforums.org/showthread.php?t=1648378")
[*][Ubuntu Help about Acer TimelineX]("https://help.ubuntu.com/community/AspireTimeline/Fixes#Bluetooth")
[/LIST]

I tried everything I could before posting the problem here, so I sure hope there's someone who managed to fix this problem. Any help greatly appreciated.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-19
Bump. Isn't there any solution for this? I'm getting a bit desperate.

I discovered that my bluetooth doesn't work even with a clean install of both 11.10 and 12.04. I suspect that it has something to do with the fact that on this model FN+F3 toggles on and off both bluetooth and wireless. It's confusing.

In Windows bluetooth works fine.

I'm clueless, any help is welcome.

---

### Post by danootz on 2012-02-19
I'm sorry I can't help with your bluetooth issue, but I'm curious to know how well the 5830 is doing out of the box otherwise.

I know that when I install 11.10, I have to do a lot to get sound and brightness function keys to work. And no apparent fix for terrible battery life (as compared to what you can get with Windows 7)

Does most everything else work after a clean install of 12.04? Did you have to jump through hoops to get things working?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-20
Actually, you can get most of those things to work. Please take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1879822](http://ubuntuforums.org/showthread.php?t=1879822)

Out of the box it's not perfect, but it takes 5 more minutes to get brightness (as well as other hotkeys) and battery life right. With those few fixes almost everything is fine. Battery life is not quite like under Windows, but it raises significantly and fan noise is down. A couple days ago I got my battery to last for 10 hours with minimal brightness, networking off, no flash/audio/video. It was just an experiment, but it was still an achievement. I'm in love with this computer.

Other than that, there is also a small issue with built in microphone and Skype, which is also easily fixable through Pulseaudio.

Now the only thing that still annoys me is this Bluetooth issue. It's really frustrating because Bluetooth is actually working, but apparently it's not possible to turn it on.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-22
The Bluez tool was just updated this morning. And still no results. Dang...

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-02
I think I've found a solution for my problem:

[http://askubuntu.com/a/82089/48395](http://askubuntu.com/a/82089/48395)

The symptoms are same. However, I'm a complete beginner with Ubuntu (and Linux in general), and all that's said over there doesn't make any sense at all to me. Can someone please help me apply this mentioned patch? I'm clueless on how to do it.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-03
Actually, I give up on this one. Patching/compiling/messing with kernel is far beyond my knowledge. I'll just have to wait until the kernel is fixed, or until someone comes up with a simple fool-proof "click-and-forget" solution. :(

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-08
There is a thread describing a similar problem, but it's closed because it's in Oneiric Testing section:

[http://ubuntuforums.org/showthread.php?t=1808143](http://ubuntuforums.org/showthread.php?t=1808143)

Solutions from the thread didn't help me, but I believe they're close to the right thing. Is there anyone who was involved in that discussion who could help me with this please?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-11
I think I've found a patch that can help me, but I will need somebody's help to actually understand what is said on this address:

[http://www.mail-archive.com/stable@vger.kernel.org/msg06358.html](http://www.mail-archive.com/stable@vger.kernel.org/msg06358.html)

Can anyone please explain to me where can I find the mentioned file bluetooth-add-support-for-atheros.patch and how do I apply it?

---

