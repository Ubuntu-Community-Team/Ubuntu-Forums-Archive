---
title: "MSI Motherboard Issues"
date: 2012-08-07
forum: Hardware
---

### Post by BlackWolfe on 2012-08-07
I am currently using (and was introduced to) Ubuntu 12.04 because of what I believe are issues with my MSI K9N2 Diamond motherboard. When I was using Windows XP SP3, I get getting "so-called" hard-drive failures (WD 1 TB drives) and returned the original two drives that I bought when I built the computer. While I understand that hard-drive failures do occur, I had the same "failures" with both replacement drives, as well as a 1 TB WD MyBook drive that I had cloned as a back-up to my C: drive. After MSI completely blew me off because the MB was "just" out of warranty, I checked around with some of my fellow builders, and apparently MSI has fallen out  of favor over the past 5 years. Which leads me to my question (sorry about all the lead-in but I wanted to cover my bases).

I'm using Ubuntu 12.04 off of a WD Passport (external) drive, which I have been using for it since I first began having internal hard drive issues. Is it possible that there is something wrong with the Motherboard that not only caused false (SATA) hard-drive reading failures, but that is now also causing External Hard-Drive reading failures as well? 

I'm back to using the second-update version of 12.04, and even then I literally have to unplug the power from the back of my computer (which I'm assuming resets something in the MB) and then when I reboot go into the "previous versions" of Ubuntu, sometimes using the recover, in order to get it to boot properly, the main issue in booting being that my simple (to me) Logitech track-ball mouse freezes every time unless I go through the above-mentioned routine.

Any answers, help or suggestions, as always, are greatly appreciated.

---

### Post by Mark Phelps on 2012-08-09
While it MAY be possible that there is a firmware problem in the SATA controller logic on the MSI motherboards, that's very unlikely.

I would tend to point to WD as the problem.  I've had more of their brand drives fail me in the last five years than all other brands combined.

What I would suggest for your Passport drive is the following:
1) Hook it up to a Windows PC (why? -- see the next line)
2) Download and install Data Lifeguard from WD.  This is a diagnosting routine that only runs in Windows -- but it can be used to scan your drive for errors.
3) Run Data Lifeguard to check your drive.  It can take HOURS.  The last time I ran it on one of my drives, it took over six hours to complete.  But, it will attempt to find and fix errors on the drive.

If the drive checks out (connected to another PC) and then encounters problems with the MSI motherboard, then you know there are drive controller problems with the MSI motherboard.

---

### Post by BlackWolfe on 2012-08-14
> **Mark Phelps said:**
> While it MAY be possible that there is a firmware problem in the SATA controller logic on the MSI motherboards, that's very unlikely.

I would tend to point to WD as the problem.  I've had more of their brand drives fail me in the last five years than all other brands combined.

What I would suggest for your Passport drive is the following:
1) Hook it up to a Windows PC (why? -- see the next line)
2) Download and install Data Lifeguard from WD.  This is a diagnosting routine that only runs in Windows -- but it can be used to scan your drive for errors.
3) Run Data Lifeguard to check your drive.  It can take HOURS.  The last time I ran it on one of my drives, it took over six hours to complete.  But, it will attempt to find and fix errors on the drive.

If the drive checks out (connected to another PC) and then encounters problems with the MSI motherboard, then you know there are drive controller problems with the MSI motherboard.

I appreciate it Mark. I've run that program on another computer on all the internal HDs that supposedly failed on me before I sent them back and they actually checked out according to WDs program. Still, I sent them back because the warranties were good and even the best diagnostic software can miss things. As to the Passport, I ran WDs Lifeguard on it when I first started having problems with the updates of Ubuntu taking me either to the "Version Load Option" place of woe or in the beginning just no where in particular. The drive itself checked out not only using WDs diagnostics but also using some older, more thorough tools I got from a tech friend of mine a few years ago. Those don't care what "brand" HD you have (although they do have brand specific checks) they just check out the functionality of everything. The Passport drive itself is in good working order and has no problem booting up on that other PC, or on my tech buddies PC either. Today, I still couldn't get it to load with my mouse not freezing up until I unplugged the machine, turned the power switch off/on, then plugging the power cord back in and turning the machine on from a dead-stop. 

So again I'm wondering whether or not it's Ubuntu itself that's playing havoc with the boot-up, or the slim but still possible reality that my MOBO is somehow giving me the finger, especially since the internals were of course plugged into the SATA jacks on the board while the Passport is plugged into a USB 2.0 jack on the outside of the case. I don't know enough (yet,  hopefully) about how the signals run from each particular jack and where the particular controllers are (or at least how to find them) to take the board out and put it under the lamp to see if I can visually see anything FUBAR-ish. 

Have you heard anything about MSI putting out a run of bad boards from 2007-2010? I was on the hunt for info and saw an older discussion about that very thing. Can't believe everything you read but I do know that since I bought this board when it was the BBD it has since gotten horrible reviews from a lot of geeks, as well as normals. Again I appreciate your help and any advice you have. Thanks.

---

### Post by BlackWolfe on 2012-08-24
Finally went all Wolverine on this issue. I took everything, including the power supply, out of this machine. Hooked everything up on an "out of the box" jig I built out of balsa (be VERY CAREFUL if you even think about taking everything out of your grounded case, it's dangerous and can fry your components as well) and started with the old stand-by of "take out the memory and then put the power cord back in and turn it on to see if you get a beep/sound out of the motherboard speaker". Nothing. So, if I'm correct in my assumptions that would mean the motherboard itself is FUBAR. Please, if you have a different opinion about my results post it here. I've been building systems for over a decade but that doesn't mean I know close to half of what we as a collective know about them. And I'm still green as Kermit about Ubuntu and Linux. Looks like I'll have to save up for a new Mobo. F(#$! >:|

Thanks for your help here, I really appreciate it!

---

