---
title: "HELP!! Intrepid+Laptop = Black Screen of Phun after splash"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by VDubCoder on 2009-03-03
Hi all. I'm a n00b to Ubuntu but not to computers.

I currently have an old laptop that I'm working on turning into a media sharing server. I currently have it dual booting with WinXP Home SP3 and Intrepid Ibex 8.10 on a separate partition of an 80GB drive.

The Specs are as follows:
Fujitsu Lifebook N5000? (not sure on the exact model)
Pentium 4 3.0Ghz
80GB HD
512 MB RAM
ATI RADEON Mobility 9600
Aetheros Built in Wireless

I originally installed Intrepid through windows via the ISO file I downloaded and had it running successfully. I had to fudge with the video drivers after I ran some automatic updates but got everything working.

Yesterday I installed a new desktop theme and attempted to install a new splash loading screen as well as a handful of other random things things.

After doing those installations I rebooted. Not only did my new splash screen not show up but Gnome didn't come up either (I have auto login enabled at this point). I first try to change the resolution settings in my /etc/usplash.conf file, save and reboot to no avail. Then I revert back to the old splash via update-alternatives --config and do the update-initramfs -v -c -k all.

After doing this the default splash shows up and then boots to a black screen. No menus. No cursors. Only "static" along the bottom of the screen and something resembling a row of red chinese characters across the top. It slightly resembles looking at a messed up VHS tape. Control+alt+F1 through F0 didn't do anything, except for once. In that instance the screen faded from black to pink to gray and that's it.

I've tried to restart, and boot from a custom line (forget what's it called), removing the quiet, splash, and vga=791 attributes. (The installation of the new usplash theme instructed to add vga=791 to the /boot/grub/menu.lst file.)

Recall that I had this system completely up and functional til I installed the new desktop theme, usplash, and the new usplash theme. I had also updated the kernel to the latest. Although this kernel wouldn't update via the update manager, i had to reboot in recovery mode and choose fix packages. It updated from 2.6.27-11 from 2.6.27-7.

At this point I'm trying to recover the Ubuntu install and avoid reinstalling which would be the easy solution for me. But I'd rather learn something. I'm thinking a problem with video drivers after the update?

I also tried removing compiz and compiz core and rebooted. No luck there either.

Also, I've tried to boot other kernels but they all boot to the same black screen.

When there's a next time, I'm thinking I'll try the Startup Manager.

Any help would be fantastic.

---

