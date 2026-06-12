---
title: "issues installing proprietary ATI driver"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by peteyoferic on 2009-02-15
Hello, having a weird issue when trying to upgrade to the proprietary FLGRX driver on my new 8.10 install...when trying to install out of the Hardware drivers menu it prompts me for my admin password when I press activate...but it never actually activates...no matter how many reboots...so I looked on the forum and found this instruction which several people seemed to have luck with:

downloaded the following from packages.ubuntu.com:
- dkms_2.0.20.4-0ubuntu2_all.deb
- fglrx-kernel-source_8.543-0ubuntu4_i386.deb
- xorg-driver-fglrx_8.543-0ubuntu4_i386.deb
2. I installed each of them from a terminal window (in the order listed above) using 'sudo dpkg -i <package_name>.deb'
3. I went into System > Administration > Hardware drivers. With "ATI/AMD proprietary FGLRX graphics driver" highlighted, I clicked Activate & entered my password.
4. Rebooted.
5. Initially, the display was a bit wacky. I couldn't see the top menu bar (or whatever it's called) in order to change my resolution. I vaguely remembered that ctrl-alt-minus (or plus) could change the resolution, so I tried that. I finally saw the top menu bar and switched to the resolution I wanted via the menus.

Which I did, except I subbed the i386 for AMD64 versions...otherwise it all seemed to install properly...no errors etc.  But when I tried to activate the driver I got the following error:  
SystemError: E:Unable to correct problems, you have held broken packages.

This error persists after a reboot.  Any thoughts?...so close to having everything up and running perfectly this is so frustrating!  haha 

Thanks

---

### Post by PGHammer on 2009-02-15
> **peteyoferic said:**
> Hello, having a weird issue when trying to upgrade to the proprietary FLGRX driver on my new 8.10 install...when trying to install out of the Hardware drivers menu it prompts me for my admin password when I press activate...but it never actually activates...no matter how many reboots...so I looked on the forum and found this instruction which several people seemed to have luck with:

downloaded the following from packages.ubuntu.com:
- dkms_2.0.20.4-0ubuntu2_all.deb
- fglrx-kernel-source_8.543-0ubuntu4_i386.deb
- xorg-driver-fglrx_8.543-0ubuntu4_i386.deb
2. I installed each of them from a terminal window (in the order listed above) using 'sudo dpkg -i <package_name>.deb'
3. I went into System > Administration > Hardware drivers. With "ATI/AMD proprietary FGLRX graphics driver" highlighted, I clicked Activate & entered my password.
4. Rebooted.
5. Initially, the display was a bit wacky. I couldn't see the top menu bar (or whatever it's called) in order to change my resolution. I vaguely remembered that ctrl-alt-minus (or plus) could change the resolution, so I tried that. I finally saw the top menu bar and switched to the resolution I wanted via the menus.

Which I did, except I subbed the i386 for AMD64 versions...otherwise it all seemed to install properly...no errors etc.  But when I tried to activate the driver I got the following error:  
SystemError: E:Unable to correct problems, you have held broken packages.

This error persists after a reboot.  Any thoughts?...so close to having everything up and running perfectly this is so frustrating!  haha 

Thanks

What graphics card are you using?

I had an utterly FLAWLESS install (8.10 64-bit), and my own system is a hodgepadge (ATI graphicxs, nForce 7100/630i chipset, Intel Celeron DC E1200 CPU), and I've even added Creative's fresh open-source X-Fi Linux drivers (64-bit, of course) to the mix.  It's *still* flawless.

---

### Post by peteyoferic on 2009-02-15
> **PGHammer said:**
> What graphics card are you using?

I had an utterly FLAWLESS install (8.10 64-bit), and my own system is a hodgepadge (ATI graphicxs, nForce 7100/630i chipset, Intel Celeron DC E1200 CPU), and I've even added Creative's fresh open-source X-Fi Linux drivers (64-bit, of course) to the mix.  It's *still* flawless.

It's an older Radeon 9600 series...which is listed as supported on the link from the ATI website (which has links to the linux driver)

---

### Post by PGHammer on 2009-02-15
> **peteyoferic said:**
> It's an older Radeon 9600 series...which is listed as supported on the link from the ATI website (which has links to the linux driver)

Actually, you should use the non-proprietary (and open-source) radeon driver, as that driver was developed specifically to support the R3xx series (of which your 9600 series is a member).  The current open-source radeonhd driver was based on this driver, and is an alternative to it for the R3xx and newer.

Surprisingly, there are some AMD-based graphics cards that should, even with Ubuntu, use the proprietary fglrx driver (a prime example includes, unfortunately, my own HD3450-based PCIe graphics card).

---

### Post by peteyoferic on 2009-02-15
> **PGHammer said:**
> Actually, you should use the non-proprietary (and open-source) radeon driver, as that driver was developed specifically to support the R3xx series (of which your 9600 series is a member).  The current open-source radeonhd driver was based on this driver, and is an alternative to it for the R3xx and newer.

Surprisingly, there are some AMD-based graphics cards that should, even with Ubuntu, use the proprietary fglrx driver (a prime example includes, unfortunately, my own HD3450-based PCIe graphics card).

Right, I did try to install the fglrx driver...both using the automated hardware driver menu item...and the instructions listed in my first post above...but neither have worked...the automated way just doesn't activate...and the way that worked for other people (listed in my earlier post) comes back with that error about broken packages...anyone know of another way to get the fglrx driver installed?...or what might be causing these issues?  My install is running fine otherwise (aside from some early dual booting issues) but every other bit of hardware is running fine.

---

### Post by peteyoferic on 2009-02-16
> **peteyoferic said:**
> Right, I did try to install the fglrx driver...both using the automated hardware driver menu item...and the instructions listed in my first post above...but neither have worked...the automated way just doesn't activate...and the way that worked for other people (listed in my earlier post) comes back with that error about broken packages...anyone know of another way to get the fglrx driver installed?...or what might be causing these issues?  My install is running fine otherwise (aside from some early dual booting issues) but every other bit of hardware is running fine.

I managed to install the Xorg version of the drivers via the add/remove software menu option instead...so far so good.

---

