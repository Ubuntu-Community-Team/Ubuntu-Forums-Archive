---
title: "nvidia drivers 460 error 1"
date: 2021-01-10
forum: Hardware
---

### Post by LMH1 on 2021-01-10
Did anybody know why nvidia drivers 460 get error:

> 
[FONT=monospace][COLOR=#000000]nvidia-dkms-460 [/COLOR]
 nvidia-driver-460 
 nvidia-driver-455 
E: Sub-process /usr/bin/dpkg returned an error code (1)
[FONT=monospace][COLOR=#000000]ERROR (dkms apport): kernel package linux-headers-5.10.0-051000rc6-generic is not supported [/COLOR]
Error! Bad return status for module build on kernel: 5.10.0-051000rc6-generic (x86_64) 
Consult /var/lib/dkms/nvidia/460.32.03/build/make.log for more information. 
dpkg: error processing package nvidia-dkms-460 (--configure): 
 installed nvidia-dkms-460 package post-installation script subprocess returned error exit status 10 
dpkg: dependency problems prevent configuration of nvidia-driver-460: 
 nvidia-driver-460 need [FONT=monospace][COLOR=#000000]nvidia-dkms-460 (<= 460.32.03-1)[/COLOR]
[/FONT][/FONT][/FONT]


Its works nice with linux mint 20.1 or 20, so why did its have issue with ubuntu 20.10? Did i need to upgrade kernel?

---

### Post by Yellow Pasque on 2021-01-11
kernel: 5.10.0-051000rc6-generic is not a standard Ubuntu kernel. Why you are using an old release candidate kernel of 5.10.x? More information needed..

---

### Post by LMH1 on 2021-01-15
What information needet? how to upgrade? look like ubuntu 20.04 works better with 
[IMG]https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/install-new-linux-kernel-11-1.png?[/IMG]

---

### Post by LMH1 on 2021-03-18
i find out if i upgrade to kernel 5.11 its fix issue, but why is issue with screen with nvidia 461 drivers? Kubuntu 20.10 Its not issue with Linux Mint 20.1 Ulyssa (GTX Titan first gen SLI) i use GTX 1080 TI on ubuntu. [https://ubuntuhandbook.org/index.php/2021/02/linux-kernel-5-11released-install-ubuntu-linux-mint/](https://ubuntuhandbook.org/index.php/2021/02/linux-kernel-5-11released-install-ubuntu-linux-mint/)  So can someone confirm its issue With kernel 5.11 and [https://www.nvidia.com/Download/driverResults.aspx/171392/en-us](https://www.nvidia.com/Download/driverResults.aspx/171392/en-us) Because i think quality of desktop image is better in windows 10 than linux. Text be sometimes invissible did not know why?  Did not get kernel upgrade software to works on 20.10 only 20.04 or older.

---

