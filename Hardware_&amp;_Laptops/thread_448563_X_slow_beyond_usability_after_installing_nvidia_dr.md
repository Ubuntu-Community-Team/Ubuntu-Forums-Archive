---
title: "X slow beyond usability after installing nvidia drivers"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by size_XXM on 2007-05-19
I have a problem setting up the nvidia binary drivers on an older PC:
```
[color="red"]MB[/color]: PC Chips M577 (VIA MVP3 based), K6-2 500 MHz, 320 MB RAM
[color="red"]graphics:[/color] nVIDIA Riva TNT2 Model 64 - AGP, 16MB RAM
```
After I install the drivers and change xorg.conf to use them, I end up with X showing black/dark screen with a cursor. If I move the mouse, the cursor will appear on a different place after ~10 seconds. Nothing happens for five minutes, at which point I get bored and hit reset on the computer - mind that Alt+F*n* doesn't switch me to the commandline terminal and I must boot into safe mode to change xorg.conf back to 'nv' driver.

Any ideas?

---

### Post by heimo on 2007-05-19
I believe you should try legacy driver.  nvidia-glx-legacy package

---

### Post by size_XXM on 2007-05-19
Sorry, forgot to mention that I DO use the legacy driver. In fact, I tried both the 7184 from the repository and 7185 from nvidia's website. In my case, both behave the same way.

---

### Post by size_XXM on 2007-05-19
BUMP!
Anyone?

---

### Post by Andrewie on 2007-05-19
That card is super old, but I still have one that I run. That is not normal, which version of Ubuntu are you using? using the newest version of slackware I don't have any of those problems

---

### Post by size_XXM on 2007-05-20
I installed 6.06 and then upgraded to Edgy with alternate CD - with 6.06, X with nvidia drivers always went crashing into textmode, don't know why. I'll probably get a lightweight desktop such as fluxbox instead of gnome, but the problem is that X freezes the whole system :-/ and I don't think it has to do with the hardware's performance, the thing is as good as dead. I'm pretty sure it's some kind of hardware problem that should be fixed with a little tweaking, I just don't know where to look.

---

### Post by Andrewie on 2007-05-20
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-33c42b3671185c2be6eec6d7528438d2f683ee95](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-33c42b3671185c2be6eec6d7528438d2f683ee95)

this should help you

---

### Post by size_XXM on 2007-05-22
hmm.. tried it, and I still can't say it solved the problem, but I think we're getting somewhere.
After changing xorg.conf and rebooting, the X server started, the backround went biege (as it chould) and the mouse responded normally. However, as soon as the login screen showed up, it froze again. After another reboot, X froze immediately after nVidia logo, just as before.
I should mention that now I left it like that for about 30 minutes - and I pressed NumLock to see if X was responding - nothing happened, but after the 30 minutes when I came back, the keyboard indicator was lit up, and HDD LED on the case was blinking intermittently in very short intervals.

I'm getting the feeling that there's some hardware issue - like the driver trying to enable AGP 4X or something :-\. The problem is that I don't know if the error would be reported and even if it was, I don't know which logfiles to look in and where they would be located - **any suggestions on this?** Last time I checked the X.org log, there were no lines labeled (EE), but who knows, will check again... also, I read in the nvidia docs that it's possible to start X in 'verbose' mode - the instruction show only to start X - how do I make the gdm run X in verbose mode on startup? Is there a config file?

---

### Post by Andrewie on 2007-05-23
its safe to say I have no idea whats wrong, have you tried a different distro?

---

### Post by size_XXM on 2007-05-23
> **Andrewie said:**
> its safe to say I have no idea whats wrong, have you tried a different distro?Not really - I started with Ubuntu 6.06 on that machine and upgraded to 6.10 with alternate CD. Can you recommend something light-weight?

Anyway, screw Gnome, it wasn't quite as fast as I hoped, so I'm trying xubuntu:
1.) install the system (the first install froze at openoffice-core (the whole system), for some reason, so I restart with safe graphics, leave the language at US English (before that I selected Slovak) and install with no problem (maybe a bug in the localization?)
2.) boot into the fresh system, set autologin with no delay (boot directly to desktop), install nvidia-glx-legacy via the Restricted Driver Manager, reboot - guess what happens->
3.) the system boots normally, directly to desktop, mouse moves as much as I want, but - I press Alt+F2 to run glxgears and the second the Run box appears is the second X freezes - I'm getting the feeling that it's either a great coincidence and the card overheats (will get a fan and check 2mrw), or the drivers have some problem displaying textfields - in the previous install, I had set a delayed autologin, so the textfield would have appeared before the desktop, which would explain the immediate freeze.

---

### Post by Andrewie on 2007-05-23
I'm sorry I couldn't be of help, the Nvidia Legacy drivers aren't really updated anymore

---

### Post by size_XXM on 2007-05-24
FIXED!!! :D
Searched the web for "x freeze nvidia", found a lot of sites, various advice, and this is what I did to my machine and ended up having a working sytem, so **most likely not all the changes are necessary:**
[list][*]added options **noapic** and **nolapic** to the kernel boot line in */boot/grub/menu.list* (I don't quite know what this is so I'll do a little research)
[*]disabled AGP mode by adding **Option "NvAGP" "0"** to the *Device* section of *xorg.conf* - some site mentioned this to be in the screen section, will look into the log to see if this is a problem
[*]another site suggested removing any out-of-spec modes, so now the xorg.conf *Monitor* section is pretty empty (no modelines) and the *Screen* section's only *Display* subsection is the one for 24bit color. The problem here is that I can't set any resolution above 800x600 despite having the 1280x1024 modes in the subsection, but this should be fixed by filling in the right frequencies in the Monitor section
[/list]
I'll keep tweaking and turning back the options on to see what was behind the problem.
Cheers!

---

### Post by Andrewie on 2007-05-25
> **size_XXM said:**
> FIXED!!! :D
Searched the web for "x freeze nvidia", found a lot of sites, various advice, and this is what I did to my machine and ended up having a working sytem, so **most likely not all the changes are necessary:**
[list][*]added options **noapic** and **nolapic** to the kernel boot line in */boot/grub/menu.list* (I don't quite know what this is so I'll do a little research)
[*]disabled AGP mode by adding **Option "NvAGP" "0"** to the *Device* section of *xorg.conf* - some site mentioned this to be in the screen section, will look into the log to see if this is a problem
[*]another site suggested removing any out-of-spec modes, so now the xorg.conf *Monitor* section is pretty empty (no modelines) and the *Screen* section's only *Display* subsection is the one for 24bit color. The problem here is that I can't set any resolution above 800x600 despite having the 1280x1024 modes in the subsection, but this should be fixed by filling in the right frequencies in the Monitor section
[/list]
I'll keep tweaking and turning back the options on to see what was behind the problem.
Cheers!

all is good then

---

