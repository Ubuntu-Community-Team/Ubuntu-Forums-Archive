---
title: "My First Linux Laptop"
date: 2008-05-14
forum: Hardware
---

### Post by systemarpi on 2008-05-14
Hi, I have just go my first Linux Laptop (well.. actually is my first laptop anyway)

I have some questions, if somebody could help would be really nice.

1)
I notice there is not a “laptop version” of Ubuntu, but I have read that is possible to optimize the kernel for better battery life (I could get source if you want), so… if do I have to do this by my own? Or I have other option?

2)
I tried to goggle for “laptop specific” cool Linux app, but fail, since I have never had a laptop, I was wonder, do you know any “cool” app for laptops? (I mean for example: battery or wireless app, don’t know… stuff more “like” for laptops)

3)
Is there anyway to control the way Ubuntu loads to RAM?, under Windows (I dual boot) I feel my ram is wasted…. ~1GB always free… I don’t know.. I read once: “unused ram is wasted ram”

4)Is there any good linux app to control CPU freq or anything can help to performance and battery life balance? I look at AMD and they have a CpuFreq utility for my processor but don’t knot.. does anybody has some experience here?

5)
Anything else I should know about Linux under laptops. (I guess I know nothing at lest no experience here… I have never had a laptop)

If its important, my specs:
OS: Kubuntu 8.04 (32bits) and Windows Vista (32bits)
CPU: AMD Turion 64x2 TL-60 (@ 2.0 Ghz)
RAM: 3GB DDR2
HD: 250GB @ 5400rpm
CHIPSET: ATI RS690T

---

### Post by tgm4883 on 2008-05-14
> **systemarpi said:**
> Hi, I have just go my first Linux Laptop (well.. actually is my first laptop anyway)

I have some questions, if somebody could help would be really nice.

1)
I notice there is not a “laptop version” of Ubuntu, but I have read that is possible to optimize the kernel for better battery life (I could get source if you want), so… if do I have to do this by my own? Or I have other option?

I believe you are talking about either laptop mode or dyn ticks.  Both are included in the live cd and will install on laptops.

> **systemarpi said:**
> 
2)
I tried to goggle for “laptop specific” cool Linux app, but fail, since I have never had a laptop, I was wonder, do you know any “cool” app for laptops? (I mean for example: battery or wireless app, don’t know… stuff more “like” for laptops)

Wireless apps included (network manager), battery app included (power manager)

> **systemarpi said:**
> 
3)
Is there anyway to control the way Ubuntu loads to RAM?, under Windows (I dual boot) I feel my ram is wasted…. ~1GB always free… I don’t know.. I read once: “unused ram is wasted ram”

Linux already uses ram differently than windows.  Once it loads something into ram it doesn't unload it until it needs that space for something else

> **systemarpi said:**
> 
4)Is there any good linux app to control CPU freq or anything can help to performance and battery life balance? I look at AMD and they have a CpuFreq utility for my processor but don’t knot.. does anybody has some experience here?

Already included, it changes the freq automatically when on battery power.  

> **systemarpi said:**
> 
5)
Anything else I should know about Linux under laptops. (I guess I know nothing at lest no experience here… I have never had a laptop)

If its important, my specs:
OS: Kubuntu 8.04 (32bits) and Windows Vista (32bits)
CPU: AMD Turion 64x2 TL-60 (@ 2.0 Ghz)
RAM: 3GB DDR2
HD: 250GB @ 5400rpm
CHIPSET: ATI RS690T

What wireless card do you have?

Why did you put a 32-bit OS on your 64-bit hardware?

---

### Post by systemarpi on 2008-05-14
I installed the 32bit version since I found no reason to go for the 64bits

1)	I have 3GB of RAM and I am not going to upgrade to more, the MAX supported is 4GB so, even with a 32bits OS will be enough
2)	Most application don’t take any advantage of 64bits
3)	There's a lot more support and app for 32bits (sadly but its true)
4)	I am working in a Open Source ERP&CRM ([http://systemarpi.googlepages.com](http://systemarpi.googlepages.com)) so, I guess is better to keep my environment at x86 instead of AMD64

I could install AMD64 but, do you really see any advantages? I know everything is possible, but there are even problems to install flash under AMD64.

The Wireless Card is a RealTek RTL8187L

---

### Post by tgm4883 on 2008-05-14
> **systemarpi said:**
> I installed the 32bit version since I found no reason to go for the 64bits

1)	I have 3GB of RAM and I am not going to upgrade to more, the MAX supported is 4GB so, even with a 32bits OS will be enough
2)	Most application don’t take any advantage of 64bits
3)	There's a lot more support and app for 32bits (sadly but its true)
4)	I am working in a Open Source ERP&CRM ([http://systemarpi.googlepages.com](http://systemarpi.googlepages.com)) so, I guess is better to keep my environment at x86 instead of AMD64

I could install AMD64 but, do you really see any advantages? I know everything is possible, but there are even problems to install flash under AMD64.

The Wireless Card is a RealTek RTL8187L

Spoken just like someone who hasn't tried it and listens to the crap on the forums.

i386 - 25125 binary packages
amd64 - 24839 binary packages
Not exactly a huge difference in packages.

Any number crunching app will see huge improvements.

And I'd like to know when installing flash on 64-bit Ubuntu didn't work for you.  Most likely you have read the forums and come up with that conclusion.  I don't blame you, the forums are a scary place to read about 64-bit Ubuntu.  Especially when the people spreading that crap don't actually use 64-bit Ubuntu.  Just FYI, if I were you, I wouldn't go to a Toyota dealership and ask them about BMW's.  It's just common sense.

---

### Post by ninowilson on 2008-05-14
Hi all,
I have a dell inspiron 6000 converted to all ubuntu (100%)
Everything OK but unable to work on the cd rom It semms to me that the OS (8.04) is not recognizing the cd rom drive.
Any help appreciated
Wilson

---

### Post by PSP_DEMOLISHER on 2008-05-14
i just wanted to say your english is great, You should upgrade to the 64bit version, its not much work and it is very comfortable once you get used to it.
When you install ubuntu on a laptop it automatically sees the fact that your on a laptop and it configures to that.
What is your native language?

---

