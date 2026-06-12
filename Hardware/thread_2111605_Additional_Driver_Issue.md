---
title: "Additional Driver Issue"
date: 2013-02-02
forum: Hardware
---

### Post by chazdg24 on 2013-02-02
I am running 12.04 and have had issues with my ATI drivers for my 5870 card.  Growing frustrated, I installed the latest Kernel available, 3.7.5.  I was given several options for the video driver when I rebooted.  The one driver that solved my problem was the fglrx experimental driver.  It was a relief to get it to work.  The kernel improves speed on my system dramatically.

The issue is several drivers appear not to be activated and will not activate.  It does say the driver was deactivated but is still functioning.  I am directed to the var/log/jockey which I can't make any sense of (I can post it if need be - it is very long).  Can someone suggest a fix for this issue?  The drivers are as follows:

1801 smbus driver
Intel TCO Watchdog Timer Driver
USB HID BOOT Protocol Driver
USB HiD BOOT Protocol mouse driver

---

### Post by grahammechanical on 2013-02-02
Ubuntu 12.10 has the Linux kernel 3.5.0. It is intended to bring the 3.5.0 series kernel into 12.04. This has been tested. I have an install of 12.04.1 that uses the 3.5.0 series kernel. I found that some of the listed Nvidia drivers would not work with that kernel. This is why we are given a selection of drivers to try.

Raring Ringtail (13.04 under development) was given the Linux 3.7.0 series kernel early on in its development cycle and is now running Linux 3.8.0 series.

Using the Linux kernel 3.7.0 on 12.04 is untested by Ubuntu developers and you are also using an experimental video driver. You are in uncharted waters. Have you since rebooted?

You may find that Additional Drivers in 12.04 in not able to cope with the present set up. Additional Drivers has been moved into a tab in Software Sources in 12.10 and 13.04 and may be it has had other work done on it to handle these kernels and drivers.

You are now in Ubuntu+1 territory whilst still on Ubuntu. See the discussion going on here:

[http://ubuntuforums.org/showthread.php?t=2074962]("http://ubuntuforums.org/showthread.php?t=2074962")

Regards.

---

### Post by chazdg24 on 2013-02-02
> **grahammechanical said:**
> Using the Linux kernel 3.7.0 on 12.04 is untested by Ubuntu developers and you are also using an experimental video driver. You are in uncharted waters. Have you since rebooted?

You may find that Additional Drivers in 12.04 in not able to cope with the present set up. Additional Drivers has been moved into a tab in Software Sources in 12.10 and 13.04 and may be it has had other work done on it to handle these kernels and drivers.

You are now in Ubuntu+1 territory whilst still on Ubuntu. See the discussion going on here:

[http://ubuntuforums.org/showthread.php?t=2074962]("http://ubuntuforums.org/showthread.php?t=2074962")

Regards.

I have with great success.  The experimental driver works perfectly with 12.04 and my system is much faster.  BTW, I downgraded from 12.10 as I could never get any driver to work properly with it.  First Ubuntu release I had this issue.

---

### Post by chazdg24 on 2013-02-03
It appears as if the issue is a Realtek driver issue. The error in the jockey.log is as follows:

Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-1.fw for module r8169 W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-1.fw for module r8169 

I'm way over my head on how to address this issue.

---

### Post by Yellow Pasque on 2013-02-03
Those files are found in the Ubuntu 12.10 firmware package, but not in 12.04/Precise, so you'll have to manually put them in /lib/firmware/rtl_nic. They're attached for your convenience, so download it to your home folder and:
```
sudo modprobe -v -r r8169
cd ~/; tar xzf realtekfw.tar.gz
sudo cp rtl8* /lib/firmware/rtl_nic/
sudo depmod -a
sudo modprobe -v r8169
```

---

### Post by chazdg24 on 2013-02-03
> **Temüjin said:**
> Those files are found in the Ubuntu 12.10 firmware package, but not in 12.04/Precise, so you'll have to manually put them in /lib/firmware/rtl_nic. They're attached for your convenience, so download it to your home folder and:
```
sudo modprobe -v -r r8169
cd ~/; tar xzf realtekfw.tar.gz
sudo cp rtl8* /lib/firmware/rtl_nic/
sudo depmod -a
sudo modprobe -v r8169
```

That worked like a charm.  I really appreciate it.  I failed to mention that I also had the following issue in jockey:

ERROR (dkms apport): kernel package linux-headers-3.7.5-030705-generic is not supported.  Is this in 12.10 as well?

---

### Post by Yellow Pasque on 2013-02-03
I'm not really sure what that error's about (maybe because you're not using the standard kernel, apport won't automatically report errors on it).

---

### Post by chazdg24 on 2013-02-03
> **Temüjin said:**
> I'm not really sure what that error's about (maybe because you're not using the standard kernel, apport won't automatically report errors on it).

I disabled apport when I reinstalled 12.04.  I'm not sure it matters as my system is running flawlessly as far as I can tell!

---

