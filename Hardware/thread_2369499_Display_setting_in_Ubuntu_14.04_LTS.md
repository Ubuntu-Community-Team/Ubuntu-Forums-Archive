---
title: "Display setting in Ubuntu 14.04 LTS"
date: 2017-08-23
forum: Hardware
---

### Post by rkmpalai on 2017-08-23
When we go to All Settings --> Display, there is only one resolution 1024 x 768 (4:3). This resolution make the windows and fonts appear big. Kindly guide us as to how change the resolution of the display. Our graphics hardware has the name 'Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)' and our processor is 'Intel® Core™ i3-6098P CPU @ 3.60GHz × 4'.

---

### Post by deadflowr on 2017-08-23
> Our graphics hardware has the name 'Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)' and our processor is 'Intel® Core&#8482; i3-6098P CPU @ 3.60GHz × 4'.
llvmpipe means the system is running in software mode, which means it's running in the cpu, as opposed to running in a graphics processor.
In layman's terms it means you're graphics card isn't properly set up. 
(It can, rarely, also mean the graphics card is not powerful enough to run Ubuntu normally; That seems doubtful, though, to me)
Unfortunately llvmpipe output is generic and can mean you have any number of gpus.

We might be able to cut that down if you open a terminal (press ctrl + alt + T, that usually works to open a terminal)
and enter this
```
lspci | grep VGA
```
the output should give us an idea of what's what.
(As this will give us the actual hardware name, be it intel or amd, or nvidia or any other graphics card)

Post back the output please.

---

### Post by rkmpalai on 2017-08-23
Thanks for your prompt reply. Please find the output below

ramakrishna@not-fully-s-this-version-of-dmidecode-H110M-S2:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 1902 (rev 06)
ramakrishna@not-fully-s-this-version-of-dmidecode-H110M-S2:~$

---

### Post by deadflowr on 2017-08-24
The output seems to indicate it's a skylake gpu.
My understanding is that it's not supported on 14.04's original kernel (ver 3.13)
but should be supported on 14.04's hwe kernel (ver 4.4)

To tell if you are using the 3.13 kernel or the 4.4 kernel again in a terminal run
```
uname -r
```
if 3.13 then you can see if updating the hardware stack to the hwe version fixes the issue

About hwe and what that means (and how to install it):
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

If that is not the problem then something else must be going on here.
I'm not attuned enough to the workings of skylake and what might need to be done, so hopefully an upgraded hardware stack will fix it out right.

---

### Post by rkmpalai on 2017-08-24
Thank you very much. After following your guidelines the display is working fine now.

---

