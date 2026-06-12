---
title: "Weird Problem: Webcam only works after restarting from Windows"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by Homayoon on 2008-04-06
I bought a Sony VAIO SZ-650 NC laptop a few days ago. I installed Ubuntu 7.10 (64 bit) along the preinstalled Vista and everything seemed to work smoothly. I installed [Cheese]("http://www.gnome.org/projects/cheese/"), then and was quite surprised to see that the webcam worked out of the box, especially because [the Laptop Testing Team review]("https://wiki.ubuntu.com/LaptopTestingTeam/SonyVaioVGN-SZ650N") suggested otherwise.

Yesterday, I ran Cheese again and run into this error message: "Unable to find a webcam, SORRY!" I was quite confused because I had done almost nothing on my laptop before that, then remembering my brother having some strange problem with bluetooth in Ubuntu on his laptop (a Dell Latitude 620, if I'm not mistaken), I restarted to Vista and then immediately back to Ubuntu and, Voila!, the webcam worked again.

Now, every time I want to use my webcam I have to restart to Windows and back to Ubuntu. Quite frustrating. Can anyone suggest how I can fix this strange problem?

---

### Post by sdennie on 2008-04-06
It could be a BIOS problem.  It's possible that Windows is initializing the webcam and a soft reboot is keeping the settings when going to Ubuntu.  I would check to see if there is a BIOS update available for the machine and see if that helps.

---

### Post by Homayoon on 2008-04-06
> **vor said:**
> It could be a BIOS problem.  It's possible that Windows is initializing the webcam and a soft reboot is keeping the settings when going to Ubuntu.  I would check to see if there is a BIOS update available for the machine and see if that helps.

Thanks. I might consider that when I have time. Meanwhile, isn't it strange that the same problem has occurred on two completely different laptop models and with two different devices? Also, if your explanation is correct, it is considered a bug in Ubuntu, or in some driver. Do you think I should file a bug report? If so, I'd be much grateful if you could point me to some guide because I have never filed a bug report for Ubuntu.

---

### Post by sdennie on 2008-04-06
It's hard to say.  I once had a laptop where, due to a BIOS problem, the graphics card fan would only run if I first booted into Windows and then rebooted to linux.  It was not a problem that could be fixed via Ubuntu/linux/nvidia but only via "fixing" the BIOS.  It sounds like you are seeing similar symptoms which is why I recommended the BIOS update (and, if that doesn't work and you are really adamant about getting things to work, you may have to learn how to fix a DSDT (which isn't that fun)).

---

### Post by Homayoon on 2008-04-06
Can you explain a bit more about the cause of the problem. I'm curious about it. If Windows does something to have the device work, Linux should be able to do that, too. Am I wrong?

---

### Post by sdennie on 2008-04-06
Well, if it's a similar problem to what I've had in the past, it's not something that linux can actually fix (or even should fix).  The BIOS more or less tells the OS what devices are available however, it's sometimes the case that vendors compile the BIOS (well, more accurately, the DSDT) using a Microsoft compiler instead of the Intel DSDT compiler.  Not surprisingly, the Microsoft compiler accepts non-standard stuff and so any non-MS OS can't figure out what's going on.  You could google for "linux fix DSDT" for more information.

---

