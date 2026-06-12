---
title: "Swap On SSD; Is It As Fast As More RAM?"
date: 2013-12-12
forum: Hardware
---

### Post by Smallwheels on 2013-12-12
I want to buy a new computer that has an SSD with 4 GB RAM. Unfortunately that model is always sold out. There is a different model sold that is almost the same. The only difference is that it comes with 2 GB RAM not 4. These RAM chips are soldered on to the board so they can't be upgraded. The one with less RAM costs $50 less. The swap is enabled on this model (so I've read) so is having a swap partition on an SSD just as fast as having more RAM? I have no experience with this but it would seem to be an extra step which would cause some slowness. Can anybody give me some advice about the real difference between the performance of a 2GB RAM machine using some of the swap partition on an SSD and a 4GB RAM machine?

Thank you.

---

### Post by MartyBuntu on 2013-12-12
It depends on what you're using (applications) and if they benefit from faster disk write speeds or from being able to load bigger projects in RAM.

---

### Post by 1clue on 2013-12-12
Not as fast.  Don't do it.

First thing, the computer should have more RAM than you need, not less.  If it's not that way when you buy it, then it will never be adequate.

Second thing, while the code for the swap mechanism is fast, it's still much more complicated than just a RAM hit.

Third thing, it goes through your hard disk drive interface when it swaps, so it doesn't matter how fast your disk is, it's still a lot slower.

Fourth thing, an SSD is limited on the number of writes before the surface fails.  In normal use it's unlikely you'll hit that, but if you start out with a machine that you KNOW you'll swap on a regular basis, you're just asking for it.

---

### Post by 1clue on 2013-12-12
Note to moderate what I just posted:

I use SSDs.  They're a huge performance gain over a spinner, much more than I thought.  But your computer should really never hit swap except in extreme conditions.  I went for several years before my main Linux box hit swap.  I use the "hit swap" event to mean I need to start shopping for more RAM.

Think of swap as the air bag in your car.  You never want to use it, it produces a moderate disaster (BIG performance hit) to prevent a major disaster (a crash).  It baffles me that people plan on using swap regularly because they use more RAM than they have.

That said, I also use swap for tmpfs and similar tricks in places where temporary files are written rapidly and frequently, it really speeds up compiling and such.  The code for the swap mechanism is fast and very good at determining what gets swapped out if it ever has to.  But again, I never actually let the machine write it out under normal circumstances.  It's a rare event that happens much less than once a month.

RAM in the quantities most people need it is really cheap.  If you're buying computers, make sure it has the ability to use at least 4x as much memory as you plan to use with it.  You can put in what you think of as a reasonable amount, (1/4 capacity for example) but before you know it, you'll want a bunch more.

---

### Post by Smallwheels on 2013-12-13
I have two computers. Both of them have just 2 GB RAM. Both of them are regularly into the swap partitions. The older one is a 2008 Mack Book. The newer one is a 2009 HP with a 2.3 GHz Sempron LE 1300 chip. These are using DDR 1 memory. Neither of them is used for more than doing word processing and web browsing, which includes watching movies. I can't open many tabs or windows without the problem of big slow downs. For the last year and a half the Mack Book spinning wheel is on all the time with the Firefox browser open. The HP running Ubuntu 13.04 is slow often using the Unity desktop. 

The computer I'm talking about is an Acer C720 Chromebook. It has DDR3 memory and the Haswell processor. Both of those features should make web browsing and watching videos hiccup free. Since it has an SSD it will be fast for opening things. I forgot about SSDs having a limited life regarding writing to different locations on the drive. Using one for swap wouldn't be a good thing. Four GB of RAM is the maximum this model has. I want to run Chrome OS for web surfing and such. For work and storing things I want to run Ubuntu from an external HD. I just need to learn how to boot it. I'll have the best of both worlds with that system.

---

### Post by 1clue on 2013-12-13
I personally would strongly recommend you get something that very easily satisfies your current needs without using swap.  What you're doing is making your laptop obsolete for ever your own purposes before you even buy it.

Spend a couple bucks more and get something that handles 8g and has slots for memory.  You can start with 4g and upgrade later.  IMO the ability to have enough RAM to run without swap except on extremely rare occasions is one of the most critical performance decisions you can make.

IMO the box with a spinning disk and more RAM would be roughly as fast as the SSD with less RAM, hitting swap.  You're spending a lot of extra money to buy an SSD for a system that will not only be slowed down for lack of memory, but you'll cause early SSD failure by hitting swap all the time.

Not only that, you'll undoubtedly have less battery life for having to exercise the SSD constantly.

SSDs are a great idea, but so is RAM.  Save up a little longer and get something that actually works for you.  Never pick a system that's maxed out when you buy it or you'll sit there waiting for it every moment you use it.

---

### Post by Smallwheels on 2013-12-17
1clue I agree with you. Your advice is good. My old Mac Book is running an 800Hz bus. Even with more RAM it wouldn't give great performance using the web today. The DDR2 667 MHz performance is also sub par. Since I don't get to play with newer machines I really can't gauge how much RAM would be plenty for my current needs. I can only guess that having a much faster bus and having faster RAM will give me such good performance that 4 GB might be awesome for now. Others have reported that when they have many tabs open on the internet, using the computer I like, and at the same time streaming a Youtube video, they have no slow-down at all. I've been in the habit of closing tabs and windows for a long time so if I continue that habit, video playing should be good without using the swap partition. 

The Haswell architecture should also contribute some to the speed of the machine. Even though the one I like has a 1.4 GHz dual core processor it will be faster than my old 2.4 GHz Core 2 Duo. I've seen a benchmark test with this processor and it does beat the old one. 

I could save for a more expensive machine but that wouldn't really work. I want a small size machine. It seems that the more one spends the larger the machine. The one I like has an 11.6" screen size which is perfect for my needs. It weighs less than three pounds too. I could save for a Mac Book air but I really don't want another Apple product, especially one that costs $999. I would consider buying a Chrome Pixel someday if I really like the Chrome OS, but it would need to have USB 3 and HDMI ports instead of the USB 2 on it now. It would also need to cost a lot less. Maybe in three years or so the smaller screens will be awesome like the Mac Book Air's Retina Display and Google will offer a high performance 11.6" model. I can only hope. 

My question has been answered and I'm marking this thread as solved. Thank you all for your input.

---

### Post by 1clue on 2013-12-17
A modern system might be able to do all that and hit swap a lot, especially on an SSD, and still have no slowdown at all.  The question is, does what you plan to do hit swap?  If it does once in a blue moon then it doesn't really matter.  If it hits swap continually, then you're slowly killing your SSD.  For that matter, you're beating up a spinning disk too but that's off topic and would take longer to fail anyway.

Most normal users I know of don't do anything else that would prematurely make an SSD fail.  If you don't use a database heavily in a read/write mode or compile a bunch of stuff, then you just don't need to worry about an SSD. But if you have 2g and you're continually trying to use 3g then you're in trouble.

Architecture:  If you have specific needs for the computer you're going to get and performance is a huge issue, then go dig into architecture.  Realistically speaking for a typical home or even office user, it doesn't matter that much.  You can try out a few different boxes at your local retailer to see what processor is fast enough for you, and then go order something with that processor family and hardware you know works well with Linux.

Again, for my personal purposes I won't buy a computer that barely fits my needs right now.  I buy something that can handle twice as much RAM, and is twice as fast as I need.  That way I get a cheap upgrade halfway through its lifespan by getting new RAM and maybe a new drive.  By the time that gets slow I'm usually ready for something new again.

---

