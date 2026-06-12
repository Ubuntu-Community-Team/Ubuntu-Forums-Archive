---
title: "Artefacts during loading OS on HD ready TV (1080i)"
date: 2020-04-15
forum: Hardware
---

### Post by frezafrezafreza on 2020-04-15
amd 4670 pci-e
TV Philips 32 (1080i and 720p)

I have artefacts on TV screen during loading linux (i tried defferent distributives). 
I see it when linux change screen resolution from 640x 480 to 1920x1080.
Possible it is problem becouse my TV have only 1080i and have not 1080P.

Some times my TV (not linux) hanging when I see artefacts. I afraid it can damage my TV.
I need switch OFF my TV when loading Linux, and switch ON after loading Linux.

In Linux I use resolution 720P, but during loading system I see 640x40, then 1920x1080 and then 1280x720.
Artefacts appear when 640x480 is changing to 1920x1080.

I tried acpi=off, noapic, nolapic, nofpu and no sync. It din not solve the problem.

nomodeset solve the problem but load system in low resolution.

It is not cable problem. I used HDMI and DVI ports in TV using different cables.

What can I try else? May be there is a way to automatically switch off TV during loading and switch on after loading system?

---

### Post by Autodave on 2020-04-15
Please give us some info on your PC: especially the graphics card, if any.  What version of Ubuntu did you install?

---

### Post by frezafrezafreza on 2020-04-15
videocard [LEFT][COLOR=#000000][FONT=Ubuntubeta]amd 4670 pci-e, not proprietary dirver
I installed ubuntu 18, Lubuntu 18, aniX 19.2
[/FONT][/COLOR][/LEFT]

---

### Post by CelticWarrior on 2020-04-15
There are a few things you should know and a few you shouldn't do. Let's start by what you shouldn't do: DON'T use any additional boot parameters unless your hardware requires them to boot successfully. Definitely NOT your case. Also don't use 'nomodeset' which is a temporary workaround until users install some proprietary graphics drivers and meanwhile have no GUI at all. Again, definitely NOT your case. 

Now, the thing you should know:

> Some times my TV (not linux) hanging when I see artefacts. I afraid it can damage my TV.
I need switch OFF my TV when loading Linux, and switch ON after loading Linux.
I'm not sure what you're talking about "hanging when I see artifacts" (this is the correct spelling but not the point anyway). If it has issues changing from one resolution to another typically you'd just have to wait, it's really doubtful it needs to be switched off and on again. And **in any case it doesn't damage the TV**.

>  Possible it is problem becouse my TV have only 1080i and have not 1080P.
It definitely isn't. **Any 1080i TV/monitor supports 1080P, that's its native (input) resolution and the only one that should be used**. 
Furthermore it's perfectly normal the boot process starting at a low (or lower) resolution, with or without Grub menu. Any flatscreen TV, even the old "HD ready" ones, is able to accept any supported resolution and seamlessly switch between resolutions served. Using supported but lower than native/recommended resolutions result in a bad visual experience, any unsupported resolution results in "no video" but in any case it doesn't damage the TV itself or anything else.

Finally, newer, better and more energy efficient 1080P TVs/monitors are comparatively very cheap nowadays. Maybe you should consider replacing it if it's so "painful" for you. But it shouldn't be, to be clear. In my current forced confinement I had to use an old LG "HD ready" which is likely some years older than yours because 1) it has no HDMI input (DVI does the job) and b) doesn't support higher than 1440x900 which is just slightly above 720P (fortunately Ubuntu detects correctly the maximum resolution in the digital connection - DVI - and adjusts accordingly) and it works perfectly.

---

### Post by CelticWarrior on 2020-04-15
> **frezafrezafreza said:**
> videocard [LEFT][COLOR=#000000][FONT=Ubuntubeta]amd 4670 pci-e, not proprietary dirver
I installed ubuntu 18, Lubuntu 18, aniX 19.2
[/FONT][/COLOR][/LEFT]


Your graphics card is working with the open-source driver. No user action required.

---

### Post by frezafrezafreza on 2020-04-15
[LEFT][COLOR=#222222][FONT=Verdana]"I'm not sure what you're talking about "hanging when I see artifacts"[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]I see static picture (with artefacts) on TV screen, but Linux continue loading. I do not see Linux screen while I switch off and switch on TV. But sometimes artefacts screen disappear without switching TV.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Screen photo you can see here[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][/FONT][/COLOR][/LEFT][https://1drv.ms/u/s!AqKhnTGkNb6EgbZMtIsXanDbYztcMw?e=nfgyXB](https://1drv.ms/u/s!AqKhnTGkNb6EgbZMtIsXanDbYztcMw?e=nfgyXB)

---

### Post by CelticWarrior on 2020-04-15
> **frezafrezafreza said:**
> [LEFT][COLOR=#222222][FONT=Verdana]"I'm not sure what you're talking about "hanging when I see artifacts"[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I see static picture (with artefacts) on TV screen, but Linux continue loading. I do not see Linux screen while I switch off and switch on TV. But sometimes artefacts screen disappear without switching TV.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Screen photo you can see here[/FONT][/COLOR]
[/LEFT]
[https://1drv.ms/u/s!AqKhnTGkNb6EgbZMtIsXanDbYztcMw?e=nfgyXB](https://1drv.ms/u/s!AqKhnTGkNb6EgbZMtIsXanDbYztcMw?e=nfgyXB)

Yes, that happens and should always go away after awhile. There's no way to change that, period. Do yourself a favor and DON'T change anything in the OS, especially those things you really don't know anything about.
Your TV is old and inadequate but works within its limitations. Just live with it or replace the TV for a cheap modern one and be happy.

---

### Post by frezafrezafreza on 2020-04-15
I have not same problem, when watching TV using media box on Android system. And I do not remember same problem, when used notebook with Windows.

---

