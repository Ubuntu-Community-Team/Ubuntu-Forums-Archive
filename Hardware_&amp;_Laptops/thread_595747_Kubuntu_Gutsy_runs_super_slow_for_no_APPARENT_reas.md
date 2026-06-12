---
title: "Kubuntu Gutsy runs super slow for no APPARENT reason"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by posingaspopular on 2007-10-29
Hey all, I'm not very good with the forums, since I mostly stay on IRC but this one is a problem that I could NOT solve, even with the help of #kubuntu and #ubuntu-chicago, which solves 98% of every problem I've run across. 

Here's what happpened. I clicked on konversation because I was getting highlighted. My screen went completly black (this was not X crashing) and I had to do a reboot. So I did a reboot and logged back into Gutsy. Now for some reason everything runs super slow, at least half of the capacity it should be running at. I figured that the issue was a onetime thing, so I did another reboot, unplugged my power supply so that the computer would be compeltly off and booted into recovery mode. The error persists. Web pages take a long time to load, my mouse is laggy, opening apps is a pain, etc.  

This is a desktop running a 2.66 ghz processor. No compiz or desktop effects, just general computer slowness. 

Things I did to try and fix my computer, and their output:

ksysguard: All the user % was under 1 or 2 percent for all the processes running, and the same goes for the system %, if i look at the system load though, it is apparent that a large amount of my physical memory is being used. approaching 348,728 of 678,360 or roughly 50%

Here is my output for glxinfo | grep render:

darkforce@speculum:~$ glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
darkforce@speculum:~$             

here the output for lscpi for anyone who wants to know my videocard/pci settings: 

[http://paste.ubuntu-nl.org/42538/](http://paste.ubuntu-nl.org/42538/)

If need be, I'll modify this post and include the output directly into the message.            

Next I tried checking the memory bar of Kinfocenter

This confirms that my memory is being sucked dry for no apparent reason. Total memory is 44% free, 56% in use.

In terms of Physical memory: Free is 36%, disk cache is 34%, disk buffers is 9% and application date is 22%. This has fluctuated a bit but I am constantly opening/closing programs to check various parts of my system, so I'm not worried. For example, the application data used to be at 4% but I opened up pidgin, so im not worried about that. Also, Free Swap is 100% empty.

ps -aux and top/htop both tell me that the apps are within normal range for CPU/mem usage however (never going above 3% for any app)

I have 2 sticks of 512 DDR2 memory installed, and my hard drive has more than enough space (80gigs free) for all the information on it.

I've basically run out of ideas and no one I've talked to has been able to give me a definitive answer to fix the issue. If anyone has questions, requests for more information, suggestions, a fix, etc. please comment and I will get back ASAP.

---

