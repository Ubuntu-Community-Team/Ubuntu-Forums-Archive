---
title: "Updates broke Ubuntu 9.04"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by Gforce20 on 2009-08-12
After various updates (I'm not sure what was changed), I rebooted and Ubuntu fell back to a command line interface. Attempting to use recovery mode revealed that this line was being repeated about four times per second for somewhere around 30 seconds:
"udevadm settle is not permitted while udev is unconfigured"
Eventually it would give up. The only prompt I received while the updates were running was about menu.lst, and I chose to keep the old version because I need some custom boot options. Would this cause the udevadm error?
Also, googling the "udevadm settle [...]" line with quotes returns no results. :(

---

### Post by Gforce20 on 2009-08-13
Apologies for double-posting, but could anyone help me out with this error? I'd rather not go through a full reinstall just because of one bug.

Edit: Switching to Debian, I'll see how things work out.

---

### Post by kelstock on 2010-02-09
I have exactly the same problem as OP with Karmic Koala.  

Here is the solution I came across after some googling:

[INDENT]Problem solved:

The work around is following (thanks to <slangasek>)
(re)Start computer
If you have grub2 installed, you need to hold down the shift key while booting. If you have grub1 installed, you need to hit escape.
Now you can select the older kernel version from the grub menu
The system will boot normally.
Now open a console and run root command:
sudo update-initramfs -u
that will regenerate the initramfs for the newest kernel,
and after reboot all will work in the newest kernel also.[/INDENT]

from [https://bugs.launchpad.net/ubuntu/karmic/+source/apt/+bug/453678](https://bugs.launchpad.net/ubuntu/karmic/+source/apt/+bug/453678)

---

