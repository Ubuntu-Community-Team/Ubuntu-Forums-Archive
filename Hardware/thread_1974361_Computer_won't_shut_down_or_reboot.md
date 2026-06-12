---
title: "Computer won't shut down or reboot"
date: 2012-05-06
forum: Hardware
---

### Post by Gannin on 2012-05-06
I have a new computer and Linux has a few issues with it.  Basically, networking and this.

When I try to turn the computer off from within Linux, it gets to the point where on the terminal (the ALT + F1 terminal) it says the system is shutting down and then it just stops.  To shut it down I have to physically press the power button.

Then when I try to restart, it does the same thing.  It gets to the point where it says the system is going down for a reboot and then it just stops, and I have to physically press the reset button.

---

### Post by Neill_R on 2012-05-06
when you say new computer do you mean it is a recently manufactured computer or just one new to you? 

If the later is the case then I had the same problem with a HP n5271 laptop via Google i found instructions on how to fix this. Here in my case is what i did.

#
# to ensure power off on shut down
#
# gksu gedit /etc/default/grub
#
# make GRUB_CMDLINE_LINUX_DEFAULT="acpi=force lapic quiet splash"
# then run 
# # sudo update-grub --output=/boot/grub/grub.cfg
#

Hope this helps.

Neill

---

### Post by Gannin on 2012-05-07
The computer is completely new.  Nevertheless, I decided to give this a try anyhow.  Unfortunately, it didn't work.

The computer acts the same as ever when trying to shutdown or reboot in Linux.  It goes through the entire shutdown process, all the lights on the keyboard even flash like normal, but then the system just stops, or hangs, without actually shutting down or rebooting.

---

### Post by Neill_R on 2012-05-08
Sorry that did not help you.

What does the "log file viewer" (syslog) say are there any clues there?

---

### Post by Gannin on 2012-05-11
There isn't anything in syslog that gives any clues.

Interestingly though, I tried out Fedora and it works just fine.  It doesn't work with my built-in networking either... I guess Linux just doesn't work with this networking adapter so I'd have to get a USB networking adapter to use instead... but it shuts down and restarts the computer just fine.

I've been using Ubuntu for so long I wasn't really thinking about the non-Ubuntu-based distros until the other night I thought, "Wait a minute, Fedora is built somewhat differently, maybe it'll work."  And it does.

So, it looks like if I want to really start using Linux on my system again, I'll be using Feodra.

Edit:  I have to modify what I said about.

Apparently the first time I tried to reboot Fedora, I accidentally hit Suspend instead.  It suspended fine, and then when I brought it back from Suspend, then I tried to reboot it, and it rebooted fine.

However later, on a second boot, when I just tried to do a straight reboot when I was done, it froze and stuck just like in Ubuntu.

So apparently, it only shuts down and reboots properly if it goes through a suspend cycle first.  Strange.

---

