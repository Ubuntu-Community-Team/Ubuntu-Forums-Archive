---
title: "Single Core To Quad Core Upgrade?"
date: 2014-04-15
forum: Hardware
---

### Post by ken0069 on 2014-04-15
I have an older system that I built about 6 years ago.  It's an ASUS P5K Pro motherboard that uses a 3.6GHz Pentium IV CPU and 4GB of DDR 800 RAM.  I've recently found out that this socket LGA775 motherboard can be upgraded to an Xeon Quad core LGA771 CUP for around $50 using an adapter strip on that CPU.  This mod would be using an E5450 CUP which is a Core 2 Quad at 3.0GHz and is a significant step up in speed for this system, however I'm wondering if Ubuntu 12.04 will see this processor change and use it without me having to do a clean reinstall?  

I'm also looking at doubling the memory to 8GB from 4GB so that's another upgrade that's being considered.  

These two modifications will cost me just a little over $100 and will probably extend the systems useful life another 3 to 5 years.

So do you think that this upgrade can be done without having to reinstall Ubuntu?  Reason I ask is because I have a limited bandwidth internet connection.

Thanks

---

### Post by Yellow Pasque on 2014-04-15
Assuming the mobo/BIOS properly supports it, then Ubuntu (or any OS) shouldn't care what your CPU is.

---

### Post by tgalati4 on 2014-04-15
It should work out of the box, but don't get your hopes up on speed increase.  Sometimes the CPU adapters become the memory and I/O bottleneck that prevent you from really using all of the horsepower of a quad Xeon chip.  For that you would need a server motherboard or a newer motherboard with a more modern memory support chipset.

Install *phoronix-test-suite *and run a few of the tests so you can quantify what the speed increase actually is.

---

### Post by oldfred on 2014-04-15
It depends a lot on where bottlenecks are.

I built my system at the end of 2006 with a 775 motherboard and CoreDuo chip. I upgraded motherboard & video card in 2009 after nVidia video card blew up (litterally caps popped). But new nVidia & new motherboard just worked with Ubuntu. But XP wanted me to re-register. 

A couple of years ago, I was going to build new system, but bought a SSD for about $80. It was a Microcenter house brand 64GB. Its speed is about half what new one's are, but still a lot faster than my hard drives. And I then have had trouble justifying to myself much less my wife on a new computer. :)

---

### Post by ken0069 on 2014-04-15
Thanks for the info and opinions guys.  I made an offer on two x5460 Xeon Quads a while ago and if he takes me up on that I'll go ahead and make the swap.  

@ oldfred, since you mentioned 2006 I do believe it was about that time I built this particular computer?  That makes it about 8 years old now, hey.  I've got another one I built a year or two after that one using an ASUS P5kQ Pro so that's probably the one I was thinking about when I made this post.  So if I get two processors then I'll do the oldest one first, then do the other if that one works out OK.  

But again, thanks all for the input!!

Ken

---

### Post by ken0069 on 2014-04-27
Final Update:

Didn't run any benchmarks on either system prior to swapping out these CPUs but did look at the Windows 7 OS on'em (multiboot systems) to see what the performance index was on each before and after.  With just the CPU upgrade I saw a noticeable amount of speed increase on both systems and some of the scores in Win 7 showed an increase of about a 30%.  According to Win 7 the slowest part of my systems are the ATI 1650 PCIe video cards in both but they do what I need done so that's not likely to change.  

Ennywho, All flavors of Windows and Ubuntu 12.04 had no problems adapting to the new quad core chips so I'm in business.  

And a final note, if any of you are interested in info concerning this processor upgrade there's more info on it on this site.  Oh, it only took me about 30 minutes to modify the CUP mount and install them.  

[http://www.delidded.com/lga-771-to-775-adapter/](http://www.delidded.com/lga-771-to-775-adapter/)

---

### Post by tgalati4 on 2014-04-27
Thanks for the link.  I was also concerned by the additional heat load of the Xeons since they are normally used in servers and engineering workstations and the article you linked addresses that.  I find it interesting that Intel motherboards won't work with this modification.  Perhaps Intel's firmware checks the CPU product code and if not on the approved list there is no boot.

---

### Post by ken0069 on 2014-04-27
> **tgalati4 said:**
> Thanks for the link.  I was also concerned by the additional heat load of the Xeons since they are normally used in servers and engineering workstations and the article you linked addresses that.  I find it interesting that Intel motherboards won't work with this modification.  Perhaps Intel's firmware checks the CPU product code and if not on the approved list there is no boot.

Heat doesn't seem to be a problem with mine.......yet, but then again, I haven't done anything to really work the system either.  Have some video to convert though so I'll give'em a workout then..  

The AMI BIOS in both my boards doesn't have that CPU listed either but it shows up at POST with the correct CPU name, speed and number of cores.  It also gives me an error message because of this but I turned that error notification off and it goes ahead and boots now without stopping.  I've considered modifying the BIOS and may do that some day but for now it's working OK and that's all that matters.  

Did I mention that I really like that Quad Core speed? =d>

---

### Post by Yellow Pasque on 2014-04-28
> **tgalati4 said:**
> I was also concerned by the additional heat load of the Xeons

The E5450 has an 80W TDP.
A Pentium 4 3.6GHZ has a 115W TDP (if it's a Prescott) or 85W TDP (if it's Cedar Mill).

---

### Post by ken0069 on 2014-04-28
The 3.6 I took out is a Cedar Mill not a Prescott.  The Xeon I replaced it with is an X5460 @135 TDP (I think) not an E5450 as noted in post #5.

Got an  additional 4GB of memory today and installed that in one box and the  speed increase with that was noticeable also.  Need another 4GB for the  other box but that's going to be a little more expensive as it's PC8500  instead of PC6400.  

I just love this technology stuff!  That goes along with my love of Hot Rods as I have two of those I mess with when I'm not doing computer stuff.  

Big Boyz Toyz!

---

