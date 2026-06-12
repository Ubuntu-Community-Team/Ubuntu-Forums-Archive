---
title: "Missing libGL"
date: 2012-07-23
forum: Hardware
---

### Post by Gannin on 2012-07-23
I'm running Lubuntu 12.04 with an AMD graphics card using the proprietary drivers.

Today I did the regular system update, which updated the kernel to 3.2.0-27.  After the update finished installing, before I rebooted the computer, I dropped to a terminal, stopped the lightdm session, and ran "amdconfig --uninstall".

Then I rebooted my computer, went to the terminal again, and re-installed the AMD driver, then rebooted once more just for good measure.

Now, whenever I try to run anything that uses OpenGL, I get a message saying that the system can't find libGL.so.1.  I've tried reinstalling the driver multiple times, both from the command line without the desktop running, and using the graphical tool within the desktop, and the driver installation always completes successfully but I still get that same message.

---

### Post by Gannin on 2012-07-28
It turns out the problem is based on how Ubuntu handles 64-bit and how the AMD drivers handle 64-bit.

Ubuntu puts its 64-bit libraries in /usr/lib.  The AMD drivers puts its 64-bit libraries in /usr/lib64.  Even though the AMD drivers work when you initially install them, after a while when you update the AMD drivers or reinstall them the system will no longer be able to find the AMD libraries.

The solution is, before you even install for the first time, create a link pointing /usr/lib64 to /usr/lib, so then when the AMD drivers install their libraries into /usr/lib64, they're actually installing them into /usr/lib.

If you already have the AMD drivers installed and they stop working with messages like no screens found or unable to locate libGL.so.1, then find where you downloaded your AMD driver and run it as sudo with the --uninstall option, like this:

sudo amd-driver-installer-12-6-x86.x86_64.run --uninstall

Then reboot your computer and you should go back to using the original open source drivers.  Then delete /usr/lib64 if it already exists, then recreate it as a link to /usr/lib, then install the AMD drivers again.  Reboot again, and it should work fine.

---

