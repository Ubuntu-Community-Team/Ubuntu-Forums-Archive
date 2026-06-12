---
title: "no wireless with compaq 615"
date: 2010-04-06
forum: Hardware
---

### Post by mett demon on 2010-04-06
Hi there, I am a total noob to anything ubuntu. I have a compaq 615 laptop and have tried various versions so far (kubuntu, ubuntu, ubuntu netbook remix all in 9.10 flavour) but cannot get a wireless connection established. I am currently running Kubuntu (my chosen flavour) and when I check the NETWORK MANAGER it doesn't give me the option to setup a wireless network. I have checked and wireless is enabled. Am i missing something????????????? thanking you in advance

---

### Post by gornety on 2010-07-21
I am is in the same deep stress.
My compaq 615 is QL-66 ATI Radeon 3200.
It's all new, looks nice, not expensive, not heavy.

To install Ubuntu 10.04 I had to find the F6 key to add the option acpi=off (refer to [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)).
After the install I had to edit the config file /etc/default/grub and add 
acpi=off at the end of the line below :
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
save the file and then do "sudo update-grub".

As a result, Ubuntu boots ok but the laptop does not switch off automaticaly : I have do press down the switch off button manually. And the power controls has no effect...

And the wifi does not run at all... even if the wifi led indicator seems to be on...

---

### Post by gornety on 2010-07-21
The Compaq 615 uses the Broadcom wireless chipset BCM4312.
And Broadcom has given a driver for linux.
More, the broadcom driver is available in the repository of Ubuntu : 

"Some distros (Ubuntu and Fedora at the least) already have a version of
this driver in their repositories precompiled, tested and ready to go.
You just use the package manager to install the proper package.  If
its available for your distro, this is usually an easier solution."
From the readme.txt of Broadcom ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)).

So goto your System > Synaptic and find "broadcom-sta-common".
Install it, reboot and the wifi is ok !

---

