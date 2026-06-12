---
title: "Main laptop display not working with NVIDIA Drivers on 18.04"
date: 2019-04-30
forum: Hardware
---

### Post by eheijkoop on 2019-04-30
I recently upgraded my HP laptop (HP Pavilion Power 15-cb040nd) to Ubuntu 18.04. I had previously been running Ubuntu 16.04 and that was working flawlessly, but during the installation process already it started giving me issues. In this case it was solved by adding "nomodeset" to Grub after installation.
The real problem, however, occurs when I want to connect my external monitor to my HDMI port. I installed the NVIDIA drivers (currently on 418, but I've tried it with 390, 410 and 430), using [this tutorial]("https://www.pugetsystems.com/labs/hpc/The-Best-Way-To-Install-Ubuntu-18-04-with-NVIDIA-Drivers-and-any-Desktop-Flavor-1178/"). I went through the whole process with my department's SysAdmin and he basically confirmed that it appeared to be installed correctly. However, when I run nvidia-smi in the terminal, I get [this]("https://i.stack.imgur.com/Fgiav.png"). The biggest red flag (to me) seems to be: 00000000:01:00.0 Off and 0MiB/4040MiB. The very first attempt at installing the drivers was through Software & Updates and Additional Drivers.
One possible solution I found was to add Option "PrimaryGPU" "Yes" to /usr/share/X11/xorg.conf.d/10-nvidia.conf. I did this and when I reboot my laptop's main screen freezes at the sda cleanup, but now my external monitor suddenly comes to life and shows the login screen. I login and then suddenly it seems like my laptop runs flawlessly. Everything is very smooth, e.g. changing workspaces is a fluid animation instead of instantaneous. nvidia-smi gives the right feedback too. However, I cannot get my laptop's main screen to work like this, which is problematic if I want to work and I don't have an external screen (and the fact that I like working with two screens at the same time). I've tried rebooting without the external monitor connected and then it just freezes on the reboot. Connecting the monitor then instantly gives me the login screen; I've done this with two different monitors too. Removing this line gets me back to where I started (empty nvidia-smi and it doesn't recognize the external monitor).
When I go to tty, my laptop's screen is responsive again, but when I go back with CTRL+ALT+F1the external screen is the only responsive one and the laptop hangs on whatever I had last in tty.
So, what else can I do to have both screens and the NVIDIA drivers working?

---

### Post by wildmanne39 on 2019-04-30
Hello and welcome to the forum!

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

