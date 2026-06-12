---
title: "Laptop fan bugging me crazy"
date: 2009-10-21
forum: Hardware
---

### Post by mjp29 on 2009-10-21
I know that this is not a topic that relates to the Ubuntu operating system, but I request your reply to this thread if you have knowledge that can help.

I have completely installed Ubuntu on a Dell Inspiron 1000 laptop computer.  I have replaced the crashed HD with a new 80 gig Hitachi HD within the past 2 weeks.  I have replaced the dead battery [was dead for probably 3 years or more] with a new battery.

I now have, what I think is the fan, that is acting up and bugging me crazy as of now [in real time tonight in the last 60 minutes].  The fan sounds normal then speeds up and speeds down in such a way that the sound of the fan rapidly firing up to maximum cool speed then very quickly firing back is bugging me nuts.

I know I could Google how to replace the fan, and that would probably fix it [if I just replaced the fan].  But I would like the nice folks in this forum to tell me their opinion, especially if they have experience with hardware that could cause abnormal fan speed if the fan might actually not be going bad.  If folks here think it is just the fan that needs to be replaced that's great.  But tell me straight up if some other hardware problem inside the laptop could be causing the fan to zip around (high speed to low speed to normal speed).  Perhaps there is some other hardware problem inside the computer, like hardware that governs the fan, that could be the cause and the fan may not be bad.

Thanks to everyone that reads this and replies to this post.  I know your time is precious.

---

### Post by zepfan on 2009-10-21
If you want to try and control it install i8k and gkrellm. Should be in synaptic still.

What it sounds like is that your bios is kicking in and trying to cool down the CPU/GPU heatsink. (one fan right?) But then turning down the speed or turning the fan off when it's reached a low enough temperature. That's my guess based on reading your description. Any temp readings?

---

### Post by PrePenguin on 2009-10-21
Ubuntu and some laptops have had issues with ubuntu causing there fans to run all the time and causing the speed to rev up and down. I would install windows if you can and see if it shuts the fan up since it usually does not do this in windows. There may be other options however the fan issue seems to have came up alot with ubuntu 9.04.

---

### Post by mjp29 on 2009-10-21
> **zepfan said:**
> If you want to try and control it install i8k and gkrellm. Should be in synaptic still.

What it sounds like is that your bios is kicking in and trying to cool down the CPU/GPU heatsink. (one fan right?) But then turning down the speed or turning the fan off when it's reached a low enough temperature. That's my guess based on reading your description. Any temp readings?

I truly appreciate your input.  I did make another post where there was and still is a quick message when the computer starts up concerning a bios problem.  See link [http://ubuntuforums.org/showthread.php?t=1289220](http://ubuntuforums.org/showthread.php?t=1289220)


The bios message so quickly flashes across the screen is "mp bios bug 8254 timer not connect to io-apic"

My Uncle, who is retired, thinks this bios bug message is one in which the laptop is looking for something in Windows where there is no Windows on this computer anymore

Perhaps this bios bug mssg is something also indicating that the bios is having problems connecting with a timer that is not associated with keeping correct time and date (my computer keeps correct time and date) but perhaps the bios bug is perhaps connected to a problem where the bios can't connect to governor the timing of something like, say, the fan inside the computer.

update:  after the laptop is on for an hour or so it no longer revs up the fan or slows it down - it is a constant acceptable fan level noise that i'm use to from any computer.

---

### Post by mjp29 on 2009-10-21
> **PrePenguin said:**
> Ubuntu and some laptops have had issues with ubuntu causing there fans to run all the time and causing the speed to rev up and down. I would install windows if you can and see if it shuts the fan up since it usually does not do this in windows. There may be other options however the fan issue seems to have came up alot with ubuntu 9.04.

The fan in this laptop does run all the time (don't most do the same in ms windows). 

But the speed of the fan rev up and down is something I just started to experience tonight after turning the laptop on for under an hour.  However, after the laptop has been on for over and our or more the fan keeps running at a normal level (to me) and does not bug me anymore in the slightest.

?

I won't install ms windows on this laptop as i had not experienced this revving up and down after many weeks of ubuntu on it until tonight (then the revving went away after an hour and longer and still no problem now - just nice quiet fan sound in cpu that i'm always use to and don't notice).

?

---

### Post by PrePenguin on 2009-10-21
> **mjp29 said:**
> The fan in this laptop does run all the time (don't most do the same in ms windows). 
 
But the speed of the fan rev up and down is something I just started to experience tonight after turning the laptop on for under an hour. However, after the laptop has been on for over and our or more the fan keeps running at a normal level (to me) and does not bug me anymore in the slightest.
 
?
 
I won't install ms windows on this laptop as i had not experienced this revving up and down after many weeks of ubuntu on it until tonight (then the revving went away after an hour and longer and still no problem now - just nice quiet fan sound in cpu that i'm always use to and don't notice).
 
?
 
 
 
Well thats good news and hope maybe it was just a 1 time kink for you or maybe something was just taxing the processor or video card hard.. Maybe you wont have any more problems with it or just find the appropriate software to monitor it for any unusua activity so you can watch for a software issue compared to a hardware issue. By the way the fan hardly ever runs on my machine especially in windows only after running extreme processor intensive programs for a long time will the fan finally run.

---

### Post by mjp29 on 2009-10-22
> **zepfan said:**
> If you want to try and control it install i8k and gkrellm. Should be in synaptic still.

What it sounds like is that your bios is kicking in and trying to cool down the CPU/GPU heatsink. (one fan right?) But then turning down the speed or turning the fan off when it's reached a low enough temperature. That's my guess based on reading your description. Any temp readings?


What I'll do is leave it alone and if it re-occurs I'll go back to this thread and it will prompt my memory to install i8k.  

By the way, what does i8k do?  I think it regulates the fan speed, right?

---

### Post by mjp29 on 2009-10-22
> **PrePenguin said:**
> Well thats good news and hope maybe it was just a 1 time kink for you or maybe something was just taxing the processor or video card hard.. Maybe you wont have any more problems with it or just find the appropriate software to monitor it for any unusua activity so you can watch for a software issue compared to a hardware issue. By the way the fan hardly ever runs on my machine especially in windows only after running extreme processor intensive programs for a long time will the fan finally run.

The only thing I did different than usual this evening before the fan started doing this is that I plugged a card reader into the usb slot and downloaded 20 megs of photos onto the laptop.

Perhaps just that little extra thing (which the card reader is non powered like most are non-powered) prompted the system to heat up a bit and prompted the laptop to speed up the fan a bit for a time to cool down a processor that was doing something extra - is that logical thinking that reading data from a card reader could tax the laptop just enough to heat it up a little bit to prompt it to speed the fan up for a while to keep things cool - ?

One other note:  I do not really know how the fan ran on this system when it had ms windows on it because it was my wife's computer at the time.  I have only used the cpu since she bought a new one when it crashed.  I installed a new hd and battery and put ubuntu on it.  The entire time i've had ubuntu on it the fan runs gently all the time.  Most all pc desktop computers, the fan runs all the time.  But I'm a bad judge for laptops.  I've actually used a Mac g4 cube for a desktop since it came out, and believe it or not, it was designed to not have a fan at all - what a quiet peaceful experience that was for so many years.

---

### Post by PrePenguin on 2009-10-22
> **mjp29 said:**
> The only thing I did different than usual this evening before the fan started doing this is that I plugged a card reader into the usb slot and downloaded 20 megs of photos onto the laptop.
 
Perhaps just that little extra thing (which the card reader is non powered like most are non-powered) prompted the system to heat up a bit and prompted the laptop to speed up the fan a bit for a time to cool down a processor that was doing something extra - is that logical thinking that reading data from a card reader could tax the laptop just enough to heat it up a little bit to prompt it to speed the fan up for a while to keep things cool - ?
 
 
 
This is very possible since there was a performance change when before there never was as far as the fan performance goes. So the next time you start your system up cold just pay attention to the fans behavior and if everything is back to normal I would say yes that is what taxed the system over the line just a bit to cause it even though you would not think that particular task would be very CPU intensive.

---

