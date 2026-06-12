---
title: "alternate text-based install problems"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by sockrebel on 2009-01-08
hello,

I'm trying to set up an ubuntu system with encrypted filesystems (/home and swap) on a HP/Compaq 2510p laptop.  I was initially trying to do this via a USB drive (unetbootin ubuntu netinstall) but after going thru the initial boot processes, the first 'select language' screen won't show up, the screen just remains blank.  Next, I tried the mini iso for a netinstall to the same result.  And finally, the alternate install cd.

I've tried each of these CDs/USBsticks on another laptop and they install fine.  The live CD works fine on the HP laptop, too (but that's not what I need).  Any idea why the graphical install would work, but the text one not?

thanks!

---

### Post by Pumalite on 2009-01-08
Probably a bad burn.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by sockrebel on 2009-01-08
> **Pumalite said:**
> Probably a bad burn.

Both CDs (netinstall and alt CD) and the USBstick (unetbootin netinstall) install fine on another laptop.

---

### Post by Pumalite on 2009-01-08
Clean the lens in your burner or try a different burner

---

### Post by sockrebel on 2009-01-09
the installation CDs are working fine.  I've used multiple burners, checked their integrity, and even installed ubuntu on other laptops with them.  Even used usbsticks.

It seems to be an issue with this laptop in particular (HP/Compaq 2510p).  I can use graphic installers, but any text-based ubuntu installers show a blank screen.  They all boot up, but all go blank screen at the first stage of the install process (selecting language).

Any ideas/solutions/work-arounds?

thanks!

---

### Post by wurststulle on 2009-07-17
i have the same problem when i try to install 9.10 on 2510p. the installation does not start, the screen remains black.

---

### Post by merlinus on 2009-07-17
Why are you installing a version that is still in alpha stage?

In any case, are you using the alternate install cd?

---

### Post by Herman on 2009-07-17
When you're at the very first screen after your 'Alternate Installation' CD boots up, (if you can see that), after you select your language, you can press your F4 key for 'other modes'.
One of your choices will be 'safe graphics mode'. Try that and see if it helps.

Ubuntu Karmic Koala is for developers and testers. It's good to install Karmic for testing puposes, especially if you care to submit proper bug reports. Good quality bug reports can help developers, but it is work to the user, and in the alpha stage a lot of times you need to be able to cope with all kinds of problems and interuptions. (Right now my volume won't work, probably an update will eventually fix it, yesterday my graphics didn't work, and I had to boot into safe mode and get an update to fix that).
If you're not keen on testing and submitting bug reports, but want to actually get some work done or have fun with Ubuntu, then you should install an earlier version of Ubuntu instead. Earlier versions of Ubuntu can also be installed in an encryted LVM file system, (partition), but use the ext3 file system by default rather than ext4.

---

### Post by Keith Graber on 2009-08-24
I have the same issue with the video mode selected by the 'Alternate Installation' CD on my HP/Compaq 6710b laptop (Intel video card).

I just booted the 9.04 Alt Install and after pressing F4 I found that 'safe graphics mode' was not listed.

I was able to continue the install by pressing F6 "Other Options", pressing the Escape key, and then typing "vga=771"  (no quotes) at the end of the boot Options line.

I found this information by pressing F1 to get into the help screen, then pressing F6 to list "Special boot parameters for special machines"

Hope this helps!

Keith

---

