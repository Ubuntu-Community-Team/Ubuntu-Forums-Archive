---
title: "Bug report - hal gives error messages &quot;command not found&quot;"
date: 2016-11-24
forum: Hardware
---

### Post by Andrew F in Australia on 2016-11-24
Hi All,

I have a new Gigabyte P57 laptop that is a trifle buggy with Linux to say the least - mainly the well known issues with i6700HQ chip/ NVidia drivers causing startup crashes (now fixed with correct drivers installed,) [fn] key plus F2 not changing brightness (kernel bug) and the Elantech Touchpad being recognised intermittently and randomly.  

I tried a bug report when the touchpad was not recognised, but it came up with the attached messages off the official 'how to report a bug' site. See attached link for image (thanks WIldmanne)

Could anybody please let me know if commands have changed or what I did wrong (more likely)

Regards,

Andrew F
[http://i.imgur.com/zIRVrdW.png](http://i.imgur.com/zIRVrdW.png)

---

### Post by steeldriver on 2016-11-24
As you may have noticed, the wiki page you are referring to hasn't been updated since 2008 - AFAIK `hal` hasn't been used in Ubuntu since around 10.04

Can you take a step back and describe the issue in more detail? Perhaps then someone will be able to point you in the right direction

---

### Post by Andrew F in Australia on 2016-11-24
OK - thanks, Steeldriver.

It's Friday morning here and I'm prepping for a day's training - will post tonight. Just put this up to acknowledge your response.

THanks for the prompt reply.

---

### Post by Andrew F in Australia on 2016-11-25
Hi again,

Two questions that I believed were both kernel bugs relating to hardware configuration on this machine.

First one: On this machine, [fn] + F7-F9 control volume, [fn] + F1 puts the machine to sleep, but the rest of the function keys are ignored, can't turn wi-fi on and off, can't control brightness through function keys, etc...
Second one: The Elantech touchpad either works perfectly (approx 80% of the time) or doesn't work at all (approx 20%) on bootup.

How do I record necessary logs for a bug report, and/or, 

Is there a fix for either problem?  I've tried the various grub bootup i8042 configurations that I could find online for the touchpad issue and a few of the scripts, as the Elantech touchpad seems buggy in Linux.

Many thanks,

Andrew F

---

### Post by wildmanne39 on 2016-11-25
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

---

### Post by cariboo on 2016-11-25
Unless you know the name of a specific file, or module, the best way to report the bug is to use the following command:

```
ubuntu-bug linux
```

Once the [https://bugs.launchpad.net](https://bugs.launchpad.net) bug reporting page opens, either select from the similar bug reports, or create a new one, make sure you add as much information as possible.

---

### Post by Andrew F in Australia on 2016-11-25
THanks for the command, Cariboo,

Have sent through one of the two bug reports - will send through a second when the touchpad fails again so there's a benchmark to aim against.

Regards,

Andrew F

---

