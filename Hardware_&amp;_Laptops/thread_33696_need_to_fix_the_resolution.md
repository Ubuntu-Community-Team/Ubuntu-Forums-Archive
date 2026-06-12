---
title: "need to fix the resolution"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by davidillerj on 2005-05-11
i have succesfully installed the ubuntu linux on my pc. But the resolution only gives me  640x480. i asume its the driver. how do i install a driver? if that is the case.

---

### Post by Xian on 2005-05-11
It's more likely that it didn't set up your monitor sync's properly.
Try this command to configure your Xorg and then reboot:

$ sudo dpkg-reconfigure xserver-xorg

---

### Post by davidillerj on 2005-05-11
Well thanks for the help. but i dont even have the slitest idea how you do that. im no programmer and im completely new to linux. So if i can get a little more detail i would greatly appreciate it.

---

### Post by Xian on 2005-05-11
No problem. You just login to Gnome (I know it looks weird with your reso right now) and then right click anywhere on an clean portion of your desktop. Choose the option that says 'Open Terminal'. When this opens you will be presented with a simple window that has only a command prompt. It is at that command prompt that you will type in the text string that I gave you earlier:

sudo dpkg-reconfigure xserver-xorg

This will allow you to reconfigure your display settings (monitor, keyboard, video, etc.). All you need is just some basic knowledge of your hardware to understand what the process is attempting to accomplish. It is very intuitive. Once this is finished you will need to reboot and then hopefully there will be an improvement in what you are currently experiencing.

---

