---
title: "XUbuntu 7.04 in a carpc corrupting the harddrive"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by mastakebob on 2007-12-01
OK, I have a weird problem here, and I wasn't sure what forum to put it in, so I put it under Hardware.  Also, I apologize for the length, but I'm hoping to get all my symptoms out there.  

I have Xubuntu 7.04 (cause anything 7.10 won't run X on my system, it just gives me a "something is wrong with X and we're waiting 2 minutes to try again", but thats another problem for another time) installed on my carpc.  Background:  A carpc is just a small form factor desktop in installed in my car.  It has a special Power Supply that can use the power from a car's battery/alternater.  More on this at the bottom.  

Now, my problem is that when I first install Ubuntu, everything works fine for about 2 to 3 weeks.  Then I start getting 2 start up issues.  The first:  When I boot up the computer, it gives me "BOOT DISK FAILURE, INSERT MASTER BOOT DISK AND PRESS ENTER".  The only way to remedy this is to just wait a while (>~3 hours) and try again and hope.  If it boots up fine, then you have about 10 more startups before the problem returns again and you have to walk away for another 3 hours before it fixes itself.  Second problem:  This is much rarer, but occasionally I get a message about the "file system being corrupt [or missing]".  It doesn't seem to be repeatable so I don't remember it off the top of my head.  This is solved easily simply by pulling up the BIOS, and then resaving it and restarting.  

So, for the first problem:  It seems like the way Xubuntu is being powered off (see below for more info) is causing it to slowly corrupt the MBR (which, I admit, I'm not too familiar with).  How this way is any different then normal is beyond me.  Has anybody else had this problem?  Or know how to fix it?  Any other ideas on what it could be?  Is it a GRUB problem?  And if it is because its a hardware shutdown vs a software shutdown (again, see below), is there anyway to set xubuntu so that it treats both the same (as a software shutdown)?   
For the second problem:  Thats not a huge deal for me cause it happens so rarely.  But, obviously, any help would be appreciated.  

Background on the power situation:  I have the PC running off the car's electrical system.  The PC knows to start up because I have a switched power line running into the PC in addition to the always on +12V and GND.  So when the car goes from 'off' to 'on', this third switched power line goes high, signalling the Power Supply to mimic someone pressing the power button (it shorts the power button leads for a second).  When the car goes from 'on' to 'off', the PC still has power running to it directly from the battery, but the switched power line goes dead, causing the Power Supply to again short the power button leads for a second, simulating someone pressing the power button on your desktop.  This sends the shutdown signal to Ubuntu, which dutifully shutsdown all programs and powers off the PC within 10 seconds.  (so its not a hard, pull-the-plug sort of shutdown, its just initiated by someone pressing the power button instead of going to the software supplied 'turn off' icon)

I know its not the hardware, cause I was running Windows for about 8 months on the exact same hardware and none of these issues happened.  When I switched to Linux a few months ago, it happened within the first month, so I bought a new harddrive and it happened again.  


Right, sorry for the hugely long post, but I'm hoping that more information leads to a quicker, better solution.  Let me know if you need any other information (you might need to post to steps required to get that info as I'm not completely used to digging around the underpinnings of linux).  

Thanks!

---

### Post by mastakebob on 2007-12-05
Bump.  

Nobody else experiences Ubuntu corrupting their harddrive?

---

