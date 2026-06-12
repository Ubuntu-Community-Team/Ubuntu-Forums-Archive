---
title: "Sony Vaio Z Support"
date: 2008-12-15
forum: Hardware
---

### Post by munsell on 2008-12-15
Hello,

I am very interested in hearing about peoples' experiences with linux on the Sony Vaio Z.  I have read a few posts on this subject, but some threads seem to have conflicting information.  I would really like to know if people have been able to control the monitor brightness and whether or not any other major issues have been encountered (graphics card switching, etc.).

Thanks!

---

### Post by motoko28 on 2008-12-17
Hi i have a vaio z21wn and i'm able to change the brihtness with the command  setpci -s 00:02.0 F4.B=FF (where FF is the max and 00 is black screen). The grafic card that i use by noe is the intel one, here  [http://neotokyo.sytes.net/](http://neotokyo.sytes.net/) explains how to switch between the grafic cards but requires install windows xp and boot it before ubuntu to choose the card that will use the ubuntu.
PS:if you discover any interesting new about how to configure other things or you have some another question to ask you can send me an email if you want to [email]jaumedarder@gmail.com[/email]

---

### Post by avilella on 2009-01-02
Hi all,

I took the liberty of creating a launchpad team for the people who own or develop for the Sony Vaio Z-series laptops, so that we can have more visibility upstream when having to ask for patches or support.

[https://launchpad.net/~z-series](https://launchpad.net/~z-series)

I'll be sending a couple of messages to ubuntuforums, nvidia and notebookreview forums to gather the ~35 users I've identified so far.

Cheers,

Albert.

---

### Post by motoko28 on 2009-01-03
Hi i've joined the launchpad teamb, i dont know about hoy works the launchpad thing, i search but i dont found anything about the laptop, i will help i anything i can

---

### Post by bherrmann7 on 2010-03-18
Hi.  Is anyone using a vpcz11x9e?   I have one on order, but as I now
understand 'z series' is really a range of hardware ... so I'm wondering
if anyone has had success with the latest in the lines of the 'z
series'.    I'm also new to launchpad so be gentle.

Note:  Alexei Pashkovsky has suggested that his general impression with sony Z-series is "broken bioses, noisy fans, poor support for ANY operating systems".

---

### Post by Xyp on 2010-04-02
Hi There.
 
I'm also seriously considering a Z purchase within the next few weeks... and I'm one of the annoying people who know just enough about linux / computers in general to get myself in trouble. I don't care at all for Windows, and I'd prefer not to drink the Apple kool-aid if I don't have to (I have experience with both).
 
I'd love to hear from anyone with insights as to how (and how well) the Z is running Ubuntu... and whether I'd (read: total noob who just installed 9.10 on a 4 year old Dell two weeks ago and knows nothing about nothing other than being pretty fascinated with the OS in general) be able to successfully install / run Ubuntu if I were to make the Z leap.
 
I've joined the Launchpad group, and look forward to hearing more.
 
Thanks.
 
-x-

---

### Post by bherrmann7 on 2010-04-03
My advice is to stay away from the Z until there is a clear guide for going from "Just purchased at store" to up and running.   I canceled the order for my Z because I believed after looking for a few days, that the waters were too murky.

---

### Post by helltone on 2010-07-19
Any advances on this matter? I'm thinking of buying a Sony Vaio Z but if Ubuntu does not run well on it I'll rather buy a Dell.

---

### Post by jothishankar on 2010-07-29
Guys,

I'm planning to buy a Sony Vaio z series machine. Well, I already own a Lenovo R61 in which I have Windows 7 + Ubuntu 9.04 dual boot. I absolutely faced no problems so far. But this machine is almost 2 years old and I'm willing to buy a new one and was seriously considering Sony Vaio Z series. I have decided that in the new machine that I buy, I would just have Ubuntu as the only OS on the machine. Now after searching for some results on installing Ubuntu on the Z series, I became really skeptical whether to buy this or not. Can anyone here please let me know if the Ubuntu installation is just out of the box on the Z series or do I have to fight with some of the device drivers to get them fixed so that they work the way they should?

---

### Post by lmlahti on 2010-08-18
I have the same problem, planning to buy Sony Vaio VPC-Z12M9E/B but not sure how Linux (Ubuntu 10.04, for instance) would run on it. Any information/experiences would be appreciated.

br.
- A

---

### Post by Jasman on 2010-11-04
I've just gone through a lot of hoops to install 10.10 (Kubuntu, in this case) as a permanent, full install on a 16gb USB stick, and I have to say, it's working quite well. One caveat: I think to make it work with full graphics support, you have to mod the BIOS to be able to unlock the setting that allows you to switch to static graphics on boot. In my case, I'm currently running the full Nvidia graphics driver and switched on Speed, meaning the Intel graphics are off (I think). Some features don't fully work, like all of the buttons (and I've tried to enable the brightness on Nvidia with no luck yet - look for tutorials), but the volume keys work out of the box.What's amazing is that it's surprisingly snappy running off a USB stick.

The interesting thing is, I did this in part to see if really erratic touchpad functionality I'm getting in Windows is really a hardware issue, which I was sure it was, but the thing's working great in Linux.

Edit: Unfortunately, I can't at this point figure out how to mount my Windows partitions, since they're in a RAID0 array, and evidently this involves some acrobatics I don't yet understand (if it can be done at all). Another thing you can do with the modded BIOS is choose to not use RAID, but I guess this isn't a popular choice, since it degrades performance. I was hoping I could at least use Linux to access my Windows partitions if problems ever arise. No luck at this point.

Edit2: I figured out how to mount the Windows partitions, so forget that. Also, while the touchpad seems ok, once in a while I get the cursor jumping around while I'm typing. Once upon a time I seem to remember when typing and navigation were rock solid on all computers. Probably the result of building in too many features. It's kind of like cell phones that do everything except work well as phones.

---

### Post by dpcat237 on 2010-11-17
I have Sony Vaio Z (VPCZ11C5E) and here ([http://goo.gl/UZQ8](http://goo.gl/UZQ8)) I explain how I resolved (thanks to another people too) this problem :))

---

### Post by cultpenguin on 2010-12-13
Hi
 
Just to let you know that with the first alpha 11.04 release, I can boot Ubuntu in live mode with full graphics, wireless,..

Haven't actually installed Ubuntu yet, but I am very very pleased to see Ubunut boot on my Sony Vaio Z directly from the live disk.

my vaio is a VPCZ12M9E

Finally it seems I will be able to run my fav OS with no hassle on the VaioZ..

- Thomas

---

