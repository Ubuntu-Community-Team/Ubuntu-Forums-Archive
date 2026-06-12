---
title: "Upgrading CPU on Dell Optiplex"
date: 2009-06-23
forum: Hardware
---

### Post by chessnerd on 2009-06-23
Alright, after many improvements I'm ready to finish upgrading a boat anchor computer that I got from my dad that he got from work for only $50 a few years ago. The computer in question is a Dell Optiplex GX240. During this upgrading process I've added more RAM, a sound card, a second hard drive, and a DVD drive along with installing Ubuntu and fixing the Windows 2000 installation that it came with. Now, I want to put in a new processor (I'm thinking a P4, 2.6 GHz, 533 MHz FSB) but I have a couple of concerns/problems with this process. Help with any of these three things would be greatly appreciated:

1. I don't think that it would be an issue, but I want to make sure that upgrading a CPU isn't going to cause any kind of software issues. I'm not really worried about Ubuntu, but I've heard of stories where a person's Windows computer stopped working after an upgrade for various reasons, the main one being a Windows anti-piracy feature that makes it stop working if it thinks that it has been put on a totally new computer. Is that feature present in Windows 2000 and would just upping the CPU cause that to happen? (I might also get more RAM while I'm at it. Would the two being done together cause it if I upgraded both at once?)

2. I want to make sure that the motherboard can handle a 533 MHz processor (the current one is only 400 MHz). Are there any free programs (online or otherwise) that could test this or is there a site that I can input the mobo type in that would give me its specs. (Also, which number on it would be the product code? There are about half a dozen stickers and numbers on the thing.)

3. This is the main problem: I don't know how to get the dang heat sink off of the CPU. The Dell site ([http://support.dell.com/support/edocs/systems/opgx240/en/ug/upgrades.htm#1107422](http://support.dell.com/support/edocs/systems/opgx240/en/ug/upgrades.htm#1107422)) is pretty much useless when it comes to telling me how to remove it, but has a basic diagram that someone might be able to decode. Does anyone know how to get the heat sink off without harming the motherboard? I've looked on Google, but the only things that seem to relate to my issue are two posts on Experts Exchange, which you need a membership for.

Thanks in advance for the help.

---

### Post by abn91c on 2009-06-23
I believe you have to push the tabs down  to release one side first then swing up and out to release the other side

---

### Post by chessnerd on 2009-06-23
I don't really understand. What are you saying I need to push down? Here, use the table from the diagram to tell me what you mean:

1 latches (2)
2 securing clips (2)
3 heat sink
4 retention base
5 ZIF socket
6 tabs (3)

I'm guessing you meant the latches but pushing down on them after they are down doesn't do anything but bend the latch.

This is the image that shows the diagram:
[http://support.dell.com/support/edocs/systems/opgx240/en/ug/upgrad97.jpg](http://support.dell.com/support/edocs/systems/opgx240/en/ug/upgrad97.jpg)

---

### Post by IcarusR on 2009-06-23
Pushing down on the latches (1) should release the securing clips (2) from lugs (on the retention base) that the ends go over. 
You may need to GENTLY pry them off with something non metal.
Then the heat sink should lift off, it may have heat transfer paste on it which may also be sticking it to the top of the CPU.

If you are not sure, or happy doing this yourself it is probably better to pay an engineer to do it. Then if it goes pete tong its his fault.

---

### Post by boof1988 on 2009-06-23
> **chessnerd said:**
> I don't really understand. What are you saying I need to push down? Here, use the table from the diagram to tell me what you mean:

1 latches (2)
2 securing clips (2)
3 heat sink
4 retention base
5 ZIF socket
6 tabs (3)

I'm guessing you meant the latches but pushing down on them after they are down doesn't do anything but bend the latch.

This is the image that shows the diagram:
[http://support.dell.com/support/edocs/systems/opgx240/en/ug/upgrad97.jpg](http://support.dell.com/support/edocs/systems/opgx240/en/ug/upgrad97.jpg)

Not trying to be rude or interupt. :)

From my experience, this may be the same as your set-up, but maybe not?  Also... maybe someone can weigh-in and tell whether both latches should be pressed at the same time or if they should be removed one at a time as described below.

[LIST=1]
[*]Push down on one of the latches (1)
[*]The securing clip (2) the the latch (1) is directly connected to will deform slightly.
[*]The slight deformation of the securing clip (2) will allow the end of the securing clip (2) that connects to the tab (3) to release the tab (3) on which the securing clip (2) is attached.
[*]One securing clip (2) should now be (relatively) easily removed.
[*]Perform similar operation for the other securing clip (2)
[/LIST]

Hope this helps a bit.

---

### Post by chessnerd on 2009-06-23
Thank you. I was able to remove the clips after several attempts. It just required a lot more force than I would have thought (similar to when I first removed the RAM, I thought I was going to break it when I put it back in, but it was fine).

Now that I can get in are their any precautions I will need to take when it comes to removing the processor other than the ones described on the Dell page?

Also, I'm still looking for a site that can tell me what kind of processor my motherboard can support. Anyone know of a site that can do this?

---

### Post by rob2uk on 2009-06-23
Before you go ahead and try to fit another CPU, it's worth bearing in mind that a lot of the older Dell desktops are pretty crippled when it comes to CPU upgrades - it can be a bitch finding a processor that'll actually work with a particular board.

Take the Dell PC I'm forced to use in my office, for example - P4, 2.4GHz CPU.

Try to put a P4 2.6GHz from the exact same product family in, and it refuses to POST

---

### Post by chessnerd on 2009-06-23
> **rob2uk said:**
> Before you go ahead and try to fit another CPU, it's worth bearing in mind that a lot of the older Dell desktops are pretty crippled when it comes to CPU upgrades - it can be a bitch finding a processor that'll actually work with a particular board.

Take the Dell PC I'm forced to use in my office, for example - P4, 2.4GHz CPU.

Try to put a P4 2.6GHz from the exact same product family in, and it refuses to POST

Duly noted. 

I definitely understand the compatibility issues with Dell when it comes to non-factory parts. For instance, I put a new fan in the thing and now it gets an error message every time I boot up saying that there is a fan error even though the new fan works better than the old one (and is much quieter).

I guess I should consider a back-up plan, then. My mother has another computer with only a 2.0 GHz P4 processor that is still in regular use. It's a Gateway E-2000 running XP. Do you think it would be possible for me to get a faster CPU that would fit within the overlap of their specs so that if it didn't work on the Dell I could put it in the Gateway instead or would I likely run into the same issues?

---

### Post by tgalati4 on 2009-06-23
Keep the current processor.  Clean off the old heat sink paste and put on some new, higher performing heat-sink paste.  See if you can overclock the ram timings.  You can get ~10% performance increase.  Verify with memtest86+.bin.  Clean the fan, oil it by removing the sticker.  Dust out with compressed air.  Reseat the RAM.

Keep a look out for a Pentium D (dual core) machine.  You will get more performance out of tweaking a dual-core machine than a single core Pentium 4.

Your current setup will run fine.  I think the P4 will support 64-bit.  It uses more RAM, but can be 8-10% faster for desktop tasks and 40% faster for mp3 and video encoding.

Put in a Western Digital Raptor disk drive for the boot disk.  You will immediately notice the performance increase.

---

### Post by chessnerd on 2009-06-23
> **tgalati4 said:**
> Keep the current processor.  Clean off the old heat sink paste and put on some new, higher performing heat-sink paste.  See if you can overclock the ram timings.  You can get ~10% performance increase.  Verify with memtest86+.bin.  

I could overclock but I would like to use this upgrade more as a learning experience and I've got some money burning a hole in my pocket. I'm not planning on building a supercomputer out of this hardware (the motherboard only supports 1 GB of RAM from my understanding so I can't do too much with it). For now I'm just trying to learn about the process so that when I do build my own computer I'll know what I'm doing.

> **tgalati4 said:**
> Clean the fan, oil it by removing the sticker.

It has a brand new Antec Tri-cool fan that I got a little over a month ago. There's no dust and it's running great.

> **tgalati4 said:**
> Dust out with compressed air.

Already been done.

> **tgalati4 said:**
> Reseat the RAM.

You mean take the RAM sticks out, dust them off, and make sure they are in their slots firmly? If that's what you're getting at I've done that as well.

> **tgalati4 said:**
> Keep a look out for a Pentium D (dual core) machine.  You will get more performance out of tweaking a dual-core machine than a single core Pentium 4. 

You mean buy a new computer with a Pentium D? This isn't my main computer (I have a laptop with a dual-core processor that I use as my main computer) this is a secondary computer. I could look into getting a Pentium D for this one, but how would I check to see if a Pentium D is compatible with my motherboard? I've looked around online and I can't find a single site or program that will tell you if a certain processor is compatible with a certain motherboard. I know what type I have now (apparently Dell uses it's own kind of motherboard that is specific to each computer model) but I can't find a way to discover what kind of processor it can support.

> **tgalati4 said:**
> Your current setup will run fine.  I think the P4 will support 64-bit.  It uses more RAM, but can be 8-10% faster for desktop tasks and 40% faster for mp3 and video encoding. 

My current setup is working but I frequently max out the CPU in Ubuntu when doing things like YouTube and it can't play games very well.

> **tgalati4 said:**
> Put in a Western Digital Raptor disk drive for the boot disk.  You will immediately notice the performance increase.

As mentioned above this is more like a practice computer for when I build my own computer either later this year or next summer. I might buy a better hard drive for more space, but I don't think I need to buy something that powerful. However, I'll definitely look into Raptor drives for when I do build a high performance computer later on.

---

### Post by tgalati4 on 2009-06-26
The multitasking nature of linux means that processes will get interrupted and rescheduled.  This can result in choppy video and game play.  A dual-core motherboard will practically eliminate this problem.  The Pentium D is the oldest dual-core that I know of.  It comes in several form factors so you will have to research what is electrically and physically compatible with your motherboard.

If the motherboard can only take 1 GB, it may have other shortcuts as well.  Optiplex machines tend to be better built than consumer Dell machines, but they are not high on the performance curve.  Do some research on the motherboard chipset and you will find the bottlenecks that prevent smooth video playback.  Not much can be done if the IO chipset is an older generation with legacy support and slow performance.

---

