---
title: "Nvidia 8300. Driver problem or upgrade card?"
date: 2013-12-14
forum: Hardware
---

### Post by goemonburo on 2013-12-14
I have been struggling with this issue for weeks, thought at first it was just a problem with Fedora but the same thing is happening now with a fresh install of Ubuntu 12.04.  I have a fairly old Dell Inspiron 530 with an Nvidia graphics card (8300, 128ram).  It worked fine under Fedora 11, but when I upgraded to 18 it had this weird issue where everything's fine until you log in, then X just seems to go haywire.  Mouse freezes for minutes, windows don't render, or they render so slowly that you have to leave the system going for 10 minutes and come back.  Sometimes at random times it just spits you back to the login prompt, which will be responsive and problem free.  I thought it was just Fedora but now the exact same thing is happening in Ubuntu, and I've tried both the non "nomodeset" and the "nomodeset" boot options.  

I took out the graphics card and it was totally covered with dust, so thick that I could easily imagine that it overheated -- cleaning out the card with compressed air however had no effect.  My only thought now is to maybe get a new graphics card, but I'm loathe to pay $50 bucks or maybe more (can't get a totally new card because the computer's so old it won't support it) only to find out that I'm exactly where I started...with some OTHER issue (drivers? software? other computer hardware?) going on.

If this IS a drivers/software issue, can someone tell me what the steps would be to fix it?

If it does look like hardware, am I right to imagine that a new graphics card might solve it?

Or should I just bite the bullet and go the easy route and get a new system, knowing that it may have other issues and incompatibilities that are equally frustrating?

Thank you in advance for help.  Please offer clear instructions if possible, as I'm less familiar with Ubuntu than Fedora and full pathnames help tremendously...that sort of thing.

---

### Post by mörgæs on 2013-12-14
How does it work in a fresh install of Lubuntu 13.10?

---

### Post by goemonburo on 2013-12-14
I haven't tried.  I want 12 because of the long term support.  But I could try 13 at this point.  My system is quite old, though, so I'm not sure that it needs the latest and greatest.  I think it's a 2008 vanilla Dell, so it shouldn't be something totally obscure that needs bleeding edge updates.  But yes, if there aren't any other suggestions I'd try 13 just to see if it makes a difference.

---

### Post by mörgæs on 2013-12-14
It was mainly about trying Lubuntu, not Ubuntu.

---

### Post by goemonburo on 2013-12-14
Sorry, didn't catch the L.  I'll look at Lubuntu...but still hoping for any thoughts about whether this might be solved with a new graphics card...anyone?  I think the new subject line doesn't really offer much to someone scrolling down the threads, too.  Any chance of returning it to "is this problem caused by a graphics card issue" or something similar?

---

### Post by goemonburo on 2013-12-14
Another thing I didn't mention is that if I connect to the machine via VNC (this was before, in Fedora) without logging in via the actual desktop, it was fine.  No problems.  It was only when I made a physical login and was sitting in front of it that it acted weird.  I haven't yet been able to get VNC going on the new Ubuntu install.  But maybe that's also a clue?  Works fine in a virtual display but not display:0?

---

### Post by mörgæs on 2013-12-14
"This" in the title makes no sense, but I have changed it again. 

Third time: Your problem is likely Ubuntu, not the card. 

Signing out.

---

### Post by goemonburo on 2013-12-14
Thanks for changing it back!  I appreciate it.  Have a fresh download of Lubuntu and will give it a whirl.  Also did some digging and found a number of other folks out there with Dell 530s with failed Nvidia cards, so I'm ordering a different card too.  If Lubuntu works, does that mean I won't be able to run Kontact or Kmail or any of those applications?

---

### Post by goemonburo on 2013-12-14
Okay, so I installed Lubuntu and sure enough, after a few minutes of hopeful waiting, the same thing happened.  I took a screenshot but I guess the forum disallows uploads?  If anyone wants I can send it to them for a look see.

---

### Post by Random-penguin on 2013-12-14
Does this pc have onboard graphics? If so try swapping the lead from your graphics card to the onboard motherboard. It may not be able to run fancy graphics but at least you could tell if it is definitly the graphics card that is dead. By the way it is always advisable to regularly check for dust and use the compressed air cans to remove it. Keeping every thing clean will extend the life of your hardware.

---

### Post by goemonburo on 2013-12-14
Yes, lesson learned about compressed air: the dust was so thick that the fan had basically carved a hole in it.  So I would not be at all surprised if something got too hot and cooked.  My board does, I think, have onboard vga graphics.  But I'm not sure my monitor can run vga.  I guess that's worth a shot.  I'm not trying for fancy graphics with this system, but having windows render right would be nice.  I did find that Lubuntu remained responsive despite the wacky display issues...whereas Ubuntu and Fedora both slowed to a crawl.  Anyway, yeah, worth a shot.  (Goes off to dig a vga cable out of the dumpster somewhere...)

---

### Post by Random-penguin on 2013-12-14
Good luck with that and at least you potentially will have a system that works. Thinking about it, if your onboard graphics is intel, then you will probably still get a reasonable result... I have acheived such in the past. For older hardware it is always advisable to go for lighter desktop managers such as LXDE as used in Lubuntu. It will make your pc run much swifter with the limited resources available. 

Distrowatch will be your friend in exploring the many alternative distros available to you. I personally like Crunchbang as it is incredibly light and fast. Not that I'm wanting to steer you away from Ubuntu of course! It's just that other options may serve you better and save you the expense of a replacement video card just before the Holiday season/christmas.

---

### Post by goemonburo on 2013-12-15
Swapped out the card for the onboard one and haven't had a problem the whole day.  Runs fine.  So good that I'm now wondering if I should have ordered that new card after all...but it's on the way.  Hopefully it will work when it arrives!  But if not, at least I have a system that's usable for the time being...thank you for all the help!!

---

### Post by goemonburo on 2013-12-15
And I am really liking Lubuntu, by the way.  I'm not a fan of all the razzle dazzle stuff.  I just want a stable system that works!

---

### Post by oldfred on 2013-12-15
With nVidia you need nomodeset. I have a 9600GT and have needed nomodeset since they made some change in the kernel.  I think it was back with 10.10. I now have to use nomodeset on every live installer boot and any boot until I get the nVidia proprietary driver installed.

I use e on grub menu, scroll down to linux line and replace quiet splash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Yellow Pasque on 2013-12-15
goemonburo, your description of what driver you tried is a bit hazy. If you tried the open-source nvidia driver (named 'nouveau') and the proprietary nvidia driver, and experienced the same result with both, we can be relatively certain it's a hardware issue since a different GPU works okay. It would not surprise me if you overheated the GPU or its memory by letting 5 years of dust accumulate, especially if it was a passively-cooled card.

---

### Post by goemonburo on 2013-12-15
Regarding drivers, good question: I didn't say specifically what I tried.  I tried a standard install of Ubuntu, then of Lubuntu.  For Fedora (which I was using for several months prior to getting fed up) I tried both nouveau and the nvidia drivers with the same problem.  With Ubuntu, I tried only whatever's standard, but with both the default and the "nomodeset" option and neither worked.  In Lubuntu, I only tried the default, which had the same issue.  But when I switched to the Intel graphics on the motherboard, everything worked fine.  

I probably COULD try putting the proprietary drivers on there instead of nouveau, which I've never really been happy with.  But I think at this point I'll do that when the new card arrives.  Apparently Dell 530s have a history of the graphics card failing, and thus, at this point, I'm okay replacing it...then doing the effort needed to make the NEW card work right rather than investing time and energy and frustration into a possibly broken card.  It's my fault for not cleaning it:  I should have taken a picture.  The dust was incredible.

---

### Post by goemonburo on 2014-01-25
Just closing this out:  a new graphics card solved it.  Zero problems since putting it in.  Whew.

---

