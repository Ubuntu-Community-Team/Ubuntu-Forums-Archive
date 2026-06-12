---
title: "Failed To Install Ubuntu Using Wubi on HP Elitebook 2730p"
date: 2008-10-31
forum: General Help
---

### Post by woozyking on 2008-10-31
Since the model doesn't have a cd-rom, I thought wubi would work. However, after installing Ubuntu using wubi, it cannot successfully boot into Ubuntu, it just freezes with a black screen.

---

### Post by ago on 2008-11-03
Uninstall, reinstall, press esc at boot and select "safe graphic mode"

---

### Post by woozyking on 2008-11-03
Thanks, Ago, I'll try that now :)

So does that mean Ubuntu still doesn't fully support the new GM45 chipset with the integrated video processor?

---

### Post by woozyking on 2008-11-04
Still failed! And I have tried the ACPI workaround as well (because I noticed that when I used the safe graphic mode, it froze at some ACPI point), nothing sweet either.

So, what's the matter? Is it because Ubuntu doesn't support Intel GM45 Chipset yet?

---

### Post by ago on 2008-11-04
Is there any message on screen when it freezes? Boot in verbose mdoe

---

### Post by woozyking on 2008-11-04
Damn I'm sorry that I can't remember now. I can't really afford to mess around with this laptop since it's the one that I'm taking notes in class and have all my university stuff.

All I'm assuming is that Ubuntu or Linux Kernel doesn't particularly support the new 4 series Intel Chipset or some new type of hardware/modules that this laptop's using. I'll wait a bit then, and have Ubuntu happily running on my old T43 :D

---

### Post by woozyking on 2008-12-07
Bump up for more help!

---

### Post by CalonD on 2008-12-08
I recommend you buy some sort of CD Drive, as you'll need it for things like build-essential if you can't connect too the internet, the ubuntu CD is an extremely useful resource after installed.

---

### Post by frncz on 2009-01-10
I also have the Elitebook 2730p. I tried USB installation and SD installation. It always hangs. I bought the CD expansion base and tried the CD installation. This also hangs. Somehow Ubuntu 8.10 (or 8.04, by the way) and the 2730p don't hit it off. I think I need to wait for the next issue of Ubuntu?

Mike

---

### Post by jimmy1960 on 2009-01-20
Sorry. I have a 2730p but with the ultraslim expansion base including CDROM.
I installed Ubuntu amd64 without problems. I got it by lunchtime and on 
the following day I had everything working including the pen, etc. 
The clue was that I followed the instructions in 
[http://www.linlap.com/wiki/HP+EliteBook+2730P](http://www.linlap.com/wiki/HP+EliteBook+2730P)
In particular the following issue

"ACPI works fine when the option “fan always on on AC Power” is turned off in the BIOS. "

If not for that webpage I would have not succeeded. 

     Good Luck

---

### Post by potamus on 2009-02-15
i downloaded ubuntu, some  other thing that everyone is saying to download ... and it still dont work

on the ubuntu site it says ... "ubuntu just works" ... mine doesnt 

obviously im doing summit wrong, i just want to download it, burn it, install it and be done, but no it seems that someone with no real knowldge of computer programming has to edit all these files that make it boot and do all this other stuff ... can someone please post a step by step walkthrough that explains how to install ubuntu linux on windows xp home edition without having to change bloomin' boot files and stuff that will potentially kill my pc!!

please and thankyou

---

### Post by woozyking on 2009-03-09
One thing I don't understand tho, jimmy, that why shall we install an AMD64 version on an Intel core laptop?

I'll try it again with the wubi, see if I get any luck.

---

### Post by woozyking on 2009-03-09
Hmm, it seems that the guide is the only way out, but I don't want to risk loading different kernel (AMD kernel for a Intel CPU, that's a bit of weird and unreliable to me).

So I'll wait, wait one day Ubuntu makes it perfectly compatible with the chipset that this lappy has :)

---

