---
title: "Slow boot and major lag after swapping Ubuntu hard drive for a Windows hard drive"
date: 2015-08-14
forum: Hardware
---

### Post by Old_Printer on 2015-08-14
Hello.

I've just started using Ubuntu in the last two weeks. I've installed it on two machines, one of which usually doesn't go on-line. In the past, I have had several hard drives with various versions of Windows that I can swap out and boot up when I need a particular platform with certain software applications. This is the machine that's troubling me. I had 14.04 on it until yesterday evening, now it has 15.04. Everything works great when I'm using Ubuntu. I've even installed VirtualBox and have both WinXP and Win7 up and running in it, both using the VirtualBox Graphics Adapter for full screen. Pretty cool.

Here's what's happening, and I'm curious if anyone else experiences this as well. When I shut down my off-line machine with Ubuntu, 14.04 or 15.04, swap out the hard drive for a hard drive with Windows XP, my machine takes about 5 minutes just to get to the desktop. It then takes several more just to be able to move the cursor. In the past, when I was swapping out Windows hard drives for other Windows hard drives, this never happened. With the slow boot, I've even removed the RAM after powering down Ubuntu, reinstalled it, then tried the XP boot again. What could be dragging down my XP drive when I want to use it? The 14.04 install was 32 bit and the 15.04 install is 64 bit. Both versions work great on my machine.

This slow boot and lag problem does eventually go away, only after about four reboots and / or half an hour.

When I get to understand more about shared folders with VirtualBox, I probably won't need to go back to my Windows drives near as often.

Any help would be greatly appreciated.

Thanks,
Old_Printer

---

### Post by efflandt on 2015-08-15
While worm booting (reboot) can sometimes leave certain hardware in a state that the other OS cannot cope with, if you are swapping physical drives and doing a complete shutdown before cold booting the other OS, I would not expect that to be an issue. It could just be that you get used to Linux booting quickly, so Windows seems very sluggish to boot. My Win8.1 PC at work takes anywhere from 5 minutes to 20 minutes after getting to the desktop to settle down from accessing its drive 100% for whatever Windows is doing including possibly checking for updates or in some cases extensive anti-virus scanning, sometimes just when waking it from suspend, not cold booting.

And when (just the Linux partition of) my hard drive went bad at home I used Acronis to clone its Windows partitions file by file instead of sector by (possibly bad) sector, so Win7 files may be in directory order instead of the order they were in originally, which along with Windows updates that modified files in place, may have resulted in fragmented system files that defragging does not touch. Because when I boot Win7 it takes a very long time seeking all over the place before it boots, compared with seconds to boot reinstalled Ubuntu (which was 64-bit 12.04 then and 14.04 now).

Or it might just be a matter of perception and unless you actually timed it, the slow boot of Windows seems slow until you do it a few times (or maybe is faster after recently checking for updates or doing any malicious software scanning during boot).

---

### Post by Old_Printer on 2015-08-15
Thanks for the reply, efflandt. I really appreciate it.

I understand what you mean about getting used to fast Ubuntu, only to have to go back to a slower OS. A person's perception can become a bit skewed at first. After my post on this board I started looking at my RAM. I may have a mixed pair, which is causing me to report 3gb instead of 4gb. I never noticed it before, so something must be on the blink as of late. The problem, if it does exist, certainly doesn't bother Ubuntu. It's an ASUS MB. I never would have thought things like this could crawl up someone's sleeve, straight to high heaven, but I guess they can. I like a fast OS. I'm going to dig through my parts drawers and look for a matching stick of RAM, otherwise I may head to the yellow tag place to buy some.

I read another post here early this morning about being able to take a Ubuntu hard drive to other machines. I nearly fell off my chair. I have some favorite machines sitting around gathering dust. I may just have to give them a try.

Thanks again for the reply.

Old_Printer

---

### Post by Bucky Ball on 2015-08-15
Off-topic to what this thread is about, but the only thing you need to be aware of when chucking a Ubuntu drive into another machine is wireless and graphics drivers. If they are not in the kernel already you will need to install them for that machine. That should be easy enough, but means it is not always as easy as just shoving in the disk, booting from it and voila, there's Ubuntu. :)

Everything else should work fine though and, with any luck, the drivers for the wireless and graphics hardware present in the machine will be part of the Ubuntu kernel already.

Carry on ...

---

### Post by Old_Printer on 2015-08-15
Thanks, Bucky Ball. I appreciate the reply.

Old_Printer

---

