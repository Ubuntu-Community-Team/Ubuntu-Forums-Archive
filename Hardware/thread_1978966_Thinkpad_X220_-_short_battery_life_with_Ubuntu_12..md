---
title: "Thinkpad X220 - short battery life with Ubuntu 12.04"
date: 2012-05-12
forum: Hardware
---

### Post by Houmie on 2012-05-12
Apparently Ubuntu 12.04 was meant to support the laptops better and allow a longer better life.

On Win7 I get 7 hours battery life with my 6 cell battery. Same laptop on Ubuntu is around 2 hours.  Thats too much of a difference.

I have tried PowerTOP and switched some entries to GOOD in order to save battery life, but without a big success.

Any idea what to do?

---

### Post by simohell on 2012-05-13
> **Houmie said:**
> Apparently Ubuntu 12.04 was meant to support the laptops better and allow a longer better life.

On Win7 I get 7 hours battery life with my 6 cell battery. Same laptop on Ubuntu is around 2 hours.  Thats too much of a difference.

I have tried PowerTOP and switched some entries to GOOD in order to save battery life, but without a big success.

Any idea what to do?

Is the battery life the reported one or the actual? With Ubuntu 10.04 with a backport kernel from Natty there are no problems. I get something like 7 hours use with WLAN or 3G. I will be upgrading in a week or two, so I hope I won't lose operating time.

Basically Ubuntu gives me now about 25% more than Windows 7.

---

### Post by Houmie on 2012-05-14
> **simohell said:**
> Is the battery life the reported one or the actual? With Ubuntu 10.04 with a backport kernel from Natty there are no problems. I get something like 7 hours use with WLAN or 3G. I will be upgrading in a week or two, so I hope I won't lose operating time.

Basically Ubuntu gives me now about 25% more than Windows 7.

Thanks for your reply. The reported Battery life is about 2.5 hours.  Maybe the actual one is around 3.5 hours max. Thats still quite worse than in Windows.

I am new to Linux. Could you please elaborate how you have achieved this? What does 'backport kernel from Natty' mean?

I am already considering replacing Ubuntu with Lubuntu just to see if Battery life is improved.  

Many Thanks,
Houman

---

### Post by lancecherry on 2012-05-15
i also have the same problem ,but i heard that 10.04 can let your thinkpad better cause its kernel version(2.6.*).there are so much articles about the 3.* kernel issues,you can google it :)

---

### Post by doublem99 on 2012-05-16
getting sick of this. everyone preaching linux. battery life is terrible for me too. my laptop fan on the left in fact get hot A LOT versus then when i was on win7. 

toshiba R835 here. it has the new i5 sandy core...

frustrated with no solutions and to hear someone on here to say they actually got improved battery life?! come on

and btw i posted this problem last yr. 

SOLUTIONS ANYONE?!

running 12.04 x64

---

### Post by simohell on 2012-05-23
> **Houmie said:**
> 
I am new to Linux. Could you please elaborate how you have achieved this? What does 'backport kernel from Natty' mean?


It means that I'm running a 2-year old Ubuntu 10.04, but with an bit later kernel version (2.6.38 ) from 11.04. (Intel graphichs and X220 networking devices did not work with the standard Ubuntu 10.04 kernel)

But as Lancecherry said, maybe I'm better off with the old version than I would be with 12.04.

( if interested see f.e. [http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_X220](http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_X220) )

---

### Post by i argor on 2012-07-10
I have Lenovo X121e with 6 Cells Battery. Lenovo claims up to 11 hrs battery life, in windows i did get about 9 hrs... in debian i got about 2,5 hrs in ubuntu i get about 4,5 hrs... i cant confirm any heat issue... laptop is very cool actually.. but in opensuse for example the cpu runs realy hot and the fan always runs at full speed... 

i am almost thinking to use windows again, even buy a copy of that fkn windows.. i mean the only reason why i got that laptop was, because it says 11 hrs battery life on the box.. and now after 4 hrs the fun comes to an end

btw, i have the intel machine not amd

so the batery life in ubuntu is compared to other distributions out of the box improved but nothing campared to the performance of powermangemnt in windos which might also leads to missing hardware drivers... in windows the lenovo laptop comes with special powermanagment device driver once and as a addition a powermangemt controll software, which i never used because it raised latency for my audio work with asio drivers

---

### Post by Houmie on 2012-07-12
Hey guys,

I am the OP of this this thread and have been researching quite a bit so far.

There is the latest PowerTop version 2.0 [https://01.org/powertop/](https://01.org/powertop/)

However its very hard to build it for non linux gurus, a pity he hasn't provided a package for Ubuntu.  I wonder if any pro here can build this package for us.

Also an interesting read is this here:

[http://smackerelofopinion.blogspot.co.uk/2011/12/improving-battery-life-in-ubuntu.html]("http://smackerelofopinion.blogspot.co.uk/2011/12/improving-battery-life-in-ubuntu.html")

and part 2:

[http://smackerelofopinion.blogspot.co.uk/2012/01/improving-battery-life-in-ubuntu.html]("http://smackerelofopinion.blogspot.co.uk/2012/01/improving-battery-life-in-ubuntu.html")

Tips: [http://zinc.canonical.com/~cking/power-benchmarking/notes/reducing-power-consumption-tricks.txt]("http://zinc.canonical.com/~cking/power-benchmarking/notes/reducing-power-consumption-tricks.txt")

There is on going work on Ubuntu Power management seen here:
[https://bugs.launchpad.net/ubuntu-power-consumption](https://bugs.launchpad.net/ubuntu-power-consumption)

The problem are Lenovo, Dell and all these hardware providers who refuse to help the open source community.  They only provide their knowledge in propriety Windows drivers and think life is good.

Anyway, if someone was so kind and make us a package from latest PowerTop, that would really be appreciated.

---

### Post by i argor on 2012-07-13
i have tried your tool Powertop.. well what i see fits, but i also see that it use 3 Watt more then under Windows, also Renoise uses more CPU than under Windows which also adds some more Watt, so in total it uses around 3 to 5 watts more. which effects the battery life with a difference compared to windows with about 1 to 2 hrs

---

### Post by Houmie on 2012-07-13
> **i argor said:**
> i have tried your tool Powertop.. well what i see fits, but i also see that it use 3 Watt more then under Windows, also Renoise uses more CPU than under Windows which also adds some more Watt, so in total it uses around 3 to 5 watts more. which effects the battery life with a difference compared to windows with about 1 to 2 hrs

Glad it could help. Are you using the version that comes with Ubuntu, which is a bit outdated?

PowerTop 2.0 has been rewritten quite a bit they claim.  I managed to compile it and build a 64Bit package on Lubuntu. I could share it on my Dropbox if you you like. Or compile it yourself.

Btw, Use Lubuntu instead of Ubuntu on your laptop.  It uses far less power.  I think its Unity that uses too much animation and hence too much power.

I have a 6 cell battery Lenovo X220 and it runs with Lubuntu 4:15 hrs. But I also noticed unlike Windows the indicator isn't as accurate. So it could be in fact more...

One more thing, don't use dark backgrounds, unlike what you would think LCDs use more power to show dark than bright colours.

---

### Post by i argor on 2012-07-14
there is something else which has an impact on battery life... in windows the cpu slows down, ok and it switches to so called passive cooling... and turns on cpu fan only when necessary...

in ubuntu also on battery the cpu fan runs at full speed which is good for cooling but bad for battery life and also lifetime for cpu fan. the longer the cpu fan runs the louder it will get in a couple months... i am not sure what is better, to buy a new cpu cooler every half year or to over heat the cpu a little, will buy a new machine anyways in 2 or 3 years :D

edit:

i did just find something, but i am not sure yet if it helps or not

[http://askubuntu.com/questions/22108/how-to-control-fan-speed](http://askubuntu.com/questions/22108/how-to-control-fan-speed)

---

### Post by i argor on 2012-07-14
i can not confirm that the link from above works perfect...

but here is another walk through which seems to work very well. i am not sure jetzt what the options in those conf files mean and i need to figure out exactly how to change them, because my goal is not to overheat my cpu... but at least it seems to work... this will probably also save battery life

[http://solutionlocker.wordpress.com/2012/04/02/installing-ubuntu-12-04-on-thinkpad-x121e-i3-fan-noise/](http://solutionlocker.wordpress.com/2012/04/02/installing-ubuntu-12-04-on-thinkpad-x121e-i3-fan-noise/)

---

### Post by i argor on 2012-07-14
Oh great.. this makes the battery last about 1 hr longer :D

i knew the running fan must have impact... it saves about 2 or 3 watts when the fan is not running..

definitively have to bookmark this blog.. so for me the problem is solved now..

---

### Post by Houmie on 2012-07-16
hmm nice one. The blog seems to be specific to a X121e i3 model. The values for the fan could be different for X220 model? No idea really.

The second one looks also interesting.

One other major problem is that I am not sure if Ubuntu makes use of Intel Speedstep technology. To use full speed only if its required.

---

### Post by wangmf8877 on 2013-02-26
Ubuntu should control cpu fan speed the same way as windows does, so to get a comparable working time as windows.

I have a T60p. The cpu fan runs like a helicopter landing after a few months under Ubuntu 11.04. Recently, sometimes I saw "fan error" while the machine starts.

Ubuntu really sucks in these aspects, although it is a good free OS overall.


> **i argor said:**
> there is something else which has an impact on battery life... in windows the cpu slows down, ok and it switches to so called passive cooling... and turns on cpu fan only when necessary...

in ubuntu also on battery the cpu fan runs at full speed which is good for cooling but bad for battery life and also lifetime for cpu fan. the longer the cpu fan runs the louder it will get in a couple months... i am not sure what is better, to buy a new cpu cooler every half year or to over heat the cpu a little, will buy a new machine anyways in 2 or 3 years :D

edit:

i did just find something, but i am not sure yet if it helps or not

[http://askubuntu.com/questions/22108/how-to-control-fan-speed](http://askubuntu.com/questions/22108/how-to-control-fan-speed)

---

### Post by jovanovm on 2013-04-03
hey OP and the rest. I don't know if you or anyone else is still reading this thread, but in case you are, this is what I use with an x220, and I have better battery life in linux than in windows.

[http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html)

i messed around with powertop and all that other crap, but this really works. instructions should be fairly simple (i don't use ubuntu primarily anymore, but this should help you)

---

