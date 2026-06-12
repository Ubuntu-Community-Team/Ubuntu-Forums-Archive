---
title: "Laptop slow some minutes after boot"
date: 2012-03-04
forum: Hardware
---

### Post by neclepsio on 2012-03-04
Hi everyone.
After over a year running Ubuntu, my hp laptop started having a problem. A couple minutes after the boot, it becomes slow an unusable.
The problem even appears booting from the installation iso, so I think it's a hardware problem.
Top shows the memory is not full, but shows great CPU usages for applications (if no application is open, Xorg takes about 100%).
Dmesg shows no strange message.

Can someone help me diagnose the problem?
Thank you.

---

### Post by mikewhatever on 2012-03-04
> Top shows the memory is not full, but shows great CPU usages for applications (if no application is open, **Xorg takes about 100%**).


That in bold is the problem. ;) Any other processes use CPU a lot?

---

### Post by codemaniac on 2012-03-04
Please have a look in the thread below .

[http://ubuntuforums.org/showthread.php?t=1808673]("http://ubuntuforums.org/showthread.php?t=1808673")

---

### Post by ahallubuntu on 2012-03-04
> **neclepsio said:**
> Hi everyone.
After over a year running Ubuntu, my hp laptop started having a problem. A couple minutes after the boot, it becomes slow an unusable.
The problem even appears booting from the installation iso, so I think it's a hardware problem.
Top shows the memory is not full, but shows great CPU usages for applications (if no application is open, Xorg takes about 100%).
Dmesg shows no strange message.

Can someone help me diagnose the problem?
Thank you.

How old is this laptop?  If it's more than a few years old, it could be overheating.  It's common for dirt and dust to clog the heat sink inside the laptop that keeps the CPU and other chips cool.  Also, there's a fan blowing (speed varies) on that heat sink to keep it cool.  If that fan has stopped working, the CPU can overheat.

The CPU gets hotter the more work it does.  Sometimes a laptop can "throttle" the CPU - make it run very slowly - to try to reduce the heat to avoid a meltdown.  This can make a laptop horribly slow.  I ran into an old Dell laptop some months ago that had this exact problem.  It was old, but I didn't think it should be THAT slow.  Turns out it was almost melting.  After I cleaned it out, it ran far cooler and much faster.

So if this thing is a few years old, look at cleaning it out.  You may have to take the keyboard off - depends on how it is desgiend.  HP may have a service manual available for it on their website.

---

### Post by neclepsio on 2012-03-04
> **mikewhatever said:**
> That in bold is the problem. ;) Any other processes use CPU a lot?

If, for example, I'm running chrome, chrome takes 100%. If, instead, I'm running nautilus, nautilus takes 100%.
I cannot interpret this.

---

### Post by neclepsio on 2012-03-04
> **ahallubuntu said:**
> it could be overheating.

A warm reboot "solves", so I think it's not the case.

---

### Post by neclepsio on 2012-03-04
> **codemaniac said:**
> Please have a look in the thread below .

It happens booting from installation iso (which previously worked and I used to install), so I think it's not a software problem.

---

### Post by LinuxFan999 on 2012-03-04
Even if your laptop is not overheating, it would be a good idea to open it up and check for dust, and clean it out.

By the way, what are the specifications of your laptop?

---

### Post by neclepsio on 2012-03-06
> **LinuxFan999 said:**
> Even if your laptop is not overheating, it would be a good idea to open it up and check for dust, and clean it out.

By the way, what are the specifications of your laptop?

I do it, from time to time.
Anyway, it's a HP Compaq 620.

[http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodSeriesId=4158455&prodTypeId=321957]("http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodSeriesId=4158455&prodTypeId=321957")

---

### Post by neclepsio on 2012-03-10
Some new information.
Resetting BIOS parameters solves for a while.
I even tried to hibernate the computer while slow, resetting BIOS then restore from hibernation: it worked.
The problem is I have to do it quite often.

Can anyone please help?

---

