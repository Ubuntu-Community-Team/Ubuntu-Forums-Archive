---
title: "Hp Pavillion DM4 hot amd graphics driver incompatable, opensource driver buggy?"
date: 2012-10-16
forum: Hardware
---

### Post by verdomde on 2012-10-16
Hallo,

This is a difficult one to explain,
First off, the problem...
I have a new pavillion dm4, 3060ef beats audio(graphics card is amd 7470m). The fan is always on full- probably to keep up with the near nuclear temperature of the thing. I thought it was due somehow to Quantal Alpha/Beta mis-managing the fan, but I am now led to believe it's the opensource graphics drivers  (xserver.xorg//ati). Strange but true.

I consider this some kind of bug, I will report it if you guys also agree.

I cant recall where I read about it being a driver issue, but I went imediately to the amd website and downloaded the latest drivers, including the beta ones. I built the package from the beta(12.9) first, then from the regular one(12.8). As many times as I tried it- same problem, also when I try it from the additional drivers window; the drivers dont work, it runs in low graphics mode, and I spend a day swearing at my Laptop trying to get back to the defaults...

But what I did notice is, when the ati drivers are installed, even though they dont work- the fan runs normally, quietly, and the laptop is about 20degrees or more cooler. It's tantalisingly wonderful.

So that is why I think this is a bug in the opensource drivers. I can't wait for potential updates! Who knows what damage this kind of temperature is doing to me internals?

Any help would be apreciated, if you think i should file a bug report please let me know.

Thanks a million.
Paul

---

### Post by verdomde on 2012-10-22
Quick update- I found instructions to disable the ati card, and am now just running on my other onboard card intel 3000, sandybridge. The computer is nice and quiet, and behaving ok, I still want to get the main graphics card woking though. Any help would be good.
p

---

### Post by verdomde on 2012-10-24
further udate, 
[http://askubuntu.com/questions/201810/amd-radeon-hd-7470m-proprietary-driver-not-working-on-ubuntu-12-04lts/201835#201835](http://askubuntu.com/questions/201810/amd-radeon-hd-7470m-proprietary-driver-not-working-on-ubuntu-12-04lts/201835#201835)

is where I found out about driver issues i think, the answer suggests my card isnt supported by any drivers atall and i have to wait for something to be released, can anyone verify? If this is the case then I guess this is not a bug...

---

### Post by verdomde on 2012-11-26
FYI, this has been reported as a bug, they seem to be working on it...

---

### Post by kareypowell on 2013-03-05
Hello vermode,

Did you ever get your main gfx card working? I have an Hp ProBook 4530s with both the **Intel HD 3000** + **Radeon HD 7470m**[COLOR=#000000] and I experience more or less the same issues as it relates to heating and fan noise. I came across a few post on how to configure your switchable gfx, but I don't see any of them specifically targeting the [/COLOR]Radeon HD 7470m card, so I'm hesitant in trying out the solutions, because they seem not to work for very long. I really want to install Ubuntu, but this is what is preventing me from doing so.

---

### Post by Mark Phelps on 2013-03-05
If you're waiting for AMD to come out with a Linux driver for these Hybrid Graphics machines -- then be prepared for a VERY long wait!

Why?

Because in the Windows world, these drivers come from the machine providers, not from AMD.

Thus, you're most likely waiting for something that is not going to happen.

Sorry, but when you have a machine with Hybrid Graphics, the best you can do in Linux is use some workarounds that, in most cases, disable the high-performance graphics you paid for when you bought the machine.

---

### Post by kareypowell on 2013-03-08
Hi Mark Phelps,

It seems like I'm stuck between a rock and a hard place. I really want to install Linux, but that doesn't look like it is going to happen anytime soon as you said. As I have mentioned, most of the work around are to disable the high-performance card, which seems like a waste of money to me, despite wanting to run Linux. I'm in the middle of developing some web apps right now, so I can't take the risk of attempting to try any of those fixes to suffer from any downtime. However, I might just end up selling this machine and getting a new one that has no problems running Linux in a couple months. 

Also, I contacted HP and they told me that this machine (HP ProBook 4530s) can only run SUSE Linux not Ubuntu. They also provide the drivers for both graphic cards on SUSE, but I don't think I want to run SUSE, I like Ubuntu better; however I might look into it.

---

