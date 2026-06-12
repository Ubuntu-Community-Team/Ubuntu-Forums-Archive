---
title: "[SOLVED] No sound on resume from suspend Inspiron 1520"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by sarth on 2007-09-26
I have an Inspiron 1520 and I lose sound after resuming from suspend.  It takes a restart to get it going again.  I have searched around and tried a few things, but nothing has fixed it yet.  All of the volume settings seem to be normal after resuming.  There just isn't any sound.  The headphone jack doesn't work either.  Any suggestions?

---

### Post by Shaidtan on 2007-09-26
I haven't had much success getting suspend to work on my 1520. Hibernating works from the console, but doesn't complete if I initiate it from within X. Suspend doesn't work in either case. It appears to suspend but when I try to resume I get only a blank screen and have to forcibly shut down the system. When hibernate works in the console the sound and wireless do not reinitialize properly.

I'm not attempting to hijack your thread, but I am curious if you've had more luck than I with hibernating and if so, what software are you using to accomplish it (suspend2, swsusp, etc.).

It's worth noting that I run Gentoo. The two distros don't seem to be too far off from each other however.

As for your sound bit, what happens if you shut down Alsa, rmmod and modprobe the hda-intel module, then restart Alsa? If that restores sound you should be able to configure the suspend software to do the same.

-Shaidtan

---

### Post by notwen on 2007-09-26
Check [this]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly") out, this is for the 1420n, which has similar issues. =]

---

### Post by Shaidtan on 2007-09-26
Although unfortunately I've not been able to use modular drivers. The module will load but Alsa wont initialize. If I compile the driver into the kernel Alsa loads fine. Headphone jack detection works so I haven't played with it much since then.

With the changes going into the 2.6.23 kernel I may give suspend another shot when it's final. I'll definitely be visiting that link. 

-Shaidtan

---

### Post by sarth on 2007-09-26
Hey thanks Notwen!  That seems to have fixed it.  The only problem is I get a message titled '"Volume Control" has quit unexpectedly' and reads "If you reload a panel object, it will automatically be added back to the panel."  When I tell it to reload it does so and everything is happy.
  
Does anyone know how to set a panel object to automatically reload without the prompt? 

Also, it appears to have been a fluke, but my wireless internet stopped working the first time I brought it back out of suspend.  I restarted before trying again and everything seems to be okay now.  

Shaidtan, I don't usually use hibernate at all.  I did go ahead and try it to see if it work and I didn't have any problems.  I'm running on Feisty and was fortunate enough to not need to install anything extra to get my suspend/hibernate to work.  My graphics card was the only thing I had issues with during installation.

---

### Post by akshunj on 2007-09-28
Awesome fix!  Thanks for connecting everyone to this.  Just an FYI, this affects more than just the Inspiron.  It affects anything with the hda-intel sound chip.  My Acer has the same issue...

--Akshun J

---

### Post by peabody on 2007-09-28
I don't think this affects everyone who has an hda-intel.  I have that on my laptop and I didn't need the suspend fix, although I did need to manually install alsa 1.0.14 to get the headphone jack to turn off the speakers when plugged in.  I used 'model=laptop' for my module parameters.

---

