---
title: "New Ubuntu 8.10 user here with Graphics Issue"
date: 2008-11-12
forum: General Help
---

### Post by skymac on 2008-11-12
Hello All,

Thanks in advance for taking a look at my post. I just install Ubuntu and althought its going to be a learning process, I see it potential already.

First off Im running two Nvidia 8600GT 256mb Cards, SLI, but right now I have the sli un plugged.  Everything else is working fine but once I install the driver it says I should 177 I think, it restarts and im stuck with the command promt, no more gui, so im lost, haha...

I have tried, sudo dpkg-reconfigure xserver-xorg  but this does absolutly nothing for me, it asks me a couple of questions about my keyboard then throws me back to the command promt.  

So I guess im asking how do I revert back to the default drivers and second, how do I get nvidia drivers installed?


I have read on several google searchs but it seems like there are thousands of ways to do this but I just want the easiest and most pain free.

Justin

---

### Post by eternalnewbee on 2008-11-12
Hi there, and welcome to the Ubuntu Forums.
To resolve the issue of the driver, go to: **Main menu > System > Administration > Hardware Drivers**. I have no experience with two graphic cards installed, so be patient until a more experienced user replies to your post. If, after 24 hours, you still haven't got a reply, use the **Quick reply button** and type **"bump**" to move your Thread to the top of the list.

---

### Post by Newtothegame on 2008-11-12
Hey I had some problems as well with my gforce7200. But the administration and reconfifure fixed all my issues. 

Here are some links to some manual installs. Perhaps these will fix it. 

[https://help.ubuntu.com/community/NvidiaManual?highlight=((FixVideoResolutionHowto](https://help.ubuntu.com/community/NvidiaManual?highlight=((FixVideoResolutionHowto)))

[http://ubuntuforums.org/showthread.php?t=976272&highlight=installing+nvidia+drivers&page=2](http://ubuntuforums.org/showthread.php?t=976272&highlight=installing+nvidia+drivers&page=2)

---

### Post by skymac on 2008-11-12
I will try these in just a bit.  All I can do is get to the Command Promt, no more gui...

---

### Post by TreeFinger on 2008-11-12
did you run, 

```

dpkg-reconfigure xserver-xorg

```

in single user mode?

---

### Post by phidia on 2008-11-12
Treefinger, what you posted does not appear to be correct.

skymac, If you are still unable to get a gui/desktop boot in recovery mode and type "xfix" without the quotation marks. Reboot. That is suppose to get you a usable gui.

Some hardware combinations have problems with the new way of configuring your xserver.
Unfortunately 8 & 9 series nvidia cards fall in that realm. I would pull the non used gpu but that's up to you. Some people recommend installing the envyng package or you could try installing that latest driver from nvidia.

I suspect from some threads I've read that the latest kernel is having issues with the nvidia proprietary driver. See the ubuntu [nvidia video wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") and the [x wiki]("https://wiki.ubuntu.com/X/Config").

---

### Post by skymac on 2008-11-12
Says   xfix can't be found

---

### Post by skymac on 2008-11-12
Yes I ran

that above code and also tried XFIX, I think im just going to reformat, and say screw it, haha... just going to run in 2D mode, only other thing im gonna try once I get it reinstalled is downloading the Nvidia driver from there and installing it like they say on their website.

---

