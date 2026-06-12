---
title: "System resumes immediately after suspend"
date: 2009-07-08
forum: Hardware
---

### Post by ThomasTC on 2009-07-08
Note: mods, if this should go into the x64 subforum, feel free to move it. I wasn't sure...

I've googled around, tried various things to debug, upgraded the kernel to 2.6.29... can't seem to find it.

The problem is that when I suspend the system (either via the Gnome menu, or by shouting "sudo pm-suspend"), the system goes down, then comes right back up again. There must be some wake-up event occurring, but I can't find where or why. The monitor goes on standby, I hear the hard drive spin down, but everything immediately comes up again.

Sometimes (but not always) I see something about "corrupted low memory" flash by while the machine is waking up.

I tried booting with the no_console_suspend, stopping gdm (and thereby X), unloading nvidia (a likely culprit, according to the web) and suspending from the console... but the same thing happens. Except that I don't get my display back after resume. It does keep responding to commands, because a blindly typed "sudo shutdown -r now" did reboot the machine :)

Distribution: Ubuntu 9.4 (Jaunty) amd64, latest updates
Kernel: 2.6.29-020629-generic

CPU: Intel Core i7 920
Mainboard: Gigabyte GA-EX58-UD4P (Intel X58 chipset)
Memory: OCZ Platinum XTC 6 GB, PC3-12800
Graphics card: Sparkle 512 MB NVIDIA GeForce 9800 GT
Hard drive: Samsung Spinpoint EcoGreen F2 1 TB

Here are some useful files and dumps:
[dmesg output](http://pastebin.com/m64ce4661) (line 189 or 190 is where everything starts waking up again)
[/var/log/pm-suspend.log](http://pastebin.com/m13a4cd21) (wakeup starts at line 79)
[lsmod output](http://pastebin.com/m7d9b16e5)
[/proc/acpi/wakeup](http://pastebin.com/m66b8167a) (as you see, everything is disabled)
[lspci -vv output](http://pastebin.com/m5f80098b)

I'm out of options here. Does anybody have an idea what else I could try?

---

### Post by liping on 2009-07-08
Are you doing a suspend-to-ram or suspend-to-disk (hibernate)? 

I had a similar problem with hibernate resuming immediately because I didn't have a  swap partition/swapfile set up.
This [guide]("http://ubuntuforums.org/showthread.php?t=1042946") worked great for me.
Even if you're using a swap partition, part 2 of the HOWTO apparently works too.

---

### Post by ThomasTC on 2009-07-11
Sorry for the slow reply.

I meant suspend-to-RAM, i.e., the Suspend item in the menu at the top right of the screen.

[s]Incidentally, hibernation also fails on my system, but I figured I'd look into the (hopefully) simpler issue first. Maybe they have the same cause.[/s] Edit: Hibernate works now. Gives some errors about USB devices not being able to restore, but that doesn't seem to give any problems. Suspend is still no go though.

Is there any way to see what event caused a wakeup? Any other ideas?

---

### Post by liping on 2009-07-20
I remembered when I troubleshooting my hibernate problems, it helped to manually run pm-hibernate so that I could see the error messages. 

Why don't you give it a try with pm-suspend in Terminal?

---

### Post by hhl1687 on 2009-08-08
I solved the problem by compiling a kernel with all the USB drivers as modules.
My original kernel, which has this "resume immediately after suspend" problem,
have all those drivers built in. 

The idea is to unload the USB drivers before you suspend. This can be
automated. Here's the thread:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289252](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289252)

The USB drivers in question include:

~/Desktop$ cat /etc/pm/config.d/00sleep_module 
# The sleep/wake system to use.  Valid values are:
#   kernel    The built-in kernel suspend/resume support.
#             Use this if nothing else is supported on your system.
#   uswsusp   If your system has support for the userspace
#             suspend programs (s2ram/s2disk/s2both), then use this.
#   tuxonice  If your system has support for tuxonice, use this.
#
# The system defaults to "kernel" if this is commented out.
# SLEEP_MODULE="kernel"
SUSPEND_MODULES="ehci_hcd uhci_hcd ohci_hcd usbcore"

I am running 64-bit Xubuntu 9.04. Didn't re-build a Ubuntu-specific
kernel, just built the latest stable trunk from kernel.org (2.6.30.4).

HTH,
- henry

---

