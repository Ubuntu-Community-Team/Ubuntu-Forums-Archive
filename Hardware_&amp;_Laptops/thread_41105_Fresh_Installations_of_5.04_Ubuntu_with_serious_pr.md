---
title: "Fresh Installations of 5.04 Ubuntu with serious problems (i.e. crashes/freezing)"
date: 2005-06-11
forum: Hardware &amp; Laptops
---

### Post by veraction on 2005-06-11
So, I have Ubuntu 5.04 installed on my main computer & it is great. No lockups or any problems. Specs for that Computer *(the one that works correctly)*: 

[list]
[*]Asus A7N8X Deluxe Mobo
[*]ATI Radeon 9700 Pro
[*] 2 Western Digital Hard Drives (180GB & 60GB)\
[*]and 3 cd/dvd drives & a floppy drive
[*] 2x 512 MB RAM 400 Mz (?)
[/list]

Now, onto my smaller computer. I've tried about 7+ times doing fresh installations of Ubuntu 5.04 from the same CD. Each time there is something severely screwed up. Common problems are:

[list]
[*]Randomly being logged out of the computer. i.e., I'm doing something for any amount of time (even under 60 seconds after boot) and the screen locks up for a second, then I'm back to the login screen
[*]Sometimes the computer completely freezes up & becomes unresponsive
[*]Various applications freeze, i.e. the Ubuntu update program
[*]other weird stuff
[*]a stick of RAM. not sure about specs
[/list] 

Specs for the computer which is having problems:

[list]
[*]Asus A7N8X Deluxe Mobo
[*]ATI Radeon 9200
[*]20 GB (?) Western Digital Hard Drive
[*]A CD Drive & Floppy drive
[*]Some random sound card
[/list] 

I tried looking at the system logs, but they don't seem to be helpful at all.

Please help ;) I'm about to install Windows if I can't figure it out soon

[edit] and it doesn't seem to be overheating. It gets plenty of airflow; all fans are working; and it feels cool inside

[edit2] I'm running Ubuntu memtest86 on it now...

[edit3] **Another thing. Before, I had Windows XP installed on it & it worked great with no issues whatsoever....**

---

### Post by veraction on 2005-06-12
Well, I did the memtest for ~15 min then my computer rebooted without warning in middle of memtest.

Then I restarted memtest. it went for ~30 min, then I decided to quit it. So, I rebooted my computer & when trying to start Ubuntu, I got this error: [IMG]http://ezenu.com/temp/ubuntu%20kernel%20error.jpg[/IMG] 

 ](*,)

[edit] turned it off after this error, let it sit for ~5 min, then I turned it on again. This time another "Kernel Panic" error, but different.

/sigh... reburning the installation CD shouldn't help? or would it?

---

### Post by codejunkie on 2005-06-12
as for the iso problem if you just downloaded it, it could be corrupt i just read a post where someone said they just downloaded the iso several times and they were corrupt, have you tried the iso you used to do the install on the working machine. also have you  tried comparing bios settings between the two machines since they have the same motherboard.

i just remembered seeing that screenshot of yours one of my pc's did that does your motherboard have onboard video plus the ati card if so that might be the cause make sure onboard video is disabled in the bios it could be causing that.

---

### Post by sunscape on 2005-06-12
I had a similar problem and the solution was that the ram module was bad. Lots of memory these days is shipped without being properly tested. In fact, I believe there is an article about it at slashdot.com.


Or it might just be loose. Try another ram slot

---

### Post by veraction on 2005-06-12
it is the same CD which was used to install the working version.

I'm gonna rip it apart & check the RAM. I might take the ram out of it & put in 1 stick from the good computer to see if that solves it (therefore the RAM is bad)

---

### Post by veraction on 2005-06-12
just realized that the mobo in the 'bad' computer isn't a A7N8X Deluxe, but actually is a "ASUS A7V8X-X Socket A (Socket 462) VIA KT400 ATX AMD Motherboard - Retail"

Shouldn't matter though.

I'm trying to install Windows now. If that works, I'll try some cpu/memory intensive tasks to see if it works.

[edit] sucks that I can't keep track of which CDkey is for which computer I have :( but I have an unopened one..

---

### Post by veraction on 2005-06-12
Grr.  ](*,) 

I have no idea whats wrong with it - I suppose either memory or overheating (though the temperature was ~30 degrees C when I checked). It keeps rebooting for random reasons. I can't even get to the login screen for Ubuntu, nor can I install Windows XP (it freezes during setup).

The weird thing is that it worked great for long periods of time approximately 10 months ago. It was left to collect dust for that time, and now its all f'ed up :(

---

### Post by electroglas on 2005-06-12
Have you tried clearing the CMOS/BIOS?

---

### Post by veraction on 2005-06-12
not yet

[edit] BTW, the RAM is Crucial 512MB 333MHz -- I thought that was a high quality brand ;\

---

### Post by codejunkie on 2005-06-12
Crucial does make good memory but memory does go bad sometimes. take the memory from the bad computer and try it in the working one also it could be a power supply problem that will cause random reboots and crashes too if it's not putting out enough power.

---

### Post by juicemansam on 2005-06-12
I'm not sure how relevant this is, but at my college where I do some part-time tech support, my supervisor had a whole batch of Dell GX280's go bad. The symptoms were random lock-ups or reboots. The problem ended up being bad capacitors, which can be visually seen as bloated (between the capacitor and the motherboard) or tilted over (more than "normal").

---

### Post by veraction on 2005-06-12
**UPDATE** 

Took the stick of RAM (Crucial 512MB 333MHz) out of the 'bad' computer. Put a stick of RAM (Centon 512MB 400MHz) in from the good computer.

Turned on the 'bad' computer. It seemed to boot to Ubuntu fine. However, I started experiencing the same problems - a lot of them within 5 minutes. Was randomly booted to login screen twice. And once when I had just firefox open, I got a message saying all these gnome programs had crashed (i.e. a gnome desktop tool) -- I've gotten this error on that computer before quite a bit.

So now I am thinking the problem isn't the RAM. There isn't much else which could be the problem other than the mobo or powersupply I think.  ](*,)

---

