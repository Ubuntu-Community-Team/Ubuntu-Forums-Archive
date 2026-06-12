---
title: "Advanced drivers for AMD Radeon 6850 OC?"
date: 2014-08-15
forum: Hardware
---

### Post by CJ_Hudson on 2014-08-15
Hi, 
I think I just successfully installed a legally purchased game with PlayOnLinux (see thread started here: [http://ubuntuforums.org/showthread.php?t=2239761](http://ubuntuforums.org/showthread.php?t=2239761) ) but graphics is notably choppier than with native Windows 8.1 64 bit.
I think this is maybe because the drivers in Ubuntu via Steam running in PlayOnLinux are only 32 bit.
Please can anyone help or explain?
Thanks in advance for any assistance.
Or perhaps, what I am hoping for, is I can just update to the latest Ubuntu driver for that card, whether it be proprietary or non proprietory.

I note the card is fully supported [here]("https://help.ubuntu.com/community/RadeonDriver"):

> [h=2]Fully Supported[/h] All these Radeon(HD) cards and derivatives have good 3D acceleration support. This is not an exhaustive list:BARTS                       Radeon HD 6790/6850/6870/6950/6970/6990

Sorry to sound like a noob but I have forgotten how to check the version of current graphics driver I am using in Ubuntu?

---

### Post by Mark Phelps on 2014-08-15
To see, open a terminal, enter "lspci" and look for the line containing VGA -- to see what video chipset that Linux sees in your PC.

You should be able to install the AMD driver using Additional Drivers.

---

### Post by CJ_Hudson on 2014-08-15
Hi Mark, thanks for your help, I think this might be it:

> 01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Barts PRO [Radeon HD 6850]

Since posting the initial post I have done two things:
1) Open Catalyst control centre and tick the box enabling "Tear free desktop" which I assume reduces video shear-effect;
2) Change the driver in the Additional Drivers options from fglrx to  fglrx-updates. It then downloaded and installed something and I restarted.

Already the graphics in my game seem smoother. I would estimate they are 50% better already. I'm tempted to mark this thread as solved but will wait a bit and see if anyone comes up with anything else.
There are a number of other options in the AMD Catalyst window, some of which I am not sure what they do.
For example, please could sombody tell me in 3D -> More Settings, what is "Enable Cataylst AI" and what is the difference between "Standard" and "Advanced"?
I have also just discovered the AMD Beta driver version 14.6 [here]("http://support.amd.com/en-us/kb-articles/Pages/Latest-LINUX-Beta-Driver.aspx") but I assume this is covered elsewhere on the Ubuntu Forum.
EDIT: You don't need Xorg installed to install the Beta 14.6 AMD driver. It works despite the error message. Just follow the instructions on the AMD website.

---

### Post by Mark Phelps on 2014-08-16
The "fglrx updates" are the latest AMD proprietary graphics available through the repos.  If you install the AMD Beta version, you will have to manually reinstall it every time you do an upgrade that affects the Linux kernel.  Unless you need the bleed edge version, it's best to stick with the ones offered in Additional Drivers -- they reinstall automatically when you do a kernel upgrade.

---

### Post by CJ_Hudson on 2014-08-23
Message received- thanks Mark.

---

### Post by QIII on 2014-08-23
Hello!

Also bear in mind that even with Wine, there is no guarantee that things will work well, or sometimes at all, compared to how they work natively in Windows.

---

