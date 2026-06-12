---
title: "Ubuntu Crashes at Boot after driver installation"
date: 2009-10-26
forum: Hardware
---

### Post by .:Justus:. on 2009-10-26
I recently installed a driver that was meant for amd/ati graphics cards which supposedly made it possible to fully take advantage of 3d graphics blablalba.

So after installing it, I did a reboot, as always.
But as the splash screen is about to load, the whole screen turns into a mix of crazy colorful lines and some bits of the computer startup screen (where you can choose to enter bios and stuff like that)are visible.
And in the corner there is a purple/blue messed up ubuntu logo leftover from the splash screen...
Whats going on?
I can enter the terminal in recovery mode, but I have no clue how to resolve this problem!
Help please :D
Thanks in advance.

---

### Post by Mr_Wonderful on 2009-10-26
Im experiencing exactly the same problem, Ive been having a little look about and it looks asthough there are some issues with Jaunty and older ATI graphics cards..... being an absolute newb I have not figured out how to fix it yet (nor have I tried very much due to an amazingly messy weekend) I shall keep you updated when and/if I make any significant progress though and shall be keeping an eye on your thread for responses that may help me.... :-)

---

### Post by .:Justus:. on 2009-10-26
Ah cool I'm not the only one ^^
Hm, I have a rather new ati card though.
Its the hd4870 x2 which is or at least was top of the line recently :0
Hm, ok if i get it fixed I'll tell you aswell :D
good luck to both of us :D
Anybody else have an idea?

---

### Post by .:Justus:. on 2009-10-27
This is very very annoying, Isn't there a command that I (we) can put in the terminal in recovery mode that will maybe delete the last driver installed or something :0
I can't access ubuntu at all :[

---

### Post by cjovergaard on 2009-10-28
I have the exact same problem.. Isn't there anyone with a solution for this?!

 - cjovergaard

---

### Post by pookiebear on 2009-10-28
did the same for my x1200 ati card. I guess we did not follow the right guide. Mine was a fresh install...so I just formatted and reinstalled. I have 2 other computers that work great. No fancy installs or anything. But this laptop with ATI is a pain for sure.. 
If I don't mess with any drivers after a clean install. My video has tearing looking at webpages or the menus off of the panels. Load either of the drivers, open or fgrlx, and reboot. I get the crazy colors and it just cycles a reboot. 
Tried the 9.10 RC today. Same results as above. I don't have a fix, just wanted you to know you were not alone.


-edit-
got mine fixed with this page. But it seems specific to my model
[http://ubuntuforums.org/showthread.php?t=1255700&highlight=x1200+ati](http://ubuntuforums.org/showthread.php?t=1255700&highlight=x1200+ati)

---

### Post by cjovergaard on 2009-10-29
ok, maybe a step closer to a solution :)
can I follow the tutorial by booting ubuntu in demo mode from live cd? what did you do?

 Regards, cjovergaard

---

### Post by .:Justus:. on 2009-11-04
Hm,I couldn't find a solution to it, and I reinstalled ubuntu.
It was basically the only thing I could do.
Stay away from the recommended drivers if you have an ati card.
Just go to amd.com and find them there.
Worked for me.
good luck ;]

---

### Post by Mr_Wonderful on 2009-11-23
After putting it off, and off, and off.... I finally got round to "having a go" at fixing it.... literally took me about half hour max.... just downloaded a program called PartMagic (bit of a free Linuxy take one Partition Magic) booted from the cd and deleted my Ubuntu partition.... restarted my computer and got a Grub error.... just popped the Ubuntu CD in and booted from that... in the installation menu screen I went into more options and selected the graphics stable install (or something like that, you'll know it when you see it) and not its working fine... dont get crap on the splash screen at load up, nothing like that... the only problem Ive got is Ive given Ubuntu twice as much as my HD as I wanted (because I only use it for work) but that is something I can live with and sort out at another day... for the time being Im happy as a pig in **** :-)

I must say I have bothered with installing any additional graphics drivers or anything, dont wanna push my luck.... 

hope this has helped

cheers

Nick

---

