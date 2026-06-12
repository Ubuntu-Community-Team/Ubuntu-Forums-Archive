---
title: "Live CD desktop not loading"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by kidux on 2009-03-10
OK, I think Jaunty may have broke something. I decided to check it out and it installed fine. However, when it would go to login, it would get the background and a frozen clam. So, with it being an Alpha, I figured there was an issue with my machine so I tried to reinstall 8.10, but cannot get the live desktop to load. I also tried Xubuntu 7.10, with the same result. The Jaunty live desktop will load. I am able to boot into my XP partition and get the desktop. I know it could be an issue with the CD's but I used the 8.10 just the other day to upgrade my laptop, and have been using the Xubuntu disc as a recovery CD, so it was working recently as well.

I thought maybe there was a problem with the ext4 file system or the swap file hanging, so I completely wiped those out. Still no luck. Anyone have a clue as to what the problem could be?

---

### Post by cariboo on 2009-03-10
Try starting in safe-graphics mode. press F4 at the menu and select safe-graphics mode and continue on.

Jim

---

### Post by Neo_The_User on 2009-03-10
Another thing you could do is when Ubuntu is starting up, you can press Control Alt F1 or F2 and see whats hanging. You can also turn off "quiet splash" in the boot options.

---

### Post by kidux on 2009-03-10
> **cariboo907 said:**
> Try starting in safe-graphics mode. press F4 at the menu and select safe-graphics mode and continue on.

Jim
I will try that, thanks.

> **Neo_The_User said:**
> Another thing you could do is when Ubuntu is starting up, you can press Control Alt F1 or F2 and see whats hanging. You can also turn off "quiet splash" in the boot options.
It's not hanging at the splash screen, rather it goes into X, shows the background and the mouse cursor, but doesn't go any further. No HDD or CD activity, and trying CTRL+ALT+F1 doesn't work as the keyboard becomes non-responsive, not even the caps lock works.

---

### Post by Neo_The_User on 2009-03-10
> **kidux said:**
> I will try that, thanks.


It's not hanging at the splash screen, rather it goes into X, shows the background and the mouse cursor, but doesn't go any further. No HDD or CD activity, and trying CTRL+ALT+F1 doesn't work as the keyboard becomes non-responsive, not even the caps lock works.

Ah sorry. My mistake. Yes, safe graphics mode would be your best bet.

---

### Post by dfields on 2009-03-10
Hi,

I've installed Intrepid Ibex.  I seem to be having the same trouble as the previous poster:  It will let me log on, then it goes to the greyish background screen.  The mouse works, but the keyboard is completely frozen and nothing else works.

I did check the CD for errors and found none.
I tried F4 and went into recovery mode, but that resulted in the same problem.

I don't know if it matters, but I installed a new hard drive that was bigger (200GB to 500 GB) and also doubled the RAM from 512MB to 1GB (left the old 512 chip in there and added a 2nd one that I just bought).

Any tips would be greatly appreciated.  I am a complete newbie at Ubuntu.

We installed it on another computer with success, but this one is being quite stubborn.:(

Thanks in advance.

---

### Post by Neo_The_User on 2009-03-10
> **dfields said:**
> Hi,

I've installed Intrepid Ibex.  I seem to be having the same trouble as the previous poster:  It will let me log on, then it goes to the greyish background screen.  The mouse works, but the keyboard is completely frozen and nothing else works.

I did check the CD for errors and found none.
I tried F4 and went into recovery mode, but that resulted in the same problem.

I don't know if it matters, but I installed a new hard drive that was bigger (200GB to 500 GB) and also doubled the RAM from 512MB to 1GB (left the old 512 chip in there and added a 2nd one that I just bought).

Any tips would be greatly appreciated.  I am a complete newbie at Ubuntu.

We installed it on another computer with success, but this one is being quite stubborn.:(

Thanks in advance.

You can't just mix and match RAM. hahahaha

---

### Post by dfields on 2009-03-10
Hi,

Thanks for responding.

I put in the other identical RAM chip I had ordered, so now both are identical.

I burned a new 8.10 install disk from a different mirror site and checked its integrity.

I reinstalled it and tried booting from the hard drive.  This time, it didn't even get as far as the login screen.  It froze up before that.  Showed a dark background (not the grey as before), and the mouse worked but keyboard didn't, same as before.

So I reinserted the Live CD, and selected the option to run Ubuntu from it.  Then it froze for me with the "timer" icon for the mouse (circle with moving lines, what would have been the hourglass in Windows).

I'm stuck.  Any other ideas you could suggest?

Thank you.

---

### Post by gmoctav on 2009-03-10
yes , u can. i mixed two ddr 2 (512Mb & 1Gb ) and is working with intrepid.

---

### Post by kidux on 2009-03-11
> **cariboo907 said:**
> Try starting in safe-graphics mode. press F4 at the menu and select safe-graphics mode and continue on.

Jim
Thanks, this worked, though I'm not sure why I had to do it since I've used that CD before on the same machine. Anyway, I got Xubuntu 7.10 back on there.

---

