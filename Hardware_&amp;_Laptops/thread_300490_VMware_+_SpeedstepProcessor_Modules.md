---
title: "VMware + Speedstep/Processor Modules"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by Izzin on 2006-11-15
This is a very popular topic and let me start out I have done massive research on this to no avail.

My situation is that I run linux previously Gentoo recently converted to Ubuntu. However at my office there are limited applications that can not be ported over to run on Linux. Thus I am required to use vmware for this function.

I have tried a lot of things to get the clock issues to resolve itself, however I have found if the dynmaic clock modules are loaded.. (thermal,processor,speedstep_centrino,cpufreq_xxxx) then VMware is virtually unusable. 

The 1 module that seams to be doing the damage is the Processor kernel module. If I unload this module Vmware runs perfectly. However I lose all abilities to run the dynamic clocking. 

Where this works for me now, I am wondering if there is any solution to run  a vmware application at proper guest performance levels and still have the dynamic cpu throttling function correctly. 

The 2nd option is either an alternate boot up option to load the dynamic modules for when I do not need to run the vmware. (IE during my hour commute every evening/morning). 

Any assistance would be greatly appreciated.

-I

---

### Post by FrankVdb on 2006-11-16
Have you tried the forum over at VMWare? Would Workstation be an option?

---

### Post by Izzin on 2006-11-16
It does not matter what version of VM I use.

Workstation 5.5x, Player, or Server..

Each version has the same clock issues.

VMServer was simply the last one I have tried.

-I

---

### Post by Leppiz on 2006-11-16
Hello!

I'm running Pentium M 1,6GHz and I've solved the CPU throttling issue by turning off powernowd & speedstep. I've created a following script to start vmware.
```

#!/bin/sh
sudo setcstate 1
sudo /etc/init.d/powernowd stop
vmplayer ~/vmware/vmware-xphome.vmx
sudo /etc/init.d/powernowd start
sudo setcstate 8

```

Setcstate is another script:
```

#!/bin/bash
echo $1 > /sys/module/processor/parameters/max_cstate

```

Setcstate and powernowd -scripts are set to be run without password in sudo-config. VMware starts without gksudo-interruption.

---

### Post by SonWon on 2006-11-16
This is what I did to use VMware Server on my laptop.

Vmware VM Time clock fix:
edit /etc/vmware/config and add the following lines:
host.cpukHz = 2200000
host.noTSC = TRUE
ptsc.noTSC = TRUE

Note, 2200000 is the maximum CPU clock speed.  On my laptop the CPU goes from 800Mhz to 2200Mhz hence I use 2200000.

The laptop cycles the CPU up and down depending on the CPU load.  I am not sure what the clock speed in the VM is doing?

SonWon

---

### Post by matthinckley on 2007-07-05
sorry to revive this old thread but I have also experienced clock speed issues in guest os's using VMWare.. I have windows XP in a virtual machine for school purposes and sometimes the clock runs fast, sometimes slow.. 

I have found that VirtualBox doesn't suffer from this problem but I have not found a way to set up bridged networking in VirtualBox in conjunction with using NetworkManager..

Has anyone found a reliable fix for this? I haven't tried the suggestion in SonWon's post but it looks as if that may ramp up my CPU usage when running the VM?

Thanks

Matt

---

