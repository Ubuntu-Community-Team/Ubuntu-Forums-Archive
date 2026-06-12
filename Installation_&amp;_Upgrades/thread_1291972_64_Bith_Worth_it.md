---
title: "64 Bith Worth it?"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by ali_williams on 2009-10-15
My 32-bit Ubuntu I have had since 7.04 and I have been upgrading ever since. The box is turning into crap (mostly because of all of the apps i have been adding) So I wanted to start off fresh with 9.10 the issue I have is that I have a 64bit processor and 4gb of ram. Now to get the 4gb of ram to work on my 32-bit was to compile it with the 32bit server kernal but I wanted to know is it worth going to 64bit os if I wanted to start over fresh?

---

### Post by Thelasko on 2009-10-15
> is it worth going to 64bit os
How isn't it worth it?  You don't have to give up **anything** these days to use 64-bit Ubuntu.

---

### Post by jackmetal on 2009-10-15
Yes, I believe it is worth it.  I started running 64bit on my 64bit capable systems at 8.10 and have had no problems with anything at all.  It all works great and of course some things are much faster.

---

### Post by dabl on 2009-10-15
There's a 64-bit forum, and the question has already been asked and answered:

[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by ali_williams on 2009-10-15
> **dabl said:**
> There's a 64-bit forum, and the question has already been asked and answered:

[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

cool thanks i will check it out

---

### Post by presence1960 on 2009-10-15
The question you should be asking is ***_"Why not 64 bit?"_***

---

### Post by Thelasko on 2009-10-16
> **presence1960 said:**
> ***_"Why not 64 bit?"_***

I couldn't put it better myself.

---

### Post by landloper on 2009-10-16
Thanks, folks.  I was lurking and looking for a 64-bit install answer because my 9.04 RISC server install CD is defaulting to 32 bits.  I will check out the link - thanks, ali_williams

---

### Post by Thelasko on 2009-10-19
> **landloper said:**
> Thanks, folks.  I was lurking and looking for a 64-bit install answer because my 9.04 RISC server install CD is defaulting to 32 bits.  I will check out the link - thanks, ali_williams

I believe a [RISC]("http://en.wikipedia.org/wiki/Reduced_instruction_set_computer") processor is something different all together.  We are talking about [x86]("http://en.wikipedia.org/wiki/X86") architectures which is a [CISC]("http://en.wikipedia.org/wiki/Complex_instruction_set_computer") design. 

The two designs are not compatible.  You will notice many differences on a RISC machine and an x86.

---

### Post by azumi123 on 2009-10-20
> **presence1960 said:**
> The question you should be asking is ***_"Why not 64 bit?"_***

This is the sort of typical knee jerk response that sends people off headlong into trouble - which then gets reported back as faulty OS and false bugs claims.

There are many reason to not change to 64 bit and very few in favour. 
Such as:
1. some applications actually run slower 
2. Very few if any applications run faster
3. Most peripherals in use dont have compatible drivers 
4. Many applications that could benefit from the larger memory space 
availabe above 4Gb aren't built to address it anyway
5. The vast majority of systems don't use all the 4Gb they already have
and have no use at all for more

and so on.

This is how you choose:

1. sit down with pencil and paper and write down the list of things you
can't already do:

2. write alongside them how 64 bits would help (and find out IF it would first - making assumtions will cause you problems by the bucketfull)

3. Now write down what you already do that you want to do faster

4. GOSUB 2 above

5. write down what you want to do that NEEDS more memory

6. Find out if applications exist that you need to use that can address it

7. Make a list of your peripherals and check for compatible drivers.

The long and short is 64 bits offers: 

1. larger memory addressing IF programs are designed to use it - some are not

2. faster processing IF programs are designed for 64 bit from the ground up 
but only in a very few instances 

3. No other advantage whatsoever. 

64 bits is problematic because:

1. existing software can often run slower and MAY not be fully compatible despite claims to the contrary (not everything is compiled as it should be)

2. Some peripherals may not work

3. Your system will be out of step with the majority of existing code

4. and of course the cost in both money and time of making everything work 
just to your existing specification should not be overlooked.

You might decide you need 64 bits now.
Personally I'll take another look at 64 bit systems about 3 years from now.
Right now I can't even get 32 bit UBUNTU to talk to my modem and I've been trying for 3 days. 

Az

---

### Post by presence1960 on 2009-10-20
> **azumi123 said:**
> This is the sort of typical knee jerk response that sends people off headlong into trouble - which then gets reported back as faulty OS and false bugs claims.

There are many reason to not change to 64 bit and very few in favour. 
Such as:
1. some applications actually run slower 
2. Very few if any applications run faster
3. Most peripherals in use dont have compatible drivers 
4. Many applications that could benefit from the larger memory space 
availabe above 4Gb aren't built to address it anyway
5. The vast majority of systems don't use all the 4Gb they already have
and have no use at all for more

and so on.

This is how you choose:

1. sit down with pencil and paper and write down the list of things you
can't already do:

2. write alongside them how 64 bits would help (and find out IF it would first - making assumtions will cause you problems by the bucketfull)

3. Now write down what you already do that you want to do faster

4. GOSUB 2 above

5. write down what you want to do that NEEDS more memory

6. Find out if applications exist that you need to use that can address it

7. Make a list of your peripherals and check for compatible drivers.

The long and short is 64 bits offers: 

1. larger memory addressing IF programs are designed to use it - some are not

2. faster processing IF programs are designed for 64 bit from the ground up 
but only in a very few instances 

3. No other advantage whatsoever. 

64 bits is problematic because:

1. existing software can often run slower and MAY not be fully compatible despite claims to the contrary (not everything is compiled as it should be)

2. Some peripherals may not work

3. Your system will be out of step with the majority of existing code

4. and of course the cost in both money and time of making everything work 
just to your existing specification should not be overlooked.

You might decide you need 64 bits now.
Personally I'll take another look at 64 bit systems about 3 years from now.
Right now I can't even get 32 bit UBUNTU to talk to my modem and I've been trying for 3 days. 

Az

Your assumptions and info are outdated & obsolete, does that qualify as knee-jerk? What you say about 64 bit was true a couple years ago, but now it is smooth sailing. So you can get up to speed on 64 bit Ubuntu see [here]("http://ubuntuforums.org/forumdisplay.php?f=343").

As far as modems what can anyone say, if you can't go broadband then stick with 32 bit. But that hardly qualifies as a valid reason to discourage someone from going 64 bit unless they only get online via a modem. That encompasses only a small fraction of the total of Ubuntu users. So you can scratch that out as an argument against 64 bit.

When you go 64 bit most applications have a 64 bit equivalent and are in the repositories. They work just fine. There is even 64 bit Flash [here]("http://ubuntuforums.org/showthread.php?t=1259102") and 64 bit java plug-in [here]("http://ubuntuforums.org/showpost.php?p=6791349&postcount=59").

---

### Post by azumi123 on 2009-10-20
> **presence1960 said:**
> Your assumptions and info are outdated & obsolete. What you say about 64 bit was true a couple years ago, but now it is smooth sailing.

Not last week it wasn't. I know because I looked at it before installing a new 32 bit desktop system.

It will continue to be true for a couple of years at the very least.
IMO of course. 

I'm glad it's plain sailing for some though. Its just a pity 32 bit computing
isn't yet.

Az

---

### Post by presence1960 on 2009-10-20
> **azumi123 said:**
> Not last week it wasn't. I know because I looked at it before installing a new 32 bit desktop system.

It will continue to be true for a couple of years at the very least.
IMO of course. 

I'm glad it's plain sailing for some though. Its just a pity 32 bit computing
isn't yet.

Az

you do realize that you are only one of a small minority who have this problem. To go making blanket claims that 64 bit is not viable because you can't get it to work is absurd.

I have problems with Fedora. I don't know why. For me to make claims like yours about fedora is beyond my imagination since most run it with no problem.

I don't bash Fedora because it obviously is a fine OS for many users. For whatever reason I struggle with it on my machine. But I have no problem with 64 bit Ubuntu & 64 bit Sabayon.

Just because you can't get it to work on your machine is hardly a reason to tell others not to use it. Since you couldn't get 64 bit up & running how do you know it's benefits? or how it runs? Or what apps work fine in it or not?

---

