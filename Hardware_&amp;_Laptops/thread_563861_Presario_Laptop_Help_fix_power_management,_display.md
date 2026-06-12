---
title: "Presario Laptop: Help fix power management, display position, multimedia keys, etc..."
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by boast on 2007-09-30
Hi, hopefully THIS thread gets a response. 

I am running Xubuntu on a Compaq Presario 1201T (12XL4)

**Problem 1) ** _Display position._ I have tried everything I could, changing the h/v sync in xorg, and using xvidtune, in an attempt to position my screen correctly, but it did not work. My screen is just a bit off the edge. By about 4 pixels to be exact.
[img]http://img216.imageshack.us/img216/9974/default009qv7.jpg[/img]
Does anybody know of another method I can use to try and fix it?

**=================================**

**Problem 2) **_ Power management._ I have set my power management as so: [[IMG]http://img64.imageshack.us/img64/7281/default010ab1se0.th.jpg[/IMG]](http://img64.imageshack.us/my.php?image=default010ab1se0.jpg) and I noticed that my laptop would just remain with the screensaver. I then tried to set it to hibernate manually, and it would not work. It would just turn black, and when I moved the mouse, the "screensaver password" login window would appear, although it is disabled, and does not occur with the regular screensaver. Manaully, suspend seems to work fine though. 
[[IMG]http://img232.imageshack.us/img232/6773/default013kl6.th.jpg[/IMG]](http://img232.imageshack.us/my.php?image=default013kl6.jpg)[[IMG]http://img233.imageshack.us/img233/197/default014pg1.th.jpg[/IMG]](http://img233.imageshack.us/my.php?image=default014pg1.jpg)
My battery % is also not detected. When I disconnect the AC-cord, I get the battery low warning. Even though if I remove the battery and press the little button it shows 100%. 

[color=red]**FIXED:** I downloaded the "[ Presario 12XL and 1200xx Series System ROM Update](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=33670&lc=en&cc=us&dlc=en&product=94933&os=228&lang=en)" F.0D (05/31/01) And now ACPI detects the battery. It also fixed hibernate and suspend.[/color]

**=================================**

**Problem 3) **_ Multimedia Keys_ I want to set my "internet zone" multimedia keys to handle my volume control, (volume down, mute, volume up respectively),  but the keyboard shortcut did not detect the keys. I tried using xev, but it was still not able to detect the keys. Am I out of luck?
[[IMG]http://img216.imageshack.us/img216/5323/defaultyo8.th.jpg[/IMG]](http://img216.imageshack.us/my.php?image=defaultyo8.jpg)

**=================================**

**Problem 4) **_ Video Card Ram_ I have the crappy trident cyberblade video card, and it is bad with playing flash videos in full screen. I was hoping that by sharing more ram, it would fix the problem. So I set the following in xorg: ```
Section "Device"
        Identifier      "Trident Microsystems CyberBlade i1"
        Driver          "trident"
        BusID           "PCI:1:0:0"
       VideoRam        8192
       Option          "DPMS"  "on"

``` and I ended up with videos that looked like this 
[[IMG]http://img216.imageshack.us/img216/4480/default012cc6.th.jpg[/IMG]](http://img216.imageshack.us/my.php?image=default012cc6.jpg)
Disabling it fixes it, but am I setting it wrong or something?
[color=red]**FIX[color=blue]?[/color]:** I believe setting xorg to 16 bit makes it play movies smoother.[/color]

**=================================**

**Problem 5) **_External Display Monitor_ When I connect an external monitor to the laptop, and press fn + f3, it freezes, and I get a black screen on both. Then I have to hard reset. 

**=================================**

**Problem 6) **_External Mouse_ When a PS/2 mouse is connected, it is not detected, and does not work. 
[color=red]**FIXED:** add  
modprobe -r psmouse 
modprobe psmouse proto=imps 
iin /etc/rc.local[/color]

**=================================**

thats about it, thanks for any help.

---

### Post by boast on 2007-10-01
bump

---

### Post by boast on 2007-10-06
bump

---

