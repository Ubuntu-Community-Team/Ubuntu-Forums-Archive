---
title: "Brand new laptop, external display not detected, need help please!"
date: 2020-08-06
forum: Hardware
---

### Post by muzzernz on 2020-08-06
New laptop 

HP-ProBook-455-G7

AMD® Ryzen 7 4700u with radeon graphics × 8 

HDMI external display works fine on Windows but does not detect on Ubuntu 18.04. Not detected on xrandr.

Can someone please offer assistance.... :-)

[ATTACH=CONFIG]286631[/ATTACH]

[ATTACH=CONFIG]286632[/ATTACH]

---

### Post by TheFu on 2020-08-07
[https://www.phoronix.com/scan.php?page=article&item=ryzen7-4700u-linux&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen7-4700u-linux&num=1)
> Ubuntu 20.04 LTS is shipping with the Linux 5.4 kernel and Mesa 20.0, which that kernel is slightly too old for Renoir out-of-the-box.

Getting a newer kernel might help.  5.6 or later.  You've found the bleeding edge.

That's my best guess, but I know next to nothing about AMD laptop onboard GPUs.

---

### Post by muzzernz on 2020-08-08
@TheFu, thx, can you update to a 20.04 kernel but stay wiit 18.04 release? I upgraded to 20.04 but could not get a few web server issues resolved with specific PHP/mySQL versions so went back to 18.04 which I'd now rather stick with.

---

### Post by TheFu on 2020-08-08
I think the kernels are separate from the userspace programs.  People grab the latest alpha kernels from kernel.org and run those on pretty much any Linux they want.  I haven't needed to do that in decades, so I don't know the process under ubuntu, but I bet a websearch for "new kernel ubuntu" would find a guide from a reputable source to add a new kernel to your grub setup.  Anything goes bad, just reboot and choose one of the older kernels.

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds) seems like the good instructions.  Don't know your level of expertise, so you'll have to decide whether that is something worthy of your time and skill level.

---

### Post by muzzernz on 2020-08-08
Thank You! Never messed with kernel level before but will give it a shot! Cheers

---

### Post by muzzernz on 2020-08-13
OK, just installed latest 20.04 and Kubuntu 18.04. Neither show any signs of detecting HDMI monitor.

As Windows detects it fine I'm assuming this is not an HDMI or hardware problem, or a BIOS issue.

Any hints on where to go next with this?

---

### Post by CelticWarrior on 2020-08-13
Post #2 has the answer.

---

### Post by kurt18947 on 2020-08-14
I too had problems with Ryzen and integrated graphics running 18.04. That install eventually got so bad it would no longer boot. You could try using Wayland instead of X.org, that seemed a little better in 18.04. The problems went away after installing 20.04. I think it wasn't just the newer kernel but also newer video components.

---

### Post by mastablasta on 2020-08-17
> **muzzernz said:**
> OK, just installed latest 20.04 and Kubuntu 18.04. Neither show any signs of detecting HDMI monitor.

As Windows detects it fine I'm assuming this is not an HDMI or hardware problem, or a BIOS issue.

Any hints on where to go next with this?


you need newest kernel possible. drivers are in kernel. you have very new hardware, so you need latest driver.

optionally you can try patching it with latest drivers. however this could cause issues if you are using secure boot.

2 months ago i was chekcing out the Ryzen 5 version of this HP and people had issue even installing linux on it.

---

