---
title: "Problems with the WiFi broadcom driver"
date: 2010-12-22
forum: Hardware
---

### Post by themoth on 2010-12-22
Well,
 I can not connect to the wireless network.

 1-First of all, I naively tried through the GUI, System> Administration> Hardware Diver I have selected Broadcom STA wireless driver and tried to activate it.
 I opened a window of that nightmare with the exclusion of access:
  "The installation of this driver failed Consult the log files for more information: / var / log / jockey.log"
 I found it in a number of debugging, but what seems important to me is this:

 12/22/2010 11:28:38,345 WARNING: modinfo for module wl failed: ERROR: modinfo: Could not find module wl

 12/22/2010 11:28:38,345 WARNING: / sys / module / wl / drivers does not exist, can not rebind wl driver

 I do not know how to solve this problem.

 2-The second step was to try to reinstall bcmwl-kernel-source through the package manager.
 I rebooted and I tried again to select it from the driver but the result is the same.

 3-then I downloaded the driver here:
  [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
 Consult the readme I happily discovered that my hardware is supported.
 In fact, typing in terminal: lspci-vvnn | grep 14e4
 comes out this:
 05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b / g [14e4: 4315] (rev 01)

 My computer is a Dell Studio xps 1645 and my distribution is Ubuntu Studio 10.04, 64bit architecture.

 -Now try to install the driver I downloaded "manually" but I have never done.
 have you got other options to offer me?!

 -I downloaded the driver should not be what you find in the repositories?


 sorry if I have been verbose and for my bad English.

 thanks in advance.

---

### Post by TBABill on 2010-12-22
Can you go into Synaptic and mark any files associated with Broadcom for complete removal? Then click apply, restart and reinstall the driver? You may get errors when you restart because the driver is mentioned in /etc/modules, but you should still be able to try to reinstall it. I have a Dell Inspiron 1564 with the Broadcom BCM4312 and I can confirm it works in 10.04, but it takes some work to get it going in 10.10.

---

### Post by cchhrriiss121212 on 2010-12-22
Studio does not come with a network manager, you can install one from these 2 methods:
If you have a wired connection, plug in and open synaptic then install gnome network manager
If you have no wired connection, browse the Studio DVD for the network manager packages and install them in order of dependency

---

### Post by themoth on 2010-12-23
I tried to delete, reboot, and reinstall bcmwl-kernel-source, the result is the same as mentioned in section -1 of the first post.
 I also tried to install network-manager-gnome, but even after this attempt, nothing has changed ...
 In the log file / var / log / jockey.log keeps telling me that didn't find wl...

 thanks for trying!

---

### Post by themoth on 2010-12-23
well,
 Now I managed to install the driver!
 missing kernel-headers.
 but still the wireless connection does not work ... actually I noticed that in System> Preferences> Connections window is empty.
 not even see the cable connection I'm using now!

---

