---
title: "Sound/acpi problem Lenovo 3000 C200"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by toolish on 2007-02-10
Hi, I've been experiencing troubles getting my onboard sound working on recently purchased Lenovo 3000 C200 laptop.
It's a Core2duo model. With intel hd audio. I'm running Edgy but it is the same for Dapper and across kernel revisions.
I do get sound but only very quietly, and no sound at all from the laptop speakers.
I have tried re-building the alsa drivers using the most current version, all installed fine but still the same low level sound issue. I also tried various alsa module options model=ref,model=laptop etc. No joy
lspci | grep Audio gives:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```
This is where it got interesting, I read a similar thread here [http://ubuntuforums.org/showthread.php?t=349231]("http://ubuntuforums.org/showthread.php?t=349231")
Where it was fixed by setting acpi=ht as a boot option. This did bring me some success, it raised the volume and enabled the laptop speakers but this also essentially disables acpi, not good for a laptop.
Has anyone had similar experiences or does anyone know if the problem is alsa based or acpi  based?
I appreciate anyones help with this.

---

### Post by dadabe on 2007-02-12
Hi,
I have not found a solution to get sound working with acpi. 
See this post :
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2725]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2725")
I'm wondering this problem is acpi based 

(Sorry for my english language . I'm french )
dadabe

---

### Post by toolish on 2007-02-12
Thanks dadabe,

Seems we will have to watch this space for a while. Back to testing...I'll keep looking in the acpi direction perhaps.
Cheers for your info.
toolish

---

### Post by Arcadian on 2007-02-15
Hi Toolish,

I've just been ](*,) with a similar problem on my laptop. I realise it's slightly different hardware (and under feisty RC1), but it may help.

Have a look here [http://ubuntuforums.org/showthread.php?t=312725]("http://ubuntuforums.org/showthread.php?t=312725")

I'll be keen to hear if you find it works for you too. Many people seem to have this issue!:-k 

Oh yeah, cut straight to the last post, I've tend to go on a bit & have been working on this for a while now!

Good luck!
[COLOR="SandyBrown"][B]Arcadian
[/B][/COLOR]

---

### Post by toolish on 2007-02-16
Hi Arcadian,

Thanks for the tip. Unfortunately this didn't work for me. It's odd though, I tried to selectively disable different modules by changing the line like you said and if I removed the processor module it would still load. The same with the others ac/battery etc. Maybe it's not looking here properly on my system. Something weird there?!
Thanks again, btw nice country you got there!
toolish

---

### Post by Arcadian on 2007-02-19
Sorry to hear that Toolish. :sad: Hope you have some luck! I'll keep an eye :shock: on this thread to see how you go. 

Am indeed lucky to live here. Thanks!

[COLOR="SandyBrown"]Arcadian[/COLOR]

---

### Post by dadabe on 2007-02-19
Hi toolish,
I have installed feisty fawn heird4 on my laptop and compiled alsa with the patch but no joy !
Sound doesn't work with acpi.
dadabe

---

