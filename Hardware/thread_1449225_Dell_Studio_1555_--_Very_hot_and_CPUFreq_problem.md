---
title: "Dell Studio 1555 -- Very hot and CPUFreq problem"
date: 2010-04-07
forum: Hardware
---

### Post by chenxiaolong on 2010-04-07
I'm running Ubuntu 9.10 x64 on a Dell Studio 1555 and after about an hour's usage, the computer gets hot to the point that I can't use the touchpad and have to use a USB mouse. The fan is always on at the same speed and does not change according to the temperature of the CPU. I'm using kernel 2.6.33 from the Ubuntu Kernel PPA (for my b43 driver testing -- for another thread). When I was testing other distros (namely Fedora, OpenSuSE, Arch, Sabayon, and Mandriva), none of their respective 2.6.33 kernels had this problem (if it has to do with the kernel).

I'm not sure if this has to do with CPUFreq, but CPUFreq does not change the processor speed at all, even on "On Demand" mode. I have to set the speed manually from 1.20 GHz to 2.10 GHz every time I need to use a resource intensive program.

I'm not sure what caused these problems. Is there a certain config option I need to change in the kernel or is there a newer version of a package that I need to compile?

Thanks for any help.

---

### Post by free2talk.183 on 2010-05-01
I am using ubuntu 10.04 x64 on dell studio 1555 and experiencing same issue . It becomes very hot and the battery life decreases to half as compared to windows 7 ! I am using 2.6.32 kernel

---

### Post by MichealH on 2010-05-01
For the heat it could be a Fan Blockage. If There is an issue with the CPU using a particular program File a bug report on Launchpad.

---

### Post by chenxiaolong on 2010-05-01
My computer runs much cooler under Windows 7, even if I leave it on for a week straight, whereas it's hot to the touch after using it for about 8 hours under Ubuntu. This happens in Kernel 2.6.32 and 2.6.33. Kernel 2.6.34-RC6 seems to have fixed it somewhat; still not as cool (as in temperature :D) as Windows.

---

