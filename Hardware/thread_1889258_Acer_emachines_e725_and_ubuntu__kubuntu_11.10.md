---
title: "Acer emachines e725 and ubuntu / kubuntu 11.10"
date: 2011-12-01
forum: Hardware
---

### Post by MyRyM on 2011-12-01
Hi! My english is reather poor. Also I'm beginner so please, have mercy :smile:

I installed Ubuntu 11.10 on my laptop acer emachines e725. Everything goes fine but after reboot I cann see just black screen :confused: The same thing happened with Kubuntu 11.10

How cann I fix this problem if I do not see nothing exept black screen?

---

### Post by matt082606 on 2012-04-11
I also have this problem. Any help would be appreciated.

I have just finished installing Ubuntu 11.10 and my external monitor works fine, however when I turn on the laptop screen it stays black. I can move windows into the space but I cannot see them on the laptop screen.

The external display works fine both while the laptop is on and while it is off.

I am in the middle of a large download, but once it is done I will reboot without the external monitor and report back as to whether the laptop display works with no eternal monitor connected.

Thanks in advance for the help.

This machine's specs:
Pentium T4400 2.2G
15.6 inch LCD Intel GMA4500M chipset

---

### Post by matt082606 on 2012-04-11
This is to confirm that without an external monitor the laptop screen still remains off.

I've searched and this is the only thread I can find that mentions the problem. I'll continue to dig, but in the meantime if anyone has any ideas please let me know.

Thanks!

---

### Post by matt082606 on 2012-04-11
Ok, I found multiple bug reports based on 2.6.38 kernel, it looks like it has not been fixed yet.

Here are the links to information on work arounds. I will attempt the simplest one (in my mind) which is:

> Add "acpi_osi=Linux" in your boot options. For example, modify /etc/default/grub like this:
GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash acpi_osi=Linux”
then run update-grub and reboot.

Links:
[http://ubuntuforums.org/showthread.php?t=1744809]("http://ubuntuforums.org/showthread.php?t=1744809")

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438")

Hope this helps others. I will report back on the Quoted solution that I will be trying.

---

### Post by matt082606 on 2012-04-11
Sorry for the multi-posts...

Here is what fixed my problem:

First I installed vim-nox:

```
sudo apt-get install vim-nox
```

This is just my preferred editor. 

Next I modified rc.local to include “setpci -s 00:02.0 F4.B=00” apparently it is also backwards on what it thinks is the brightness level, where the =00 is actually 100% on, and FF is 0%

```
sudo vi /etc/rc.local
```

Add the line above before the "exit 0" line.

Finally I modified grub and updated it:

```
sudo vi/etc/default/grug
```

Find the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and made it this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

```
sudo update-grub
```

Reboot.

I tested booting with out a monitor, it worked, and when I plugged the monitor in it picked right up with no problems. 

I have also read of problems with closing the lid, and coming in and out of suspend. I'll save the additional posts here, anyone that stumbles on to this thread can see the links above and get the corrections.

---

