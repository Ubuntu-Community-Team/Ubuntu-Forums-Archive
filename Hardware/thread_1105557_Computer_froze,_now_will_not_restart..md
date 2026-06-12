---
title: "Computer froze, now will not restart."
date: 2009-03-24
forum: Hardware
---

### Post by Motorhead Kaze on 2009-03-24
Before I take my PC into a shop and give up the $ (actually YEN for me) that I don't have, I thought I would check and see if any of you had some clues for me. Let me know if I can provide any more info. Photos of my screen will be uploaded.

I am posting from another computer because the desktop I am referring to will not run. 

I was in the middle of typing an email, and everything froze. No keyboard or mouse control."ctrl+alt+delete" did not even work. After a couple minutes of hoping control would return, the only choice was shut off the power and try restarting the hard way. When I restarted the computer, it would not go past the initial brand-name screen which I normally see only for a brief moment at startup (attached here, named screen1.jpg). Aside from the PC hanging up here, the image was all pixelated/garbled as you can see.

5min. and nothing, so I shut the thing off and came back a couple hours later. I tried several times to turn on the computer, hoping maybe that I could get in through the Windows partition. Once or twice I got to the screen where I choose Ubuntu or Windows, but the keyboard was locked up, and the words on the screen were garbled/pixelated. I only knew what the words said from memory, the text was unreadable and the computer's movement stopped here. After I retried this a couple times, once the computer threw up a black screen with a garbled looking BIOS type message that I assume says something like "This thing is busted, get a new computer and reboot." 

With the CD, I had a bit of movement. Normally, when you boot Ubuntu off the CD, you will have an orange bar moving back and forth as it starts up...not THREE as you can see here in my second attachment (screen2.jpg). Here all I got was the Ubuntu logo, 3 bars with weird pixelated streaking. But after a few minutes, even this froze up and the bars stopped moving.

Tried again the next day, but no luck. The hard drive does appear to be moving, and is only 1 year old. I wonder if there is anything here that makes you say "OH, it's the ferginplaster switch!" or if my only shot is the shop? 

The extent of my hardware experience is installing a graphics card (last year) and a new hard drive (also last year).

Hints? Clues? Thanks for reading!

---

### Post by sailthesea on 2009-03-24
Ok that looks like a hardware problem to me 
Try unplugging everything from your computer apart from monitor and keyboard (try a psp one if you have one) and reboot if it works then start to reattach everything till you find the offender 
 Good luck!

---

### Post by Motorhead Kaze on 2009-03-25
Yes, I had tried starting without anything but the monitors and keyboard, but there is no change. In fact, now I don't get anything at all.  
I don't own a PSP.

It is clearly some sort of internal hardware problem.

---

### Post by sailthesea on 2009-03-25
It does look that way I'm afraid, the only real way to tell would be to open it up and test which I can't really do from this hemisphere. try reposting though someone may have a better idea
 Good Luck!

---

### Post by KCG102282 on 2009-03-25
The first thing I would look at is test your hard drive because it sounds like a hard drive failure to me.

---

### Post by lindsay7 on 2009-03-25
It could also be the graphics card. You said that you replaced it in the past. Does you motherboard have onboard graphics?  You could try taking out the graphics card and see it you can get the computer to start on the onboard graphics if it does.  Do you still have the old graphics card? If it still works you could try that.

---

### Post by Motorhead Kaze on 2009-03-26
Hello there! I am back and have done a whole lot more checking now, learned a lot personally, but have had very much more luck in bringing the PC back to life. This will be a long explanation, hope you don't fall asleep.

Going in order,

1. my computer froze while I was composing an email.
2. I was forced to shut off the PC (because even ctrl+alt+del did nothing) and could not get back in. At this point, the computer would stop at the "Biostar" logo, and the image was garbled.
3. after several tries my PC finally got to the point where it let me choose which OS to load up, but the keyboard would not respond to let me choose, plus the screen was all garbled. Normally, Ubuntu would load up after 10sec. but instead a black screen with an unreadable DOS type message came up.
4. after more tries with no computer response, I tried to run Ubuntu off the live CD with no luck. Garbled screen, orange motion bar thingy froze after 1 min. (On top of that, there were 3 orange startup bars.)
5. removed all external hardware except keyboard, and nothing at all would come up, not even a garbled screen. I did get in to BIOS, but could not read a thing because the screen was garbled.

TODAY
6. finally, talking with a friend, I unplugged the video card I had installed, and tried to restart the computer on the stock vid card that is attached to the motherboard. Holding F12 brought me to a BIOS screen that was partially off the screen. There a message either reads "CMOS checksum error - Defaults loaded" OR MAYBE "BIOS checksum error - Defaults loaded" But because part of the message was off screen, all I could read was "...OS checksum error". Pressing DEL when starting got me into BIOS, and it was actually readable. I selected "Load Optimized Defaults" then "Save and Exit Setup". BIOS turns off (goes away) computer does nothing -- does not restart or shut down, but screen is black.

7. Unplugged hard drive, floppy, and CD drive. All that is plugged in was the keyboard and monitor (running on the stock vid card). Many times I tried to start the PC and get into BIOS with no luck and with no beep, just the fan coming on. 1 time out of nearly a dozen tries, I got into BIOS, and it looked fine. Just like regular old BIOS, but took forever to get there.

8. With PC unplugged, I removed nickel-sized lithium battery, let set for a few minutes to set BIOS to default, put it back, nothing changes.

9. Removed RAM and for a couple starts, the computer does nothing. No errors, no beeps. Finally, after a few tries, computer gives long warning beeps as it is supposed to do without RAM installed.

With no drives plugged in, and the computer beep that accompanies startup only coming on once every dozen tries or so, and only being able to get into BIOS every once in awhile it seems that something on the motherboard is causing it to be confused about just how to deal with BIOS. Of all the times I have left things unplugged and did NOT hold down DEL, the computer did not produce any error message on the screen about a problem, or something missing, etc. Unless I push and hold DEL absolutely nothing happens now, not even the Biostar screen comes up.

It also seems in all this, my switch may have broken? When I shut off the computer, and turn it back on, the computer powers up automatically now without me switching it on with the front power switch. But even if all this messing around broke the switch, my problems started far before the switch started acting weird.

Finally, my choices are to replace the small battery and see if that helps anything. Or to assume that something in the mother board are broken. It is possible the CPU is having difficulty, but there is no way for me to check that.

A new mother board for this computer may only cost $100 (10,000yen actually), but without knowing if it is actually broken, that is kind of an expensive gamble, and one that will cost me a lot of time in unplugging the old one and replugging in a new one. If I do get a new motherboard, I have to get one that will fit my CPU and my RAM as well. I hear that used computers are at around $200 now, just not sure that used is a very good route to go.

I did find out today that I am using
an AMD Athalon 64 Processor, and the motherboard is a GeForce 6100-M7 (mirco ATX)Ver 1.1

CPU Socket size 754

This computer was running really great until all of a sudden...

I have had it for 2.5 years or so.

Have I exhausted all the options now? Or did I miss something? Seems my drives are all fine and the graphics card too.

---

### Post by lindsay7 on 2009-03-26
You have done everything that I would have tried.  I just went through a similar situation, but I did not have the display problems. I had the no start, could not get into bios, and power up and stay on, problems, by the way it was a Biostar mother board too, I changed out the battery and did all the things that you did and still no luck. I ended up buying a new mother board and put all the componets back in, ram, vid card, cpu, dvd, and hard drive. The new setup runs fine now. At the time that I did this I was running Vista only and I was supprised that Vista accecped the new motherboard with only a few driver adjusttments.  I added a Ubuntu 8.10 dual boot to this system when I got it fixed.

---

### Post by kpatz on 2009-03-26
It could be faulty RAM.  Try booting an Ubuntu live CD and running the Memtest86 that comes on it, or download a Memtest86 ISO, burn it to CD, and boot that, and see if you get any errors.

Try removing/reseating the DIMMs on the motherboard.  If there's more than one, try switching them around or remove one and see if it boots then.

---

### Post by Dngrsone on 2009-03-26
Sorry, guy... this looks like a motherboard problem to me.  NOw it is possible that kpatz is right and RAM is faulty, but RAM, as a general rule, doesn't corrupt the BIOS.

Obviously the power supply (PSU) is working, and you are having troubles before you even get to Power-On Self-Test (POST), so the Hard drive is unlikely.

Time to shop for a new board, maybe upgrade your system.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/nod.gif[/IMG]

---

### Post by Motorhead Kaze on 2009-03-27
Thanks guys. I just thought it was worth asking. Commiseration is always good too, thanks lindsay7.

kpatz: Yes, I removed the RAM, put the one from the #2 spot into the #1 spot, etc., switched them around...tried these different combinations and got no change. But thank you for mentioning this!

And yeah, I could not boot off the CD at all.

One last question. I am not sure about computer prices where you all live, but here in Osaka a mother board is relatively cheap at about $100 or so, but I am concerned that I have no idea if the CPU is to blame too. Is there anyway for me to make sure that the CPU is not failing me too? Or is this a gamble I will have to take and cross that bridge when I come to it, etc. If the CPU is bad too, it would be cheaper for me to get another used computer. One about the same level/age as mine would be $200ish here.

Again, thanks for your input. I appreciate your reading my post.

---

### Post by Dngrsone on 2009-03-27
There's really no way to ascertain the condition of the processor without having a good motherboard to plug it into.

It is not totally dead because you have some operation (video, BIOS checksum, etc. require a working processor), but no guarantee it's 100%.

In my experience, though, processors are pretty robust, and the few I've seen fail were due to catastrophic events such as lightning strike.

I recommend getting a new motherboard.

---

### Post by Motorhead Kaze on 2009-04-01
Thanks much. I really appreciate the feedback. For now going to go ahead and check this off as "Solved" because there is nothing else to be done about the PC without another motherboard. Over here, the only motherboards like mine (that will fit my RAM and CPU) are used ones. Nothing new being sold anymore like mine. (In Japan 1 year old is "Old") (annoying but true)

Thanks again.

---

### Post by Motorhead Kaze on 2009-04-19
I am back.

I just put in a new-used motherboard/CPU/RAM from a reliable shop and guess what? After about 1 minute, the mouse and keyboard freeze up and I cannot do a damn thing.

And this is running the computer off the Ubuntu live CD with NO HDD anywhere near the case. BIOS is fine so GAAAHHH!!! It wasn't my motherboard OR the CPU! %#^@@*! I am glad that it was only $100 for these new-used parts, but I am now out $100 and the computer is still not working.

---

### Post by Dngrsone on 2009-04-19
Wow, that's odd.  

Are the symptoms similar or different?  If different, then maybe you got a bum board.  If similar/same, then perhaps your keyboard or mouse are at fault.

---

### Post by Motorhead Kaze on 2009-04-20
Hi there Dngrsone

Well shucks huh? I use the same mouse on the laptop and it works awesome.

The only things it could be are 
1. I just happened to get another motherboard/cpu/ram with the same freezing issue???

2. My power supply is wacko...if it were though it would SEEM that things would just shut OFF instead of freezing.

3. My CD/DVD drive is wacko...but I can get in to Ubuntu via live disc, and even played a game of solitaire just to see if I could. But when I went online, the moment I began to navigate anywhere, the thing froze up. I also tried the Gutsy live disc and same thing happens. I tried again, and instead of going online, I tried to start Open Office. Thing froze up again.

CDrom would not seem to be to blame because this issue began while I was online typing an email. There was nothing in the CD drive at all at the time.

Power supply?

---

### Post by Dngrsone on 2009-04-20
Well, if one of the output voltages is a tad low, it's possible that the PSU could be doing it... 

Rest assured, you aren't the only one who gets strange hardware issues-- I am regularly plagued with broken or misbehaving hardware.  My friends in the hardware forums I hang out with marvel at the tremendous bad luck I seem to have with computers.

---

### Post by Motorhead Kaze on 2009-04-20
First I want to thank people for the comments, and Dngrsone for coming back to look at my update.

It was the motherboard...TWICE.

I talked to the guy at the computer shop and his idea was to buy another motherboard and cpu and take them home, and try them out. With 2 CPUs and 2 motherboards (not including my original ones) that left me with 4 combinations.

The used motherboard and dual-core cpu I bought on Saturday did not work for me. So I put the (single-core) cpu that I bought today in there...nada. Same freaky freezing issues as I had when I started this thread.

I removed all that and put in the motherboard and cpu which I bought today, and successfully accessed the net and Open Office. 

Unfortunately, my old HDD was IDE and the only available motherboards that fit my case were SATA. But, this store had a whole shelf full of 250Gb SATA drives for the equivalent of $20. So, the only things I have in this computer case that I started with, are the case, power supply and the CD/DVD drive and floppy drive. I suppose I could put my old cpu in here, but it works now.

Verdict, I had a bad motherboard, bought another bad motherboard and ended up with one that works.

It does not look like I will get to keep this one either however...WHY? because I plugged in my video card, and it doesn't work. So no dual monitors? Can't do my job with one head...maybe the vid card driver was not picked up, but all I get is black screen if I use the dual head vid card.

Hey, but at least I know what started all this mess!

---

### Post by Dngrsone on 2009-04-20
250GB SATA for $20?  Sign me up!  :D

Glad you've isolated your problem... hope you will be able to get your system back up to speed soon.

---

### Post by Motorhead Kaze on 2009-04-21
Dunno how it is in the US/Canada, but at the shop I go to in Osaka if you buy NEW computer stuff you cannot return it. If it doesn't work, most of the time you have to send it to the maker. Used however is totally refundable. Sounds reasonable, but backwards from the US?

Anyway, I can't deal with this single monitor jive. I hope to find a driver or something soon.

---

### Post by Dngrsone on 2009-04-21
Yeah, here in the US, one can generally return new merchandise within say, 30 days.  There are exceptions, of course, notably electronic parts for motor vehicles and such.

---

### Post by Motorhead Kaze on 2009-04-21
Ah yes. Well, it has been nearly 7 years since we moved to Osaka so I am getting on the forgetful side of some of the finer details of American life. Born and raised Seattlite myself...though I did live down in your state for a bit...Lancaster...HOT.

Just a side note, when I started this thread, a motherboard change sounded like the end of my computer...but that turned out to be far, far less scary than I thought. This event got me to be able to change out a motherboard with confidence, which is precisely how I learned how to fix old motorcycles. Funny that.

---

### Post by Dngrsone on 2009-04-21
Baby steps, my friend... I've been working with/on computers and hardware for twenty-five years and still learning stuff about them.  :)

---

### Post by Motorhead Kaze on 2009-04-23
OK then. It took no less than THREE tries with used motherboards to find a good one. So this is what I ended up with:

Elite Group A770M-A (AMD 700 chipset) motherboard (6 USB ports, very nice)  ($50 used)
AMD Athlon dual-core BE2400 processor with fan ($40 used)
2Gb of RAM (UMAX, DDR2, Pulsar) ($19 used)
2, 250Gb internal SATA disc drives (total $40, used)
All new cables ($3 new)

This stuff is clearly not the top of the line, but it does give me twice the PC I had 3 weeks ago, for roughly $160. (16,000yen) But on top of that, I feel like I have learned quite a bit more.

---

### Post by Dngrsone on 2009-04-23
That's pretty darn good, man!

---

### Post by JCFranklin on 2009-04-24
I had a similar problem.  I have replaced a bad motherboard with a new one.
I am having a difficult time getting the components of the new motherboard to be recognized. 
Here is the summary: 
old system
homebuilt Chaintec nvidia board, 6600 PCIe X16 video, AMD Athlon64 proc

new system
gateway case, intel motherboard with integrated video (845 i think), intel p4 2.4

the video card does not get detected, the DVD burner is not recognized, the network card was not recognized, but I have fixed that.

It seems to me that there should be a fairly easy way to remove all the old drivers and rediscover the new hardware.  I am not opposed to a fresh install, but I think it may not replace all the bindings in things like fstab and the network gear and mounting DVD/CDROM drives like I want it to.

Thoughts? Suggestions?

---

### Post by Dngrsone on 2009-04-24
> **JCFranklin said:**
> I had a similar problem.  I have replaced a bad motherboard with a new one.
I am having a difficult time getting the components of the new motherboard to be recognized. 
Here is the summary: 
old system
homebuilt Chaintec nvidia board, 6600 PCIe X16 video, AMD Athlon64 proc

new system
gateway case, intel motherboard with integrated video (845 i think), intel p4 2.4

the video card does not get detected, the DVD burner is not recognized, the network card was not recognized, but I have fixed that.

It seems to me that there should be a fairly easy way to remove all the old drivers and rediscover the new hardware.  I am not opposed to a fresh install, but I think it may not replace all the bindings in things like fstab and the network gear and mounting DVD/CDROM drives like I want it to.

Thoughts? Suggestions?

This probably should be its own thread.  If I recall correctly, having your /home directory residing on a separate partition (or even its own drive) should allow you to reinstall without losing all of your data and settings.

Installing a new motherboard is definitely much easier with Ubuntu than with Win...  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/nod.gif[/IMG]

---

### Post by Motorhead Kaze on 2011-07-17
And a year later...saaaaame old **** in a very similar pile. I put up with the PC freezing up 3 times a day or more, for MANY months, just hitting restart and trying again. It would lock up especially when writing mails online, using Facebook, changing my blog design, viewing videos and even when in screensaver mode. Temp at a steady 30C even.

Started by buying a new PSU because mine was 7 years old (yes, I know). But that didn't solve my problem. I WAS going to buy a new vid card, but THAT turned out to be 7 generations old and it was only $140 to buy a brand new motherboard WITH outlets for both my monitors, CPU and 2gb of RAM. So, while I will never know now if it was the motherboard or the vid card, the computer is fixed...again.

Something has been causing trouble in there, taking a couple months to gradually kill off other sections. I HOPE now that everything is new that things will just work right.

---

