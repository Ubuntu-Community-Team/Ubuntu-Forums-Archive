---
title: "Acer Aspire periodically hangs."
date: 2009-09-28
forum: Hardware
---

### Post by gloken on 2009-09-28
Hey, I've got a brand new Acer Aspire One with the Jaunty netbook remix on it. I've been finding that the computer will occasionally hang. The monitor will freeze, caps-lock lights, etc all stop working but the power light remains green. The only thing that continues to work is the mouse pad, I can move the pointer, but otherwise the desktop is frozen.

I've never encountered anything like this before, and don't know where to begin. It seems to happen when I'm working with multiple firefox or download windows, and has never happened at any other time. Could be related to network drivers?

Anyone have any ideas?

---

### Post by KingLear0 on 2009-10-09
I have no idea if this will affect your Acer or not, but it affected mine.

I have an Aspire One, the 751h model.  I was playing with Jaunty and Karmic, and a few other systems, installing, removing, and repartitioning a lot.  I noticed that my system started to hang after running for about 15-20 minutes.  The screen would freeze, the keyboard wouldn't do anything, but like you, I could still move my mouse around.

Reinstalling didn't help, but when I check my disks for consistency, Fsck found an error.  After it reported the error fixed and I rebooted, my computer no longer froze.  My assumption is that I had a corrupted sector, and my Acer froze whenever the computer tried to access that area of the drive.


So, long story short, you may want to run fsck on your drives and see if anything happens.

---

### Post by gloken on 2009-10-09
Hey, thanks for the response.

I actually resolved this by wiping the thing and running 8.10 instead. It's much more stable on the Aspire.

I was never able to discover what caused the initial problem.

---

### Post by diosif on 2009-12-13
Hello. 
I had the exact same problem with UNR 9.04. It happened when downloading (usually with DownThemAll plugin for Firefox) and when playing long flash videos. 
Recently i did a clean install of Ubuntu 9.10 and i have hang ups with blank screen and caps lock flashing. Frequency and initiating factors are the same as before. 
I've read about hardware problems, about wifi drivers, about fglrx problems but nothing that really convinced me since no solution proved universal. I hope someone can really identify the cause and provide a solution...

---

### Post by gloken on 2009-12-13
> **diosif said:**
> Hello. 
I had the exact same problem with UNR 9.04. It happened when downloading (usually with DownThemAll plugin for Firefox) and when playing long flash videos. 
Recently i did a clean install of Ubuntu 9.10 and i have hang ups with blank screen and caps lock flashing. Frequency and initiating factors are the same as before. 
I've read about hardware problems, about wifi drivers, about fglrx problems but nothing that really convinced me since no solution proved universal. I hope someone can really identify the cause and provide a solution...

In all seriousness, going to a more stable release is probably the best bet. I've had no problems since I went to 8.10.

I'm starting to think that I want something lighter than Ubuntu for the thing, but that's another story entirely!

---

