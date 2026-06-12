---
title: "Help! My Asus monitor goes to sleep during boot"
date: 2016-11-26
forum: Hardware
---

### Post by zavior2 on 2016-11-26
Hi all. :D 

Just installed Xubuntu 16.10 (also 16.04 LTS) on my desktop system. But I've ran into a odd problem with my Asus monitor that goes into sleep mode when lightdm loads. No matter what I do the monitor keeps going into sleep mode and the orange standby light is on. But if I unplug / turn off my monitor it works again and my monitor wakes. 

So how do I keep my monitor from going to sleep at boot? 

Note that suspend, logout and power management seems to work fine. It's only when I start or restart the system. :) 

Spec.: 
Asus VW222u monitor
Intel Core2Duo 
ATI Radeon
4GB RAM

---

### Post by zavior2 on 2016-11-27
Hi, again

Through trial and error I have been able to get my monitor to not go to sleep after Xubuntu splash screen and show lightdm login screen. \\:D/

It seems that if I remove **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**, my system will boot without Xubuntu splash screen and go to the lightdm / login with no problem. No more monitor going to sleep at boot, but it will show Ubuntu startup messages.

[SIZE=5]Workaround monitor going to sleep[/SIZE]

1. sudo cp /etc/default/grub /etc/default/grub.old
2. sudo vim /etc/default/grub
3. Edit out GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
4. sudo update-grub
5. reboot

But if there is a better way, I would like to know :D

---

