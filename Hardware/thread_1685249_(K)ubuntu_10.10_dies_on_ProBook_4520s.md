---
title: "(K)ubuntu 10.10 dies on ProBook 4520s"
date: 2011-02-10
forum: Hardware
---

### Post by dijxtra on 2011-02-10
Hi there everybody!

Few weeks ago I bought a brand new ProoBook 4520s which was shipped with SuSe which worked flawlessly. I booted up Kubuntu 10.10 live CD, everything went fine (it had sound and recognised my neighbours' wireless routers) and I decided to install it. I reformated hard disk and to installed Kubuntu 10.10, which went fine. I then decided to turn off wireless, pressed the wireless button and then hell broke lose. Kubuntu 10.10 froze and would not boot (boot process ends up in a frozen pinkish-bluish-static-noise screen). Kubuntu 10.10 live CD would not boot (it stops on splash screen and just hangs there). Kubuntu 10.4 booted just fine. I installed Kubuntu 10.4 and it works well, except: it has no sound, it didn't recognise my wireless card (I connected to Internet successfuly using LAN cable) and it, check this out: won't upgrade to Kubuntu 10.10. I've been using it for few weeks now, and this Kubuntu 10.4 installation just won't inform me that a new version of Kubuntu exists. Other updates for Kubuntu 10.4 are installed nicely.

I then tried to instal vanilla Ubuntu 10.10, and it worked. It gives me sound, it connects to my girlfriend's wireless connection. Cool. I then decided to turn off wireless. Lo and behold, it worked as advertised. I turned wireless back on and everythign went fine until today. When I again decided to press the "turn on/off wireless" button. And since then Ubuntu 10.10 boots up to login screen and starts repeating the login form drum. It doesn't respond to keyboard or mouse, it just repears the drum. Ubuntu 10.10 live CD now also won't boot (hangs on splash screen with whiteorange dots frozen).

Kubuntu 10.4 continues to work fine (apart from the fact that it has no sound, no wireless and doesn't know Kubuntu 10.10 is out.

Does anybody have any idea what could be wrong and where do I look? I fear that if I take the laptop back to the shop, they will tell me to buy Windows 7 which supports wireless and stop acting wierd with this Lynuks stuff.

Any ideas?

---

### Post by dijxtra on 2011-02-14
OK, it turns out that several of this problems are unrelated.

1. Kubuntu 10.4 wont upgrade to 10.10 because it is LTS and you have to edit /etc/update-manager/release-upgrades and set Prompt=normal. Now I can't upgrade because I get "Could not calculate the upgrade" error. All efforts to fix that failed.

2. Sound on 10.4 didn't work because PCM in alsamixer was set to 0. That one is fixed now.

3. Wireless not working was a common problem for my card (RT3090), I found the solution here: [http://ubuntuforums.org/showpost.php?p=9355390&postcount=5](http://ubuntuforums.org/showpost.php?p=9355390&postcount=5) I just installed that package and now wireless works (sometimes with problems, but generally works).

I'm now trying to cope with other problems listed here...

---

