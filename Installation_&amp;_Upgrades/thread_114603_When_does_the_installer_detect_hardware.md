---
title: "When does the installer detect hardware?"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by doug.salah on 2006-01-08
I have a Fujitsu LT P-600 that is currently running XP/tablet.  I don't have working floppy nor can it boot to CD (BIOS limitation).  to get XP on the system I started the install on another system then before finalizing the install I switched the HD back to the Fujitsu.  XP does a fair job with this type of change but I am unsure if Ubuntu will kinda freak out.

When does the installed detect hardware?  I have installed Ubuntu on my Thinkpad X41 tablet and love it!!!  I want to use the fujitsu for some wireless security stuff and need Linux on it.  Fedora didn't like the switch when i tried a few months ago.  If I can't do the swap can is there a way to install from the HD?  I can get files to the HD and even partition it but am not that familiar with the process of starting the install from the HD.

Any help will be appreciated.  I want to document my X41 install is there somewhere here to put a step by step?  I had to piece the install together from a number of documents from TuxMobil for different distros and different thinkpads.

Doug

---

### Post by Herman on 2006-01-08
doug,salah, you asked:
>  When does the installed detect hardware? I don't know anything about the rest of the project you want to try, but as far as answering that one simple question goes, the Ubuntu installer detects hardware after it asks you your language, country, and keyboard layout.
As soon as you press 'Enter' after the keyboord layout question it starts detecting your hardware to find CD-ROM drives, Scanning CD-ROM, Loading additional components, Detecting network hardware, and configures your network with DHCP.
Then, it asks for a host name for your system, then it detects disks and other hardware, then starts up the partitioner.

Check my signature link and find one of the three different example installs to see some illustrations. I hope this helps you somehow. > I want to document my X41 install is there somewhere here to put a step by step? I had to piece the install together from a number of documents from TuxMobil for different distros and different thinkpads.It's a great idea to document your steps. You never know when you can help someone some day. There are special places here you can submit such information, like the Wiki, forum Wiki delta, and customization tips and tricks. I'm still learning about those myself.

---

### Post by az on 2006-01-09
[QUOTE=doug.salah] XP does a fair job with this type of change but I am unsure if Ubuntu will kinda freak out.

Doug[/QUOTE]

Hard drives and partitions are detected and written to /etc/fstab and grub config just as you begin the install.  If you only have the one drive, then that will not matter - it will be the same on your other box.  If not, just edit it before you reboot.

Network interfaces are also written then, but you can always edit those using the networking GUI.

Sound cards and other peripherals are detected on each boot, so no problem there.

Video is configured as the X packages (xorg) are configured - the second boot.  If you install the system using one box, and then shutdown when it asks you to reboot, you should be good to transfer your drive and complete the install on the other box.

Ubuntu handles hardware changes better than windows in many respects.  In others, you have to reconfigure it by hand.  But you should be able to get it going easily.

---

