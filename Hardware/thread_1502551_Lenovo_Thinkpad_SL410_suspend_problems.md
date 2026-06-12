---
title: "Lenovo Thinkpad SL410 suspend problems"
date: 2010-06-05
forum: Hardware
---

### Post by skylar on 2010-06-05
I'm having trouble getting suspend to work with Ubuntu 10.04 (lucid) 64-bit on a Thinkpad SL410. When I press Fn-F4 (suspend) it goes to sleep just fine, but I cannot get it to come out of sleep. This works fine in Windows so I don't think it's a hardware problem. If it helps, I've attached the output of dmesg and lspci.

Thanks in advance for any suggestions!

Skylar

---

### Post by skylar on 2010-06-06
I've been playing around with different kernels, and think I'm making progress with 2.6.35-rc2 over the stock Ubuntu kernel (2.6.32-22). When I use the stock kernel, both the power button light and the sleep light (or whatever the crescent moon is supposed to represent) start blinking, and the CPU fan starts spinning up. With 2.6.35-rc2, the sleep light only blinks a couple times, but the power button light keeps blinking. The CPU fan also doesn't spin up. This more closely jives with the experience I have in Windows, and also with my older T30 Thinkpad. Unfortunately, the system still doesn't come out of sleep mode, so any suggestions on how to get that working are welcome.

Skylar

---

### Post by Junx on 2010-06-26
I have this same problem. I've tried suspend on Arch Linux as well, and it didn't work there. Perhaps there are certain kernel modules not suspending/resuming correctly?

---

### Post by skylar on 2010-06-26
> **Junx said:**
> I have this same problem. I've tried suspend on Arch Linux as well, and it didn't work there. Perhaps there are certain kernel modules not suspending/resuming correctly?

That's what I'm leaning to. It seems that 2.6.35-rc2 is starting to have support for ACPI for the SL410 now. The good news is that hibernate works, and coming out of hibernate is so fast that I've just been living with that for now.

Skylar

---

### Post by anairam on 2011-11-02
> **skylar said:**
> I'm having trouble getting suspend to work with Ubuntu 10.04 (lucid) 64-bit on a Thinkpad SL410. When I press Fn-F4 (suspend) it goes to sleep just fine, but I cannot get it to come out of sleep. This works fine in Windows so I don't think it's a hardware problem. If it helps, I've attached the output of dmesg and lspci.

Thanks in advance for any suggestions!

Skylar

Hi! I was having the same problem on suspend and hibernate. 
Thinkpad SL410, Ubuntu 10.04, 2.6.32-34-generic.
After weeks of banging my head against the wall I found that, at least in my case, it was a conflict with the **Virtual Box modules**.
So, if you have virtual box installed, please try to stop all modules. 
I had to manually stop them:
1. To know which are the modules running
```
$ lsmod | grep vbox 
```
2. Then, in my case I had 4 modules and I stop them:
```
$ sudo rmmod vboxpci vboxnetflt vboxnetadp vboxdrv 
```

3. After that, I suspended the machine and worked as expected

4. So then I have added the vbox main module in pm-utils modules file, pm-utils will first stop this module and then suspend:
In /etc/pm/config.d/modules (if does not exist, just create it) and add 
```
SUSPEND_MODULES="vboxdrv"
```

This worked just fine and now I can suspend without problems. 
I have also checked and after suspend, when system is back, the vbox modules are loaded back :)

Apparently this was a Virtual Box bug and is fixed in last version (4.1.2): [https://www.virtualbox.org/ticket/9305](https://www.virtualbox.org/ticket/9305)

Another related post: [http://ubuntuforums.org/showthread.php?t=1810091](http://ubuntuforums.org/showthread.php?t=1810091)

Cheers!

m

---

### Post by skylar on 2011-11-03
> **anairam said:**
> Hi! I was having the same problem on suspend and hibernate. 
Thinkpad SL410, Ubuntu 10.04, 2.6.32-34-generic.
After weeks of banging my head against the wall I found that, at least in my case, it was a conflict with the **Virtual Box modules**.
So, if you have virtual box installed, please try to stop all modules. 
I had to manually stop them:
1. To know which are the modules running
```
$ lsmod | grep vbox 
```
2. Then, in my case I had 4 modules and I stop them:
```
$ sudo rmmod vboxpci vboxnetflt vboxnetadp vboxdrv 
```

3. After that, I suspended the machine and worked as expected

4. So then I have added the vbox main module in pm-utils modules file, pm-utils will first stop this module and then suspend:
In /etc/pm/config.d/modules (if does not exist, just create it) and add 
```
SUSPEND_MODULES="vboxdrv"
```

This worked just fine and now I can suspend without problems. 
I have also checked and after suspend, when system is back, the vbox modules are loaded back :)

Apparently this was a Virtual Box bug and is fixed in last version (4.1.2): [https://www.virtualbox.org/ticket/9305](https://www.virtualbox.org/ticket/9305)

Another related post: [http://ubuntuforums.org/showthread.php?t=1810091](http://ubuntuforums.org/showthread.php?t=1810091)

Cheers!

m
Interesting. I do indeed have VBox installed so that might have been it. My own solution was to upgrade to 11.10 when it came out. :)

Thanks for the tip!

Skylar

---

