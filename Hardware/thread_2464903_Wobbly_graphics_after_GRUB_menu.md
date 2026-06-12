---
title: "Wobbly graphics after GRUB menu"
date: 2021-07-15
forum: Hardware
---

### Post by troffasky on 2021-07-15
Lenovo Y70-70
Kubuntu 21.04.
I am having a problem with the builtin screen on my laptop, whereby after the GRUB menu, there is horrible wobbling of the video from side to side.
[https://www.youtube.com/watch?v=LyRTuPzCe2I](https://www.youtube.com/watch?v=LyRTuPzCe2I) doesn't really do it justice, it's far worse IRL and a few tens of seconds is enough to give you a headache.
If I select recovery mode and continue boot, it works OK [ish - I then can't use the HDMI output]. Letting it boot by default leads to the issue from the disk decryption prompt onwards and even affects the text-mode console.
I think I had this issue when I first got this laptop in 2014 but I can't remember what the fix was. In the couple of times I have reinstalled since then, the issue has not recurred.
The issue began this time when I installed the Nvidia drivers in an attempt to improve the frame rate on a new UHD monitor I have connected. It obviously can't be anything to do with the Nvidia drivers if it happens  straight after the grub menu though, right?

---

### Post by cryptearth on 2021-07-15
Well, that looks bad, sorry to see that. It's a very wild guess in the blue - but after reading your post twice I still suspect it may could be a hardware issue.
As you said you encountered the issue the very first time you got the device I would had RMA'ed it as faulty righty away - the issue you experience shouldn't happen at all - no matter of driver used.

But, I also got a bit deeper into it - so, let me address my ideas one by one:

1) From the time it takes from GRUB to the unlock screen it seems like the kernel and initamdisk is loaded and the system switches from text console to graphics mode - hence the nvidia driver seems already be loaded. And, as you said you got this error after installing the nVidia driver it very well could be a driver issue.
2) You mentioned a UHD display - so anything bigger than 1920x1080. According to its datasheet your system has a [COLOR=#333333][FONT=Lato]NV N15P-GX gpu - which, according to google, is a GTX 860M. A TechPowerUp report I found here [/FONT][/COLOR]https://www.techpowerup.com/gpu-specs/geforce-gtx-860m.c2536 suggests only resolutions up to 1600x900 - and 1920x1080 is already marked yellow. So, no matter the used driver, the chip doesn't have enough power for a UHD screen anyway - and I guess it uses a far old HDMI standard not able to drive that resolution.
3) As I use two nVidia GPUs in my KVM host (my AMD card failed after overheating after I did not noticed a failed fan soon enough) I experienced issues after installing the nVidia driver myself, both on the host as well as in the kvm guest. I had to log in via ssh and purge it to get the host up and fully running again. As for the kvm guest - well, I was able to figure it out to get it at least running without issues. TLDR: Using vendor gpu drivers, no matter if nVidia or AMD, seems to always ends up in issues - but using the open source drivers most distros come with often not unlock the full 3D power of them. Just one reason why I set up a KVM and use windows within it and a passed through gpu for games - aside from all that werid anti-cheating services crap modern games require and work on Linux natively.

I would recommend this: Boot up the system either in rescue mode or log into it remotely via ssh and purge the nvidia driver (switch to no-gui mode with SUDO TELINIT 3) and re-install the nouveau driver (should be used again automatically if you not purged it after installing the nvidia driver). This why you should at least get up a clear screen again for the main integrated screen. As for your external uhd screen - I'm not so sure about that - but I would guess it's just simply the combination of the gpu chip not having enough "oomph" to drive it and the hdmi link using a too old spec hence not able to transfer enough bandwidth even if the gpu chip would able to power uhd with at least 60hz. Or, to put it simple: Your device might just be too old for a uhd (4k?) screen.

Please keep in mind: These are just possible guesses based on my personal experience and knowledge from what was I able to find from the device model you provided. I may be wrong - as it's often said: "your mileage may vary".

---

### Post by troffasky on 2021-07-16
Yes, GT860M. 
It can drive an external display adequately [ie 60Hz] at 2560x1440 so I am happy to live with that, but really want to use both displays at the same time.
I am back on the Nouveau driver now. I will purge the Nvidia driver later tonight and report back. With the Nvidia driver installed, X will not start at all [as the warning says might happen] when in recovery mode.
> 
1) From the time it takes from GRUB to the unlock screen it seems like the kernel and initamdisk is loaded and the system switches from text console to graphics mode - hence the nvidia driver seems already be loaded.
I am surprised by this, given how quick it is, but I don't really have any other explanation.

---

### Post by troffasky on 2021-07-16
So I tried 

dpkg -P nvidia-settings nvidia-prime nvidia-kernel-common-460 nvidia-dkms-460 nvidia-compute-utils-460 libnvidia-compute-460:i386 libnvidia-compute-460:amd64


and it made no difference. I uninstalled and reinstalled the Nouveau Xorg driver, no difference.
What did make a difference, however, was....booting the previous kernel.

linux-image-5.11.0-18-generic    = all Ok
linux-image-5.11.0-22-generic    = wobbly video

Rebooting after messing about with Nvidia drivers was probably the first time I booted with that newer kernel and this was all just an annoying coincidence.
So how can I track down what has changed here or report a bug against the right thing?

---

### Post by troffasky on 2021-07-16
This guy might be having the same issue:
[https://forum.ubuntuusers.de/topic/laptop-monitor-flackert/](https://forum.ubuntuusers.de/topic/laptop-monitor-flackert/)

This guy *definitely* is:
[https://askubuntu.com/questions/1351188/weird-graphical-glitches-appears-only-on-integrated-display-on-any-ubuntu-base#](https://askubuntu.com/questions/1351188/weird-graphical-glitches-appears-only-on-integrated-display-on-any-ubuntu-base#)

---

### Post by cryptearth on 2021-07-17
Well, I wasn't able to find a changelog - but that's worth investigating further.

---

### Post by troffasky on 2021-07-19
I've logged this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1936708](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1936708)

---

