---
title: "Resolution Limited to 1152x864 instead of 1680x1050 - Ubuntu 14.04.3, Nvidia 8800GTS"
date: 2016-02-12
forum: Hardware
---

### Post by bewildered3 on 2016-02-12
[COLOR=#111111][FONT=Ubuntu]GPU: Nvidia (BFG) 8800 GTS 320Mb
Monitor: Acer 22"
Max resolution supported by the GPU: 2560x1600
Max resolution supported by the monitor: 1680x1050
Resolution stuck at: 1152x864

I have spent almost two weeks so far trying to fix this resolution limit issue on Ubuntu 14.04. I have gone through any result that comes up in Google in the first five pages, I have read at least 10-15 topics on this forum alone, and many more on other websites, I have tried the **xrandr** trick, the **xconfig** file trick, updating/reinstalling/uninstalling Nvidia drivers, trying different versions of the Nvidia driver (official/unofficial/open-source/latest version/older versions), checking the monitor plug, etc. NONE of them have worked at all. I have reinstalled my Ubuntu 14.04 three times (every time a completely clean install, formatting the "entire" hard disk), I even tried 15.10, Linux Mint, elemntaryOS, Korora, etc - since I thought the problem is only with Ubuntu, but I have the same problem on all these distributions. I do not have this resolution limit problem on Windows at all, it is only on Ubuntu.. I can go up to 1680x1050 on Windows.

It is so mental, and I have spent hours and hours trying any possible fix that I have found online, and absolutely nothing has worked.. Does anybody know any fixes for the issue?
[/FONT][/COLOR]

---

### Post by gordintoronto on 2016-02-13
What exact model of Acer? With Ubuntu 14.04 and the suggested Nvidia proprietary driver, can you run NVIDIA X Server Settings? What does X Server Display Configuration say about your monitor?

---

### Post by bewildered3 on 2016-02-14
[COLOR=#ff0000]**Acer AL2216Wbd 22"**[/COLOR]

[IMG]http://s28.postimg.org/xjnjbr7lp/Screenshot_from_2016_02_14_17_25_41.png[/IMG]

---

### Post by bewildered3 on 2016-02-14
So the Ubuntu "community" hasn't got a single working fix for their [COLOR=#ff0000]_**LTS**_[/COLOR] (the so-claimed "stable") version of Ubuntu?

---

### Post by gordintoronto on 2016-02-14
The problem is that there are many "fixes", and choosing the right one requires more information. Your computer is not recognizing your monitor. How is it connected?

The only time I have observed something like this, there has been some kind of adapter to convert from one type of connection to another.

Note that on the screen you included in your message, the resolution can be changed. Have you tried changing it there?

---

### Post by bewildered3 on 2016-02-19
Thanks a lot for your answer. It is frustrating to know that there are still no official fixes from Ubuntu while many people have been facing the same issue.

In all the forums and posts that I have been reading about the same problem, everyone who was experiencing the resolution limit problem, was also facing the "unknown monitor" problem. Even for those whom the fixes worked, they were still seeing the unknown monitor/monitor not recognized error..

My monitor is connected through a converter to my GPU; i.e. VGA to DVI converter.

Yes, I have tried changing it there, there is only and only one more resolution available above the current one, but there are three problems with that option: (i) the ratio does not match my monitor, simply put, that is not a standard resolution for my monitor (ii) upon choosing that resolution everything goes black and I have to enter terminal (not the casual terminal, but the one which looks like recovery mode in an entirely black screen; I'm not quite sure what that mode is called) and manually change everything back to where it was (iii) the resolution is not at all that higher than 1152x864, so I have not tried staying on it, because it is still much lower than 1680x1050

---

### Post by gordintoronto on 2016-02-19
Your monitor has a VGA port. Shut everything down, plug the VGA cable into it, and your problem will be solved.

---

### Post by bewildered3 on 2016-02-20
> **gordintoronto said:**
> Your monitor has a VGA port. Shut everything down, plug the VGA cable into it, and your problem will be solved.

I did not expect that I would come here on Ubuntu Forums (whose users boast so much about being geeks) to receive mediocre advice on how to connect a freaking monitor to a GPU. Anyhow, you did not read what I said or truly do not have any idea that newer GPUs no longer support VGA ports.

My monitor has a VGA cable/port, that is true, however my graphic card (8800 GTS) does not support VGA ports, and only has two DVI ports. That is why I am using a connector to connect my monitor to my PC. And this can hardly be the reason, I have used the exact same PC and monitor with Ubuntu 11.04 without having this mental problem.

---

### Post by gordintoronto on 2016-02-20
When I looked up the specs for your monitor, it said the thing has a DVI port, so there would be no need for a DVI to VGA adapter.

---

### Post by tokyobadger on 2016-02-21
[quote="bewildered3"]I did not expect that I would come here on Ubuntu Forums (whose users  boast so much about being geeks) to receive mediocre advice on how to  connect a freaking monitor to a GPU.[/quote]
I think you're lucky gordintoronto bothered coming back. Unless you have an unusual eg pre-production version of that monitor, I'll also say that the spec sheet says it has a DVI-D as well as VGA[COLOR=#ff0000][/COLOR] port and without further information would also recommend trying DVI to DVI

---

### Post by him610 on 2016-02-21
Here is a suggestion that may or may not work for you. In the grub.cfg file, there is a line that begins with "set gfxmode=....". Change it to read "set gfxmode=1680x1050".
Don't forget to run "update-grub" from the CLI. Reboot to see if helps to solve your problem.

Another suggestion, the folks that provide helpful advice on these forums are all volunteers that get no monetary compensation whatsoever. Your crass attitude turns people off. Be a little more humble, after all, you are the one seeking help.

---

