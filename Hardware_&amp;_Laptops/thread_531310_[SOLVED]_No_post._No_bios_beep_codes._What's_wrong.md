---
title: "[SOLVED] No post. No bios beep codes. What's wrong?"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by angryhomer17 on 2007-08-21
Well, I finally got around to building a brand new system which I've been meaning to do for about 5 years now. I put it together last Thursday and it has been working well until this morning. I've run slax and feisty live cd's on it for this time. 

Last night I started about 400 gigs of data from a few ide's to my new 500 gig sata. I noticed the system was getting quite warm, so I put my box fan next to the computer so it wouldn't overheat. Anyway, I got most of what I wanted transfered over leaving the rest for today. I powered down the machine last night and tried to bring it back up today to finish my transfer, but I get no video output. 

So I check all the connections, they are fine. Turn on the computer again and still nothing. No video output--the video card might have come loose. I checked that, but it was seated properly, though I still reseated it. Turned to machine back on and nothing. Checked all the connections again. 

Then I remembered that I usually get some beeps when the video card is detected at post. I wasn't getting these. I check my jumpers to make sure they hadn't come loose and reseated those. Still no post.

I then tried taking out the video card to force the system to beep, saying it had no video card. Nothing. Maybe bad ram? Took out the ram after putting the video card back in and turned on the machine, still no beeps or post.

Bent pins on cpu or cpu fried? Took off the fan and popped the cpu out. Looks ok, no bent pins, thermal grease kinda sucks though, but it does not smell fried. I turn on the computer w/o a cpu, video card, ram, or anything else hooked up and still no beeps.

Tried unhooking the cdrom and the hard drive to eliminate any probs with those. Don't need either to post. 

I am at a loss at what to try next. I have no extra parts to try out unfortunately. Like I said everything was working well last night. Reading other posts concerning this it sounds like it could be any number of problems. One of those posts said that you need a cpu in order for any beep codes to go through. Another said it was a bad motherboard. 

Oh, and the power supply seems ok.

Here are some specs:
MB: Asus p5k se
Ram: A-data ddr2 800 2x1024
Psu: Thermaltake Purepower 500
Gpu: Evga Nvidia 7600GT
Cpu: Intel E6550

Thanks for any help. I'd really like to get off this tiny laptop and have a nice desktop to work with.

---

### Post by l33t_3lv3n_g33k on 2007-08-21
That sounds like a bad motherboard to me.  I highly recommend getting a [POST PCI Card]("http://www.amazon.com/Startech-com-PCIPOST-Post-Diagnostics-Test/dp/B00006B8EZ").  One of these babies is worth it's weight in gold if you do a lot of hardware work.

---

### Post by oddball on 2007-08-21
I can confirm that I have had several systems that have not provided me with any beep codes whatsoever when the CPU hasn't been seated correctly or completely dead.

The unfortunate thing is that the motherboard can also fail in such a way to not give any beep codes at all.

So it is a bit of a guess without trying another CPU in the machine.

If you noticed that the thermal grease wasn't great then that would probably sway me towards trying a different CPU to start with since it's all you've got to go on, and you'd be amazed at the problems that bad conductivity between CPU and heatsink can cause.

Unfortunately it can still often be cheaper to go to a local computer shop just to get the problem diagnosed, rather the throwing cash at the problem.  I have about 7 years experience in the IT industry, but I still don't have loads of spare parts lying around at home so I find a decent small local computer shop, get them to diagnose the problem, and if they aren't gonna charge extra to fix, I have them swap the affected part while they're at it, unless I know that I can get the part way cheaper elsewhere.

---

### Post by angryhomer17 on 2007-08-21
Thanks for the help. I am going to try to rma the cpu first. Hopefully that works. Otherwise I'll try the mobo. Or I guess I could try them both at once. This really sucks since I just built the machine 5 days ago. I wanted it ready for school, not trying to make it work at school. 

I don't think it is a mobo issue because I can turn the machine on, it responds when the cpu is pulled out (system can turn on w/o the cpu but not off), and I get a power indication on the mobo. Though I am not sure if you can have a half working mobo? 

I will have the machine for another few days while I get the original boxes shipped to me. So if anyone has any other suggestions, I would appreciate them.

---

### Post by w4ett on 2007-08-22
Don't forget to check the Power Supply too...a lot of problems can be traced back to bad PSU's...hopefully it hasn't spiked the voltage to the motherboard/CPU.

---

### Post by angryhomer17 on 2007-08-22
What's a simple way to check if the psu is working? I have no spare parts to work with and not even a multimeter to check the output. I'd really like to have the time to troubleshoot this, but I just started school and don't have much time to mess around with it.

I know that anything could be the culprit, unfortunately. I've seen enough hardware failures where I've worked. The nice thing is that all the machines are the same, so there is no problem swapping parts to troubleshoot the bad one. 

I am still at a loss to what caused the failure of whatever component in the first place. Like I said, the machine was working fine for 5 days and on the 6th, something went bad. it appears that everything is is in good condition. 

Bah, speculating isn't going to help. I guess I just have to do this the hard way and start replacing parts. This sucks.

---

### Post by johnny4north on 2007-08-22
i believe that it maybe your power supply, but have you checked your power switch.  i've had 3 power switches go bad on me. two would stick down and the last one popped off the faceplate. you may check the power supply by unplugging all the plug-ins. except the cpu fan, videocard and motherboard with the cpu installed(1 stick of memory on the board).  this just might get it to turn a fan and/or give a beep.  if it does, you may have a dieing power supply. good luck.

---

### Post by angryhomer17 on 2007-08-25
Well it's been a few days now, and I thought I would try to boot my machine again. What do you know, it booted, although I did get one long beep, and three short ones (no vga detected). Somehow I still got video output. So I rebooted and get one long beep followed by two short ones (no memory detected) I take out one of the memory modules and reboot the machine once more; I get no beeps.

I tried switching the memory around to different slots, using one stick, then the other, then both of them, and I couldn't get anything. I'm not sure what is different now than it was 3 days ago, so that the machine could turn on....same setup as it was 3 days ago. 

Anyway, looks like I am back where I started. Looks like I either have bad memory modules or a bad motherboard. I'm going to guess it's the motherboard since it seems everything is being affected in an uncertain manner.

I was going to get a replacement cpu, but that seems ok, the power supply looks to be fine. So I guess it has to be the mb, memory, or gpu. I'm not sure what to replace first, or what the hell is going on with my machine.

As always, any help would be appreciated.

---

### Post by angryhomer17 on 2007-08-28
I'm back again a few days later, and guess what? The machine is working again.... This time everything was attached (2 sticks of mem, cpu and fan, gpu, cdrom....everything except the hard drive) and I booted a live ubuntu cd without any problem. 

I rebooted the machine because I wanted to do a memtest. Resart through the live cd and I get the machine to beep (finally. One long beep followed by three short beeps (means no vga detected), although I was able to see a post and had just seen the live cd run. 

I also received a cmos error (cmos corrupt/invalid parameters) which I solved by pressing f2 which resets the bios to it's default values. (This was expected because I reset the cmos clock a few days ago to try and clear up the post issue.)

Then the live cd loads and I choose memtest which is 50% complete now. I have received 0 errors so far. Based on all the problems I have been having it appears to be an issue with the motherboard itself.

I am still not sure why I can only boot every few days and without a hiccup. I am thinking it might have had to do with the computer being in a room that has been up to 100 degrees, though it was getting cooled fairly well. Maybe a short circuit somewhere? But having reseated everything (cpu, gpu, ram, atx power, etc.) I think I would the machine would have worked sooner, and not as intermittently. 

After the memtest finishes I will probably run the live cd and work the cpu a bit to see if that craps out, reboot a few times, and turn it off for the night. I wouldn't be the least bit surprised if it didnt work tomorrow. At least I have the boxes to return the mobo now. I am supposed to play games with my computer, not have it play games with me.

---

### Post by angryhomer17 on 2008-04-15
Well, what happened in the end was that I RMA'd the motherboard and the CPU back to newegg. I was an idiot and sent back the motherboard risers too (which had come with the case I bought separately). 

So I got a new mobo and couldn't install it til I got some risers off of ebay.

Anyway, it's been working fine for the past 8 months. So I'm guessing it was just a faulty motherboard.

One extra thing: I've transported my machine around a bit and the stock cpu fan fell off. Damn clips. I thought I had put it back on right, but I didn't and ended up wondering why my computer kept on randomly shutting down. Well my cpu was going to 85C degrees, no good. Got a nice new fan/heatsink and some thermal grease. Running a cool 25-30C now.

And the best thing about it, my cpu didnt get fried after spending a few weeks at over 75C. Core2Duo's are pretty sweet.

---

