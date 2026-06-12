---
title: "nvidia fx 5500  configure on ubuntu?"
date: 2015-05-17
forum: Hardware
---

### Post by Portaro on 2015-05-17
I'm buy recently this card nvidia fx 5500 to have a replace card to this old pc, but I try to install the drivers that can I see on the package manager , nvidia-173.

However I see that this  drivers dont work-

What I can do to configure properly the driver on Lubuntu?

[[img=http://s25.postimg.org/6qc9lvsnf/2015_05_17_185016_1280x1024_scrot.jpg]](http://postimg.org/image/6qc9lvsnf/)

---

### Post by Portaro on 2015-05-17
Well , I find an amazing help on a external forum & amazing Debian, UBuntu, Arch, Slack community of friend users of GNU/linux called - GNULinuxVagos - you can see the solution on the forum here - [http://gnulinuxvagos.es/topic/4674-nvidia-fx-5500-es-posible-configurar-con-driver-en-ubuntu-14/page-3#entry29485](http://gnulinuxvagos.es/topic/4674-nvidia-fx-5500-es-posible-configurar-con-driver-en-ubuntu-14/page-3#entry29485)

Very easy if you need .

**Install nvidia** (version of your required card) by Ubuntu repository - for me is nvidia-173 for my fx 5500 .

> sudo apt-get install nvidia-173 nvidia-settings

**Add xorg edgers **ppa to your repos - [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

**Update , upgrade you softwares by synaptic to see if appear any update of xorg-edgers**, if see any install.

**Then see if in the process of updates appear any message like** - ERROR (dkms apport): kernel package .... is not supported.

**If in your case you see this message you need other kernel** in my case **I install 3.13.0-49 **and then works - 

**Try the command :**
> $ lsmod |grep nvi

[B]if you have an error on the command return, you need test other kernel, I recommend 3.13.0.49 is the lts kernel. 
[/B]If you see the external forum thread you can see that I test Liquorix, and 3.16 and I have problems to enable the driver configs properly on this kernels.

**When you have a kernel configured with driver , the result of command**:

> $ lsmod |grep nvi 

**he is always a good  return like** ->

> $ lsmod |grep nvi
nvidia               7108418  24 

I hope this help others if need, and finally thanks for Shiba87 by GNULinuxVagos.ES  because he help me on the path to solve my problems day after day.

Thanks.

---

