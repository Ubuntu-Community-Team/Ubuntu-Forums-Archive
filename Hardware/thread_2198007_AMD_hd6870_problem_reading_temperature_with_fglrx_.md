---
title: "AMD hd6870 problem reading temperature with fglrx driver on 13.10"
date: 2014-01-06
forum: Hardware
---

### Post by fir3wir3d on 2014-01-06
Hello,

I am trying to assess the feasibility of running 13.10 Ubuntu as my main operating system on a machine with a Radeon HD 6870 GPU.

I have a stock install of Ubuntu, freshly updated, and with the AMD driver from fglrx-updates installed through the Software&Updates -> Additional Drivers window. The system has been restarted.

Unlike with the normal AMD driver installed from the AMD support website (which doesn't have one for 13.10) I cannot use the aticonfig command to check idle temperatures, core voltage, gpu load, etc:

```
~$ aticonfig --odgt
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configuration file manually and run aticonfig again.
aticonfig: parsing the command-line failed.
```

I did some googling but I am a linux newbie and cannot find a solution. It is very important important for me to verify that this GPU runs cool when the system is idle so any help would be hugely apprieciated!

EDIT: changed -odgt to --odgt

---

### Post by QIII on 2014-01-06
Hello!

aticonfig has been deprecated in favor or amdconfig.

It looks like you need to run 

```
sudo amdconfig --initial
```

to create an xorg.conf and reboot.

Let us know if that helps.

---

### Post by fir3wir3d on 2014-01-06
Thank you! I have run the command and rebooted straight into unity without any issues. The system runs very cool and the idle gpu load when moving windows around, smooth scrolling, etc is the lower then I have ever seen before (with the exception of catalyst for windows of course).

---

