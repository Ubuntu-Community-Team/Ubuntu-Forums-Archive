---
title: "Geforce 8300 crashes on 14.04"
date: 2014-04-25
forum: Hardware
---

### Post by simstim2 on 2014-04-25
I am installing Ubuntu 14.04 on two machines with Geforce 8300 chipsets (Asus MSN-H/HDMI motherboards). Both are giving NAK bailout errors at the terminal and then eventually crash. This happens after a while when using the open-source Nvidia driver, and immediately on reboot if I install one of the proprietary Nvidia drivers. The same happens with both 32- and 64-bit versions of 14.04. 

The full error is: 

i2c i2c-2: sendbytes: NAK bailout

The machines worked fine with Ubuntu 13.10, so I am assuming this is something to do with the new kernel?

---

### Post by nedrerairo on 2014-04-25
there is a kernel update in the apt repos for 14.04 , did you do this update before installing the proprietary nvidia drivers?

i.e., output from console:  uname -a

---

### Post by simstim2 on 2014-04-25
I have just reinstalled and run the update to kernel 3.13.24.29, which I think is the latest one in the repo. Seems to be working a bit better with the open source driver, but still crashes on reboot when I install the nvidia driver.

---

### Post by simstim2 on 2014-04-25
Ah-ha, seem to have got it working now. So far stable with the nvidia drivers.

---

### Post by nedrerairo on 2014-04-25
ok, so the computer is stable with the nouveau driver after kernel update? good.

the question then is, which nvidia driver do you install when it crashes?

ubuntu driver search usually gives you 4 different suggestions (2 new versions, 2 of the old and apparently well tested), and tbh, I have no clue as to which works better than the other.  There is however the 331.* which is labeled as "tested", and it works for my gtx 670 card .. so my bet would be trying that one.

edit:

seems like you sorted it out, good :)

---

### Post by anthonytiongson on 2014-10-02
Can you let me know what you did to get it running stably? I'm experiencing the same issues as you. The Nouveau drivers are working for now, however I can't help but feel like I'd get more performance out of decoding h.264 and Steam In-Home streaming by using an NVIDIA proprietary driver.  I've so far tried the drivers presented in the Additional Driver utility and also one from NVIDIA's site, but using any other driver besides the Nouveau ones cause my display to lock up, artifact, and freeze.  Any input would be helpful on how you got it working on your end.> **simstim2 said:**
> Ah-ha, seem to have got it working now. So far stable with the nvidia drivers.

---

### Post by david-cavallini-gmail on 2015-05-16
I was stuck to old driver serie 304 because every recent drivers crashed (IGP Geforce 8300 on ASUS mainboard). Disabling MSI fixes the issue for me:
either disable on system level:
by adding: pci=nomsi to kernel boot command line
or just disable for nvidia module:
by creating a file named nvidia_whatever.conf in /etc/modprobe.d
with: options nvidia_340 NVreg_EnableMSI=0
remark: exact name for the module can be checked using: modinfo nvidia<TAB>

Verify then that the module does not use MSI anymore using:
cat /proc/interrupts | grep -i nvidia

---

