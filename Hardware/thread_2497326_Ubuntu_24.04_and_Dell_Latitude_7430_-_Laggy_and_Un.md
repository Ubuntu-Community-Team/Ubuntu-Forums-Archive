---
title: "Ubuntu 24.04 and Dell Latitude 7430 - Laggy and Unresponsive"
date: 2024-04-30
forum: Hardware
---

### Post by Jonathons on 2024-04-30
Hi all, 

I have a Dell Latitude 7430 notebook. Specs below. 

It runs Ubuntu 20.04 with no issues at all, but anything newer (22.04, 24.04) is incredibly laggy/unresponsive. That said, if I run the installer for 24.04 in safe graphics mode then the performance is much better; I think it might be a graphics driver issue but I'm not sure. 

Specs of the machine are:

Intel 1265U 
16GB RAM
512GB SS
The display has a native resolution of 3840x2160

Grateful for any advice.

---

### Post by gezzer2 on 2024-04-30
in a terminal  write

cpupower frequency-info

and post back the details ..

---

### Post by Jonathons on 2024-04-30
> **gezzer2 said:**
> in a terminal  write

cpupower frequency-info

and post back the details ..

Thanks, I've put the info below. Interestingly, I've just discovered that if I use an external display then there's no lag on the external display (even if both displays are active at the same time). It only seems to affect the inbuilt display of the laptop. Not sure if that helps narrow down the cause. 

```
analyzing CPU 2:
driver: intel_pstate
CPUs which run at the same hardware frequency: 2
maximum transition latency: Cannot determine or is not supported.
hardware limits: 400 MHz - 4.80 GHz
available cpufreq governors: performance powersave
current policy: frequency should be within 400 MHz and 4.80 GHz.
The governor "powersave" may decide which speed to use within this range.
current CPU frequency: Unable to call hardware
current CPU frequency: 1.25 GHz (asserted by call to kernel)
boost state support:
Supported: yes
Active: yes
```

---

### Post by gezzer2 on 2024-04-30
your CPU is the same mode mine was 'powersaver' which seems to be a default setting set by Ubuntu for laptop CPU.

my CPU is an AMD 5000 series Ryzen 7 Zen 3 5825u.

this is easy enough but a bit around the houses so do you want to take the red pill or the blue pill.
have a read of this please and post back if you wish to continue ..

[https://www.kernel.org/doc/html/latest/admin-guide/pm/cpufreq.html?highlight=schedutil](https://www.kernel.org/doc/html/latest/admin-guide/pm/cpufreq.html?highlight=schedutil)

---

### Post by gezzer2 on 2024-04-30
if you have had a read now for the details.

open a terminal and write
gedit admin:/etc/default/grub

you are looking for this line.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

you need to place in that line.
GRUB_CMDLINE_LINUX_DEFAULT="intel_pstate=guided quiet splash"

save the file and go back to the terminal and write.
sudo update-grub

restart the computer

#####

when the system has restarted open a terminal and write.
cpupower frequency-info 

and please post back the results ..

---

### Post by Jonathons on 2024-04-30
Thanks, but the fact only the in-built display of the laptop was affected and not the external monitor led me down a different path. 

Some googling later and it seems the issue is with the Intel Panel Self Refresh (PSR) setting. 

I was able to resolve the issue by adding "i915.enable_psr=0" to grub. 

```
 # /etc/default/grub (before)
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

 # /etc/default/grub (after)
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.enable_psr=0"
```

Helpful links below for anyone else facing the same issue:

[https://ljvmiranda921.github.io/notebook/2021/09/01/linux-thinkpad-screen-flicker/](https://ljvmiranda921.github.io/notebook/2021/09/01/linux-thinkpad-screen-flicker/)

[https://www.reddit.com/r/linuxhardware/comments/165293r/dell_latitude_laptop_unbearably_slow_with_ubuntu/](https://www.reddit.com/r/linuxhardware/comments/165293r/dell_latitude_laptop_unbearably_slow_with_ubuntu/)

---

### Post by gezzer2 on 2024-04-30
glad you got it fixed ..

---

