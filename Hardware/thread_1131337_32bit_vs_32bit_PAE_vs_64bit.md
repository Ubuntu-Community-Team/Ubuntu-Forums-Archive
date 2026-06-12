---
title: "32bit vs 32bit PAE vs 64bit"
date: 2009-04-20
forum: Hardware
---

### Post by dhysk on 2009-04-20
While looking into my options about getting my system to use all the ram I have in it I ran across PAE.  I've been hesitant to run 64bit versions because most my apps are 32 bit, I do a lot of multimedia, and although I know there are work a rounds I'm not sure I want to deal with the headache.

The question will the extra 1.3 GB of memory really boost system performance under PAE, and how does 32bit w/PAE enabled compare to Ubuntu_64.

System:
Intel Core2Duo E8400 3.0GHZ
2 x2GB sticks of Corsair XMS RAM
9800GTX video card
500GB Maxtor HD

I'm thinking of waiting until the 23rd and using Jaunty to test.  First I would install the x86 Desktop version and run the Phoronix -universe test.  Then install the server kernel and run the tests again.  After that do a clean install of the 64bit Jaunty for one more run.  I'm interested in seeing the performance differences.  This takes a long time to do so I was wondering if anyone has seen any benchmark testing along these lines.  All the ones I've seen comparing PAE with x64 are using less than 4GB RAM.

My initial feeling is that the x64 will have a little advantage, based on what I've seen from the past.  However its so little and most apps still show very little to know difference between x64 and 32 bit solutions.  That being said PAE also comes at a performance cost, and I'm not sure if enabling the extra 1.3 GB RAM will do much good.  What are your thoughts?

P.S.  This is not another 64bit rules thread, its about the cost/benefit of enabling the extra ram via PAE or 64bit OS.  So please only **QUANTITATIVE** inputs if possible.

---

### Post by 00b00nt00 on 2009-04-21
My understanding is that Ubuntu 32bit comes with PAE active as standard.

As for 64bit, well, really that OS if for addressing <4GB RAM. It's the way of the future, of course, but so many programs these days are still 32bit.

I'd stick with the 32bit OS, for reasons of stability and compatibility. Learn to use your computer within it's limits (i.e. if you are short of RAM, don't have scores of applications open). It's not a Ubuntu thing; you'd have the same problems on OS X and Windows.

As for quantitative input, why don't you install the 32 / 64 bit versions of Ubuntu and try yourself. Ultimately, only you know your needs.

---

### Post by dhysk on 2009-04-21
Thank you for your input.  I would rather stick with 32bit, however I run VMware and the extra ram helps a lot.  The standard Ubuntu doesn't have PAE enabled.  I thought so too until I resized it's only seeing 2.5 GB of my 4GB of RAM.  I ran the Jaunty x64 and it saw 3.8GB so I know it wasn't a hardware issue.

Although the question remains what are the performance differences?  For instance benchmarks show that unless your using specific programs, running 64 bit OSs show no improvement, and normally a few less FPS in game performance.  This information is based on a test done by Phoronix over a year ago.  I believe they used 32,64bit versions of Fedora and Ubuntu for their tests.

In other tests I've seen PAE didn't provide any performance increase.  Most of them showed the same performance however one test using 1GB of ram showed 3%-6% decrease in performance.  None of these tests used more than 4GB of ram though.  Just like x64 pays an overhead for all the extra RAM addressing so does PAE.  Unfortunately since I'm right on the cusp of it I'm not sure if the performance boost from the extra ram will out way the performance hit from PAE.

**Conclusion**
Testing shows that 64bit(unless your using specific programs) shows little to no performance improvement over 32 bit systems.  So operationally x64=x32 with <4GB of RAM.

Testing also shows that x32 PAE = x32 with <4GB of ram.

My thinking is that, since given the above, x64 and x32 PAE will be fairly close in performance from 4GB - 64GB of ram.  However, I would like more recent data.  Anyone else interested in me doing the test I stated above?

---

### Post by 00b00nt00 on 2009-04-22
By all means have a play around and report back with your findings. I'm running Ubuntu on a Yonah based Celeron M with 2GB RAM, so 64bit is out of the question. With Virtualbox I allocate 512 MB to Windows XP, and my system is stable, but then I don't ask much from it.

If you're after bleeding edge performance, or you're running your system on the edge, dual-booting could be an option.

---

### Post by dhysk on 2009-04-24
I have just installed 9.04 x86 desktop and I am now starting testing.  Unless I have issues I will have some results(hopefully) in a few days.  I'm using phoronix with the Nvidia 180.51 drivers and im running the universe test suite so it takes about an entire evening to run the test.  Not to mention the install process for it.

I will recap once I'm done however this is my plan.

Install 9.04_x86 on a 10GB partition.  Install Nvidia drivers enable compiz.  Install phoronix from the Ubuntu repos and start the universe test suit.(I'm installing the universe suit now)

Then I will use the same install and enable PAE by installing the server edition kernel, hopefully it will work the same as it did in 8.10.  Then I'll run the universe test suit again.(Probably tomorrow)

Then I will wipe out the install and do a clean install of Jaunty 64 desktop and run the test again.(possibly Sunday or Monday)

---

### Post by PendragonUK on 2009-04-24
Once you are sorted would please write a "How to" for installing PAE.

I also have 4Gb of RAM but prefer to use 32bit due to compatibility. The RAM is there might as well use it...

---

### Post by dhysk on 2009-04-24
This is how you do it with 8.10.  I presume it will be the same with Jaunty.  Basicaly from what I understand is you are replaceing the kernal with the server addition that has PAE enabled.  Other wise you would have to recompile the kernel.

The link bellow has a how to for Ubuntu 8.10

[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

---

### Post by dhysk on 2009-04-27
Ok, I have done almost all the testing unfortunately the last 3-4 tests don't work under the 64 bit.  The enemy territory quake wars demo, 2004 quake wars demo, and the two uniengine tests don't run.  So if anyone has any inputs on what libs I need I can run the tests and post the results.  A basic run down is the 32bit vs PAE are pretty much the same with some apps running only slightly faster in PAE, most run the same and a few actually run better under 32bit.  From what I saw of the 64bit tests with the exeption of the gaming tests the 64bit tests numbers looked like the best of the 32bit and PAE numbers.

---

### Post by ursoouindio on 2011-04-20
Hello you all.

Right now I'm facing exactly the same question. I'm downloading Ubuntu Natty Beta 32-bit, while I've been using Ubuntu Natty Beta 64-bit.

I've always used 32 bit systems but now I got a new notebook with a Core i7 Sandy Bridge processor, 8 GB Ram and a nVidia GPU with Optimus Technology. As the larger RAM, I decided to give it a try on 64 bits systems. 
(Optimus is other completely different issue that I already learned how to handle)

The reason I used the newest beta release is that it was the one that better suited my new hardware.

I'm facing some instabilities and I'm not sure if its due (or maybe partly ) to the video driver, the Beta release or the 64 bits overall compatibilities. Besides incompatibilities, I've also had difficulties compiling some of my favorite apps.

BTW, the most important part of getting me back to 32-bits is that I need (for work) to compile and run some software that are not supported for 64-bit yet. I'll probably get into developing it soon as well and there are no expectations on embracing 64-bits compatibility (I fiund this important, but its not my call). For now, my attempts to compile some needed libraries failed (problems with .so or .a libraries, as I assumed) and I can't use that software on my new machine.


Just a couple of days ago I read somewhere that there is a 32-bits support for larger ram, the PAE module. I also read that it would have a bit worse (how much?) performance when compared to pure 32-bits or 64-bits.

What would you recommend to me?

Reading this thread so far, I realize that I will not miss much by going for 32-bit pae, but maybe something has changed since 2009 and probably people have more experienced opinions now.

I look forward for reading your thoughts. But I wouldn't wait much longer :P

Regards!

---

### Post by gradinaruvasile on 2011-04-20
You should have started a new thread.

I use 32-bit "bigmem" kernel (=32bit kernel with PAE enabled) on my machine albeit on Debian. I have 4 GB RAM.
I dont see any performance difference vs the non-bigmem kernel.

Ubuntu has the pae-enabled 32-bit kernel in the package named

linux-image-2.6.38-8-generic-pae

Just install it and boot from it. In theory 32-bit PAE kernel should make possible the addressing of 64 GM RAM.

---

### Post by ursoouindio on 2011-04-20
> **gradinaruvasile said:**
> You should have started a new thread.

I use 32-bit "bigmem" kernel (=32bit kernel with PAE enabled) on my machine albeit on Debian. I have 4 GB RAM.
I dont see any performance difference vs the non-bigmem kernel.

Ubuntu has the pae-enabled 32-bit kernel in the package named

linux-image-2.6.38-8-generic-pae

Just install it and boot from it. In theory 32-bit PAE kernel should make possible the addressing of 64 GM RAM.

Thanks for your thoughts, I really do think that there is no discernible difference on 32-bits with pae and 64-bits besides the actual huge upper limit on RAM size and the possibility for one single application use more than 4 GB of ram. The last is the more concerning to me, but even then I don't recall being on such situation actually.

---

### Post by gradinaruvasile on 2011-04-20
> 
and the possibility for one single application use more than 4 GB of ram


This means that in 32-bit PAE kernels applications are capped at 4 GB?

---

### Post by oldfred on 2011-04-20
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Essentially says if you can use the 64bit kernel you should.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)

Phoronix also has several versions of Sandy Bridge that they tested. They say if it works it is great, but there still are issues.

---

### Post by ursoouindio on 2011-04-20
> **gradinaruvasile said:**
> This means that in 32-bit PAE kernels applications are capped at 4 GB?

Actually I wouldn't affirm that for sure. I'm the one here questioning on APE :P

As I understand (and it is quite limited through this things) the system and every of each apps are still 32-bit. PAE is something that allow the system to map more RAM than the usual limitation of 32-bit. It is clearly something when the system deals with a number of applications and those would have more working space to share.

But those apps are still 32-bit and usually they wouldn't have a similar PAE thing on their compilation to map more than 4 GB of RAM to each of them itself.

But I may be wrong, as I'm just supposing.

---

### Post by ursoouindio on 2011-04-20
> **oldfred said:**
> Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Essentially says if you can use the 64bit kernel you should.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)

Phoronix also has several versions of Sandy Bridge that they tested. They say if it works it is great, but there still are issues.

My hardware supports 64-bit, but I'm more concerned on compatibilities. The headache to make things work may not pay for minimal performance gain.

I'm not aware of what kind of problems are happening with Sandy Bridge, but I'll take a search on this.

Thanks!

---

