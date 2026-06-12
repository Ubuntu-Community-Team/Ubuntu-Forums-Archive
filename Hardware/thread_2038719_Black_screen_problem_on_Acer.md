---
title: "Black screen problem on Acer"
date: 2012-08-07
forum: Hardware
---

### Post by Beershaw on 2012-08-07
Hello everyone,

I've got an Acer Aspire 5732Z with Ubuntu 12.04 installed as the only OS. When I first installed it, I used to get a black screen right after boot, which I managed to fix using unkown47's solution here [http://ubuntuforums.org/showthread.php?t=1743301](http://ubuntuforums.org/showthread.php?t=1743301) . Had Wubi on Windows 7 before that, and fixed the same issue using the laptop's brightness controls, but that didn't work. Now, my problem still remains that whenever I close the laptop lid or send it to suspend/hibernate it brings up that dreaded black screen when I turn it back on, and I need to reboot. And I also found that when playing Battle of Wesnoth 1.10 on fullscreen my screen goes black again in the same way, and the only way to fix it is reboot. Tried to use the laptop's brightness controls, but it seems like keyboard is not really responding in any way, can't even get to terminal with ctrl+alt+f1 or f2...Also tried all sorts of fixes found through forums such as modifying the grub default line and such but with no luck...Anyone got any ideas/has this issue? 
Thanks:)

---

### Post by foresthill on 2012-08-09
In the same boat here, with Intel 4500 MHD graphics on my notebook.

About all you can do is go into System Settings / Brightness and Lock and set it so the screen never turns off when inactive. If you want to lock the computer, hit Control-Alt-L. As far as playing your game goes, I don't see a way to fix that.

All variants of Linux are affected by this bug, unfortunately. Maybe the kernel developers will fix it in the next year or two.

---

### Post by Beershaw on 2012-08-09
Yeah I did that and I just leave it on all day but it's a bit annoying really...as for the game, I found a fix, open it from the terminal with wesnoth --w, that will bring it up in a window...from what I've gathered the problem has been around since Ubuntu 11, and no one really seems to care about it enough to fix it...Oh so all kinds of Linux have this issue, even Mint and others? That's sort of comforting I suppose cos people suggested to me try and turn to Mint, but if it just has the same issues then it's useless..

---

### Post by foresthill on 2012-08-09
It's much worse in other variants like Open Suse, because not as many people use it, so it takes much much longer to find a fix. I installed OpenSuse 12.1 yesterday on this machine, and had the exact same problem. I was able to add boot options to Grub to get me to the desktop, but could not find a permanent fix, despite searching for several hours.

We'll never know how many thousands of people have had to fight this problem and ultimately gave up and went back to Windows, since Intel 4500 graphics chips are pretty common these days.

---

### Post by Beershaw on 2012-08-15
Also found another workaround that works quite well here workaround B got rid of my problem (for now lol) [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

---

