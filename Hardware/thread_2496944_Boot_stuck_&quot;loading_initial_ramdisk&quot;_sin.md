---
title: "Boot stuck &quot;loading initial ramdisk&quot; since 6.5.0-33,GeForce GF117M - 6.5.0-27 works"
date: 2024-04-18
forum: Hardware
---

### Post by isoaglib on 2024-04-18
I have a quite old notebook from Acer (Aspire E17) with the following graphic hardware:
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] (rev a1)
	Subsystem: Acer Incorporated [ALI] GeForce 820M

I use kubuntu 23.10 with the nouveau driver.
Everything works fine with Kernel 6.5.0-**27.**
But the newer kernels 6.5.0-**33** and 6.5.0-**34** cause problems - even with rescue boot mode, nothing happens after displaying "loading initial ramdisk".
I tried already to install the nvidia 390 driver. But as the configuration step of "apt-get install" triggers some faults, I removed those packages again.

So my questions:
What changed between 6.5.0-27 and 6.5.0-3x, which could cause a boot problem with an integrated NVIDIA GF117M?
What could I do, to get 6.5.0-3x running again? 
Is there a chance, that (k)ubuntu 24.04 will work with GF117M (GeForce 820M)?

Bye,
Achim

[EDIT]**[SOLVED]**:
I installed today the kernel **6.5.0-40-generic **- and THIS one provides again a **running nouveau driver for my old GF117M graphic system**. Whatever was different in 6.5.0-3x - this has been fixed in 6.5.0-40. So there is no need to switch to the NVIDIA proprietary driver PPA - nouveau works fine for my needs.

---

### Post by MAFoElffen on 2024-04-21
It's an NVidia 390 driver problem with the newer kernels. There is a work-around for it...

Use the nvidia-driver-390 from this PPA: [https://launchpad.net/~dtl131/+archive/ubuntu/nvidiaexp](https://launchpad.net/~dtl131/+archive/ubuntu/nvidiaexp)

Join this bug "as affected": [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2051436](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2051436)

---

### Post by isoaglib on 2024-04-21
Hi MAFoElffen,
thanks for your hint - I tried it - but it made things worse - I was not even able to boot 6.5.0-27 at my 23.10 Kubuntu.
With nvidia-driver-390 from the cited PPA, the 6.5.0-34 kernel still got stuck directly after boot of RAMdisk (even in rescue mode).
When I booted 6.5.0-27, I had to force booting to level "3" (i.a. Commandline), to get my notebook up and running in interactive mode. When I call "startx" within level "3", I get a blank black screen with a white underscore in the top left corner. The LOG in /var/log/Xorg.0.log provided no error information - only several debug information which don't indicate any problem source (i.e. graphic card found, modesettings detected ..).
After purging nvidia 390 from my system, I'm able to use the nouveau driver with kernel 6.5.0.27.

Thus I'm stuck with linux 6.5.0-27 kernel.

Any other ideas?
It's strange, that there is such a big difference between minor revision changes - from 6.5.0-27 to 6.5.0-33

Bye,
Achim

---

### Post by MAFoElffen on 2024-04-22
Mine:
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt list nvidia-driver* --installed
Listing... Done
nvidia-driver-390/jammy,now 390.157-0ubuntu9~nvidiaexp4 amd64 [installed]
N: There are 2 additional versions. Please use the '-a' switch to see them.
mafoelffen@Mikes-ThinkPad-T520:~$ uname -r
6.5.0-27-generic

```
So how is "yours" different than mine?

---

### Post by Yellow Pasque on 2024-04-24
> **isoaglib said:**
> But the newer kernels 6.5.0-**33** and 6.5.0-**34** cause problems - even with rescue boot mode, nothing happens after displaying "loading initial ramdisk".
Then it seems very unlikely the graphics (especially the Nvidia GPU) are the problem. Note that by default, your laptop uses the Intel GPU to run the system and only uses the Nvidia GPU when you explicitly tell the system to use it for something (with DRI_PRIME=1).

> What changed between 6.5.0-27 and 6.5.0-3x, which could cause a boot problem with an integrated NVIDIA GF117M?
Again, I don't think the Nvidia GPU is the issue. When you boot into rescue mode, can you get to a terminal by pressing Ctrl+Alt+F1 ? If you can, look for clues in (especially towards the end of the log):
```
sudo dmesg
sudo journalctl -b
```

> Is there a chance, that (k)ubuntu 24.04 will work with GF117M (GeForce 820M)?
There's a chance. But unless you figure out the exact cause, no one can tell you for sure whether it will work. You're going to have to upgrade to 24.04 in the next few months anyway. Maybe try a LiveUSB first when 24.04 is released (tomorrow, IIRC).

---

### Post by Yellow Pasque on 2024-04-24
One other thought - If you're going to use the Nvidia 390 driver, make sure you're using X11 and not Wayland.

---

