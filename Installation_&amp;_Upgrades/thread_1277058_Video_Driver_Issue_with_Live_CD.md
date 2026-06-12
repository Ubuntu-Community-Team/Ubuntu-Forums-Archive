---
title: "Video Driver Issue with Live CD"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by DrLew on 2009-09-27
I am an old hand at windoze but a newbe at Linux.
I cannot get the ubuntu live CD to complete. It appears that my video adapter, a NVIDIA Quatro FX580, is foreign to the drivers included with the distro.
I have MagicIso so I can put the Linux drivers in the iso if I knew where to put them and whether I should use the 64 bit or 32 bit driver.

Any help and guidance would be appreciated.

Thanks,

Lew

---

### Post by elliotn on 2009-09-27
its a liveCD rememba u might have to dload the drivers, but u cant install em in a liveCD.

---

### Post by overdrank on 2009-09-27
> **DrLew said:**
> I am an old hand at windoze but a newbe at Linux.
I cannot get the ubuntu live CD to complete. It appears that my video adapter, a NVIDIA Quatro FX580, is foreign to the drivers included with the distro.
I have MagicIso so I can put the Linux drivers in the iso if I knew where to put them and whether I should use the 64 bit or 32 bit driver.

Any help and guidance would be appreciated.

Thanks,

Lew

Hi and welcome, Have you tried any of the options under the F4 keys at the start install screen.

---

### Post by PmDematagoda on 2009-09-28
What version of Ubuntu are you trying to install? If it's 9.04 or less then support for the FX 580 still isn't there in the opensource nv driver which is included in Ubuntu 9.04, it was added after Ubuntu 9.04 was released.

To fix this problem you would:-

1) Have to install Ubuntu 9.10 which is still under development(not recommended if you are looking for stability). 

2) Include the latest proprietary driver from Nvidia in the live CD. The package required is:-
nvidia-glx-180

3) Use the alternate CD to install Ubuntu.

---

### Post by DrLew on 2009-09-28
Yes, I have been trying 9.04.
Where do I put the package in the CD iso?
 
I am after the partition resizing, is that stable in 9.10
 
What is the alternate CD that you are referring to?
 
Thanks,
Lew

---

### Post by PmDematagoda on 2009-09-28
I haven't made an ISO myself, so unfortunately I do not know where to put the package.

I am not sure about the stability of Karmic as of now, but perhaps you could try asking that question in the Development section, although if you are looking for stability you should try something else before trying Karmic.


The alternate CD is the text based installer CD which can be used to install Ubuntu when such problems like yours occur. It can be obtained from [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

