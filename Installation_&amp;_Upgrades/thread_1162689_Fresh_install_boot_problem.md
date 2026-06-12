---
title: "Fresh install boot problem"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by LinuxDanP on 2009-05-17
I have just installed Kubuntu 9.04 on a desktop machine, and after only one boot, it freezes on startup. I installed it twice, but it behaves identically. When the computer reboots from the installation, it's fine, but on subsequent starts it seems to hang when starting kdm. It prints out something along the lines of *Checking battery state   [OK] then it stops. If I leave it alone for about half an hour, it will say something about starting a system log daemon, I think. At any point I can switch to a different tty and log in, but the X server will not start from the command line using startx. I re-installed Kubuntu, with the same results. I used the same install cd to install it on a laptop, and it went perfectly there. The problematic machine has an intel x86 quad core processor. Has anyone had a similar problem? I haven't the faintest idea how to deal with kdm, as I have never had problems of this nature before. 

Thanks in advance

---

### Post by LinuxDanP on 2009-05-18
I just tried Kubuntu 8.10, and this seemed to work until I installed the proprietary Nvidia graphics driver. This may have been causing my original problem, as I had previously installed the driver as soon as I logged in. Has anybody else had similar problems?

---

### Post by LinuxDanP on 2009-05-19
This is an issue with the proprietary Nvidia graphics drivers. I have no problems with either Kubuntu 9.04 or 8.10, until I install the graphics driver. The recommended driver for my hardware is version 180.51, which I just tried. Here is what gets printed out:

Starting K Display Manager: kdm.
*Starting network connection manager NetworkManager        [OK]
*Starting Avahi mDNS/DNS-SD Daemon avahi-daemon         [OK]
*Starting Common Unix Printing System: cupsd                    [OK]
saned disabled; edit /etc/default/saned
*Starting anac(h)ronistic cron anacron                                 [OK]
*Starting deferred execution scheduler atd                           [OK]
*Starting periodic command scheduler crond                        [OK]
*Checking battery state...  comment: this is where it freezes. It shoudln't check battery, this is a desktop computer.
*Reloading Common Unix Printing System: cupsd
*Reloading System log daemon  comment: the final freeze. It doesn't go any further than this.

However, when it freezes I can still ctrl-alt-f2 to a different tty, and then login from the terminal, and execute terminal commands, but I can't launch X or KDE. After switching back to tty1, I see the following printout:

pre boot message: Boot from (hd0,0) ext3        # followed by long alphanumeric code
Starting up...
Loading, please wait...
then after the tty swap: 
19+0 records in
19+0 records out
kinit: name_to_devt(/dev/disk/by-uuid/long alphanumeric code here) = dev(8,5)
kinit: trying to resume from /dev/disk/by-uuid/same alphanumeric code here
kinit: no resume image, doing normal boot...

After this I can do a normal terminal login.
Does anyone have any ideas here?

---

