---
title: "Unity Crashes on Ubuntu 14.04 LTS with Nvidia ppa x edgers drivers"
date: 2014-08-23
forum: Hardware
---

### Post by chris-broll on 2014-08-23
I recently upgraded to 14.04 LTS and started getting Unity problems when running the Nvidia ppa x edgers drivers in Performance mode.

The GUI crashes and can be restarted by CTRL+ALT+F1, sudo service lightdm restart.

All I can see in the kern.log relating to Nvidia is:

Aug 23 23:15:12 Ubuntu-M11x kernel: [  617.441011] nvidia 0000:01:00.0: irq 47 for MSI/MSI-X
Aug 23 23:15:12 Ubuntu-M11x kernel: [  617.449217] ACPI Warning: \_SB_.PCI0.P0P2.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Aug 23 23:15:12 Ubuntu-M11x kernel: [  617.449320] ACPI Warning: \_SB_.PCI0.P0P2.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Aug 23 23:15:12 Ubuntu-M11x kernel: [  617.449711] ACPI Warning: \_SB_.PCI0.P0P2.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Aug 23 23:15:12 Ubuntu-M11x kernel: [  617.449787] ACPI Warning: \_SB_.PCI0.P0P2.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Aug 23 23:15:12 Ubuntu-M11x kernel: [  617.449861] ACPI Warning: \_SB_.PCI0.P0P2.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Aug 23 23:15:12 Ubuntu-M11x kernel: [  617.449933] ACPI Warning: \_SB_.PCI0.P0P2.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Aug 23 23:15:12 Ubuntu-M11x kernel: [  617.450006] ACPI Warning: \_SB_.PCI0.P0P2.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Aug 23 23:15:12 Ubuntu-M11x kernel: [  617.450079] ACPI Warning: \_SB_.PCI0.P0P2.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Aug 23 23:15:15 Ubuntu-M11x kernel: [  621.080263] hda-codec: out of range cmd 3:5:707:ffffffbf
Aug 23 23:15:24 Ubuntu-M11x kernel: [  629.832030] hda-codec: out of range cmd 2:5:707:ffffffbf
Aug 23 23:15:25 Ubuntu-M11x kernel: [  630.984082] hda-codec: out of range cmd 3:5:707:ffffffbf

Anyone any idea what is going on here? It's getting a little annoying restarting the desktop.

---

### Post by chris-broll on 2014-09-02
So after trying various 3xx Nvidia drivers and tracking messages in the Kernel/Xorg log I ruled out the logs as a source of useful information.

I then installed the Nvidia CUDA toolkit:

sudo apt-get install nvidia-cuda-toolkit

The laptop has been switched on for two days now (most of that in sleep mode) without a Unity crash. I have noticed a reduction in the temperature of the GPU being reported in the Nvidia X-Server Settings and the laptop base is much cooler to the touch. It is an Alienware M11x so it was always pretty hot but since "upgrading" to 14.04LTS the fan seemed to be working a lot harder and the base was warmer compared to Ubuntu 13.10 running (which was always warmer then Windows 7).

Not sure why the Cuda toolkit would make any difference (if in fact it has, it might have been one of the many driver uninstall/re-installs) but initial usage is looking promising. It needs some load testing now to see if I can push up the GPU temperature and see what happens.

Current driver is 331.38 updates (proprietary) which was in use previously during crashes.

---

### Post by chris-broll on 2014-09-02
So ten minutes later GPU reporting 52C - Unity crashes. Next job work out why temperature could be causing the crashes.......

---

### Post by chris-broll on 2014-09-15
So fought my way back through the tumbleweed to this post after 20+ re-installs of Ubuntu 13.04, 13.10 and 14.04 and 14.04.1 using various methods of install Nvidia drivers none of which provide installed usable Nvidia drivers.

Tried the Nvidia drivers that came from the Ubuntu repository (can't remember the name) on all versions mentioned above - installed command line.
Tried the ppa x edgers repository on all the versions mentioned above - installed command line.
Tried the Nvidia drivers in the Ubuntu Software Centre - installed via Unity GUI.
Installed Bumblebee from the software Centre and command line.

Each install was attempted from a fresh OS install with all the recommended updates installed. All failed to varying degrees, some installs allowed log in but then showed a black screen, others allowed log in with 800x600 resolution which could not be fixed by building a custom xorg.conf, others booted to a black screen (no loging prompt). So suspecting that this might be a Unity issue and started the procedure again With Ubuntu Gnome 14.04.1 with the same results but this time uninstalling the drivers actually reinstalled the Nouveau driver allowing me to log back in again and open this browser session.

I am not used to working with X sessions so not sure how to debug and the help on the forum has been rather underwhelming so the only debugging has been looking at the xorg.log and dmesg which hasn't given anything away to the untrained eye.

I haven't mentioned which drivers I tried, all the 3xx versions compatible with the GeForce 335M in an Alienware M11x Core-Due.

I see some bug reports that mention similar issues which have not been fixed so the upshot is something in one or more of the updates is most likely breaking Nvidia funtionality and no-one is in a rush to fix. So after a week without a fully funtioning laptop it is time to give OpenSUSE a try (tried MINT and it was rubbish, tried Fedora and spent most of my time fixing it, work with RHEL/CENTOS every day and they are great for business use but not home) and then its back to Windows 7, a pity but it works and I can fire up a game when i feel like without spending a week messing with settings.

---

### Post by redrumrogue on 2014-09-17
You could try installing the nvidia driver from the nvidia site.  This driver is for your GeForce 335M  [http://www.geforce.co.uk/drivers/results/77572](http://www.geforce.co.uk/drivers/results/77572) - version 340.32.  Was this version available in the edgers ppa?  I have this driver installed for my GeForce GT620 card and have no issues at all.  Follow the second reply on this thread ... [http://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidia-driver](http://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidia-driver)
You've tried everything else you might as well give it a shot!

---

### Post by chris-broll on 2014-09-20
Thanks, 

That version was not available in the edgers ppa but I did download it directly from the Nvidia web site and it also crashed Unity and Gnome. I suspect that this is down to the xorg.conf file that is created but as I said I don't usually work in X environments so I don't have the knowledge required to build a custom xorg.conf file.

I installed OpenSUSE 13.1 with a Gnome desktop and bumblebee, I think its running the Nvidia's 304 drivers which seems to working so far but I might look at an upgrade later.

---

### Post by redrumrogue on 2014-09-20
Hmmm ... Do unity crash if you set nvidia power management to Adaptive instead of performance?  Perhaps it wasn't the driver or the GPU but something else.  Not sure what to suggest next really.

---

### Post by chris-broll on 2014-09-25
Initially I was able to get Prime working by using an xorg.conf I had from a working 13.04 install that been upgraded up to 14.04.1 (where the trouble started). It ran fine on the low power setting but crashed in any Performance mode.

Then after I wiped the Hard Drive I couldn't get any of the fresh installs working with a mixture of Nvidia drivers.

I am now running openSUSE 13.1 with Bumbleebee and 343.xx something drivers without any problems.

---

