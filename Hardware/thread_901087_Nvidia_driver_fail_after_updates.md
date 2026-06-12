---
title: "Nvidia driver fail after updates"
date: 2008-08-26
forum: Hardware
---

### Post by technotika on 2008-08-26
Hi guys bit of help required here please.

I am installing official latest nvidia drivers from nvidia website and installing them with commands found in this forum on the net.

Just so you understand I log out the X session, kill the X server install the driver with the SH "blahblainstall.dkpg.run" and it goes and does its thing and I reboot and is great with nvidia splash screen at log on.

But I have noticed each time I run updates with kernel packages in them it breaks the nvidia install and I have to re do it??

Am I doing something wrong? Doesnt seem like it as its very stable and fine till these updates.

Is there anyway to stop this from happening?

Thanks guys, Jerry:popcorn:

---

### Post by jacksaff on 2008-08-26
You need drivers compiled for the specific kernel.
If you use the ones with ubuntu, when they upgrade the kernel they also recompile and upgrade the driver package.
As you are not using this package you have to do this yourself.
So, yes, if you upgrade your kernel you will need to reinstall your nvidia driver. The install program recompiles the code for the kernel you have running whcih is why it takes a little time to install.
You can pin your kernel version so that it doesn't update, but I wouldn't recommend it as new kernels are usually to patch security vulnerabilities.

---

### Post by malachi1990 on 2008-08-26
I have the exact same problem.  Normally, you can just open the hardware drivers app, and do it from there, but the new updates killed that particular option (for me at least).

Odd thing is that I could download the proprietary driver in the 17 kernel, but not 19.  

Other than the Nvidia website, you could try Synaptic.

UPDATE: You can restore your ability to change screen size by using the recovery mode, though I still can't get the driver to compile.

---

