---
title: "Asus NJ73Jn with GeForce GT335, unable to enable NVIDIA driver."
date: 2011-10-20
forum: Hardware
---

### Post by Garmr on 2011-10-20
I have a problem with my NJ73Jn laptop. I can't seem to get the NVIDIA driver to work. This is how I'm going at it:

1. Use "restricted drivers" manager to install the driver and reboot the machine.

2. Check the manager, which now tells me that the driver is "active but not in use"

3. Run "sudo nvidia-xconfig" in a terminal to set up the x-server. This results in an error message that say that it was unable to generate the file properly. When opening the file i see that it is empty, except for one line about a "generic device".

4. Reboot the machine. Which won't, because the xorg.conf file is wrong.

I have tried several times but I can't seem to get it to work.

I also tried downloading the file from NVIDIA.com, which went something like this:

1. After downloading the file I set it to executable and used <ctrl> + <alt> + <F1> to get into the terminal.

2. When in the terminal i ran "sudo ./NVIDIA*" (it is the only file in its directory with a name that starts with NVIDIA). It completes the setup process and allows me to restart the machine (done with "sudo shutdown -r now"). Upon rebooting the machine I am again treated to a machine that stops when it is checking the laptop battery status.

3. After restoring the old /etc/X11/xorg.conf the machine is bootable, but the NVIDIA driver is still not in use.

Does anyone here know how I would go about installing the file, loading it into the kernel and checking that OpenGL and the rest works?

With regards
Garmr

---

