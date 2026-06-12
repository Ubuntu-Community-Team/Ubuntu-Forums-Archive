---
title: "Kubuntu 14.04 boots occassionally with blank screen."
date: 2014-10-22
forum: Hardware
---

### Post by steve-cookson on 2014-10-22
I have a custom all-in-one with an Intel i5 and Xeon E3-1200 v3/4th Gen on-board graphics card running Kubuntu 14.04 with all outstanding updates applied.  From the beginning, booting has been very sporadic.  A typical boot sequence will go as follows:

- Intel splash screen giving options for f11 setup and so on,
- konsole splash very quickly giving some sort of bootlog dump;
- grub options with countdown from 9secs.

If I let the count down proceed to 0 secs, the boot continues, there is a slight display of a few graphical lines and the screen goes into suspend and stays there.  No further indication of activity is shown.

However, the boot continues successfully and I can still access the machine through teamviewer.

If there is a second monitor attached, I can plug that in and it will succeed and I can manage through the second monitor.

If I power down the machine and power it up again, I can press eneter at the count down and will usually boot successfully.

If the machine goes into screen suspend (not suspend to ram), the same thing happens.

I have refreshed the linux kernel from the current (3.13), to 3.14, then 3.15 and now 3.16 to no avail.

However sometimes it boots perfectly.

Any ideas what this is caused by and how I could fix it?  It's causing a lot of stress.

Thanks in advance.

Regards

Steve.

---

### Post by steve-cookson on 2014-10-23
**Dead, blank, or black screen on resume** (from here:[ https://wiki.ubuntu.com/DebuggingKernelHibernate]("https://wiki.ubuntu.com/DebuggingKernelHibernate"))

 In some  cases, a machine can hibernate just fine, and resume without issue, with  the exception of waking up to a blacked-out screen. In other words, the  computer is running just fine, but the display appears dead. One thing  to try is disabling Kernel Mode Setting. One may do this by editing the  grub configuration: 

     sudo kate /etc/default/grubFind the line reading: 

     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Add nomodeset to the end, inside the quotes: 

     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"Exit from nano and save the file. Make grub aware of the new changes: 

     update-grub2

When  that exits, reboot the computer normally, then test hibernate. This  change will persist across reboots unless you explicitly revert it. In  some cases, this will also fix another issue where the screen doesn't  dim after a period of inactivity like it should, assuming it is  otherwise configured to do so in your desktop environment.

---

