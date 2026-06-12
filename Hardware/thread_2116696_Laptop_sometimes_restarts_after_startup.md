---
title: "Laptop sometimes restarts after startup"
date: 2013-02-16
forum: Hardware
---

### Post by vxs8122 on 2013-02-16
I had this similar problem with Windows 7 on this laptop and after the recent installation of Ubuntu 12.04 yesterday.  Usually, the laptop works fine after one unintentional restart when I try to start up my laptop.  However, it is getting pretty annoying and am wondering if there is a way to fix this.

My laptop is Acer Aspire V3-571G-9435.  I can't remember exactly what caused the problem since I had this problem for about a year.

---

### Post by vxs8122 on 2013-02-21
Just today, the problem has worsen--it has restarted about 5 times itself.  Any help would be appreciated.

---

### Post by BrandonC19 on 2013-02-21
Before we can do any troubleshooting to help resolve your issue, we'll need more info about what's actually going on when your machine restarts. Are you just web surfing? Are you playing games or rendering video? Do you notice the machine is getting really hot before it restarts? (In which case it could be overheating and the CPU shuts down to protect itself.) Also, when is the last time you cleaned the fans?

---

### Post by vxs8122 on 2013-02-21
Thanks for a reply.

Usually, my laptop restarts just about 1-3 minutes after boot and logging before I could do anything.

My laptop didn't feel hot when that happens, and usually it happens after leaving my laptop off for a long time.    It seems to run fine after my laptop has warmed up.

Also, I just checked for dust.  I don't see any in my laptop at this moment.

---

### Post by BrandonC19 on 2013-02-24
That's a very peculiar problem. Have you tried it with and without the battery? If it seems to work better once it "warms up," that makes me want to think it could be something circuitry-related. But at this point I don't know enough to guess what. It could be anything from a dying battery, to a failing voltage regulator, and anything in-between.

---

### Post by vxs8122 on 2013-02-28
Regarding the battery: when it is turned on unplugged (using the battery only) it shuts down itself, and when plugged in it restarts itself instead.  I repeated those steps (unpluged then plugged again), I get the same results.  Again, I don't get those problems once the laptop has warmed up.

---

### Post by matt_symes on 2013-02-28
Hi

As it happens under both windows 7 and ubuntu, i would place money on hardware or BIOS/ACPI.

Is there a new BIOS update for it ? (don't run it yet, just check).

Have you looked in the logs ?

```
/var/log/kern.log
/var/log/syslog
```

look around the time it reboots for anything interesting.

run a memtest on memory and check the hard drive. run smart tests on it.

Kind regards

---

### Post by vxs8122 on 2013-03-02
In the Acer website, there is an update for my BIOS from 1.07 to 1.13.  But it is under Windows 7 section and I do not see an Ubuntu section.  Is it still safe to update the newer BIOS?

I did memory and hard drive tests and both passed with no errors.

[SIZE=-1]See attachment for my logs.[/SIZE]

---

### Post by tgalati4 on 2013-03-02
Go ahead and boot into Win7 and download and install the BIOS update.  It sounds like you have a motherboard problem, either a bad solder connection, or broken trace.  Because it happens intermittently and in both Win7 and Ubuntu, you can be pretty sure it's a hardware problem.  Acers are not known for their build quality.  Where did you purchase it from?  Do not say Costco.

---

