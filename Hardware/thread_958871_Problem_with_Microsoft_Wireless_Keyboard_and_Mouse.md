---
title: "Problem with Microsoft Wireless Keyboard and Mouse"
date: 2008-10-25
forum: Hardware
---

### Post by PKGINGO on 2008-10-25
Greetings!

I am trying install Ubuntu for my family's computer, and their keyboard/mouse combo is not working.

The combo is the Microsoft Wireless Desktop Comfort Edition 1.0a. This doesn't work in any Linux distro correctly. What happens is, the keyboard works in the BIOS, and telling Ubuntu to start the installer or live cd mode. Then during the the OS load, the LED on the USB receiver goes out and comes back on, but now it's blinking, as if it doesn't have enough sustained power.

The keyboard can grab about one 1 stroke for every 60, but the mouse doesn't work at all (both go to the same receiver). I did a search and nothing cropped up.... any help would be greatly appreciated.

edit: I suffered through the install and booted to the desktop, I was greeted by a lovely error that said failed to initialize HAL..... could this be the problem?
edit2: Searching I found a way to fix the HAL problem... I had to leave a CD in the system at boot... any CD... really weird....
edit3: Forgot to mention, the keyboard works just fine on multiple computers with windows, but none with linux. I also have another keyboard set just like this, same issue.
edit4: The Intrepid RC works perfectly! Though it is odd it took so long to fix this... The keyboard is about 7 years old... So for anyone else with this problem, you need a kernel at least as new as intrepid's.

---

### Post by PKGINGO on 2008-10-26
I found a solution!

[http://ubuntuforums.org/archive/index.php/t-438112.html](http://ubuntuforums.org/archive/index.php/t-438112.html)


However, I can't use it since I can't open the terminal to even compile the kernel :(. Can someone tell me what kernel version this patch made it in to? I'm on hardy, and its still not in there...

---

### Post by Faryshta on 2008-10-26
Well, what kernel are you using currently?

8.04.1 has kernel 2.6.24 and the 8.10 has 2.6.27.

I suggest to try the liveCD of the RC to check out if the newest kernel works.

---

### Post by PKGINGO on 2008-10-26
> **Faryshta said:**
> Well, what kernel are you using currently?

8.04.1 has kernel 2.6.24 and the 8.10 has 2.6.27.

I suggest to try the liveCD of the RC to check out if the newest kernel works.

I'm on 2.6.24 then, the default, can't move or anything... I'll download the RC and try and report back, but I figured a problem 6 months back of release time for this would have hopefully been fixed. Thanks for the suggestion!

---

### Post by PKGINGO on 2008-10-26
Beautiful! Works like a charm! Thank you so much!

---

