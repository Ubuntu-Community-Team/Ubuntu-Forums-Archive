---
title: "Nvidia drivers crash - failsafe VESA driver loaded instead"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by t-dome on 2007-11-07
Hi,

I'm using Ubuntu 7.10 and I have a Turion X2 notebook with Geforce Go 7300 graphics.

The open source "nv" driver work, but they're too lame. I installed the newest proprietary driver (V 100.14.19) using synaptic, but this driver crashes after every few minutes. The same happens with Kubuntu 7.10 and Open Suse 10.3. I followed another post with one guy using a desktop Geforce 7300 graphics card, who had the same issue as me. He got rid of the crashed with an older nvidia driver, V 100.14.03.

It doesn't matter if I use compiz-fusion or not.
I tried older nvidia drivers (100.14.03 and 96.xx) but they don't even start. Ubuntu starts in the safe graphics mode with the VESA driver, but I can't find any error message in the logs. In Xorg.0.log it states that "xorg.conf.failsafe" was used, but I can't find the reason why or any error message!

Now I cannot even use the 100.14.19 driver anymore, which worked before. The same things happen.
After every retry I delete the previous drivers with "sudo ./NVIDIA-....run --uninstall", so that the right nvidia kernel module is loaded after installing other nvidia drivers.

-did the graphics memory check fail? This happened to me under Kubuntu 6.06 and 7.04 before with various nvidia cards and chipsets;
-did the graphics chip detection fail?
I have no idea, I can't find any error message.

Do you know where I can find any log file for this "failsafe VESA driver" or a solution the nvidia problem?

PS: this is how I manually install the nvidia drivers, excepting V100.14.19 which are in the ubuntu repository: I log off, then I switch to the first text terminal with ctrl-alt-f1. Then I kill GDM and run the install "script". Am I doing something wring?

Many thanks

---

