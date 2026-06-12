---
title: "Toshiba Satellite L505-S6946 wireless keeps dropping"
date: 2010-08-28
forum: Hardware
---

### Post by jewfromdahood on 2010-08-28
hi my toshiba laptop keeps having the wireless drop every now and then, it shouldn't the router is perfectly fine and just will drop every so often...

---

### Post by meditatingfrog on 2010-08-29
> **jewfromdahood said:**
> hi my toshiba laptop keeps having the wireless drop every now and then, it shouldn't the router is perfectly fine and just will drop every so often...

I've had this problem, and resetting the router would fix it.  I'm not sure what was causing it.  How do you know the router is perfectly fine?  Do you have another device that can connect to the wireless access point when your laptop can't?  How do you get it working again?  Does it happen after resuming from suspend/hibernate?

---

### Post by jewfromdahood on 2010-08-29
I know the router is fine because my main laptop, the one I build also running on Linux, has never dropped a single connection, the toshiba is the one i gave my mom. And I have two routers and the same result on both a 2wire AT&T Uverse  modem with built in wireless router, and a D-Link DGL-4500 same thing with both drops every so often

---

### Post by meditatingfrog on 2010-08-29
> **jewfromdahood said:**
> I know the router is fine because my main laptop, the one I build also running on Linux, has never dropped a single connection, the toshiba is the one i gave my mom. And I have two routers and the same result on both a 2wire AT&T Uverse  modem with built in wireless router, and a D-Link DGL-4500 same thing with both drops every so often

Man, and it isn't happening because of suspending/hibernating your laptop?  The only thing I can think to recommend is to try a different kernel.  There should be kernels you can try that are already loaded on your laptop that are accessible from the grub boot menu.  If that doesn't work, you can try upgrading to the newest ubuntu, if you already haven't done so.  

I am currently running jaunty with kernel 2.6.30 because of suspend/hibernate wireless issues I was having, but this isn't recommended if you can avoid it.

---

### Post by jewfromdahood on 2010-08-29
moms laptop is running the latest ubuntu, and I make sure to drop by every few days and when I visit, to upgrade her laptop completely for her as she is not linux savy, nor computer savy. Lets put it this way, she is still new to learning how to download new apps on her iPhone. yet she youtubes all the time. Always upgrading her kernel.

---

### Post by meditatingfrog on 2010-08-30
> **jewfromdahood said:**
> moms laptop is running the latest ubuntu, and I make sure to drop by every few days and when I visit, to upgrade her laptop completely for her as she is not linux savy, nor computer savy. Lets put it this way, she is still new to learning how to download new apps on her iPhone. yet she youtubes all the time. Always upgrading her kernel.

i just noticed you didn't post the model of the wireless nic we are dealing with.  you should probably run "lspci | grep Wireless" to get the wireless nic.  then you can search google, and even these forums to see if anyone else has had trouble with the wireless nic you are dealing with.  try searching [http://www.google.com/blogsearch](http://www.google.com/blogsearch) and site:[http://www.ubuntuforums.org](http://www.ubuntuforums.org) <wireless-nic> to see what you get.

This all having been said, let me try to clarify what i was getting at with the whole kernel business.  i wasn't saying to use the newest kernel, i was suggesting using a "different" kernel.  sometimes a newer kernel may have problems with certain hardware that the older kernel doesn't.  try out an older kernel and see how it works (but first run lspci and see if anyone else has had problems with your nic).  if you can identify the problem is with the kernel, then you can create a bug to hopefully get a kernel hacker to fix the problem in the next build.  

another option you can try, and i know this is weird, is use ndiswrapper with a windows driver for the wireless card on the laptop that is having trouble.  but search for info with ubuntu and your wireless nic first, then try *different* kernels.  this option is really a last resort kind of thing.

if you post the model of the nic on here i can help you search too.

---

### Post by jewfromdahood on 2010-08-30
03:00.0 Network controller: Intel Corporation WiFi Link 5100
        Subsystem: Intel Corporation WiFi Link 5100 AGN
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at d4600000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

---

### Post by trash on 2010-08-30
This seems to be an issue with my L350 as well, wireless is fine and dandy in windows but intreped i disconnect repeatedly often requiring a reboot.
will post card details when i boot back into linux

---

### Post by meditatingfrog on 2010-08-30
Well, i searched the web for "ubuntu Intel Corporation WiFi Link 5100 AGN" and couldn't find anything that would help.  i also searched the forums, didn't find anything.  I've already spilled out all my knowledge.  you should probably create a bug in launchpad, try what i recommended, and wait and see if anyone has any other ideas.

---

### Post by trash on 2010-08-31
well it turns out i have the same card.. WiFi Link 5100 AGN and my system is 64bit and the router i connect to is a dlink 628 or something like that.

Another strange thing that happens in ubuntu only is that when i use my phone or the phone rings i get disconnected.. it is a 2.4g cordless but it does nothing to my connection when i'm in windows.

---

### Post by jewfromdahood on 2010-08-31
well my phones are all 6Ghz and 5.8Ghz so even if my computers were on the available 5Ghz I wouldn't have an issue. I don't use the 5Ghz wireless even though my router and main laptop support it as my mothers laptop doesn't.

---

### Post by jimstar79 on 2010-09-01
i've been experiencing problems with my wifi connection all day. 

and i noticed that when i connected to the internet on my phone i lost wifi on my laptop, and later when i switched off the internet on the phone i again lost wifi on the laptop. 

I though nothing of it. thought it was a coincidence as my wifi connection has been all over the place today - but then i read this thread and thought - eh, what? it may be possible!

acer laptop w ubuntu lucid and i have a tocco lite mobile?!?

curios!

---

### Post by trash on 2010-09-06
Just a thought but my router has always been on mixed mode and i noticed that i always connect 'n' instead of 'G or B' like everybody else on our network.. i switched to 'b/g' mode so i'll see if that helps.
First think i did noticed is signal strength 'n' mode was around 50-58% while 'g' is 80-85%

---

