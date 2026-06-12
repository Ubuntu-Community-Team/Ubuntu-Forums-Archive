---
title: "Update broke everything"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by VanS on 2006-10-09
First off, I am not a novice computer user by any means, but I am a bit sketchy when it comes to Linux, and am pretty new to Ubuntu.

I installed Dapper for i386 off of the install CD onto my HP zv6000 laptop.  It took me a little while, but I got everything working.  I had 3D acceleration and Wireless internet all working great, even had Compiz working perfectly.  Then, along comes this "You have updates" thingy in the corner of the screen.  I, being a good little user, install said updates.  I reboot and, lo and behold, nothing works anymore.

My hardware acceleration is gone, and so is my wireless.  It'll still boot to the desktop, but without wireless it's about as usefull to me as car with no engine.  Is this a common problem with a common solution, or am I just up a creek here?

Here's what I was using for my hardware:
Broadcom Wireless w/ ndiswrapper
ATI Radeon Xpress 200m w/ binary drivers (8.28.something I think...I'm in windows right now and didn't think to check when I rebooted.)

Please help...

If you need any more info, I will be glad to provide it.

---

### Post by koshari on 2006-10-09
if you had a compiz session, log out and log into a gnome session and see how it goes, 

the compiz packages are generally svn so one advantage is rapid development however on the flip side is breakages may occur.

as for the wireless, i cant see whay that would fail, 

you didnt do a dapper->edgy update did you?

---

### Post by IoCaster on 2006-10-09
If it was a kernel update then you probably have to reinstall the drivers. Once you reinstall and reconfigure you should be back up and running again.

---

### Post by eggdeng on 2006-10-09
I had the Compiz part of this problem with the last batch of updates (including kernel update) & have seen in the forums that the same thing has happened on at least one occasion in the past. 
The solution seems to be to reinstall the drivers but it would be nice if someone would explain what drivers & how? (My card is an ATI Mobility Radeon X1400.)
Rapid development is no excuse for having half-baked updates screw up a system the user has put a lot of work into to get working the way he wants. With this sort of carry-on, who needs virus?

---

### Post by VanS on 2006-10-09
Yeah, there were kernel updates involved.  I had a feeling that I might need to reinstall the drivers, but have not had any success in doing so.

I can boot into a compiz session, but none of the effects function.  I'm pretty sure that this is just the result of failure of 3D acceleration, not compiz itself.

Can anyone tell me if I have to completely remove the drivers to reinstall them?  How do I remove Ndiswrapper and the ATI Binaries?

Ugh.  I really like linux, but sometimes I doubt that I'll be able to give up windows entirely.

---

### Post by koshari on 2006-10-10
> Rapid development is no excuse for having half-baked updates screw up a system the user has put a lot of work into to get working the way he wants.

while i agree with your sentiment, it will always be a problematic running alpha software and having automatic updates.

---

### Post by koshari on 2006-10-10
> How do I remove Ndiswrapper and the ATI Binaries?

lets concentrete with one problem at a time, and if you need your wireless going to download updates i suggest that be the one to solve first.

---

### Post by eggdeng on 2006-10-10
Just on the compiz side of this, I don't think it's a 3d acceleration problem. You can check by typing 'glxinfo' in a console; if you see a line which says 'direct rendering: Yes', it's OK. A prettier alternative is 'glxgears'.
I have started another thread 'update broke compiz'on this. There's stuff there about how to go back to the previous kernel which you might find interesting.

---

### Post by eggdeng on 2006-10-10
Correction to my last post. I have just realised that although I have 3d acceleration under gnome, it isn't available under xgl. 

glxinfo gives:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No

I think this pins the problem down. Any ideas on how to fix it?
 
Re koshari's comment, it would be nice to have a system restore option, otherwise keeping your system up to date is a risky business in the current situation.

---

### Post by VanS on 2006-10-10
I'm sorry I forgot to mention this, but I already know that my direct rendering isn't working, which is why I said that I believe that 3d acceleration is the problem.  Actually, I haven't even bothered with trying to fix aiglx/compiz yet.  I am mostly focusing on the wireless.  

It's actually kind of annoying, because I have a full time job and am also a full time student, so I can't dedicate a whole bunch of time to fixing linux when I have a boring but fully functional copy of windows running on the same machine.

I'll check out that "update broke compiz" thread.  Moving back to the old kernel sounds like the most universal solution to me.

On that note, is there any way to "roll back" updates, windows style?

---

### Post by Mimsy on 2006-10-10
> **VanS said:**
> Yeah, there were kernel updates involved.  I had a feeling that I might need to reinstall the drivers, but have not had any success in doing so.
...
Can anyone tell me if I have to completely remove the drivers to reinstall them?

To my knowledge you shouldn't have to. What happens if you try to reinstall the drivers just the way you installed them originally?

/Mimsy

---

### Post by koshari on 2006-10-11
a good tip would be to boot of the dapper live disk, install ndiswrapper to the image drive, than ```
dmesg
``` ans save the output.

compare that to the hdd version installs dmesg, and it may give some hints as per whats not happening, 

my wireless works on dapper but is broken on edgy, but thats of cos its on my development box and not my anchor.

---

