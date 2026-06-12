---
title: "multiple 4k monitors on 16.04, many different issues on various desktops"
date: 2016-08-17
forum: Hardware
---

### Post by jjv on 2016-08-17
The problem is supporting two external 4k monitors from a notebook that has a built in 4k display.

I can run either external 4k monitor from HDMI or mDP just fine on all desktops (Unity, Gnome, Gnome classic, Gnome Flashback (Compiz) and Gnome Flashback (Metacity)). I am forced to reboot any time I plug in or unplug an external monitor. If I do not all I get is a set of displays flashing on and off and the system is unusable. But I experience several problems using both external monitors along with the builtin display.

I would like to know if anyone has had any luck configuring two external 4k monitors to a notebook with a native 4k display. The hardware specifications indicate it is possible.

**Hardware:**

Dell Precision 7710 notebook (one HDMI port and one mDP port)
No docking device being used.
Nvidia M5000M graphics card
Dell P2715Q diplays
16.04 using 4.4.0-31


**Testing**

Testing done with both Nvidia 361.45 and 367.35 drivers installed. I have not yet tested the 370.23 drivers that were recently released
Testing with different desktops
Testing with single HDMI monitor
Testing with single mDP monitor


**Results**

**Misc** The nvidia tool does not show any displays with either driver or any desktop. I am using the system tools supplied with Ubuntu.

**Unity desktop** - With two monitors the settings menu crashes when I attempt to go into System Settings -> Displays. Nothing has allowed me to configure two external monitors under unity. Tests were done using both Nvidia driver versions noted above.

**Gnome Flashback (both types)** - Using one external screen with either connector works fine, but screen positions are not remembered and must be restart each login (usually associated with a reboot). Using two external monitors does not work. The system will not let me login and always cycles back to the login page.

**Gnome Classic** - insufficient testing done on this desktop.

**Gnome** - This is the most successful combination. Running with the Nvidia 361 drivers works the best. The Nvidia 367 drivers would not work using external monitors. The three displays would always be presented as mirrored and the settings would not allow the builtin to be primary and the externals to be secondary. Only be reverting back to the Nvidia 361 drivers was I able to configure the external monitors. When running with one monitor all is well. When running with two external 4k monitors the system will boot up and I can login. The screen locations are remembered (good) but the system will usually freeze in 10 - 60 minutes. The system is completely unresponsive. No mouse or keyboard interaction, none of the displays (clock or interactive output on a terminal window) are updated.

When the displays freeze, the system appears to keep running based on the entries in the /var/log/syslog file. Entries keep coming in but the the system cannot be interacted with from the screens, keyboard or mouse. The freezing only seems to occur when the mouse is on one of the external displays or the active window is on one of the external displays. I will continue testing and post any other information here as I get it.

I also wonder if the monitor issues are somehow related to how the OS was installed. I had to install Ubuntu 16.04 server in order to install RAID during the initial install, then added the desktop packages later via apt. I work principally with Linux servers so I do not have much working knowledge concerning the video system.

---

### Post by jjv on 2016-08-31
I got both external 4k monitors working correctly, along with the built in 4k display.

The solution was a combination of kernel and nvidia driver.

Since I last posted I was using the 4.4.0-31. I upgraded to the 4.4.0-34 kernel but that caused even more problems. Things that worked in -31 no longer worked in -34. One example is a video converter to take mDP output and convert it to VGA for a conference room projector. Under -31 it worked perfectly, using -34 it would not recognize the projector at all.

I then recently updated the kernel to -36 and at the same time purged the existing nvidia drivers and installed 370.23. This combination of kernel and video drivers allowed me to use both external 4, monitors along with the built in 4k display on the notebook.

---

