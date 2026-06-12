---
title: "Locked black screen when starting X on fresh jaunty install"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by PunchMonkey on 2009-04-27
I just received a new Optiplex 760 with nvidia 9300 GE video card here at the office. I installed using the jaunty alternate x64 cd to set up a striped install. Installation went fine and the system initially boots fine with the Ubuntu progress bar. Once the progress bar completes the screen flashes to black. I can't CTRL+ALT+Fn to another tty, CTRL+ALT+BACKSPACE doesn't do anything (I did install and run dontzap --disable).

I booted off the regular desktop x64 installer and found the same thing occurs normally. However, if I choose the safe graphics mode option when booting from the cd, X starts just fine.

I've also tried dpkg-reconfigure xserver-xorg (it never asks me about my graphics card) and dpkg-reconfigure -phigh, and the recovery option xfix. None of these change the symptoms. 

Booting in recovery mode is fine until I type startx which results in the same problem. 

I've also installed the nvidia-glx-180 package.

Any other ideas?

---

### Post by aaronwinborn on 2009-04-27
I have the same problem, and have tried the same things as you:

* dpkg-reconfigure xserver-xorg (doesn't ask me for a video card either)
* dpkg-reconfigure -phigh (this boots up to a command line every time now after running this)
* startx fails hard, telling me 'Fatal server error: No screens found.'

I did read somewhere that nvidia-glx-180 may be broken; perhaps you can go back to another version? (I don't know how to do that.)

Regardless, I'm in the same boat right now, and will subscribe to this thread and post any other tips I might find.

Thanks,
Aaron

---

### Post by aaronwinborn on 2009-04-27
> **PunchMonkey said:**
> 
I've also tried dpkg-reconfigure xserver-xorg (it never asks me about my graphics card) and dpkg-reconfigure -phigh, and the recovery option xfix. None of these change the symptoms. 


[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760) indicates that "newer versions of xserver-xorg rely more on auto-detecting the configuration during runtime rather than looking at xorg.conf," as of Hardy Heron and later.

---

### Post by PunchMonkey on 2009-04-27
I've managed to fix this up after finding this handy ubuntu document, Troubleshooting Blank Screen Issues.

[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

I set the driver to vesa as mentioned in the doc and that let me load X. Once logged in I did the usual steps to enable the nvidia driver, rebooted, and I'm right as rain now!

Hopefully this will help you too Aaron.

---

### Post by aaronwinborn on 2009-04-28
Thanks, the tips there haven't fixed my problem, but they have given me a bit more understanding of what might be going on.

Oddly, a new installation from the Live CD works, so in a worse-case scenario, I can just do that.

I know I won't be able to restore any old settings if I do that, but does anyone know if I can safely install it on the old partition? Or would that wipe out my old data? If so, I can repartition the drive so I can still access it, but I don't want to do that if it's unneccessary.

Thanks,
Aaron

---

### Post by aaronwinborn on 2009-04-28
Additionally, I boot into tty2 every time I restart the computer now, even when restoring old xorg.conf backup files. I have to hit ctrl-alt-f7 to access the (still dead) xserver screen. Anyone know how I can fix that little problem too?

---

### Post by aaronwinborn on 2009-04-28
fyi, i'm troubleshooting on the related item at [http://ubuntuforums.org/showthread.php?p=7168619#post7168619](http://ubuntuforums.org/showthread.php?p=7168619#post7168619)

---

### Post by Bobrm2 on 2009-04-28
I've the same blank background, but it's color is the same as the 8.10. But here the kicker. The blank background is the attempted upgrade(?).

   I also did a new install, replacing the old windows XP partition with 9,04. The new install works perfectly. 
   
   I've left everything, bookmarks, passwords, etc over on the unusable upgrade. 

   Trying not to have to attempt another upgrade, thinking that I could, if I knew how, to simply point to the needed files.

   Not tired, just confused:). Thanks

Bob

---

### Post by Bobrm2 on 2009-04-29
I went back to "Grub", and opened the backup, after it opened in "Safe" mode I ran the utilities provided there. Black screen disappeared, however I have a problem with wireless connection. It is simply easier to move the files needed. Passwords/email addressed., etc. marking this solved.

---

