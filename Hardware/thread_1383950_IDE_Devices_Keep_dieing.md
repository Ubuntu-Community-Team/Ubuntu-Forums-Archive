---
title: "IDE Devices Keep dieing"
date: 2010-01-17
forum: Hardware
---

### Post by 3djake on 2010-01-17
Hi, this is a problem I have being to lazy to get around to figuring out and fixing so its about time I get to it. I want to know what could be causing my IDE devices to fail

It started  in early 2009 lol, One day I was doing some maintenance on my main computer, when I booted it back up my CD/DVD drive was not working at all, not even any power was going to it.
So thinking that drive had broken I took it out and removed the jumper then I took another DVD/CD drive I had laying around and that stopped working too along with my 300gb IDE hard drive which had my ubuntu install :(
So I plugged in a really old cd rom drive and that has not failed me but its really slow and its just a cd rom drive, my sata drive with windows still works luckly
I have plugged in my CD/DVD drives into my server box to see if I could get them to power up and had no luck.

I think one of the following 3 could be the issue 
Faulty Mother Board?
Faulty jumper?
Faulty Power Supply?

In any case I cannot afford to fix or replace any of this and there is some files on my IDE ubuntu drive I would like to get.
Any ideas on what is causing the problem and any ideas on how to get my IDE drives fixed?
my power supply should be able to handle everything (500V)  

Thank you for your time :)

---

### Post by Tp2357 on 2010-01-17
Logically, I would start by replacing the Jumper. IF that works, Great! If not have it looked at by a nerd/professional.

Hope this helps!

---

### Post by JackRock on 2010-01-17
To me, this sounds like a faulty motherboard, not putting enough power to the optical drive IDE port.  Your older drive works because it doesn't use as much power as the newer devices.  But it's still needing more than it gets, so you get a brownout at the drive.

Is this occurring only on this one port?  Can you use another IDE port, but use the same drive, to test?

If I were a betting man, I'd say it's the motherboard, if the other devices are working normally.

---

### Post by 3djake on 2010-01-21
Well what ever it is broke my ide devices, the do not work in any computer any more(they do not even power up), maybe its putting to much power to them.
I am thinking its a faulty motherboard

Any one know how to fix the IDE devices? so I can use them with a new system if I can ever afford to start building one?
Can a simple part such as a jumper really cause a device to break?

I am really careful when building computers and even make sure there is no way for static to get to the parts. 
I have build 6 computers and this is the first time something like this has happened.

---

### Post by azagaros on 2010-01-21
I agree with the guy says its a bad motherboard.  The situation sounds like a device interface is working, which works on millions of machines in the linux world.  The two cases is a faulty power supply or a bad motherboard to cause devices to fail most likely.

I do know that linux likes to drive machines a little harder than Windows, and physical wear and tear is not unlikely but what you describe is more related to power regulation from the Motherboard and power supply.

---

