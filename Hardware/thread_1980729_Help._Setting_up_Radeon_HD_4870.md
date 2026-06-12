---
title: "Help. Setting up Radeon HD 4870"
date: 2012-05-15
forum: Hardware
---

### Post by dat789 on 2012-05-15
**$ lsb_release -all**
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise

**$ lspci -v**

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV770 [Radeon HD 4870] (prog-if 00 [VGA controller])
	Subsystem: XFX Pine Group Inc. Device 2448
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at ff6f0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 8000 [size=256]
	Expansion ROM at ff6c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

**Additional info/ image**
[IMG]http://i.imgur.com/wMdt5.png[/IMG]

At the moment of this writing, my xorg.conf (/etc/X11/xorg.conf) is empty.

Referring to the image above, I have previously activated the first item -- ATI/AMD proprietary FGLRX graphics driver (post-release updates) -- and after rebooting my screen shows a message that says "No input signal... out of range" or something similar to that effect. I had no choice but to reinstall Ubuntu. 4 times already.

I am using a VGA input LCD screen.
Screen resolution is, I believe, small -- fonts, images appear fairly large on a 17" screen.

Question is how to update the graphic card so that Ubuntu takes advantage of every aspect of the graphics card? It is now a fresh install. If I have missed out any info or that you need more info, I'll be happy to provide. Let me know.

Any help appreciated. Thanks!

---

### Post by dat789 on 2012-05-16
Hello? If you have a Radeon graphics card set up on your Ubuntu machine, your response is much valued here.

Or, please point to a direction where I can read up and configure it.

Thanks!

---

### Post by pme 72 on 2012-05-17
If you run into an issue with an AMD driver you should be able to remove it without having to reinstall the OS. There are instructions for removing the proprietary driver in the Precise Installation Guide. They have saved me many times when curiosity and experimentation have gotten the best of me. 

[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

I have an entry level HD4550 card running 10.04 with the radeon driver from the x-swat PPA.

---

### Post by dat789 on 2013-02-24
I have finally resolved this issue that has plagued me for over a year and thensome.

There was one other additional element that is now different from my first post -- now I have 2 screens where one is new.

Basically, I have reinstalled Ubuntu 12.04 LTS (precise). My graphics card is still the ATI Radeon HD 4870 1 GB.

First, I've edited grub from /etc/default because I had a problem with it booting to black screen / straight to command prompt. The following had resolved it amicably.
```
sudo vi grub
```
Make sure you make a backup of this file.
Here is the paste of my grub.
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Set the GRUB_CMDLINE_LINUX_DEFAULT to nomodeset.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=\"Linux\""
```

Then save and quit. Remember to update grub.
```
sudo update-grub
```

From the launcher, I searched for 'Additional Drivers'.
There was only 1 item -- ATI/AMD proprietary FGLRX graphics driver.
Activate this driver. Reboot.

Once you get back onto the desktop (Unity), open launcher and search for Catalyst. Once you activated the FGLRX, Catalyst was downloaded and installed.

Start the 'AMD Catalyst Control Centre (Adminstrative)'.
Enter your sudo password (if you have set it).
On the left, expand Display Manager.
Adjust for your screen's settings.

For my case, since I now have 2 displays, I've selected "Multi-display desktop with display(s) 2 under the Multi-Display tab on the right. How the clown fish appears will give you a clue to how your monitor will be displayed.

Apply. Reboot!
All set!

---

