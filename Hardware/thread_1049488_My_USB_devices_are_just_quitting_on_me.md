---
title: "My USB devices are just quitting on me"
date: 2009-01-24
forum: Hardware
---

### Post by birddog165 on 2009-01-24
So I've got three USB devices plugged into my computer.

-Apple Aluminium Keyboard
-Logitech mx600 Mouse
-WD 500Gb External Hard drive

The mouse and keyboard work fine and then I plug in the HDD and all heck breaks loose. The HDD starts spinning and is recognised. Then the keyboard stops working and the HDD keeps spinning but disappears. I click shutdown and it takes 2 or 3 minutes and gives me error messages about not being able to shutdown the HDD. The computer still shuts down in the end.

What is going on? Is there some sort of USB enhancer that I need?

---

### Post by birddog165 on 2009-01-24
Basically the best way to kill the USB stuff is just opening up Listen and trying to run some music files that are on my HDD.

---

### Post by birddog165 on 2009-01-24
UPDATE: So when I leave the harddrive plugged in, everything runs fine. It seems that this only happens when I am loading songs into the Listen library. I'm going to try and use it in other players and see if the problem still occurs.

---

### Post by birddog165 on 2009-01-25
So it appears that I am getting this problem whenever I plug in the drive. It'll just start booting up and then disappear and the keyboard will quit on me to.

When I click on "Shut Down" I get this error message:
> unable to enumerate USB device on port <number>
(Where is says number, it's just the port number that I have the drive plugged into. Right now, it's 3.)

---

### Post by birddog165 on 2009-01-25
Okay folks here are my lsusb outputs:

When I mount the hard drive initially:
> stoffj@Eustace:~$ lsusb
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 005: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 005 Device 004: ID 05ac:0220 Apple, Inc. Aluminum Keyboard
Bus 005 Device 002: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c518 Logitech, Inc. MX610 Laser Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by cariboo on 2009-01-25
Is your external drive powered by usb? If so you may want to try a powered usb hub.

Jim

---

### Post by birddog165 on 2009-01-25
Naw, the hard drive has it's own power supply that plugs into my power strip. When I say that the device just quits, I mean that it's still spinning but all of a sudden it's not recognised anymore. But the computer still knows that it exists. I'm gonna try and use the on screen keyboard to get an output from lsusb when the drive and keyboard stop working.

And just for fun, I'm gonna change the port as well :)

---

### Post by birddog165 on 2009-01-25
And here's the output of the pre and post-fail: (with switching the HDD and the mouse ports)

Pre:
> stoffj@Eustace:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 003 Device 004: ID 05ac:0220 Apple, Inc. Aluminum Keyboard
Bus 003 Device 002: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c518 Logitech, Inc. MX610 Laser Cordless Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


post 
> stoffj@Eustace:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 05ac:0220 Apple, Inc. Aluminum Keyboard
Bus 003 Device 002: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c518 Logitech, Inc. MX610 Laser Cordless Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


but now only the mouse works

---

### Post by birddog165 on 2009-01-25
Hey guys! Throw this into the equation. After both keyboard and drive shut off, I unplugged the external drive and keyboard and put them into different ports *after a few minutes* and they remount. Weird. I just wish that I didn't have to replug every time they disappear. Can someone help me?

---

### Post by birddog165 on 2009-01-26
hmm, no difference between USB 1.1 and 2.0. I've also tried using two different USB cables.

---

### Post by birddog165 on 2009-01-26
This is interesting for anyone following along. When I transfer files at 870kb/s (why it does that sometimes and other amounts other times is beyond me now) it lasts longer. By longer I mean consider this:

When I open up Songbird or Listen and try and load my library of songs off the external, it'll get sick and stop after like 30 seconds. However...

when I am transferring files at a slower rate, I can unusally get through the whole thing. Which leads me to some thoughts for the night:

1) It bothers me that I am pretty much the only one who writes on my own post, but that's cool. I'm just impatient, and this has become sort of a livejournal.
2) It doesn't matter how long the HDD is plugged in, but rather the amount of data that is trying to be written/copied at one time. My current record is > ~1.0Gb.
3) I have no idea why my keyboard cuts out, but who cares anymore. I just unplug, replug, and use the on screen for the time being.

Good night

---

### Post by birddog165 on 2009-01-26
> **birddog165 said:**
> ... My current record is > ~1.0Gb...

Okay, I'm not going to bed. But I'm going for 1.5Gb. :D

---

### Post by birddog165 on 2009-01-28
So this morning I didn't have classes, so I hacked my kernel for fun while I waited for breakfast.

Now [probably by coincidence] I was able to transfer 2.2Gb of music from the external to the internal with a speed of 18.8Mb/s.

I will not suggest anything until I have confirmed that my problems are over. Nor do I know how this would change anything. But I will keep everyone posted.

---

### Post by birddog165 on 2009-01-28
You gotta be kidding me.
I just did 17.8Gb of data at 20Mb/s.


I have no idea what's going on, but I'm not complaining.

---

### Post by Rich663 on 2009-01-29
So I am reading this thread because I have a Samsung USB drive that sort of has the same problem you were describing. It will mount fine after a system boot. I can access and read from it. As soon as I transfer data from my hard drive to he USB drive it disappears. That is it is no longer mounted and it won't come back. Move the drive to my WinTel laptop and the new data is there but incomplete or corrupted.
Put it back on the Ubuntu system and it is still AWOL till I reboot.

So what hack did you do to make it stay on solid?

---

### Post by birddog165 on 2009-01-29
> **Rich663 said:**
> So what hack did you do to make it stay on solid?

See I'm still trying to figure that out myself.
But I am proposing theories. Either:

1) It just suddenly started working
2) There was a USB conflict with Sun MicroSystems VirtualBox
3) I rebuilt the kernel

See rebuilding the kernel sounds all smart and whatnot, but I don't think that did anything. All I did was follow the online instructions that you can find at every website when you google search "Custom Ubuntu Kernel." Then I just played around in it, turning off things like amateur ham radio, and toshiba laptop support. If it made no sense, it went.

But I don't think that was the solution. I'm still trying to figure it all out, and I really wanted to say it was virtualbox, but I just am so unsure.

Anyways, I would have posted everything sooner, but I tried updating my video card and really screwed up the graphics and been spending every other minute the past 24 hours trying to debug that. But I'll keep posting.

---

### Post by birddog165 on 2009-01-29
I would almost suggest that you do some personal tests to find out exactly what makes the hard drive freak out. Transfer small stuff like I did and see how much you can do.

---

### Post by birddog165 on 2009-02-04
Well for anyone still following this:

I don't think it's the kernel anymore. I did this by performing a very easy task...
I started up and selected to use the generic kernel.
No problems.

I'm just gonna guess that something with virtualbox made it go mad.

Also, I am planning on doing a fresh install of 64bit Ubuntu, so I probably won't be posting on this thread too much more. This is because I want to do 64 and I screwed up my video card beyond repair. (But that's another story).

For anyone else who has this problem, I wish you the best of luck. Just try and look back to see if there was ever a time when your HDD worked, and try and figure out what you did to make it stop working. Many people complain that a computer messed something up, but a wise man once said to me
> Computers aren't smart, they only do what you tell them too. If something breaks, it's because you broke it.

Good luck World!

---

