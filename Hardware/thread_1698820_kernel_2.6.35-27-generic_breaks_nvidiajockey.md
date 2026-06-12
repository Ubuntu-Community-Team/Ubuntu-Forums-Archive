---
title: "kernel 2.6.35-27-generic breaks nvidia/jockey?"
date: 2011-03-02
forum: Hardware
---

### Post by jbro on 2011-03-02
Hello,

Today I did a normal update through the Update Manager, which updated the kernel to 2.6.35-27. Once the update was done, I rebooted as normal. When the machine rebooted, it hung on the splash screen, right before starting X. I can log into the machine via ssh and everything else works, but I can't get into X. I am using 64-bit Maverick and an nVidia Quadro FX 1700 with the nvidia-current drivers.

Figuring I could get around this by just reinstalling the proprietary video drivers, I removed everything related to the nvidia drivers and rebooted. The machine booted fine, but now using the nouveau driver. However, when I go to System->Administration->Additional Drivers, it does not indicate that I can use the nvidia proprietary drivers. The GUI simply says "No proprietary drivers are in use on this system." I tried checking things out through jockey-text and it doesn't list any available drivers for my hardware.

So now I am stuck with nouveau, which is no good because I need hardware accelerated 3D. Has anyone else seen this problem? If so, have you managed to get around it? The nvidia-current drivers were working fine before this update.

Update: I removed the nouveau drivers and then rebooted into X with the VESA driver. I then did "jockey-text --check-composite" and I get "There is no available graphics driver for your system which supports the composite extension, or the current one already supports it." Clearly, VESA does not support compositing, so why can't jockey find the nvidia proprietary drivers?

---

### Post by havany on 2011-03-03
Hello,

Sorry for my poor english...

I have the same problem, and the solution is:

1 - Boot with the kernel 2.6.35-25 
2 - Desactivate nvidia driver, use "additional drivers" application in kde
3 - Reboot with the new kernel 2.6.35-27
4 - Re-activate nvidia driver
5 - Reboot

And if all is fine, it's work !

by

---

### Post by jbro on 2011-03-04
Unfortunately, I had completely removed all the nvidia package, so this did not do the trick. However, it did lead to a search that mentioned reinstalling nvidia-common, so I did this and now jockey detects that I can use the proprietary drivers, but when I install them, I'm back to where I started -- the machine's GUI hangs just before X starts, so the only way to log in is via ssh. I also cannot switch to any VT, I am just stuck at a pure purple screen.

Thanks.

---

### Post by Kareeser on 2011-03-08
jbro, I am having a similar issue, except I get dumped to a shell (which is at least workable, lol).

At work now, but I did notice that nVidia released a new driver update yesterday, so I am planning to try this out at home.

64-bit:
```

cd /usr/local/share/ && sudo mkdir nvidia && cd nvidia && wget http://us.download.nvidia.com/XFree86/Linux-x86_64/260.19.44/NVIDIA-Linux-x86_64-260.19.44.run
sudo service gdm stop # Just in case :)
sudo sh NVIDIA-Linux-x86_64-260.19.44.run

```

---

### Post by jbro on 2011-03-08
> **Kareeser said:**
> jbro, I am having a similar issue, except I get dumped to a shell (which is at least workable, lol).

At work now, but I did notice that nVidia released a new driver update yesterday, so I am planning to try this out at home.

Interesting. I could not wait any more to solve the problem, so I just reinstalled 10.10 preserving my home directory. After that everything worked fine. However, in fear of this happening again, I have not upgraded to the 2.6.35-27 kernel. Though I cannot prove it, I suspect 2.6.35-27 changed something that affected my nVidia setup. Perhaps the nVidia update will solve the problem if it happens again when I do an update. I'll be sure to image my root partition first before updating, though.

Regards.

---

### Post by Kareeser on 2011-03-08
Heya jbro,

Just got home, rebooted - worked fine. Guess nvidia stepped up, hm?

Doing an image is a good idea, although I find keeping a separate home partition easier. With a usb startup disk, I can format my computer and do a complete format be up and running in under 20 minutes. (minus updates, which can be postponed for a bit, really)

---

