---
title: "Building a system"
date: 2015-08-22
forum: Hardware
---

### Post by jcm1107 on 2015-08-22
Hi,
I would like some advice on building a new system. I have been using linux in some variation for some time now (Ubuntu and mint).
I recently tried to upgrade to Mint 17 mate and killed my motherboard somehow. Yes I am sure, did CMOS reset, removed memory and reinstalled and anything else and could not even boot into bios!!

The mint 17 iso will install on a laptop I bought in a virtual machine so it was not the iso that was the problem.

I want my desktop back with mint to run compiz cube and other things. I want to run windows in a virtual box and anything else I need to work, surf the net and watch and convert video. 
I want to build a system that is made to run mint, with windows 10, or 8.1 or 7 professional in a virtual box while I use mint with all the features in the background. I used to think my system was slow due to internet connection or old processor. I know have a new laptop with i3 processor and it is like windows 98. I am sick of a slow system. When I click something I want it to open. Oh and I know an i3 is not top of the line, but I would have thought it should be faster than my old one was with mint, it is slower!!!

My new system should open and run all my applications seamlessly with no lag. I would like some suggestions on what I should go with for a processor, motherboard and memory. I would like to even have 3 display screens running if possible. This way windows open in one, and my other windows in the other 2. I was thinking of the intel 5930K processor and building around this? Is there a better option, do I need more processing power, or is this over kill? I don’t game, I just surf the web, email, and some of the websites I use for work have wiring diagrams that take forever to load. I also like to play with new operating systems and do not like to take a long time to install or boot. I do not like the lag time. I want instant and am willing to pay for it. I would rather overbuild my system than deal with windows 98 and dial up type speeds! Saving files, pictures and videos should also be fast as possible. So should copying dvd’s. I do use a computer pretty hard. I want to be able to do all of these things at once while I surf the web, check email and pay my bills online (I can multi task, my computer should too).

I know the 5930K will require ddr4 memory and certain motherboards. My question is which mother board is right and is this processor enough. I even saw the 5820K at less price, but see that is has less pcie lanes and I want to use a wireless card and add on other cards so think the 5930 will ensure that I have enough power.

I would like a mother board and graphics that play well with mint. I have been using nvidia and it takes some work, to get things to play nice together. I can deal with that if I have to, but if it could be plug and play that would be nice. The plug and play is why I like linux in the first place. My printer and other things just work (mostly).

---

### Post by TheFu on 2015-08-22
Before you go crazy - do you have SSD?  I didn't look up any of those models - would help me if you said the family. The Core i5 'k' versions have something that makes them slower than the non-K versions. It has been a few years since I looked that up.

Also - it would be helpful BEFORE you go crazy to do some system monitoring, which will show where the slowdown is.  Run something like **munin** for a month to get your normal workload captured.  Doing anything before doing that is 100% guessing. I'd rather KNOW the answer than guess at it.

Also, wifi sucks. Don't use it. Always go wired ethernet if you care about performance. There is NO comparison between **any** wifi and a gige wired connection.  Saying you want downloads to be instantaneous isn't anything we can control. Get a 2G connection from your ISP.  Here, that runs ... about $1000 setup plus $350/month, if it is even available in that location.  You'll need a different router ($$$) and a 10G card in the system ($$$$) which is NOT compatible with ethernet and there isn't any wifi that comes even close to those speeds.  For a good home broadband connection in the USA - 50/8Mbps, most WiFi-N devices should be able to saturate that connection, assuming there aren't **any** other wifi devices connected. More devices on wifi makes the total wifi network slower.  Go with wired, be happier.

Transcoding video will always take time. If you use process management to batch those tasks and run them at a  lower priority, you can make it so they don't impact other work. TaskSpooler with ffmpeg or handbrakeCLI can do this.  For transcoding or any high-CPU use task, it is best to not do that inside a VM. VMs are about sharing resources. Sadly, the intel transcoding extensions which access the GPU power wheren't available under Linux last time I checked. OTOH, under Windows, they only seemed to provide about a 13% improvement in time over the CPU alone. Honestly, I'd build a separate box for transcoding and downloading instead of using a desktop for that. Or if you can wait for transcodes to happen overnight, then you can live with 1 machine.

You talk about diagrams.  I worked in electronic publishing of extremely technical documents. We found PDF to be too slow for our needs and wrote a custom solution for 12 platforms. Plus, at the time PDF didn't have search capabilities, which we taught Adobe how to do.  Your NASA dollars at work - technology transfer.

For the workload you describe any current-gen core i3 should be fine (assuming you batch transcoding overnight).  But if you just want to blow money send me $5k and we can work something out - tax/VAT + shipping extra.  ;)

---

### Post by oldfred on 2015-08-22
At $579 just for cpu, you will do better with TheFu's offer of just sending him $5 grand and using smoke signals.
If money is unlimited then that is fine, but then you are looking at a very expensive system that may be good for gaming or some requirement needing very powerful systems.

My old Intel core2-duo system from 2006 & 2009 improved dramically in boot and software loading time with an inexpensive SSD back in 2011. I was then going to build new system, but put it off as it was working so well.

I just build new UEFI system last fall. I do have 120GB SSD, 1TB HD and Intel Core i5. I was just going to use Intel internal video as I do not game and that is about equal to the old nVidia 9600GT I had in old system. But did end up with a nVidia 620GT, just to have correct ports.

But I also got a Dell for my TV. It only has a Haswell i3 and decent 1TB HDD and seemed a lot faster than my old system and not all that much slower than Desktop.

Many laptops have slower 5400RPM drives that slow entire system. And 4 to 8GB of RAM is all you really need.

I find the slowest part of system seems to be the part between the chair & the keyboard and that seems to be getting slower.  :(

Update just saw this comparison new skylake i5, haswell i7 and broadwell i7:
[http://www.phoronix.com/scan.php?page=article&item=intel-6600k-linux&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-6600k-linux&num=1)

---

### Post by jcm1107 on 2015-08-23
I didn’t say that I had an unlimited budget. I would like to keep it within reason. I just feel that the I7 processor I mentioned seems like it would be a bit overkill and handle all the tasks I usually do. I feel it would be better to overbuild the system than to wish I would have sprung for better components. I feel that my internet connection is fast enough. It is 19mbs on a speed test. I could get 75mbps for around $50 a month but do not feel I need that much speed. I used to only have 1-2mbps but recently moved.

I could also connect with a Ethernet cable but the wireless N card and antenna I have is very good and I would have to buy a long cable, might as well use the wireless. I don’t feel it is the cause of web surfing being slow. I know it is the computer. I have always had 4 gig of memory and never used near all of this. My processor and running too many things at once has always been what slows my system. I just want to build a new system that can handle the things I normally do.
 The laptop with the i3 seems to be maybe the same as the dell you mention. My laptop is also a dell with a 1T hard drive. I just think all the applications on windows slow the system down. It was mentioned that a second system can be built to run other processes on. I would think this would be more expensive than just building one good system. I bought the laptop because it was cheaper than the components to fix my broken desktop. I just realize I do not like the keyboard on the laptop, I use a regular keyboard and mouse and find it awkward to be using the laptop as my regular computer in this fashion. I have since been budgeting for a new build and feel I can build a decent system and just wanted opinions on If the processors I mentioned would suffice. It seems the consensus is that it is overkill and a waste of money. I also thought that it was overkill but as mentioned I would rather go this route than to under build the system. I find that the system will last a good 5 years or more if I do this.

I usually build a system when a component fails and the memory, motherboard, or processor is out of date and new components are not easily available. My motherboard died and it is time for a new build.

I don’t really like windows, this is the reason I want to run it in a virtualbox. I know this shares the system resources and this is the reason I would like to go with a good processor. I need to use windows on occasion. The wiring diagrams I mentioned are accessed on the internet and require internet explorer and a plugin to open. I have tried wine and other options to open them in linux and nothing works, if I can get it to it is very buggy and crashes. The virtual box is the best option for me, as I like all the features of mint and the easy access to windows when I need it.

I had an nvidia 630i motherboard with an old 775 processor and 4 gig of memory the processor would be maxed out when the system was running slow. The built in nvidia card would often cause issues when installing mint or ubuntu. Some versions were easier than others but this is another reason I was asking about the hardware. I just wanted to know if certain hardware is known to work nicely with linux. The bios settings on that board and the graphics card made installing a new OS a pain sometimes.

---

### Post by TheFu on 2015-08-23
(2) $450 systems are cheaper than (1) $1800 super-PC.  Plus you get redundancy, IO balancing and can put non-immediate tasks into a batch queue to run in order on the other box --- all this just because it is a different machine.

Ever heard "the network IS the computer?"  That's how things work here. Right now, I'm running tasks on 5 different systems. The Linux desktop GUI I'm typing into is actually running inside a VM on a different Linux machine.  If you batch things up and always use a queue for tasks on a machine, it is easy to have things done overnight while not impacting the speed of a desktop.

If you want exact answers, *please provide the requested monitoring*.  Nobody here uses that IE webapp. We don't know how heavy it is. We probably don't do other things that you do either. Anyone who says "I want everything to happen instantly and I'm willing to pay for it" ... gets a less than optimal system.

I'll explain using an absurd, but true example:
I used to work as a systems architect. A huge, new, project started on a Monday. We were just starting to gather requirements a few days later as teams were formed and an S-VP for this large company told us on the following Wednesday to buy all the hardware we would need for the project for the next 5 yrs **immediately**.  Myself and 5 peers (each with over 20 yrs experience) got into a room and started guessing. We didn't have time to gather requirements, clearly. The next day we presented a budget estimate for about $500M in servers, networking, storage, and infrastructure to manage, monitor, backup, test and have disaster recovery for all of it.  The S-VP freaked - wanted to know what we were thinking, so we explained that gathering requirements would take time. He agreed to wait for orders until we were ready. Over the next few months, we did that and orders for about $300M in HW happened.  My little part was only about $35M, but that included equipment for  outsourced developers from overseas (hosted in the USA on new equipment due to SW licensing restrictions) and all their dedicated remote access lines.

The point?  Weak requirements mean any guesses will be off by 40-200%.  Sometimes that is just fine - "I'm willing to pay for it" set that expectation to me. I figured you were a stock trader-type-A person and for some people $10K for a fast PC is nothing.  That doesn't apply to me. My last build was $180, because it was exactly what was needed - no more. ;)

Get an SSD. Seriously.  Do that first.

Lastly, you don't need to use the laptop keyboard, screen or touchpad. There are USB ports on it which will connect to a mouse and keyboard and there is at least 1 video output to connect to a huge monitor.  My Core i5 laptop is used daily with dual monitors, a great, mechanical keyboard and nice-enough mouse.  It is basically a remote access machine into more powerful systems.

**The network IS the computer.** [https://www.youtube.com/watch?v=kWNtaUaDxZw](https://www.youtube.com/watch?v=kWNtaUaDxZw)

Update:
You probably already know this, but some of the newest DDR4 motherboards only have drivers that can be loaded with Windows. This is always a risk with brand new tech and being on the bleeding edge with Linux. I like to wait at least a year before using any new major tech leap forward. For my budget and to lower power use, the Core i5 6600K is very interesting - it appears to be about 40% slower than your options for some tasks like transcoding, but competes well for the types of things I do.  Maybe next summer, the Linux kernel will have good drivers for the most popular MBs?  I dunno.  Most of my current workloads are I/O bound, not CPU.

Some MB reviews for Skylake CPUs:
[http://www.tomshardware.com/reviews/intel-z170-lga-1151-skylake-motherboard,4254.html](http://www.tomshardware.com/reviews/intel-z170-lga-1151-skylake-motherboard,4254.html)

---

### Post by tea for one on 2015-08-23
> **oldfred said:**
> 
I find the slowest part of system seems to be the part between the chair & the keyboard and that seems to be getting slower.  :(




I wish that I had written this.....................;)

---

### Post by Yellow Pasque on 2015-08-23
> 5930K
I wouldn't bother with LGA2011 socket chips now that Skylake CPU's are out. If you're trying to future proof, a Z170 mobo will have more current features.

> **TheFu said:**
> The Core i5 'k' versions have something that makes them slower than the non-K versions. It has been a few years since I looked that up.
I think you're referring to lack of VT-d (speeds up virtualization). Thankfully, Intel has ended that artificial product segmentation with the latest 'k' CPU's (Skylake).

---

