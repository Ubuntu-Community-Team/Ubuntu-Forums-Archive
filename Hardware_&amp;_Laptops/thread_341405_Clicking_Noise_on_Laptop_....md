---
title: "Clicking Noise on Laptop ..."
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by A.I. BOT on 2007-01-18
I have a Dell Latitude D600. My father gave it to me around September in exchange for my Mac Mini (which had Ubuntu on it). So I installed Ubuntu on this laptop in October. From then until now (January), I have noticed that a clicking noise is comming from inside the laptop. I am assuming this is a hardware related issue, though.

I have done some Googling and searching and some people say it is a defective hard drive. When I find it happens is when I go out, I shut the laptop lid and the laptop is cool, but when I come home several hours later the laptop is a bit hot and the fans are running. Then, during the fan process and after the fans shut off, I start to hear the noise. After a while, it does stop the clicking noise :/ but later will start up again.

I am looking for suggestions and ideas of the cause. I really at the moment dont have the money to spare to pay for a new hard drive if needed, at the moment.

Thanks for the help.

---

### Post by john_spiral on 2007-01-18
Try moving a large amount of data few gigs from a USB key onto the hard drive, if the clicking goes mad it looks like your hard drive.

---

### Post by A.I. BOT on 2007-01-19
Alright, same noise so i'll go buy a new HD. Thanks for the help :)

---

### Post by RandomJoe on 2007-01-19
Is it an obviously bad noise?  (Yeah, that's not subjective at all...!)  I've had a number of laptop hard drives that just made weird nosies when accessing the drive.

Have you tried installing the smartmontools package and seeing what your drive says about its health?  It isn't the _easiest_ report in the world to read, but can give advance indication of failures.

Or, try using Dell's diagnostics disk if you have it.  They boot off CD now (at least, the ones we get at work do) and you can tell it to test the drive, see if it reports any issues.

---

### Post by closey on 2007-01-20
> **A.I. BOT said:**
> I have a Dell Latitude D600. My father gave it to me around September in exchange for my Mac Mini (which had Ubuntu on it). So I installed Ubuntu on this laptop in October. From then until now (January), I have noticed that a clicking noise is comming from inside the laptop. I am assuming this is a hardware related issue, though.

I have done some Googling and searching and some people say it is a defective hard drive. When I find it happens is when I go out, I shut the laptop lid and the laptop is cool, but when I come home several hours later the laptop is a bit hot and the fans are running. Then, during the fan process and after the fans shut off, I start to hear the noise. After a while, it does stop the clicking noise :/ but later will start up again.

I am looking for suggestions and ideas of the cause. I really at the moment dont have the money to spare to pay for a new hard drive if needed, at the moment.

Thanks for the help.

I have noticed on my (new) HP Pavilion dv9008tx that after a while I will get some odd clicking noises coming out of what I think is a hard disk. It isn't apparent straight away, it only happens after a while. I have a hunch it's some power management feature trying to put the disk into a standby mode, but it's not 'all the way there'. I don't have any idea on how to fix it though.

Can you determine what part of the laptop your sound is coming from accurately?

---

### Post by GordSellar on 2007-03-08
I'm having the same issue on a HP Pavilion dv2000. I have yet to check whether it occurs when I am running Windows, so I'll try boot to that (it's dual boot) and report back if it looks like an Ubuntu-related issue. I, too, was thinking it might be something like a power-management issue. It sounds weird, to me, anyway.

---

### Post by GordSellar on 2007-03-08
by the way, the source of the noise on my pc seems to be at or near the fan vent. If the laptop is on the desk in front of me, the sound is coming from the rear left side. I'll go see if it continues when I'm running under Windows.

---

### Post by GordSellar on 2007-03-08
I'm hearing the sound less often when booted in Windows -- it's much less regular then when I'm booted in Linux -- but it's still there. And having listened closer, it is the hard drive clicking, so I'm going to take it to the  After-Service center... it's free here in Korea, if it's just service, but since I'm intending to upgrade the drive (which I'll have to purchase myself if I want a bigger one), I'll just ask which brand of drive I should get to avoid the problem.

---

### Post by treesurf on 2007-03-09
You might try checking out this thread.  One of the suggestions in here solved my hard drive clicking problem.

[http://www.ubuntuforums.org/showthread.php?t=331418](http://www.ubuntuforums.org/showthread.php?t=331418)

---

### Post by GordSellar on 2007-03-11
> **treesurf said:**
> You might try checking out this thread.  One of the suggestions in here solved my hard drive clicking problem.

[http://www.ubuntuforums.org/showthread.php?t=331418](http://www.ubuntuforums.org/showthread.php?t=331418)

Thanks! I tried the hdparm thing. Of course, the clicking seemed to have stopped by itself before I tried the hdparm adjustment, but I'll hope that this keeps it that way. Cheers, treesurf!

---

### Post by GordSellar on 2007-03-24
Ack. The clicking is back, and I think it had to do with having booted up, gone to battery power, and then plugged in again. How annoying. All the hdparm resetting I've done has had no effect...

---

