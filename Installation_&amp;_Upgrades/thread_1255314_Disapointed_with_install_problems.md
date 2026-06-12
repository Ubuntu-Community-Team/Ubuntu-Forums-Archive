---
title: "Disapointed with install problems"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by AshmanE on 2009-09-01
So, I swore off Linux and it's many variations 10 years ago when I got tired of having to compile a kernel every time I changed a piece of hardware.
 
But the hardcore geeks at work swore up and down that Ubuntu was "totally user friendly" so I decided to give it a try again.
 
I must say that I'm extremely disappointed.
 
I put in the install CD into my IDE DVD-ROM drive and booted to it, chose the install option and watched as it bombed out and left me at a (initramfs) prompt. Lovely.
 
I managed to troubleshoot that as a problem with IDE by trying the install on a USB drive which got me further. (Funny that the system handles USB CD-ROMs with flying colors and can't seem to handle IDE from a standard i845 Intel chipset which is probably about 300x more prevalent.)
 
But the IDE is still giving me problems because now when I get to the partition menu, there are no drives listed even though the BIOS has my 120 Gig Western Digital drive listed.
 
So, I've gone through about 20 different "boot flags" trying to get the stupid thing to recognize that there's a drive there (pci=nomsi, all_generic_ide, yadda, yadda, yadda.)
 
No joy.
 
So after hours of screwing around with it, I said, "the hell with it" and threw in my DVD for Windows 7 RC 1. Maybe 40 minutes later and it's running like a champ. No boot arguments. No errors. Just butter...
 
I'd love to run Linux because of it's improved efficiency and lower overhead, and I want it to work, but I can't see how things have gotten any better on the "ease of use" front in the past 10 years if I have to search for needle-in-a-haystack boot options in order just to get the thing to install. 
 
Can anybody tell me why the Ubuntu install won't recognize a standard Intel chipset that is in thousands of machines all over the world?
 
Color me not impressed.

---

### Post by Swagman on 2009-09-01
You should feel pleased

**YOU'RE** the one in a million !!

/sarcasm

Sorry to hear you're having problems

---

### Post by AshmanE on 2009-09-01
Thanks for feeling my pain.
 
/sarcasm  ;)
 
Is there some way I can troubleshoot my issues with IDE?  Is there any repository for this sort of information other than searching the forums?
 
Like I said, I really don't want to be forced to use Windows, but if I can't get Ubuntu installed, then I guess I'll have to try a different flavor of Linux or resign myself to Win7.
 
Sorry for venting. I guess I just expected things to be a bit easier considering my colleagues' glowing endorsement, but maybe that was an unrealistic expectation.  I'm not opposed to doing some extra work to get it installed, but you'd think that it really shouldn't take hours of research...

---

### Post by Mark Phelps on 2009-09-01
Understand your frustrations.  The expectation with any product is that over time, it gets better, so it's not surprise that folks who tried Linux variants years ago expect that the most current version of Ubuntu will simply install and "just work" -- and are very disappointed when one or both of these fails.

I've been using various flavors of Linux for several years and found, of Ubuntu, that 8.04 had the most success on all my machines.  Since then, 8.10 and newer won't work well on my tablet PC, also won't provide full-screen displays on other legacy laptops, and now with 9.04, for the first time in years, I've had to do without ATI restricted drivers on my desktop.

Which is why I strongly suggest two things to folks:
1) Try the LiveCD first.  Whatever doesn't work there is going to range from trivial to impossible to fix after install.
2) Try other distros.  Since Ubuntu 8.10, I've had more success with other distros such as OpenSuse and PC Linux OS.

There are enough alternatives out there that, if you try different ones, you're likely to find a distro that "just works".

---

### Post by scratman on 2009-09-01
On the single occasion I have had an initramfs error when installing Ubuntu from CD, it was due to a failed burn.  I strongly suggest checking the MD5 sum of your disc, as that may be your error.  I'd personally verify the checksum of the ISO you downloaded too, just to be on the safe side.  You can verify the checksums with ubuntu.com.

Failing that, there are other ways of doing things.  It is possible (although not a popular solution) to install Ubuntu from Windows.  Boot into Windows, poop the CD in, and run Wubi.exe from the CD.  You could also get Ubuntu on any pen drive > 2gb.  If you don't have one to hand or spare, mention your intentions to the guys at work who recommended Ubuntu to you, and I'm sure you'll have a bootable pen drive with Ubuntu on it by the following morning ;)

Any further problems, please give us a shout.  And remember that 99.9% of the people who reply on these forums are friendly and helpful, and  99.9% of the questions you have in the first few weeks with Ubuntu have probably been asked before.  Just do a quick search when you hit trouble.  You'll almost certainly find what you're looking for.

---

### Post by buseness on 2010-03-12
Don't bother. Ubuntu will not work with an Intel I845 chip-set! Nor will your on-board video work ether. I'm using it right now and the only drivers I have been able to find are here [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/) and the directions make absolutely no sense whats so ever, 

 This is very disappointing for me because I need this computer for my work as a graphics designer and I love the Graphics Programs that Linux has. Because I used more money than I had to put this computer system together, Ubuntu looked like it was heaven sent. But because I can't find the proper drivers to run the video - this makes the computer randomly freeze without warning and it looks like I will be forced to shell-out another $100.00 for a "Windows XP Operating System." So if anyone knows where I can get drivers for this thing, please let me know. I'm using a 310B Gateway 2500 MHZ CPU with the I845 Chip-Set.

---

### Post by neySto on 2010-03-12
AshmanE: 'when I get to the partition menu, there are no drives listed'

I have the same problem as AshmanE in the partition menu there are no drivers listed. I dont know what to do.
I am new to Ubuntu, this is the first time I've tried it on my computer.

---

