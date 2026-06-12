---
title: "nvidia driver 169.12 breaks my X"
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by nelio2k on 2008-03-12
Hello,

After I've downloaded nvidia driver 169.12 from the NVIDIA website, I installed it just like how i usually install other drivers, by running the .run file as su.

Except now, my X won't start, or it starts but with vesa drivers at 640x480 resolution. It tries to start, because my computer will show the booting up texts, and then blank screen for like a second (as if X is trying to start), text again, and then it'll boot into low-graphics mode.

I've checked my xorg.conf, and i made sure that the driver used is nvidia, and nothing else.
I've disabled nv in the restricted modules list.

I've run ENVY, to let it automate the process for me. Even then, it still didn't work.

So, I figured I'd downgrade to the previous working driver, which was 100.14.19. So I wget'ed it from the terminal from NVIDIA, installed it (the installer removed the 169.12), and the same problem with X happens now.

I don't know where I can start diagnosing. Could anyone give me a hand? Thanks so much!

---

### Post by PmDematagoda on 2008-03-12
What VGA card do you use?

---

### Post by nelio2k on 2008-03-12
I have a NVIDIA Geforce FX Go 5200.

---

### Post by PmDematagoda on 2008-03-13
Try getting your desktop back by running:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then:-
```
sudo /etc/init.d/gdm start
```
If that gets your desktop back then we can move onto finding the solution for the Nvidia driver.

---

### Post by nelio2k on 2008-03-13
So I reconfigured my X with that command, and reinstalled the NVIDIA driver.
Now it works, albeit that I lost some customed Xorg tweaks. 
Thank you.

Just FYI, I've done dpkg-reconfigure before, but not with those parameters.
What do those parameters mean? (the -phigh)

Thanks so much!

---

### Post by nelio2k on 2008-03-13
So, I tried updating my desktop, which has NVIDIA GeForce 7025 with a driver.

The same problem happened, but I also found out what caused it, even though I don't know why this matters...

This is taken from the NVIDIA Forum, [http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modul```

```es-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed


Yeah... as to why they couldn't write the shell script a bit better to automate this process is beyond me, given the nature that the NVIDIA driver installation script has super user priviledge... It would have saved people hours of time. 

If anyone knows why these procedures matter, please feel free to share.

Also, NVIDIA wrote:
Please note: unfortunately, it has become difficult to keep track of the pre-/post-installation steps required for [K]Ubuntu, and the above instructions may be incomplete. If in doubt, it is recommended that you use your distributor's NVIDIA Linux graphics driver packages, exclusively.

What is the "Ubuntu's driver package"? I believe Envy is a third party, yet most people use it. (Even Envy couldn't have caught this one)

---

### Post by PmDematagoda on 2008-03-13
> **nelio2k said:**
> So I reconfigured my X with that command, and reinstalled the NVIDIA driver.
Now it works, albeit that I lost some customed Xorg tweaks. 
Thank you.

Just FYI, I've done dpkg-reconfigure before, but not with those parameters.
What do those parameters mean? (the -phigh)

Thanks so much!

The -phigh options instructs the X-Server reconfigurer to pick the high priority options which in this case was the vesa driver along with a few other "fail-safe" options.

---

