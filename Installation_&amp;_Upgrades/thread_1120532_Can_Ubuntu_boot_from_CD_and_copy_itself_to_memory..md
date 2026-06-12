---
title: "Can Ubuntu boot from CD and copy itself to memory."
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by prioryjim on 2009-04-09
Hello, this is my first post, I have search the forums but there doesn't seem to be a relevant post, so...

To save reading below the question is can Ubuntu boot from CD and copy itself to memory.

I aquired a Ubuntu CD some while ago. I have not used it much but it seemed to work OK.
I assume it boots from CD and runs off CD, as the CD seem to be accessed most of the time.

Recently I saw a Slax CD that had an option to boot from CD and copy to memory. Unfortunatly it didn't like My Dell/Intel video card and X would not start up, Ubuntu seems OK.

However given I have 4G memory the copy and run in memory option seemed to offer many advantages.
1) Does not affect my Vista ( am I allow to use that word ? ) install which took an amazing amount of time to get working ( well nearly working ).
2) Possible speed gains.
3) As it runs clean every time it has minimal chance of being affected by viruses.

Thanks
Jim

---

### Post by JackH79 on 2009-04-09
I don't really understand your question. If you do start ubuntu (or any other liveCD for that matter) from CD, it does run from your CD and yes, it uses your computer memory to run. But the moment you shut down your computer, your memory is lost - and therefore your ubuntu. There is no way to "install" any form of software into your RAM.

If, on the other hand, you mean whether it's possible to install ubuntu on to some form of memory (USB) stick, flash, or external hard drive and then boot it from there then yes, it is possible.

Check out:
[http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/)
or
[http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

Hope that helps

---

### Post by prioryjim on 2009-04-09
No the SLAX option copys the CD rom contents to RAM and runs from there. It doesn't run from CD.

With the the Ubuntu CD when you click an application to run the CD winds up and the application is run from CD.

But with the totally in memory option you can remove the CD once the image is copied into memory. The system runs totally in memory.

If needed you can still mount USB and Hard drivers.

Thanks
Jim

---

### Post by JackH79 on 2009-04-09
Okay, sorry, got it now. Never heard of such an option for ubuntu. But that's probably due to its rather large size compared to slax. But the problem of losing everything once you switch off your computer remains (i.e. you'll lose all settings and changes you may have made).
If I were you and you don't want to fiddle around with your Vista, I'd install ubuntu on an external drive and run it from there. Thus you'll have at least the possibility to run your OS to your specifications. But that's just me ;-)

---

### Post by upchucky on 2009-04-09
Yes the ubuntu cd/dvd is called a live cd, meaning it sets itself up in ram, and gets data from the cd when it needs to, it does not install to or affect the existing hard drive of the pc unless you actually select install to hard drive when booting the cd.

you have the option to keep your windows and be able to run ubuntu too.

im pretty sure hes wanting a dual boot setup where windows is still there and not disturbed, with the choice of either booting into ubuntu or windows.

with this in mind, some dual boot setups seem to fail where neither os will boot, or one or the other will boot.

The seemed failure is not a failure at all. the bootloader just needs some missing information to be able to boot either os. this is easily fixed.

in this situation, all the windows stuff is still there, as well as the new ubuntu os.

in other scenarios the ubuntu install can not figure out how to set up the video to provide a graphical display, this is not a ubuntu problem, but a problem of the vid card manufacturer still brainwashed by the Microsoft way of doing things thus they have not written complete support for Linux yet.

if the Live ubuntu cd does boot up when booted from the cd-rom, and you get a graphical display, then it will also work when actually installed onto the hard drive. with that said, sometimes all that is needed is a file edit to get the display working.

I hope this answers your questions, and kinda prepares you ahead of time of what you may or may not run into.

welcome to the open world.

---

### Post by JackH79 on 2009-04-09
Very true. I would go with a dual boot (worked a breeze on my  (vista + ubuntu 8.10)) but he can still put it on an external drive if he doesn't want to, or feels uncomfortable, messing around with his partitions.
I think that was the initial worry.

---

### Post by prioryjim on 2009-04-09
Well one of my requirements is for a secure mechanism for performing financial transactions.

I worry greatly about if my Vista system is secure, even with my Virus scanners etc.

Now I am not a security expert, but...
If the system boots from CD and runs in memory and has no USB or harddrive and does not allow remote logins, then the possibility for viruses is drastically reduced.

If then you don't surf the net but go directly to your financial site security must be maximised.

I guess the Ubuntu CD fits the above, but is a bit slow runnig from CD.

Thanks
Jim

---

### Post by upchucky on 2009-04-09
After seeing your replies to those that responded, yes ubuntu can work from ram completely,  it involves configuration changes so it know where to load and save files to.

to have such a setup is risky tho, the slightest power glitch renders ram scramble. as Linux places markers for the processor to come back to while it is busy doing something, if that something is a kernel write, down it goes. if that something is a pet project that was just was loaded into ram, goodbye. any inopportune event can crash and permanently damage the os and or files.

---

### Post by prioryjim on 2009-04-09
Not really bothered if the system gets trashed.

And I would have thought that most power glitches that corrupt system ram run the risk of trashing the system regardless.

Anyway I think just running from CD will fit my bill.

Must be better than trusting my Vista system with all it's potential viruses and key loggers.

Thanks
Jim

---

### Post by upchucky on 2009-04-09
Microsoft just announced that Vista users will have a free upgrade to Windows 7, and Windows 7 will be downgradeable to Xp
XP users will have to pay to upgrade to Vista then get the free upgrade to Windows 7.

When I read this and was done shaking my head, I immediately thought of a reason that Windows 7 would be made downgradable to XP,
Windows 7 fully patched was brought down in the hacker challenge within 20 minutes last month. A fully patched Mac pro was hacked in ten seconds at the same event. I have to admit though the Mac was hacked while it was running software that was designed to run in windows.

Last year Vista fell after a day, and Mac fell after 2 days.

I suspect that a Linux box was not invited to the challenge this year, because last year the Linux box was the only system left standing after the dust cleared.

---

### Post by prioryjim on 2009-04-09
Very worrying.

I have suggested in the past, although not on this forum, that the banks/credit card companies could do a lot better for a very small outlay.

If the banks provided their users with a secure boot CD that only contacted the banks own secure servers, no wandering off on the net.

Then the amount of keyloggers and viruses would be virtually eliminated.

The boot CD could be based on Linux but may not need to be that complex. Just a user interface and some secure comms to the banks server.

A while ago there was a lot of very small CDs around. Perhaps these could be used as they would probably fit the pocket better.

Thoughts ?
Jim

---

### Post by dandnsmith on 2009-04-09
That would pose the problem for the banks of having to have their offering work on all hardware, under all circumstances of networking.

No bank is going to take on that task - it would be easier to provide each user with a secured PC (and then it would only fail on the networking)

---

### Post by prioryjim on 2009-04-09
I don't think it would be that big a task for the "banks" to come up with a stratergy. Don't forget they have unlimited resources ( well did have and probably still do! )
Ubuntu runs on most hardware.
Like Ubuntu they would have to state what the basic hardware requirements were. If you PC didn't meet that then you don't get secure banking !

---

### Post by snowpine on 2009-04-09
Hi Jim, 
I do understand the question. :)

I have used several distros that have this capability. Usually it is accomplished by adding the "toram" option to the boot options. On the Ubuntu live CD, you can specify additional boot options by pressing one of the function keys, but I don't know if Ubuntu supports the toram option.

Distros that I've tried where toram works include AntiX and Sidux (which is very similar to Kubuntu in many ways). Tiny distros like Puppy and SliTaz have the toram behavior by default, since they are so small. I personally like to use a Slitaz live CD for online banking.

---

### Post by prioryjim on 2009-04-09
Thanks
Slitaz looks like it might fit the bill.
Looks unclutered.
Will give it a try over the weekend.

---

