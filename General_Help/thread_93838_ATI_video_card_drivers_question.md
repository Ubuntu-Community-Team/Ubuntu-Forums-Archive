---
title: "ATI video card drivers question"
date: 2005-11-22
forum: General Help
---

### Post by mbourd25 on 2005-11-22
Hi, I installed the xorg-driver-fglrx ATI drivers from the repositories using the package manager Adept and when I try the openGL screensavers, they are not smooth. Is their something missing that the acceleration is not turned on? When I was using my nvidia card, the openGL screensaver were very smooth when I installed the nvidia drivers form the repositories.

I have a AMD Athlon 1800+ with a ATI All-in-wonder 9700 pro 128 mb ram with 1 gig of ram and running Kubuntu 5.10 with linux kernel 2.6.12.10.

I've updated everything using the Adept program.

Any help would be great. Thanks.

---

### Post by daller on 2005-11-23
[QUOTE=mbourd25]Hi, I installed the xorg-driver-fglrx ATI drivers from the repositories using the package manager Adept and when I try the openGL screensavers, they are not smooth. Is their something missing that the acceleration is not turned on? When I was using my nvidia card, the openGL screensaver were very smooth when I installed the nvidia drivers form the repositories.

I have a AMD Athlon 1800+ with a ATI All-in-wonder 9700 pro 128 mb ram with 1 gig of ram and running Kubuntu 5.10 with linux kernel 2.6.12.10.

I've updated everything using the Adept program.

Any help would be great. Thanks.[/QUOTE]

You have to edit your xorg.conf!

Follow this howto:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by mlomker on 2005-11-23
Daller's correct.  Here's a [how-to]("http://ubuntuforums.org/showthread.php?p=408111") that I wrote.

---

### Post by daller on 2005-11-24
[QUOTE=mlomker]Daller's correct.  Here's a [how-to]("http://ubuntuforums.org/showthread.php?p=408111") that I wrote.[/QUOTE]

Hi mlomker,

Wouldn't it be a good idea to implement your howto into the wiki-page?

---

### Post by mlomker on 2005-11-24
[QUOTE=daller]Wouldn't it be a good idea to implement your howto into the wiki-page?[/QUOTE]

They are on the KB's [unofficial wiki]("http://doc.gwos.org/index.php/Install_ATI_driver") but getting things into the main Ubuntu wiki is difficult.

---

### Post by daller on 2005-11-24
[QUOTE=mlomker]They are on the KB's [unofficial wiki]("http://doc.gwos.org/index.php/Install_ATI_driver") but getting things into the main Ubuntu wiki is difficult.[/QUOTE]

What's so difficult about it? - I've edited a lot of the pages on [http://wiki.ubuntu.com](http://wiki.ubuntu.com)

---

### Post by mlomker on 2005-11-24
[QUOTE=daller]What's so difficult about it? - I've edited a lot of the pages on [http://wiki.ubuntu.com](http://wiki.ubuntu.com)[/QUOTE]

We've had problems with our posts being rejected.  They only want how-to's that work 100% of the time and that's not realistic, especially with video drivers.

I already have my how-to's on the [ATI wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide") and they've remained mostly intact.

---

