---
title: "computer KILLED"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by towsonu2003 on 2006-01-04
:confused: 

problem: my old computer is KILLED. Not sure if (x)ubuntu is to accuse...

How: I started the computer and was using the Sound Juicer on that for about 40 minutes. While I was watching tv, I heard the computer shutting down, for no reason. The shut down sound was its regular sound. Tried to start it but it seems no power is going to it?? The power button is simply not responding at all. 

When I unplug it, wait for 5 seconds, then plug it back, I hear a sound like its accessing something for half of a second (no lights -nothing), but power button is still not responding... 

How to diagnose the problem??? Any clues?????

Computer:
Packard Bell Multimedia 875
300A Mhz Intel Celeron, 64MB RAM, 4GB Hard Disk

---

### Post by Omnios on 2006-01-04
From personal experience auto shutdown could be because it was overheating, Mine did that and I found out that the power supply fan was cooked. This sounds a lot more serios though.

---

### Post by dcast on 2006-01-04
well.. when you plug it in and you hear something thats probably a good sign because that might means your power supply hasn't kicked the bucket. What you probably hear is your drive spinning. Other than that I dont know sorry.

---

### Post by encompass on 2006-01-04
well, start with just trying to get it to go to the post screen... unplug everything and try to turn it on... even take out the keyboards and mouse and try to turn it on...
you also said something about a shutdown sound?  Is it like a sound that it makes when shutting down or is it the pop that soundswhen the system shutsoff suddenly.
I may be your powersupply, from what you tell me...

---

### Post by towsonu2003 on 2006-01-04
[QUOTE=encompass]
you also said something about a shutdown sound?  Is it like a sound that it makes when shutting down[/quote]
it is the sound when it makes during reglar shutdown (for example, after sudo halt)

I will try your suggestions... in the meantime, how do I diagnose it if it is a power supply or a fried fan problem?

---

### Post by towsonu2003 on 2006-01-04
nope, no response from power button whatever I unplug / plug from / to the computer... 

There definitely comes a sound when I unplug, wait 5-10 sc, then plug it back. Cant understand where the sound is coming from though...

---

### Post by towsonu2003 on 2006-01-04
I just took its parts out to observe better. Here is what I see: 

after uplugging, waiting for 10 seconds, then plugging it back: 
* the fan turn a couple of times and stops
* the lights of the computer come up and blink then go off
* it sounds like it is accessing eiher the harddrive or the flopp (empty, also tried uplugging) for half of a second

but does not respond at all when I hit the power button. help needed here...

thanks :confused:

---

### Post by handy on 2006-01-04
If it was a PSU fan failure, your machine would still boot & run for a while atleast, a PSU fan failure usually causes no problems in cool conditions.

Has the fan been noisy lately?  Fans tend to get noisier in the bearings as they get closer to death!

You can see if the fan is spinning, look at the back of the computer (it's a desktop right?).  

If it is not spinning, that is more likely an indication that the PSU has failed.  

PSU's, are not very expensive & are quite easy to replace (with care)  

oh - power supply unit = PSU

The easiest way to test if it is the PSU is to plug another in.  If you are lucky enough to be able to borrow one or steal it from another machine, you will know very quickly.

If your CPU fan failed, it would still boot up to the post screen at least, before resetting, your cpu is not a super hot variety so it would definitely proceed far enough into the boot process for you to see something on the screen.

If you open the case of your computer you will see if the internal fans are spinning.

It is possible for CPU fans especially to look good, but not be spinning as fast as they should.

If you have not noticed your system's fan/s getting louder lately I think it is highly unlikely that you have lost a fan, it is very rare for them to just stop, without audible warning.

Otherwise if you are not seeing anything, no lights on the front of the case, no post beeb, you may have lost something more important, motherboard, cpu (quite rare), ram usually causes beeps but?

Cheers,

handy

---

### Post by codejunkie on 2006-01-04
[QUOTE=towsonu2003]I just took its parts out to observe better. Here is what I see: 

after uplugging, waiting for 10 seconds, then plugging it back: 
* the fan turn a couple of times and stops
* the lights of the computer come up and blink then go off
* it sounds like it is accessing eiher the harddrive or the flopp (empty, also tried uplugging) for half of a second

but does not respond at all when I hit the power button. help needed here...

thanks :confused:[/QUOTE]
if you have another powersupply laying around swap it out. to me that seems to be the problem.

---

### Post by handy on 2006-01-04
You haven't had any stormy weather, or mains power spikes?

They are the most common causes of symptoms like these.

All the best,

handy

---

### Post by handy on 2006-01-04
Yes I think if you are fortunate you will get away with a PSU.

I tend to think that you more likely are in far more serious trouble.

Problems like these are very hard to diagnose, you MUST swap known good for potential bad components.

Disconect all drives from the motherboard, & any cards except your display adapter.  Try to boot up & see if there is a difference.  If no difference then swap PSU, if that works great put it all back together again.

[Edit:]  I did leave graphics adapter out of this, you could try swapping that also before going further.

If it doesn't work, you can swap ram, then CPU, then mainboard.

This stuff happens to us all :rolleyes: 

handy

---

### Post by jazzer on 2006-01-04
Actually, first thing I would try is making sure all your cards that are plugged into you slots are tight.  After that I would try doing as handy said and disconnect everything you don't possibly need if it still doesn't work.  Was the computer moved or at all jostled lately?  

Myself, I wouldn't be surprised that it's your motherboard or cpu, but it's hard to diagnose without actually swapping out parts.

---

### Post by handy on 2006-01-04
You'll certainly end up with the whole course if you wait long enough...;) 

Something else you may or may not know, is that it is not good practice to touch the contact surfaces on any cards.  

That's the shiny metal part that goes in the ISA, PCI, AGP, RAM etc. slots. 

If you ever think contact surface on any sort of card is dirty, (you can't necessarily see this kind of dirt either!) you can clean it with an office rubber, you know the type you rub out pencil with.

You'll be able to start your own technical service with all the info' in this thread! :KS 

Cheers,

handy

---

### Post by towsonu2003 on 2006-01-04
okay, here is the weird thing about this: I unplugged the thing, went to sleep, came back after about 7 hours and plugged it back. the PSU fan spinned 1-2 cycle, the thing accessed something (harddrive? floppy?), and the lights blinked once as they did before. But this time, the power button responded and powered the computer for *half of a second*, but then it went dead again (i.e. computer powered off after that half second and power button not responding) :confused: :confused: Well, at least the power button seems not to be broken?

[QUOTE=handy]Has the fan been noisy lately?  Fans tend to get noisier in the bearings as they get closer to death![/quote] no, there was no unusual noise at all...
[QUOTE=handy]
You can see if the fan is spinning, look at the back of the computer (it's a desktop right?).  [/quote]the fan spins only 1-2 cycles after I unplug then plug the computer in...
[QUOTE=handy]The easiest way to test if it is the PSU is to plug another in.  If you are lucky enough to be able to borrow one or steal it from another machine, you will know very quickly.[/quote]ah, I don't think I will be able to swap any parts... I don't have any around, and the computer is pretty old to buy it new stuff... I wouldn't deal with this any further but the thing is weird (see beginning of this post) :confused: 
[QUOTE=handy]
If your CPU fan failed, it would still boot up to the post screen at least[/quote]hmm, then this is not the CPU fan... there is no screen at all :(
[QUOTE=handy]
If you open the case of your computer you will see if the internal fans are spinning.[/quote] they put those fans to a weird place, I just cannot see any fan inside... It seems I will need to take it apart even further
[quote=handy]You haven't had any stormy weather, or mains power spikes?[/quote] No, the wheather was okay... but now that you say it, I remembered this thing... I was trying to listen to the CD, and the external speakers (very old) went kind of "boom" (+ bad smell from speakers) and died on me about 35 minutes before the computer died. The speakers were connected to where you usually connect external speakers in a desktop computer... I did not connect this to my problem because of the long time between speakers going byebye and the computer dying... 
[quote=handy]Problems like these are very hard to diagnose, you MUST swap known good for potential bad components. Disconect all drives from the motherboard, & any cards except your display adapter.[/quote] I can't do the first one, but I will do the second one (strip it, especially the sound card, if I can manage to do so) and let you know what happened / I observed... 
[quote=jazzer]Was the computer moved or at all jostled lately?[/quote]Not really. I always move it back and forth 1-2 cm (to plug in a flash drive for example) but everything seems to be tight...

PS. I really appreciate the help :)

---

### Post by handy on 2006-01-04
Don't like the sound of that speaker routine.

Did they have an AC adapter, you know the little (usually black box) that steps down from mains voltage to 12volts or there abouts?

Or, did they plug straight into the powerpoint in the wall, or powerboard?

A 2nd hand working ATX, (which is most likely the type you need) PSU should cost next to nothing, $10 Aus' is reasonable.

I would be surprised if the PSU is the culprit though.  They can carry on as exotically as your machine, but in my experience that is very unusual behaviour for a faulty PSU.

95 out of 100, just stop!  Usually from a power surge in my part of the world.

I'm off to bed, 2am again...  :rolleyes: 

Let us know how you go, I guess your about run out of places to go?

Regards,

handy

---

### Post by towsonu2003 on 2006-01-04
[QUOTE=handy]Don't like the sound of that speaker routine.
Did they have an AC adapter, you know the little (usually black box) that steps down from mains voltage to 12volts or there abouts?
Or, did they plug straight into the powerpoint in the wall, or powerboard?
[/QUOTE]
I'm still at work so didn't have time to try out anything. just wanted to answer this one... 
The speaker has an AC adapter. Or may be I should say it used to have an AC adapter but I believe it is pretty much burnt now (I meant smell of burning plastic as the bad smell)...

PS. have a nice sleep :)

---

### Post by lgmdaniel on 2006-01-04
Looks like its a pull out everything and start from scratch seeing if you have any faulty hardware. You may also want to check that things like your Video card and memory are not loose. Normaly if your PC has no memory or video it bleeps at you but a loose card may do something else. Also the CPU or Main-board may have given up the ghost, though its probably the main-board due to the lack of system response.
Another one I've seen before is a screw fallen under the Main-board that caused a system short wouldn't boot up, well untill I removed it.

---

### Post by ekarni on 2006-01-04
[QUOTE=towsonu2003]okay, here is the weird thing about this: I unplugged the thing, went to sleep, came back after about 7 hours and plugged it back. the PSU fan spinned 1-2 cycle, the thing accessed something (harddrive? floppy?), and the lights blinked once as they did before. But this time, the power button responded and powered the computer for *half of a second*, but then it went dead again (i.e. computer powered off after that half second and power button not responding) :confused: :confused: Well, at least the power button seems not to be broken?
[/QUOTE]

My $0.02:  I think you had a powerspike that took out your speaker adapters and damaged your computer PSU.  Was the PSU plugged into a surge strip, or straight into the wall?  My hunch is that there's now a bad capacitor somewhere in the power supply.  I've heard of ones going bad, then partially "healing" if left alone for a while.

Solution:  get a new powersupply.  They've been standardized for many years now, so finding a compatible one shouldn't be too hard, and they're pretty cheap.  Pull the old one, look up the specs (often a sticker on the side), and replace it.  It will take a few hours to unplug *everything* and likely require unscrewing some stuff, but it's monkey work -- much simpler than software!

---

### Post by towsonu2003 on 2006-01-04
ok thanks so much everyone for the help... I took the thing, strip all of its parts, and tried powering from stripped down motherboard + psu + hard drive. I was not able to get the on board sound car out ;)

anyways, it did not work. the computer is too old and even if I buy a $5 psu (avail?) I will not stay around here too long to enjoy the thing. 

So, the computer died and I do not know whether ubuntu killed it during a CD rip / encode with Sound Juicer or there was a power thingy... Now I have a couple of computer parts laying around. I will leave the computer alone for a while as [quote=ekarni]I've heard of ones going bad, then partially "healing" if left alone for a while.[/quote] and try again. 

if that does not help, I will be be updating this post and giving away the parts for free to anyone living near Towson University, Baltimore, MD. 

Wish good luck ;)

Thanks.

---

### Post by handy on 2006-01-04
As powerful as we all know Ubuntu is, it is not possible for it to have done this to your hardware...

Happy computing...  :rolleyes: 

handy

---

### Post by oceanhippie on 2006-01-21
I don't think it is the PSU, I've seem simlar symptoms to the above on old PC's (all of mine are "old").

The way Mboards work (atx ones) is they get powered by the PSU, even when off. But won't power on fully if they have a problem. Sometimes if its been unplugged for a while - say in a skip;)  then when you re-apply power it takes a while for the board to realise its of, and you get half a tern of hte PSU fan etc. However if the'res somthing wrong it won't wake up cos it knows soemhting is wrong.

Its worht pulling oth everthing or wobbling it and putting it back. Minimum first 1 stick ram PSU and Graphics.

Tom

---

