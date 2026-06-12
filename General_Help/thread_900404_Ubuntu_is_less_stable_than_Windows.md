---
title: "Ubuntu is less stable than Windows?"
date: 2008-08-25
forum: General Help
---

### Post by SlyReaper on 2008-08-25
Yes, you heard correctly.  I'm getting frequent crashes while running ubuntu.  Basically, it freezes up and I have to force reboot.  I'm not even doing anything particularly demanding when it crashes either.

It was installed using wubi - could that be the problem?

---

### Post by mellowd on 2008-08-25
We need a lot more info than that.

What version are you running? What computer and hardware do you have? How often does this happen? Has it always been like this?

---

### Post by niccholaspage on 2008-08-25
Well the crashes really depend on the hardware you computer has.My Laptop and Desktop haven't crashed since I installed it.What are your Computer Specs?

---

### Post by SlyReaper on 2008-08-25
Motherboard: Gigabyte P35C-DS3R
CPU: Intel E2160 overclocked to 3GHz
Graphics: Radeon 3850 using flgrx (or whatever they're called) drivers
Sound: Xonar DX (using ALSA 1.0.18 drivers)
RAM: 2GB of 800MHz dual channel 4-4-4-12 latencies
PSU: Corsair TX650W
HDD: 1x 160GB and 1x 320GB
OS: Ubuntu 8.04 Hardy Heron

For added information; I've been running Ubuntu on a laptop without problems for nearly a year now.  It's just the PC described above that has been having crashes.

Edit: and it's fully updated

---

### Post by tuxxy on 2008-08-25
What exaactly are you doin when it crashes, videos? youtube?

---

### Post by SlyReaper on 2008-08-25
Browsing forums, downloading the Eve-online client (which I've still not managed to do because of the crashes).  One crash happened when I closed a firefox tab after watching a BBC news video.

---

### Post by tuxxy on 2008-08-25
When it crashes have you tried just killing X and logging back in rather than booting down?

CTRL + ALT + BACKSPACE

---

### Post by tuxxy on 2008-08-25
When it crashes have you tried just killing X and logging back in rather than booting down?

Try this when it crashes next,

CTRL + ALT + BACKSPACE

---

### Post by SlyReaper on 2008-08-25
Ok I'll try it but I doubt it will work.  When I say it crashes, I really mean it.  Even the mouse cursor won't move.

Edit: and right on time, I got another crash.  And no, ctrl-alt-backspace does nothing.  My crime this time was to click a link to go into another part of a forum.  Wasn't even downloading anything that time.

---

### Post by niccholaspage on 2008-08-25
Weird.That really shouldn't happen.Even though it crashes completely uasully CTRL+ALT+BACKSPACE Works still.Try it when it crashes the next time.Now if I could only remember where the log file is stored...

---

### Post by mellowd on 2008-08-25
> **niccholaspage said:**
> Weird.That really shouldn't happen.Even though it crashes completely uasully CTRL+ALT+BACKSPACE Works still.Try it when it crashes the next time.Now if I could only remember where the log file is stored...

/var/log

---

### Post by pmlxuser on 2008-08-25
> **SlyReaper said:**
> 
 I've been running Ubuntu on a laptop without problems for nearly a year now.  It's just the PC described above that has been having crashes.


Then its not "Ubuntu is less stable than windows?" is it?
Its basically you PC that is less stable right??

Did you customary built your PC , i would think its to do with fault RAM Cards/ DISK (stand to be corrected)

---

### Post by LateNiteTV on 2008-08-25
ive read about a lot of crashing with ubuntu. and the common denominator seems to be firefox...

---

### Post by SlyReaper on 2008-08-25
I just told you, ctrl-alt-backspace doesn't work.  I tried it.

---

### Post by SlyReaper on 2008-08-25
> **LateNiteTV said:**
> ive read about a lot of crashing with ubuntu. and the common denominator seems to be firefox...

Can you recommend a different browser?

---

### Post by -Zeus- on 2008-08-25
> **SlyReaper said:**
> Ok I'll try it but I doubt it will work.  When I say it crashes, I really mean it.  Even the mouse cursor won't move.

Edit: and right on time, I got another crash.  And no, ctrl-alt-backspace does nothing.  My crime this time was to click a link to go into another part of a forum.  Wasn't even downloading anything that time.


Next time it crashes, hold down the buttons Alt+Print Screen and press these buttons, in order: REISUB (if there's no effect, wait about 30s and try it again)
This will try to "nicely" shut down rather than just pulling the plug.

---

### Post by SlyReaper on 2008-08-25
> **-Zeus- said:**
> Next time it crashes, hold down the buttons Alt+Print Screen and press these buttons, in order: REISUB (if there's no effect, wait about 30s and try it again)
This will try to "nicely" shut down rather than just pulling the plug.

Should be interesting.  My print screen button needs shift to be held down.  So I'll be trying to hold down 3 buttons while typing stuff.  Maybe I can use my nose.

---

### Post by LateNiteTV on 2008-08-25
> **SlyReaper said:**
> Can you recommend a different browser?

try opera or konqueror... see if that helps.

---

### Post by LateNiteTV on 2008-08-25
> **SlyReaper said:**
> Should be interesting.  My print screen button needs shift to be held down.  So I'll be trying to hold down 3 buttons while typing stuff.  **Maybe I can use my nose**.

lmao thank you for the laugh.

---

### Post by SlyReaper on 2008-08-25
> **pmlxuser said:**
> Then its not "Ubuntu is less stable than windows?" is it?
Its basically you PC that is less stable right??

Did you customary built your PC , i would think its to do with fault RAM Cards/ DISK (stand to be corrected)

Well it IS less stable than windows on my PC given that I have never had a crash or BSoD with windows on it.

---

### Post by SlyReaper on 2008-08-25
Well, It's not firefox causing the problem.  I just downloaded and installed Opera.  First time I fired it up (with no firefox windows anywhere to be seen), I get a crash.  Bah.

And alt-shift REISUB doesn't work.

---

### Post by Hyper Tails on 2008-08-25
I have experanced this too with both my laptop and desktop.
so i swicthed to kubuntu.
so much happier

---

### Post by LateNiteTV on 2008-08-25
install freebsd on your computer. i will configure it remotely for you. :D

---

### Post by Skorzen on 2008-08-25
> **LateNiteTV said:**
> ive read about a lot of crashing with ubuntu. and the common denominator seems to be firefox...

Yup, my firefox also crashes when watching videos or listening to samples on MySpace, both versions 2 or 3 with both flashplugin-nonfree or flash version 10, downloaded directly from Adobe's site.

---

### Post by anotherdisciple on 2008-08-26
Try running firefox in the terminal that will tell you why it is freezing.

However, you need to read that after you reboot, so make it save the information to a file. Do all that by running....

```
nohup firefox
```

...then run firefox until you get a crash. After that post the nohup.out file that is now in your home directory.

---

### Post by Inane_Asylum on 2008-08-26
Also, try booting up with a Ubuntu liveCD and run Memtest.  My desktop was giving me **all** kinds of problems...my memory only passed 4% of the tests...

Are you on a dual-boot?  If so, does Windows still run flawlessly?  Possibly the overclocked CPU? :confused:

---

