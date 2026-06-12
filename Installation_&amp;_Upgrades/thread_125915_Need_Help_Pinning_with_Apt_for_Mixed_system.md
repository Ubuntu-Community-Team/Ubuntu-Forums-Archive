---
title: "Need Help Pinning with Apt for Mixed system"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by dutler on 2006-02-05
Hi, Im trying to do some pinning with apt. If I understand the concept correctly, I will be able to have universe, multiverse and user depo enabled in my sources.list, and yet only have select packages outside of main. Right now, if I enable multiverse for package x, then the next apt-get upgrade fills my entire system with updates to the less stable multiverse.
Here are a few Mixed system references:
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version)
[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)
[http://wiki.serios.net/wiki/Apt-Pinning_on_Ubuntu](http://wiki.serios.net/wiki/Apt-Pinning_on_Ubuntu)

Here is what i have so far in my apt preference file:
> Package: *
Pin: release a=ubuntu-seveas c=freenx
Pin-Priority: 990

Package: *
Pin: release a=breezy-security  c=main restricted
Pin-Priority: 802

Package: *
Pin: release a=breezy-updates  c=main restricted
Pin-Priority: 801

Package: *
Pin: release a=breezy=main restricted
Pin-Priority: 800

Package: *
Pin: release a=breezy-backports
Pin-Priority: 700

Package: *
Pin: release a=breezy-security c=universe
Pin-Priority: 601

Package: *
Pin: release a=breezy c=universe
Pin-Priority: 600

Package: *
Pin: release a=breezy-seveas c=extra, java, seveas-meta, custom
Pin-Priority: 500

Am I doing it "right"? Any comments?

Also, I need to edit my /etc/apt/apt.conf file. Kubuntu did not come with one, but has a apt.conf.d - is this a replacement or a complement?

Thank you for your help, 
dutler

---

### Post by dutler on 2006-02-06
Ive been at this all weekend with Kunbunt and with Mepis.... no luck at all, but I have learned that I can just create a new apt.conf and APT seems to merge it nicely with the existing apt.conf.d (for any with such a question).

So, let say I dont pin with the preferences file. But create a apt.conf  with the default release line - "APT::Default-Release "breezy";"

I run apt update and upgrade then In my sources.list I had the dapper depo. When i run apt update and upgrade I shouldnt get any new packages right? But I do - lots.  What gives? 

If I use the pinning with the preferences file does the APT::Default-Release "breezy"; from apt.conf still work?

Lets assume it doesnt, for my next questions.
I have two pins in preferences:
> Package: *
Pin: release a=breezy
Pin-Priority: 600

Package: *
Pin: release a=dapper
Pin-Priority: 200

Then run apt-get update / upgrade with only breezy sources. Then enable a dapper depo run update/upgrade again and apt wants to update kdebase-data kdelibs-data kdemultimedia-kappfinder-data libartsc0.

I get the same resualt when I remove the apt.conf.  What am I doing wrong?

thanks a ton
dutler

---

### Post by dutler on 2006-02-07
In the past, responses have came quickly... did i post this in the wrong place or is little known about apt pinning by my fellow ubuntuians?
-dutler

ps yes i know that is a false dichotomy :D

---

