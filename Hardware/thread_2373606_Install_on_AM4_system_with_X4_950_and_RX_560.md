---
title: "Install on AM4 system with X4 950 and RX 560"
date: 2017-10-07
forum: Hardware
---

### Post by H3R3T1K on 2017-10-07
I've only ever used Ubuntu on Intel-based systems. Also AM4 is quite new and I don't know what the state is regarding AMD graphics drivers. I plan to dual boot Windows and Ubuntu. The former will be used for play, the latter for (office) work and surfing. Will there be compatibility issues?

---

### Post by kurt18947 on 2017-10-07
As I understand it, there are two AMD graphics drivers, Radeon and AMDGPU. The latter is intended for newer higher performance graphics systems. I have an older AMD system which works with no issues but Ryzen is pretty new. If I were going to run Ubuntu on a Ryzen/AM4 system, I'd use newer releases/kernels. I've had an itch to replace my Athlon II X2 system but I'm inclined to wait 'til 18.04 has been in the wild for a while.

---

### Post by Yellow Pasque on 2017-10-08
[https://www.phoronix.com/scan.php?page=article&item=radeon-rx580-linux&num=1](https://www.phoronix.com/scan.php?page=article&item=radeon-rx580-linux&num=1)
[https://www.phoronix.com/scan.php?page=article&item=radeon-rx-560&num=1](https://www.phoronix.com/scan.php?page=article&item=radeon-rx-560&num=1)

The same site also has a couple of AM4 mobo's reviewed: [https://www.phoronix.com/scan.php?page=category&item=Motherboards](https://www.phoronix.com/scan.php?page=category&item=Motherboards)

---

### Post by H3R3T1K on 2017-10-08
Well I don't need great gaming performance on Linux. I want to keep Windows for gaming only and do my work on Ubuntu which I trust indefinitely more as a platform for getting stuff done. Will chipset and CPU be supported?

---

### Post by Yellow Pasque on 2017-10-08
> Will chipset and CPU be supported? 

They will be supported in Ubuntu 16.04.3 and Ubuntu 17.xx. Will they be free of bugs? No one's going to make you that guarantee..
I also advise doing your homework on whatever specific mobo model you intend to use.

For graphics, you should be aware of this:
> The major support shortcoming right now for the Radeon RX 500 series on the mainline Linux driver is no support for FreeSync nor HDMI/DP audio nor any other advanced display features implemented only on the DC (formerly DAL) display stack.
Hopefully, this support will be ready "out of the box" for Ubuntu 18.04.

---

### Post by kurt18947 on 2017-10-11
Here is some info that might be relevant to current AMD Ryzen and possibly older systems:

[http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx#](http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx#)

---

