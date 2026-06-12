---
title: "Ryzen 7 Pro 4750G Linux Support"
date: 2021-04-29
forum: Hardware
---

### Post by robn30 on 2021-04-29
I built a machine using the Renoir Ryzen 7 Pro 4750G APU and it runs beautifully on Ubuntu 20.04 but I would like to run Davinci Resolve but it keeps telling me that I need a qualifying GPU.  I have this machine dual booted with Windows 10 and Davinci Resolve runs perfect on Windows 10.  Are there any Linux Drivers for this APU that would work?  On Windows it detects the GPU as it should but on Ubuntu it doesn't, and I think that's the problem.

---

### Post by robn30 on 2021-04-29
I found this at the AMD site.  It says that this driver supports AMD Radeon RX Vega Series Graphics.  The 4750G runs Vega 8 which I believe is also RX Vega 8.  Am I correct in stating that?

[https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20)

---

### Post by robn30 on 2021-05-08
I tried installing the AMDGPU Drivers in an attempt to get Davinci Resolve operational and used the ./amdgpu-pro-install -y opencl=rocr, legacy but it made my graphics all wonkie.  In general it didn't work at all.  I had to uninstall it to get things working again.  Is there anyway with this APU to get Davinci Resolve working?  Do I need to use a different option with AMDGPU drivers.  Davinci Resolve works perfectly when I boot the machine on Windows 10 and using proprietary graphics drivers.  Any insight would be much appreciated.  Thanks.

---

### Post by mikewhatever on 2021-05-08
1. There aren't any secret "Linux drivers" for Vega GPUs.
2. Perhaps you could look up the exact hardware, and post the output: <lspci -nnk | grep -A3 VGA>.
3. I hope Ubuntu 20.04 runs beautifully on the Renoir Ryzen 7 Pro 4750G APU machine, and not the other way around. 
4. The link abobe has a list of supported GPUs. Is yours among them?
5. Perhaps you could also look up the reccomended hardware for that program.
6. I am very glad it works well on Windows, but now is the time for more relevant info to the problem at hand.

---

### Post by Yellow Pasque on 2021-05-09
Instead of using amdgpu-pro, try using the regular amdgpu installer. You shouldn't need the Pro stuff just to install OpenCL.

---

### Post by mastablasta on 2021-05-11
you might also want to explore newer kernel. by default 20.04 uses 5.4 version, but you can use HWE support to get newer version. more here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

