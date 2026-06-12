---
title: "PC Slow watching movies"
date: 2012-04-15
forum: Hardware
---

### Post by venerable13 on 2012-04-15
I installed drivers via synaptics, then privative nvidia drivers, and in chrome I watch youtube good, but movies with resolution on 360px slow. I have to put full screen and improve it, but also a few slow. My PC is an AMD Sempron 1.9, 4GB DDR2 and lubuntu 11.10 x86. I have the ultimate version of chrome and adobe flash player

What can I do? Thanks

---

### Post by lovinglinux on 2012-04-15
Try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/).

---

### Post by venerable13 on 2012-04-15
I've chrome

---

### Post by lovinglinux on 2012-04-15
> **venerable13 said:**
> I've chrome

Just install it on Firefox if it is still installed, run the Wizard, close Firefox. Restart Chrome and it will benefit from the changes as well.

---

### Post by venerable13 on 2012-04-15
-I played a 720 HD movie on vlc player and it goes perfect, the problem is flash plugin!
-I removed flash installation
-I installed restricted addons and extras for lubuntu, surprisingly it wasn't installed yet(flash, codecs, etc...)
-and play a 320 movie on chrome

the perfomance increase at 90%, but can I do another thing to get the same performance on windows 7, 100%?

the only thing that can I do is to install your extension?

Thanks men!

---

### Post by lovinglinux on 2012-04-15
> **venerable13 said:**
> -I played a 720 HD movie on vlc player and it goes perfect, the problem is flash plugin!

The reason for that is because VLC and other movie players can use XV output, which reduces CPU usage a lot. Flash can't do that and it has trouble with hardware acceleration.

> **venerable13 said:**
> -I installed restricted addons and extras for lubuntu, surprisingly it wasn't installed yet(flash, codecs, etc...)


It is not installed because of license issues. It cannot be distributed with Ubuntu.

> **venerable13 said:**
> the perfomance increase at 90%, but can I do another thing to get the same performance on windows 7, 100%?


In this case, you can't compare with Windows. Flash in linux has terrible performance.

> **venerable13 said:**
> the only thing that can I do is to install your extension?

You can do it manually, but one of thee reasons I developed the extension is to facilitate. Besides, you could have conflicting plugins that are removed by the extension.

What you can do is to try this:

```
gksudo gedit /etc/adobe/mms.cfg
```

Add **OverrideGPUValidation=true** to that file and save it. If your nVidia GPU supports vdpau, install libvdpau1.

```
sudo apt-get install libvdpau1
```

Then add **EnableLinuxHWVideoDecode=1** to the mms.cfg.

---

### Post by venerable13 on 2012-04-15
I read a few things that you comment in another sites but step by step is perfect, you know a lot men! Tomorrow I'll say to you the results. Thanks! In process...

---

### Post by lovinglinux on 2012-04-16
Let me know if people become blue like Smurfs, after those tweaks.

---

### Post by venerable13 on 2012-04-16
I hope that in persons you see anything on change because on my pc not. I did all the steps, libvdpau1 was installed and flash crashed. I removed the line "EnableLinuxHWVideoDecode=1" and flash execute but with the same performace. Mi GPU has 512MB. In full screen is savable, but in normal mode...not.

Can I do another thing?

I have:

chromium codecs installed
restricted addons lubuntu
restricted extras lubuntu

In case that not, how I can play the content on the temp folder, because I don't see the movie? In Chrome folder?

In summary, I have a flash problem on chrome and with the normal methodology I hadn't resolve it. hardware acceleration isn't compatible. Have I to resign on linux with adobe flash or can I probe with [this? ]("http://www.noobslab.com/2012/02/no-adobe-flash-on-linux-except-chrome.html")

**update** -> on vmware of an i5 the perfomance is 95%, not perfect. On lubuntu x64 11.10. Better than on a slow PC with x86

**What existent flash plugin for chrome have best performance on linux?** because on a medium-low pc adobe flash player plugin not

**Other persons say intall the .rpm of adobe web, others that flash on chrome have not solution on slow pc's.**

I need a chrome-flash plugin-slow pc without hardware acceleration 512MB GPU solution? Can you help me please?

---

### Post by lovinglinux on 2012-04-16
> **venerable13 said:**
> I hope that in persons you see anything on change because on my pc not. I did all the steps, libvdpau1 was installed and flash crashed. I removed the line "EnableLinuxHWVideoDecode=1" and flash execute but with the same performace. Mi GPU has 512MB. In full screen is savable, but in normal mode...not.

Can I do another thing?

I have:

chromium codecs installed
restricted addons lubuntu
restricted extras lubuntu

In case that not, how I can play the content on the temp folder, because I don't see the movie? In Chrome folder?

In summary, I have a flash problem on chrome and with the normal methodology I hadn't resolve it. hardware acceleration isn't compatible. Have I to resign on linux with adobe flash or can I probe with [this? ]("http://www.noobslab.com/2012/02/no-adobe-flash-on-linux-except-chrome.html")

**update** -> on vmware of an i5 the perfomance is 95%, not perfect. On lubuntu x64 11.10. Better than on a slow PC with x86

**What existent flash plugin for chrome have best performance on linux?** because on a medium-low pc adobe flash player plugin not

**Other persons say intall the .rpm of adobe web, others that flash on chrome have not solution on slow pc's.**

I need a chrome-flash plugin-slow pc without hardware acceleration 512MB GPU solution? Can you help me please?


These are the facts:

[LIST=1]
[*]Flash has terrible performance in Linux. If you don't have at least a dual core CPU, then most likely your video experience will be limited
[*]The recent version of flash has several issues, specially in regard to hardware acceleration.
[*]Adobe has stopped providing support for Linux. They won't be fixing bugs or improving flash performance anymore, but they will offer security updates for 5 years.
[*]Adobe partnered with Google, which will distribute a new kind of flash plugin using Chrome's Pepper API. When that happens, is most likely that performance improves. This plugin won't be available for Firefox, Opera or other browsers users, just Chrome.
[/LIST]

There isn't much you can do for low-end computers.

You might want to try alternatives. See the last item on this list:

[http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization](http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization)

---

### Post by Yellow Pasque on 2012-04-16
I don't normally recommend throwing money at problems, but your system could perform a lot better with a dual-core CPU. Keep your eyes open for cheap Athlons/Phenoms

---

### Post by venerable13 on 2012-04-16
So, the best thing for less complication is to adquire an AM2 dual core? Really can not I change the plugin for another alternative like [these]("http://www.muylinux.com/2010/09/28/flash-en-linux-4-alternativas/")? Has anyone probe the perfomance and compare it among themselves?

---

### Post by Yellow Pasque on 2012-04-16
> the best thing for less complication is to acquire an AM2 dual core?
The first thing I would try is flashvideoreplacer plugin in Firefox. 

> Really can not I change the plugin for another alternative like these?
The best one is probably lightspark, but it still struggles to get basic stuff like youtube working.

---

### Post by venerable13 on 2012-04-16
Ok, thanks I go to do probes!

---

### Post by venerable13 on 2012-04-16
Best results

1.Firefox+Adobe
2.Chrome+Adobe
3.Chromium+Adobe

I try to install lightspark in Firefox but in youtube only I heard the sound and videos in it and in another places don't are showed. I uninstalled adobe and install lighspark on a tutorial for ubuntu 11.10 and don't result.

So flashvideoreplacer and gnash plugin are the ultimate think to probe by now. Opinions?

---

### Post by lovinglinux on 2012-04-16
> **venerable13 said:**
> Best results

1.Firefox+Adobe
2.Chrome+Adobe
3.Chromium+Adobe

I try to install lightspark in Firefox but in youtube only I heard the sound and videos in it and in another places don't are showed. I uninstalled adobe and install lighspark on a tutorial for ubuntu 11.10 and don't result.

So flashvideoreplacer and gnash plugin are the ultimate think to probe by now. Opinions?

I am the developer of FlashVideoReplacer, so I am biased. :-) 

Unfortunately, it is limited to a few sites, otherwise it would be the perfect solution.

Gnash works on YouTube for me, but not on any other site I need.

Have you tried Minitube?

---

### Post by venerable13 on 2012-04-16
My necessity is to play videos in another sites, not in youtube using anothers special embedded players. I will use firefox+adobe and chrome+adobe for now. If there is another solution advice me, **how**?

**My basic problem is that in chromium (the browser that I was using) the perfomance was less because the adobe plugin is not the same that in chrome, I believe.**

By now my solution is:
1.firefox+adobe
2.chrome+adobe
3.to buy a dual core processor

---

### Post by lovinglinux on 2012-04-16
> **venerable13 said:**
> My necessity is to play videos in another sites, not in youtube using anothers special embedded players. I will use firefox+adobe and chrome+adobe for now. If there is another solution advice me, **how**?

**My basic problem is that in chromium (the browser that I was using) the perfomance was less because the adobe plugin is not the same that in chrome, I believe.**

By now my solution is:
1.firefox+adobe
2.chrome+adobe
3.to buy a dual core processor

Well, there is a not very elegant "alternative", which is to try running the browser and the plugin for Windows, using Wine. However, I am not sure if it will solve your problem, since I wasn't paying much attention to CPU usage when I tested this. Additionally, it will probably add other issues, like instability and errors in browser functionality. 

I was able to run Flash on Opera last week, using this technique.

---

### Post by venerable13 on 2012-04-18
I have new news.

Summary hardware:
 
I have an [Alive NF6P-VSTA]("http://www.asrock.com/mb/overview.asp?model=alivenf6p-vsta")

It have 256MB GPU onboard selected

And a 1.9 Sempron

4GB DDR2 800 in dual channel.

I tested in lubuntu x86 with nvidia privative graphic drivers.

Firefox+Adobe
Chrome+Adobe
Chromim+Adobe

And also I tested the same in Windows 7 x64 except Chromium and the results are the same. For that reason the problems aren't for the plugins on linux, are high demand of flash plugin on CPU not? because I have practicly the same graphic card on my intel i5 and I don't have problems with flash. I note that speaking graphicly the pc is slow (I have all drivers) so I have to buy a new HD graphic card or for flash isn't relevant?

The significative difference between i5 pc and sempron pc are the CPU, if I buy an AMD Athlon 64 X2 4000+ solve my problem? or I have to buy an
AMD Athlon 64 X2 5000+? or an AMD Athlon 64 X2 6000+?

I know 100% the problem and now I need the perfect solution. Thanks.

It's incredible that you need a dual core for flash plugin

**My best solution is to use an extension, extensions o programs to download videos (in .mp4 for example) and play on a native players like vlc for example** I play 720p videos on sempron without problems (1080p I don't probe yet)

Another thing to say or I mark this thread as solved because embedded flash players (like vk video player 4.0, vk.com) can't be replaced with vlc plugin, not (only in youtube is supported, not)?

---

### Post by lovinglinux on 2012-04-19
> **venerable13 said:**
> I have new news.

Summary hardware:
 
I have an [Alive NF6P-VSTA]("http://www.asrock.com/mb/overview.asp?model=alivenf6p-vsta")

It have 256MB GPU onboard selected

And a 1.9 Sempron

4GB DDR2 800 in dual channel.

I tested in lubuntu x86 with nvidia privative graphic drivers.

Firefox+Adobe
Chrome+Adobe
Chromim+Adobe

And also I tested the same in Windows 7 x64 except Chromium and the results are the same. For that reason the problems aren't for the plugins on linux, are high demand of flash plugin on CPU not? because I have practicly the same graphic card on my intel i5 and I don't have problems with flash. I note that speaking graphicly the pc is slow (I have all drivers) so I have to buy a new HD graphic card or for flash isn't relevant?

The significative difference between i5 pc and sempron pc are the CPU, if I buy an AMD Athlon 64 X2 4000+ solve my problem? or I have to buy an
AMD Athlon 64 X2 5000+? or an AMD Athlon 64 X2 6000+?

I know 100% the problem and now I need the perfect solution. Thanks.

It's incredible that you need a dual core for flash plugin

**My best solution is to use an extension, extensions o programs to download videos (in .mp4 for example) and play on a native players like vlc for example** I play 720p videos on sempron without problems (1080p I don't probe yet)

Another thing to say or I mark this thread as solved because embedded flash players (like vk video player 4.0, vk.com) can't be replaced with vlc plugin, not (only in youtube is supported, not)?

If you download the videos, then most likely they will play, because unlike flash, standalone video players can use xv output, which is very economic in CPU processing power.

---

### Post by venerable13 on 2012-04-19
So I need a dual core, not? With sempron never will can play on flash decently, not? Ok thanks. SOLVED!!

---

