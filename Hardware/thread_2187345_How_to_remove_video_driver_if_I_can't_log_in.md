---
title: "How to remove video driver if I can't log in?"
date: 2013-11-11
forum: Hardware
---

### Post by lucasfxd on 2013-11-11
I just installed the last AMD Radeon Linux driver from AMD web site. I restarted the computer, but now when I log in, I got a black screen and can't do nothing... I have no idea how to remove this. Is there a "safe mode" startup or something?

Edit: I'm using Ubuntu 13.10.

---

### Post by QIII on 2013-11-11
Could you describe the exact steps you took to install it?

There are a couple of different ways to uninstall depending on how you installed it.

---

### Post by jp734 on 2013-11-12
In my experience, when you use the driver from AMD, it creates a xorg.conf file to use fglrx. So you can start your pc using a live media and simply move the configuration file, [COLOR="#0000FF"]/etc/X11/xorg.conf[/COLOR], to a different folder and reboot. It will use the default driver after that. Worked for me so many times. While using the live media, look at the log files as well and check what's stopping it from booting properly.

---

### Post by grahammechanical on 2013-11-12
Ubuntu does have a Recovery mode. If you are using 12.04 you will find Recovery Mode listed at the Grub boot menu. If you are using 13.04 or 13.10 you will find Recovery Mode listed under Advanced Options for Ubuntu on the Grub boot menu.

At the Recovery menu select Resume and that may get you to a working desktop running a non-accelerated video mode using a subset of the Nouveau open source video driver called llvmpipe. That is the case if you are using 13.04 or 13.10.  On 12.04 it loads Ubuntu without activating a video driver.

Also at the Recovery menu you can select Network and that will make a network connection using the existing settings. It will also put the file system in read/write mode which is necessary if you want to edit system files from the Recovery menu.

Also at the Recovery menu you can select Root and you will be at a command line prompt. There you can run commands. But the file system will need to be in read/write mode to update or edit files. Which is why I recommend selecting Network first.

Regards.

---

### Post by lucasfxd on 2013-11-12
Thanks, I will try these suggestions.

I installed this way:
```
sudo ./amd-driver-installer-catalyst-13-4-x86.x86_64.run
```
And followed the wizard.
I installed accessing my machine via TeamViewer (I don't know if this cause some problems...)

---

### Post by jp734 on 2013-11-12
Check the folder where you ran the installation script, it should have created an uninstaller script a well.

---

### Post by Mark Phelps on 2013-11-13
Just out of curiosity, what make and model AMD video chipset are you using?

---

