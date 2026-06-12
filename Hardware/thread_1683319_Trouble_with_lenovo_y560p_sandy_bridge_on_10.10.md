---
title: "Trouble with lenovo y560p sandy bridge on 10.10"
date: 2011-02-07
forum: Hardware
---

### Post by jonpry on 2011-02-07
Hi All,

   I recently got a y560p and installed ubuntu 10.10 64bit on it. My setup is pretty stock except that I installed the latest (11.1) catalyst from ATI to solve issues I was having with 32-bit wine using the 3d. 
   My laptop appears to not be able to fully resume from going to sleep. If it is inactive for long enough for automatic log out. It is fairly unlikely that I will be able to login again. The machine seems to be active, ie the disk becomes active now and then and certain buttons on the keyboard seem to work. However I cannot get it to come alive or shutdown. I have tried switching to vt, logging in and shutting it down, but nothing happens. 
   This is all really annoying :p. I do not understand why it is even entering sleep. I turned it off in the power management deal. But it seems determined to eventually power down. A couple of times it did resume and I looked at dmesg, which indicated the machine had actually entered and exited S3. 
   I'm guessing that real fixes for this problem are unlikely as sandybridge is basically pulled from shelves, leaving not many testers, no known good hardware, and no support from the manufacturers. So I'm looking for band aids. How can I stop it from sleeping? Is there someway to rig the power button to shut it down?

Thanks,

Jon Pry

---

### Post by jonpry on 2011-02-07
I managed to get some dmesg logs, indicating a kernel panic. it alternates between this

BUG: soft lockup - CPU#1 stuck for 61s! [wpa_supplicant:1133]

and this

[85176.719216] BUG: soft lockup - CPU#5 stuck for 61s! [ksoftirqd/5:19]

until the log stops, presumably because i turned the power off. 

I found some *old* posts about this being caused by lack of microcode. So apt-get'd the intel microcode packages. Not sure if it is working yet.

---

### Post by jonpry on 2011-02-07
Nope that didn't fix it.

---

### Post by jonpry on 2011-02-08
I have tried several different kernels now. At this point I am running 2.6.38-rc4 with a hacked fglrx 11.1. This all seems to work while not alleviating the sleep troubles. Setting acpi=off in the kernel boot parms does stop the hangs, but at the cost of losing hyperthreading on all 4 cores and turbo boost while creating massive amounts of heat since the idle loop does not seem to be sleeping the chip correctly. Arghh.

---

### Post by jonpry on 2011-02-09
Setting acpi_osi="Linux" seems to stop the problem. It runs quite hot, but at least all 4 cores/8 threads are running.

---

### Post by sml on 2011-02-17
would you recommend the y560p with ubuntu?

i am concerned about the radeon graphics as the drivers have never been as good as nvidia.

any other issues?

---

### Post by jonpry on 2011-02-19
Its a pretty nice laptop in my opinion. After some fiddling I was able to get the catalyst 11.1 drivers to work with all my apps. I'm not sure how the performance compares to windows, but it is quite fast. 

The ACPI issue is kind of a big deal though. Idling it runs at 70C, and its easy to get it close to 100. These kind of temperatures are not good for anything, ie clockspeed, electric bill, or life span. I hope a bios update in the future will rectify this.

---

### Post by audie2k3 on 2011-03-03
Hi... how things on the y560p... I also have this blessed beast.  I loaded mine with Mint 10 on it... it work right out the box, but haven't played any games on it yet.  Do you think we can make this laptop switchable graphic under linux

i also tried this [http://ubuntuforums.org/showthread.php?t=1666626](http://ubuntuforums.org/showthread.php?t=1666626)

---

