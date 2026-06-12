---
title: "Jaunty doesn't boot, garbled screen"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by jic2000 on 2009-07-26
I just upgraded to 9.04 from 8.04, by way of 8.10. In 8.04 and 8.10 my laptop booted fine, but now I get stuck at a screen of garbage when I try to turn it on. Choosing the kernel that came with 8.04 from the GRUB menu, I don't get the garbled screen, but instead a message that the X server failed to start. The option to show the output of the X server just says:

```
Warning: Failsafe mode was already attempted within 30 seconds.
Warning: Falling back to gdm to report the issue.
^Y
```

Then I get put into the command line mode, where it should let me log in, but instead shows some cryptic error messages:
```
Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/8967a1ce-9bfc-42c4-bdb5-97ca823bac19) = sda7(8,7)
kinit: trying to resume from /dev/disk/by-uuid/8967a1ce-9bfc-42c4-bdb5-97ca823bac19
kinit: No resume image, doing normal boot...

Ubuntu 9.04 jic2000-laptop tty1

jic2000-laptop login: [   51.566109]  iwlagn: Nic access not held from iwl5000_nic_config line 246
[   53.678100]  iwlagn: Nic access not held from iwl5000_nic_config line 246
```

My laptop is a Fujitsu Lifebook A6230, with 4GB of RAM, a 500GB hard drive, an ATI Mobility Radeon HD 3470 graphics card, and an Intel Core 2 Duo processor at 2.26 GHz. I can still switch into a working terminal with ctrl+alt+F2, so I can run any diagnostic commands that might be helpful. Thanks in advance for any help.

---

### Post by bemar on 2009-07-26
I had the same problem with my P3 500 Notebook. No chance to get it running. 8.10 is the last running version on this notebook. It seems they changed anything so the chipset is to old or whatever.

---

### Post by jic2000 on 2009-07-26
Are you sure that's the case? The laptop is less than a month old and is the newest one in Fujitsu's A series, and the Jaunty live CD boots fine. I also installed Jaunty on a separate partition by itself and it worked with no flaws until I installed the restricted driver for my graphics card, at which point I got the same symptoms that I'm having now.

I also get the same problems with a clean installation of 8.10 as I'm having now - 8.10 only seems to work when I've upgraded from 8.04.

---

### Post by .Garrett on 2009-07-31
I've got the exact same machine, with the exact same problem, except I can't ctrl-alt-f2 and get to a virtual console. Help would be greatly appreciated.

---

