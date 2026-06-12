---
title: "Installation of &quot;Dynamic Hybrid Graphics System&quot;"
date: 2010-11-20
forum: Hardware
---

### Post by YnkeBaBz on 2010-11-20
Hi there!
(This is a two part question)
I'm quiet new to use Ubuntu, but I do understand some "programming languages".
My laptop is a Sony VAIO VPC-Z12Z9E/X and when I type "lspeci -v | grep VGA" I get:
```

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2) (prog-if 00 [VGA controller])

```When I boot Ubuntu 10.10 in "normal" I've just got a blackscreen and there is no action when I push Alt + F1. But when I boot in recovery mode I can use Ubuntu as I should. So I figured that it must be a graphic drivers there must be a problem.
I've searched the Internet for some answers, found a lot of information what to do and tried, if not all, so many of type help for installing the GeForce graphic card, but then I was wondering:
"It is a Dynamic Hybrid Graphics System, so maybe I should try installing the Intel VGA Controller", but I do not know which driver I should search for?

Any ideas on how to install either the Intel VGA Controller or the whole Dynamic Hybrid Graphics System?

Part 2:
On the same laptop I can't use the mousepad, how to install this?

Best regards
YnkeBaBz

---

### Post by monstara on 2011-04-29
It's a dark and muddy issue that I've been having too. My laptop overheats, I think for this reason.
Have a look at this
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
might be helpful.
Basically, it seems current kernel versions don't support hybrid graphics too well. But perhaps someone more knowledgeable should say.

---

