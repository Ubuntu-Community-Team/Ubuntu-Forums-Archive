---
title: "Toshiba Satellite A665 Overheating Problems"
date: 2011-02-22
forum: Hardware
---

### Post by shawnc_nmb on 2011-02-22
I've been using Ubuntu for awhile now and I have installed it on my Toshiba A665 which has a i7 Core, 8g Ram using 64bit 10.10 ubuntu

It ran ok for afew months minus afew Wifi problems, but now I turned it off on Friday after work and when I booted it back up on Sunday it overheated within 10mins.   I have searched the forums over for hours and can find no solution to what happened.  My Apt Logs show no Upgrades that would effect it so I'm not sure what to do.  Without that computer I can not work,  and that's not good.  

I use Conky to keep tabs on my system and it used to report my GPU around 153degrees which seems hot but it was stable,  My hard drive never went past 60-70degrees.  

Now All of a sudden My GPU hits 210++ and my HD is 90-100 and then I get shutoff on a Thermal Overload.

This system is a single boot Install of Ubuntu so I have no Windows to fall back on and I'm not sure what to do next.

I can try to access it tommorow when it cools down again and get a LSCPU, LSPCI and LSUSB dump of the Computer

and a ASPI -V dump

The only thing I can think of causing it is that at Work I run Dual monitor one External and the Laptops using Seperate Screens. Could this be causing the problem?

I am using the Latest Nvidea Driver in the Repo also.

The other thing I noticed that was weird is that it seems I have 2 profiles or icon sets or something as randomly when I come home from work The Icons are set Wrong and I have to Switch themes back to my theme. The other thing when that happens is Nautilis is very strange looking.  I never could figure out what is happening with that but it might be part of the problem.

Any help would be greatly appreciated as I donnu what to do,  I have been using Ubuntu since Edgy and Fiesty and Don't wanna switch to another Distro but I need a working cpu.  

Thanks
Shawn C

---

### Post by Omega The End on 2011-05-05
I have the i3 model (with 4GB of RAM) and mine also overheats from time to time. It gets really annoying, I don't know how to fix this, it gives no warning as to when it's going to shut down either, it just happens abruptly.

---

### Post by shawnc_nmb on 2011-05-06
This may not help you but my problem turned out to be the internal fan.  I had to send my Laptop back to Toshiba to have it fixed.  

I purchased this model based on the specs it had without seeing it in person and I will never do that again. What amazes me is that I purchased this laptop on 8/25/10,  I sent it back on 3/06/2011 so the internal fan just went bad in less then what 6-7 months?  There tech support would not tell me anything about what they replaced or did to the laptop.  The return invoice just said replaced internal fan.


After 2 weeks when I finally received my laptop back from Toshiba's Depot they forgot to put the screw that holds the DVD-ROM drive so when I ejected the DVD the entire drive came out.  I called support again, they thought it was funny as hell but could not send me the screw to replace it with instead wanted me to send the laptop back.  This is my work laptop so I obviously could not return the laptop for 2 weeks over a screw.

Anyway to sum things up. Toshiba has gone down hill since there older P205 models and I won't purchase another one in my life.

---

### Post by Junx87 on 2011-06-25
Sorry for adding more to the complaint box, but I am also having this same problem. 

I am running Ubuntu 10.10 on a Toshiba Satellite L350D (Athlon X-2). I am a relatively new user to Ubuntu, let alone a Unix operating system so please forgive me if I say something dumb. 

Every once in a while I will be doing my usual thing on my laptop, surfing the web, watching youtube videos etc, and my laptop will just shut off without warning.

Obviously the first thing that popped into my mind was a thermal protection failsafe. But then it occurred to me that I've been running Windows ever since I got the laptop and never have experienced this. Of course dust and debris could have been building for a long period of time, but I think there might be something more. 

Could it be possible that there is a bug in the kernel that would trick the kernel into thinking that the CPU has overheated and should execute an immediate shutdown? Just a thought, but like I said I'm a noob so go easy on me. 

Any help would be most appreciated.

---

### Post by Yellow Pasque on 2011-06-25
> watching youtube videos..
The Flash plugin on Linux is known to be inefficient and use a ton of CPU, hence the overheating. Use Firefox Flash-Aid extension to view Youtube video in a native Linux media player. Note that this won't fix the overheating if you do something else that puts your system under load for an extended period of time. It's my opinion that a system should never overheat, even if under load, or else the cooling is inadequate. Unfortunately, that seems to be the exception to the rule with laptops :(

---

### Post by solom991 on 2012-03-13
got the same problem on the same laptop model, the following fix solved the problem completely

[http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/](http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/)

---

