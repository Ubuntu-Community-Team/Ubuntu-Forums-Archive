---
title: "Why Does my 16BG Ram Desktop Slow Down So Quickly with Ubuntu"
date: 2014-10-16
forum: Hardware
---

### Post by vincej on 2014-10-16
I have just come over from Win7.  I have a Dell 8300 desktop with an i7 and 16GB of ram. 

I like have a lot of tabs open on Chrome. Maybe 25 at a time. I will also have Thunderbird open, then a java based development tool ( PHPStorm) , Apache and MySQL running. The system monitor is telling me that I am using 5GB of the avaiable 16GB yet, the system is clearly struggling. Response times on the keyboard are slow as too is Chrome.  My CPU occasionally jumps top 60% but averages 40%. 

So I don't get it. My system should be walking under Ubuntu 14, yet it struggles. 

Any ideas ?? 

Many Thanks !

---

### Post by weatherman2 on 2014-10-16
I open lots of Chrome tabs on my Ubuntu 12.04 laptop, which has 16GB of RAM but only a dual core Celeron CPU.  No speed or lag issues here - or at least, not very often.  I could never tolerate lags typing in Chrome.

What's eating 40% of your CPU?  Are you serving up web pages via Apache (public server?) or is Apache only for testing?

How much swap space do you have?  What kind of hard drive, and have you tested it?

---

### Post by vincej on 2014-10-16
I created a dual boot. The Ubuntu partition has 185 GB of useable space and 17GB of swap. 

Looking at the system monitor Chrome and Java is eating resources, but even if it is eating 40% I should not be getting any slow down until I get to 80% at least. The way I bring it under control is doing a restart or at the very least just down all the chrome browsers and then reopen. I tried using an AMD fan control utility ( AMDOverdriveCTRL)earlier today to solve a different problem and I had to shut it down as it almost brought my system to a stand still.

Apache runs locally. The drive is a Seagate. Testing ... don't know how to do that. 

Any ideas ? Many Thanks !

---

### Post by tgalati4 on 2014-10-16
If you have ads (javascript and flash) running in several of your tabs, then that will eat up CPU cycles.  Do you have adblock and a javascript blocker installed in Chrome?

Try running the same workload in Win7 and let us know how that works--but you have to reply while in Windows--no cheating by booting back into Ubuntu.

Running several java apps will eat up CPU cycles.  Chrome has become pigish itself.  Count the number of Chrome threads that get created with 25 tabs.  I would guess 200 or so.

Many of those tabs have javascript widgets that are reporting back to facepalm and twittle generating traffic and eating CPU cycles.  Check your network throughput with this workload.

Install *htop* and identify the top 20% bad actors.  Sort by CPU.

---

### Post by sp40140 on 2014-10-17
adding to what tgalati4 said:
Try using different browser and see if you run into same thing. There are lots of browsers you can pick from. Also, your graphics hardware / drivers might have a hand in this. What are the hardware specs of the machine?

---

