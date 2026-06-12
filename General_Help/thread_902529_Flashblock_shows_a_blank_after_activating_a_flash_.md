---
title: "Flashblock shows a blank after activating a flash element"
date: 2008-08-27
forum: General Help
---

### Post by chronos00 on 2008-08-27
Hi!

I have always used firefox with the flashblock extension, and it worked flawlessly until a few month ago.

The problem is almost described in the title:
When you load a web page filled with flash elements, flashblock properly blocks every element. The problem arises when you wish to UNBLOCK certain element. If I click on the element to unblock, I just get a blank square instead of the flash element.

I have done a lot o googleing for this issue and found out that many people is having problems with flashblock, but not THIS problem. Hence, I don't know how to solve it.

I am using latest firefox (3.0.1) and latest flashblock (1.5.6) in ubuntu 64bit on a 64bit system.
Just in case, for flash I am using flashplugin-nonfree (10.0.1.218 +10.0.0.525ubuntu1 +really9.0.124.0ubuntu2). I don't have a clue how to read this last version number.

Any ideas??

---

### Post by chronos00 on 2008-08-30
bump!
Any ideas people?

---

### Post by EmanresuusernamE on 2008-08-30
Are you sure the flash isn't really big and taking a long time to load?  It's possible that the flash requires some of the other flash files to be loaded before it will load properly.  Also have you disabled FlashBlock to see if it's not the website?

---

### Post by chronos00 on 2008-08-30
If I disable flashblock everything works properly (including the monstrous amount of flash elements eating my CPU).

I have let this white squares for hours and they never finish loading.

An interesting behavior is that when I try to unblock any flash object in a webpage, I not only get the white / gray square on the flash element I want to unblock, but on every other flash element in every other webpage open in firefox AS WELL!

In conclusion, this problem should be caused either by the flash plugin for firefox or by flashblock. Having tested the flash plugin alone and not having problems, I can only blame flashblock.

---

### Post by EmanresuusernamE on 2008-08-30
Sounds like you need to remove and reinstall Flashblock then.  What website where you going to that has so much flash?

---

### Post by chronos00 on 2008-09-01
while using firefox, I generally have many firefox windows, with many tabs each. If flash went uncontrolled, I would normally have a CPU usage of 40%-50%. You can guess the impact of that in a laptop's battery.

I was sure I had already tried the uninstall / reinstall, but in any case this time it did solve the problem!

Thank you for your patience. Sometimes retelling a problem and going through the basic steps helps to solve the problem.

---

### Post by EmanresuusernamE on 2008-09-02
Always glad to hear that issues solved.

---

### Post by phyzome on 2009-07-05
> **EmanresuusernamE said:**
> Always glad to hear that issues solved.

Unfortunately, mine are not. I uninstalled FlashBlock, restarted the browser and confirmed that Flash worked after several suspend/resume cycles, reinstalled FlashBlock, and found that the bug had reoccurred.

---

### Post by chronos00 on 2009-07-05
Are you using 32 or 64bit OS?
adobe's flash or gnash or swfdec?
what version of flash?

---

### Post by phyzome on 2009-07-05
> **chronos00 said:**
> Are you using 32 or 64bit OS?
adobe's flash or gnash or swfdec?
what version of flash?

(Ah, yes, sorry.)

[LIST][*]64 bit Ubuntu 8.10 on an Intel 64 architecture.
[*]Firefox 3.0.11
[*]Adobe's Flash: 10.0.22 via flashplugin-nonfree
[/LIST]

---

### Post by chronos00 on 2009-07-05
You've got the exact same configuration as me. I must admit until recently I have been trying to use "swfdec" for flash, because I was using Ubuntu 8.04 and It's repos didn't have the latest version of Adobe's flash. After I upgraded, the latest version was available, and I installed it. It works just fine now (latest version of flashblock: 1.5.11.2)

Try uninstalling any other flash alternative (gnash, swfdec) and reinstall Adobe's flash. You could also try reinstalling flashblock, just in case.

A little advise that might help you with flash in linux:
for youtube videos use: greasemonkey + freeYoutube

for greasmonkey: ```
apt-get install firefox-greasemonkey
```
for freeYoutube: [http://userscripts.org/scripts/show/34765]("http://userscripts.org/scripts/show/34765")
Just click on the green "install" button.

This configuration will allow you to watch youtube videos directly on your local media player, makeing everything much faster.

Regards

---

