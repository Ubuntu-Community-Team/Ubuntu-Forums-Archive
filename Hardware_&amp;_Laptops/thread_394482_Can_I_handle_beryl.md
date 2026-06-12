---
title: "Can I handle beryl?"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by WetWired on 2007-03-27
I'm running a 3.0 Intel Pentium 4
2GB DDR2
Nvidia GeForce 7600 GS
400GB HDD Space
22" Flat Panel LCD Dell Monitor
Ubuntu 6.10 Edgy

Can I handle beryl without much of a slowdown? Or would it slow things down considerably?

Also, can you simply turn beryl on and off? Or is it either on or off. lol. I'm sure there'd be times when I didn't want the eye candy, and others when I did. It is easy to turn on and off?

---

### Post by nick_karstedt on 2007-03-27
With no problem at all (assuming you already have the nvidia drivers)

I'm running 2.5gb ddr, amd 3200+ 64bit, and a GeForce 6800gs.  Beryl does not affect the performance of any other apps for me and runs VERY smoothly.

And yes, you can turn it on and off, it's really just an application that runs in the background.

---

### Post by WetWired on 2007-03-27
Sweet... and on that note, I'll install it. If I have problems, I'll update this thread.

---

### Post by jinx099 on 2007-03-27
Your computer will handle beryl just fine.  I dont know if YOU can handle beryl though! 

only kidding :)

---

### Post by WetWired on 2007-03-27
Oh my GOD! This is frickin' AWESOME! One thing though, How do I do the cubed multidesktop thing?

---

### Post by nick_karstedt on 2007-03-27
hold down ctrl and alt, then drag your mouse.  You can also hold ctrl & alt, then press an arrow key to move it at once.  There's a section in the settings for keybindings

---

### Post by WetWired on 2007-03-27
hmm, mine isn't working. At least not with dragging the mouse.

My settings for Desktop Cube are

Unfold Cube <Control><Alt>Next Disabled (mouse)
Next Slide Disabled Disabled
Previous Slide Disabled Disabled

Am I looking at the right one?

---

### Post by Devius on 2007-03-27
See if you have 4 virtual desktops activated somehwere in the beryl settings manager. BTW, I have an AtlhonXp 2400+ and Geforce4 Ti4200-8X and beryl runs smoothly (there's just a small hiccup for about 1/2 second when minimazing and restoring windows)

---

### Post by WetWired on 2007-03-27
Ah, it worked all along, I just needed to reboot. Killing X alone, wasn't enough.

---

### Post by Slim Odds on 2007-03-27
> **WetWired said:**
> Ah, it worked all along, I just needed to reboot. Killing X alone, wasn't enough.

Ahhhh, the Windoze users...........

I say this on many threads in hopes of helping out some poor souls. The ONLY reason to reboot linux (ubuntu or others) is when you install a new kernel.

Any other time you just need to restart a service or reload a kernel module.

Like, for example, the proper way to "Kill X" is not to Control-Alt-Backspace. That is a "last resort" kind of an option. The proper thing to do is restart gdm (or kdm, or xdm). Like: ```
sudo /etc/init.d/gdm restart
```It's also proper to logout from gdm and excute the restart from a console (Control-Alt-F1).

---

