---
title: "Laptop just shuts off"
date: 2009-11-08
forum: Hardware
---

### Post by xedth2 on 2009-11-08
Okay I installed ubuntu after my computer was acting all weird with some windows errors. I took the computer to geeksquad because its still under warrenty. It pasted there hardware tests so it seems fine. I was able to get ubuntu on it but something strange has been happening. I was running a virtual machine installing a virtual xp. It was set to use slightly more than 50% of my RAM. Then I was surfing the internet and then computer just shuts off, like someone just completely cut the power. But I was still getting power because the lights for the battery power was still on. This has happened twice, the first time i was ripping a CD and surfing the internet. Before all this I was running Vista without any problems. Now I think the problem is that the OS uses up all the RAM and just kills itself. Does anyone know anything about this? I really want to use Ubuntu as my main OS, I mean the only thing I don't like is that google chrome isn't out for it yet and I can't get the sims 2 to run on it(hence the reason I was installing a virtual machine on it).  I should also say that I have searched other fourms and found people talking about heat and I don't think thats the issue because it really doesn't feel that hot.  Also I have upgraded the bios to the newest bios.  It's a Toshiba Satellite L355D-S7901.
 
Please help
Thank you all

---

### Post by Intel91 on 2009-11-08
1. Google Chrome for Linux: [http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux](http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux)

2. The Sims 3 (I know you said 2) works just fine if you use PlayonLinux frontend for wine.

3. Check your Power Management to see if it is set to go to sleep or hibernate after a set time of dormancy, which it might be considering if you are inside a virtual machine, or doing nothing waiting for a cd to burn. System>Preferences>Power Management. If so, turn these off.

---

### Post by xedth2 on 2009-11-08
Okay I'll look at those.  I installed windows 7 on it and did exactly what I did on ubuntu and it runs fine not even lag.  And I was using the Dev of google chrome but it was very slow and just didn't run as smooth as I would like so I'll wait for the beta.  This problem is just really weird.  I even looked in the bios for a shut off temp option and there isn't one.

---

### Post by HunkirDowne on 2009-11-08
which version ubuntu?  9.10?

This sounds a bit like a problem I was having a while back.  Turned out that Ubuntu (or Debian for that matter) wasn't correctly handling the temperature control and the hardware was shutting down in some sort of self-protection mechanism mode.

For me, this issue seemed to be fixed with Intrepid (8.10) and doesn't occur with Debian GNU/Linux 5.0.3 (but don't recall 5.0.0 -- I spend more time in Ubuntu than in Debian).

But your's could be any number of other issues including improperly seated components.

---

### Post by xedth2 on 2009-11-08
I'm running 9.04.  I did find a review that had this problem in it.  But didn't list anything that they tried to fix it.

---

### Post by xedth2 on 2009-11-08
you know i was doing an install with a virtual machine is it possible i hit a key combo that told the machine to just kill itself?  anyone know what key combo would do this?  because i just reinstalled ubuntu and im currently installing the os on the virtual machine and opened like twenty tabs with google searches and had two of my friends spam im me and nothing just a little lag.

---

