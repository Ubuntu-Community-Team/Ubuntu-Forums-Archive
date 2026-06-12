---
title: "AMD Ryzen 7 1700 and Gigabyte GA-AX370-Gaming K7 woes"
date: 2017-08-30
forum: Hardware
---

### Post by mdlayher on 2017-08-30
Hi all,

I just built a new machine as a hypervisor/NAS of sorts with an AMD Ryzen 7 1700 CPU and a Gigabyte GA-AX370-Gaming K7 (BIOS F4), and am running Ubuntu Server 16.04 on it.

I've had the machine for about a week and a half, and it's hard-locked/crashed on me 5 times in that time span.  I started out by installing 16.04 with the HWE kernel, assuming it would be necessary for Ryzen.

On kernel 4.10, I experienced two hard-locks after the machine ran for about 24 hours each time.  Symptoms include loss of network connectivity and either no output or frozen output on the console (using an EVGA GT 210 because Ryzen doesn't have integrated graphics).

After a couple of days and crashes, I decided to try installing kernel 4.11.0-14-generic, as it was newest available in the repositories.  Again, the machine locked up after about 24 hours.

After some research, I decided to try disabling SMT to see if that alleviated the problems.  I was able to keep the machine running for roughly three days.  Subsequent reboots have lasted about 24 hours and now about 12 hours without crashing, with SMT disabled and kernel 4.11.

I did try to boot one of the mainline 4.12 kernels, but since I use ZFS on this machine, it doesn't really work for me. In spite of this, I've decided to let the machine run for a few days with 4.12.9-041209-generic and see what happens.

At this point, I'm kind of at a loss as to what to do next.  Any time I've looked for logs or clues related to the crashes, I've found nothing.  It seems like the machine is going to keep crashing continuously at this point, so I'm really up for trying anything.  I've read a couple of times about folks having trouble installing Ubuntu with an AMD CPU and a Gigabyte motherboard, but this problem seems different to me. I suppose I'm not even sure if it is the CPU and/or motherboard, but that is what various forums have lead me to believe.

I'd really appreciate any insight that someone may have, and thanks for your time.

---

### Post by Autodave on 2017-08-30
That sounds more like a RAM module failing to me. Could also be the GPU. I tried looking up your GPU, but didn't find it on Nvidia's site. Are you sure of the model? Did ytou install any drivers for the video card? If so, what one and where did you get it from?

Have you tried running a RAM test on it?

The fact that it runs for a day or two and then locks up leads me to believe that it is not an operating systme problem or even and conflict of hardware problem.

---

### Post by oldfred on 2017-08-30
Did you see this. & read comments where users did do a RMA return.

[https://linux.slashdot.org/story/17/08/29/184243/new-ryzen-running-stable-on-linux-threadripper-builds-kernel-in-36-seconds#comments](https://linux.slashdot.org/story/17/08/29/184243/new-ryzen-running-stable-on-linux-threadripper-builds-kernel-in-36-seconds#comments)

---

### Post by mdlayher on 2017-08-30
I'll give memtest a shot if you believe that could be a problem.  I'd find it a little surprising since the RAM is brand new, but who knows.

Apologies, I was incorrect about the GPU model.  I have the passively cooled model of this: [https://www.evga.com/Products/Product.aspx?pn=01G-P3-1312-LR](https://www.evga.com/Products/Product.aspx?pn=01G-P3-1312-LR).  I'm just using the nouveau driver at the moment.

---

### Post by mdlayher on 2017-08-30
> **oldfred said:**
> Did you see this. & read comments where users did do a RMA return.

[https://linux.slashdot.org/story/17/08/29/184243/new-ryzen-running-stable-on-linux-threadripper-builds-kernel-in-36-seconds#comments](https://linux.slashdot.org/story/17/08/29/184243/new-ryzen-running-stable-on-linux-threadripper-builds-kernel-in-36-seconds#comments)

I did see quite a few threads talking about the segfault issue, but I'm not sure I've run into that issue.  I haven't tried any heavy concurrent compilation jobs, and a segfault wouldn't cause the machine to lock up, right?  I'd just expect it to make the compiler fail.

---

### Post by Bashing-om on 2017-08-30
mdlayher; akso :

Be aware AMD has a recall on some Ryzen 7  CPUs :
[https://www.extremetech.com/computing/254750-amd-replaces-ryzen-cpus-users-affected-rare-linux-bug](https://www.extremetech.com/computing/254750-amd-replaces-ryzen-cpus-users-affected-rare-linux-bug)

[INDENT][INDENT]AMD, taking care
[/INDENT][/INDENT]

---

### Post by Autodave on 2017-08-30
The 340.102 Nvidia driver is what the Nvidia site is calling for, so you would be safe installing that. Alternately, you can go to Settings -> Additional drivers and let it scan. Whatever one it recommends, I would install that one.

Is that what is causing the computer to lock up? Pr5obably not. But it could be.

As far as the RAM sticks, I understand that they are new. However, "new" doesn't mean "good". It doesn't happen often, but I have seen new ones fail. You could also (and I am pretty sure you did this already) make sure that all cables and RAM chips are properly seated.

---

### Post by mdlayher on 2017-08-30
I'm actually running Ubuntu Server.  I only have the GPU because I may occasionally need access to the console to troubleshoot problems if networking is out.  I could try removing it for a few days and seeing what happens.  Would rather not install Nvidia proprietary drivers on a headless machine, heh.

I've been running memtest86 for about 5 hours now.  It's on pass 3 and zero errors so far.

As far as checking the cabling and RAM seating, I could do that tomorrow most likely, though I'm almost positive everything is set properly.

---

### Post by Bashing-om on 2017-08-30
mdlayher; 'Nother thought -

I too experienced unexplained system freezes on my AMD CPU running nvidia graphics with the open source nouveau driver .
After months and extensive looking testing ; no positive result - out of nothing else to try I did install the nvidia proprietary driver .

At the time of the nvidia card install also instlaled a SSD .

No more freezes - period - after installing the proprietary driver.

[INDENT][INDENT]who wodda thunk it
[/INDENT][/INDENT]

---

### Post by mdlayher on 2017-08-30
No kidding! Perhaps it's worth a shot.  If this memory test doesn't report anything bad, I'll pull the GPU and see what happens.

---

### Post by Bashing-om on 2017-08-30
mdlayher; Uh Huh .

I tell you the truth .

Months spent ! Lots of time and effort .

[INDENT][INDENT]I learned -
[INDENT][INDENT][INDENT]time well spent
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by elcct on 2017-08-31
> **Bashing-om said:**
> mdlayher; 'Nother thought -

I too experienced unexplained system freezes on my AMD CPU running nvidia graphics with the open source nouveau driver .
After months and extensive looking testing ; no positive result - out of nothing else to try I did install the nvidia proprietary driver .

At the time of the nvidia card install also instlaled a SSD .

No more freezes - period - after installing the proprietary driver.
[INDENT][INDENT]who wodda thunk it
[/INDENT]
[/INDENT]


I have installed proprietary driver and I still have crashes. It can run for couple of days then crash or can crash multiple times a day. I am sure memory is alright and the GPU.

My CPU also fails kill-ryzen test.

---

### Post by mdlayher on 2017-08-31
Just installed nvidia-340 as recommended, and I'm back on the current HWE kernel.  Guess we'll see what happens.

I have not tried kill-ryzen.

---

### Post by mdlayher on 2017-09-02
After installing the nvidia driver on kernel 4.10.0-33-generic (SMP still off), the machine has been running for roughly 50 hours without a crash.

I did see a couple of kernel oops in the log today.  I honestly don't really know how to read these, but the line "amd_iommu_show_cap" sticks out to me.

A cursory google points at KVM acceleration?  I did enable the AMD virtualization extensions or whatever because I want to use VMs on this machine. I do not have any VMs running right now. No idea if it's related.

[https://gist.github.com/mdlayher/50d966fd0023598e07790325aa9b56f4](https://gist.github.com/mdlayher/50d966fd0023598e07790325aa9b56f4)

I'll leave the machine running, but if anybody has any insight about these oops, I'd appreciate hearing from you.

---

### Post by Bashing-om on 2017-09-02
mdlayher; Well ...

Does your bios have a IOMMU setting ? - mine (AMD)  does not and I also get some IOMMU warnings .. they are just that .. not errors, on my system . Just cost me a bit of memory .

-maybe you too can live with the situation ?

---

### Post by mdlayher on 2017-09-07
The machine has been running for over a week now with no issues.  I'll be damned, it probably was the GPU.  Going to turn SMT back on and see what happens, but I think this issue is solved!

---

### Post by Bashing-om on 2017-09-07
mdlayher; 

:)

---

### Post by mdlayher on 2017-09-14
I guess I spoke too soon!  The machine has now locked up twice in 12 hours with no changes.  I think I'm going to try to pull the GPU, and maybe check the power supply as well.

---

### Post by Bashing-om on 2017-09-14
mdlayher; Ouch !

> **mdlayher said:**
> I guess I spoke too soon!  The machine has now locked up twice in 12 hours with no changes.  I think I'm going to try to pull the GPU, and maybe check the power supply as well.

Sure makes one do frequent backups :(

And I take it , nothing in any of the log files to give a hint ?

[INDENT]tough nut here to crack
[/INDENT]

---

### Post by mdlayher on 2017-09-20
Nothing of note in the logs as far as I can tell.

Update time.  6 days and 1 hour of uptime with the GPU pulled.  Wondering if something about that GPU and Linux don't get along.  Maybe Ryzen has nothing to do with it!  I'll post more updates if anything changes.

---

### Post by Bashing-om on 2017-09-20
mdlayher; Ummmphh;

Well sure do point to a GPU issue .

What have we now to work with :
```

dpkg -l | grep nvidia*
cat /var/log/gpu-manager.log
cat /var/log/Xorg.0.log

```

And what is the DE :
```

cat /etc/X11/default-display-manager
echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP

```
No GUI started then there will be no output

[INDENT][INDENT]I do feel your pain
[/INDENT][/INDENT]

---

