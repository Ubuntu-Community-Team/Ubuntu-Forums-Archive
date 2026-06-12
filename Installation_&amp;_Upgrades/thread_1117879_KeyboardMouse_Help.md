---
title: "Keyboard/Mouse Help"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by stylusiam on 2009-04-06
Ive installed 8.10 but once I boot my keyboard and mouse no longer work. I checked the compatability and others have said that they work out of the box (Logitech MX3200 keyboard/mouse combo).

I would like to get it working (it does work in BIOS and running terminal commands, just doesnt work when it comes time to log in).

If anyone has suggestions please let me know. 

Or please recommend a keyboard/mouse I can go buy so I can start working with Ubuntu asap. I want to start familiarizing myself with Linux as I start a new job in 2 weeks where they use Linux as their OS, and of course ive been trapped in Windows for over a decade (and its situations/experiences like this that keep me there). 

Much appreciated.

---

### Post by stylusiam on 2009-04-06
any advice or recommendations for a keyboard/mouse to purchase?

---

### Post by stylusiam on 2009-04-06
bump as I would like some help finishing the install

---

### Post by upchucky on 2009-04-06
if the keyboard and mouse worked using the live cd, then i suspect the install failed.

the installable may be bad on the live cd, possibly from being created at too fast a speed, test cd to verify it is ok or try alternate cd to install.

---

### Post by wylfing on 2009-04-06
If they are just typical USB keyboard and mouse, then there is no reason they should fail to work. I agree that something amiss with the installation is a possibility. Did you make non-default choices about the keyboard and mouse during the install?

Also, you could simply try unplugging them and plugging them back in.

Another possibility is that your hardware is flaky or failing -- since it's both devices then I might suspect your USB hub. Try plugging the devices into two entirely different USB ports and see what happens.

---

### Post by stylusiam on 2009-04-06
The keyboard/mouse didnt work with Live CD. I actually couldnt even get the gui login to work on liv CD so I did a full install instead. The only keyboard option I selected was US. I have tried unplugging it and doing it again. Ive tried other usb connections. Ive even tried my G15 keyboard and G5 mouse. At the login screen I have a blinking cursor, but nothing responds. The keyboard is working because I can alt+ctrl+f key and do a command line login. However, when I exit and go back to the login gui no keyboard or mouse.

any other suggestions/ideas? And thanks for trying to help me, I appreciate it.

---

### Post by upchucky on 2009-04-06
aha... more information


the blinking cursor is called busybox.
the install worked but boot information is missing and the gui cant come up until the graphics is set up.

Grub did not get set up so it is waiting for you to tell it what to do.

you should be able to boot from the live cd and from the menu choose repair grub

---

### Post by stylusiam on 2009-04-06
Thanks again. I cant boot from the live CD, and my only options at the load menu are try without change to computer, install ubuntu, check cd for defects, test memory, and boot from first hard disk.

I ran each of the tests, and did the install, but I still cant figure out where the problem is. Ive burnt numerous copies as slow as 4x so the cd should be ok. 

Any other suggestions? And thanks again.

---

### Post by stylusiam on 2009-04-07
bump

---

### Post by wylfing on 2009-04-07
> **stylusiam said:**
> I cant boot from the live CD

Why not?

---

### Post by upchucky on 2009-04-07
Quote
"The keyboard/mouse didnt work with Live CD. I actually couldnt even get the gui login to work on liv CD so I did a full install instead. The only keyboard option I selected was US. I have tried unplugging it and doing it again. Ive tried other usb connections. Ive even tried my G15 keyboard and G5 mouse. **At the login screen I have a blinking cursor, but nothing responds. The keyboard is working because I can alt+ctrl+f key and do a command line login**. However, when I exit and go back to the login gui no keyboard or mouse."


I do believe it is booting from live cd, and he is getting the blinking cursor which indicates the busybox prompt which is waiting for him to tell it what to do next, this indicates grub is not set up.

since this is happening on the live cd boot then he needs instructions on how to fix this at the busybox prompt this will enable him to get to a ubuntu prompt which in turn should allow him to set up the gui.

since he said he did an install, I'm thinking supergrub may get him as far as the ubuntu prompt and if successful we can go from there.

Get Supergrub to set up/repair Grub here:

[http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

---

### Post by stylusiam on 2009-04-07
> **wylfing said:**
> Why not?

My screen remains blank and the cd is idle. I go through the loading process, the status bar works and completes the load. But when the login screen should show I get a blank/black screen.

---

### Post by stylusiam on 2009-04-07
> **upchucky said:**
> Quote
"The keyboard/mouse didnt work with Live CD. I actually couldnt even get the gui login to work on liv CD so I did a full install instead. The only keyboard option I selected was US. I have tried unplugging it and doing it again. Ive tried other usb connections. Ive even tried my G15 keyboard and G5 mouse. **At the login screen I have a blinking cursor, but nothing responds. The keyboard is working because I can alt+ctrl+f key and do a command line login**. However, when I exit and go back to the login gui no keyboard or mouse."


I do believe it is booting from live cd, and he is getting the blinking cursor which indicates the busybox prompt which is waiting for him to tell it what to do next, this indicates grub is not set up.

since this is happening on the live cd boot then he needs instructions on how to fix this at the busybox prompt this will enable him to get to a ubuntu prompt which in turn should allow him to set up the gui.

since he said he did an install, I'm thinking supergrub may get him as far as the ubuntu prompt and if successful we can go from there.

Get Supergrub to set up/repair Grub here:

[http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

I will try this when I get home. One point though, you mention that I am booting from live CD, but im actually booting from the hard drive. I installed from within Windows (could that be a related issue?). After the install I was directed to reboot without the cd, which I did, but I was only able to get to the blinking cursor login with no mouse/keyboard.

If I keep the cd in and boot from the cd, I get the blank/black screen after everything loads up (I see the status bar complete the load, but everything idles after that point. I can still do the alt+ctrl+f key and run commands, but there is no gui with a blinking cursor when I boot from the CD.

Thanks again to everyone trying to help me. I really do appreciate it.

---

