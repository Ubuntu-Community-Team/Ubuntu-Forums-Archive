---
title: "old equipment"
date: 2024-07-08
forum: Hardware
---

### Post by vpn9601 on 2024-07-08
I'm interested in the question - there are all sorts of distributions for old machines with low resource consumption. The question is, how do these distros solve the problem of video card drivers? I have an old Asus p5k machine at home, I loaded it with 24.04 lts, and there is a problem with the Nvidia 8800 driver. If before, at the very least, it was possible to edit the xorg file, but now my friend said that now it is almost impossible, you need to change the computer. The free driver certainly works, but everything is fuzzy. Interested to get a comment on this

---

### Post by TheFu on 2024-07-08
They use VESA drivers, which suck.  For nvidia stuff there are the F/LOSS drivers when nvidia drops support after 5-10 yrs.  From my experience, this is mainly an issue with nvidia, as AMD and Intel GPU driver support is in the modern kernels from v5.10 and later.

You could just get a newer GPU that is still supported if you decide to stick with nvidia, but why.  PCIe is PCIe, after all.  Next time, if you aren't spending $1000+ on the GPU, skip nVidia and get a well, long, supported GPU from someone else.

---

### Post by guiverc on 2024-07-08
> **vpn9601 said:**
> I'm interested in the question - there are all sorts of distributions for old machines with low resource consumption. The question is, how do these distros solve the problem of video card drivers? I have an old Asus p5k machine at home, I loaded it with 24.04 lts, and there is a problem with the Nvidia 8800 driver. If before, at the very least, it was possible to edit the xorg file, but now my friend said that now it is almost impossible, you need to change the computer. The free driver certainly works, but everything is fuzzy. Interested to get a comment on this

I don't know your hardware, but I'll comment generally.

The oldest machine I use in *Quality Assurance* testing of Ubuntu and *flavors* is a 2005 HP Compaq. I've changed hardware in that box many times though; with it having many times more RAM, a newer CPU (*original was giving me problems*), but is still the same mainboard, but I've swapped video cards numerous times.

That box has a Nvidia card in it (*I can't recall what, and aren't going to look*), but as the box is mostly used in install testing, I didn't want the additional hassles of video issues, thus the last change of video cards.

What I have noted though (*and I use a number of machines though most are two+ years younger than that 2005 box*) is what you install & use makes a difference.

The kernel makes a huge difference, as kernel modules (aka *drivers*) are related to the kernel in use, thus if using a LTS kernel stack on really old hardware, I often find the least problems with the GA or older kernel option.

Up until August-2020 my oldest hardware used in QA dated back to 2003, but some of those devices (*laptops so not easily changed*) started having issues with the 5.3 kernel from 19.10, and thus also had issues with 18.04 when it upgraded to that (*and using the HWE kernel stack*), and again at 20.04/18.04.5. The easiest fix for that was sticking with 18.04 and using the GA kernel stack; which had 5 years of *standard* support anyway.

Problems usually appear first in GNOME then KDE Plasma on a kernel, in time they'll appear in Budgie/MATE & other desktops... before finally appearing much much later in Xfce or LXDE/LXQt. Back in the 2019-2021 age I found LXDE/LXQt the last impacted with Xfce before that... however more recently the last impacted is Xfce, and these issues are often related to Nvidia GPUs I'm talking about here.

For my boxes used in install testing; I just replaced the GPU when it started taking time away from what I wanted to do with the box; this is an easy option with desktop systems and not as easy for laptops.

If you can't change the hardware, the next choice is trying different Desktops, as the lighter desktops usually have fewer graphical glitches for a given kernel, but also even more useful is just using an older kernel stack when you have an option (for non-LTS that's an older LTS, if its a LTS then try the older kernel GA stack).  

Ubuntu 24.04 LTS is still *new*, and the GA & HWE kernel stacks are still the same, but if using older releases such as 20.04 - you can download ISOs with the 5.4, 5.8, 5.11, 5.13 & 5.15 kernels for trial, for 22.04 you can get 5.15, 5.19, 6.2, 6.5 ... and whilst not all are *supported* as they'll upgrade post-install, the oldest (GA) & newest (HWE) are still supported and get security fixes/patches.

---

### Post by Yellow Pasque on 2024-07-09
There is a version of 340 packaged for noble/24.04 here: [https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy](https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy)
I have no idea whether it works or not. The 390 driver has issues with 24.04

---

