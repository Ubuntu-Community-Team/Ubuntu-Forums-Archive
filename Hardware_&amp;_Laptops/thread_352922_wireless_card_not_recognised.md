---
title: "wireless card not recognised"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by stephen in houston on 2007-02-03
Need help,I have HP Pavillion ze4800, after installing I does not see wireless card any ideas

---

### Post by H.E. Pennypacker on 2007-02-04
Through a few minutes of Internet searching (Google, Ubuntu forums, ndiswrapper website, etc.) , I found out the wireless card your HP Pavillion Ze4800 notebook uses is HP WLAN 54G W450.  Using that information, I was able to do a search that revealed the chipset is BCM4306.

That information found a thread in which someone using the same chipset was able to get wireless working.  Check out his/her instructions in this this thread (the last post):

[http://ubuntuforums.org/showthread.php?t=135808&page=2&highlight=HP+WLAN+54g+W450](http://ubuntuforums.org/showthread.php?t=135808&page=2&highlight=HP+WLAN+54g+W450)

If those instructions don't work out, check out the following:

[http://ubuntuforums.org/showthread.php?t=201902&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=BCM4306)

That should work...but here's yet another thread:

[http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306)

Good luck!

---

### Post by gradedcheese on 2007-02-04
> **stephen in houston said:**
> Need help,I have HP Pavillion ze4800, after installing I does not see wireless card any ideas

By the way, when you are curious about hardware such as wireless cards/chipsets, run 'lspci' in a terminal.  For example, my Belkin WiFi card shows up as:

07:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

in lspci.  This lets me know a little more if I want help with it (namely, Belkin used an Atheros ARG5005G chip, etc).  You should try this on your HP to double check as far as what chipset is installed.

---

### Post by werebear on 2007-06-24
Hullo!
I own a Presario 2500 w/512 mb ram, P4 2.66 ghz, ATI card which works excellent without using the "custom" ATI drivers for Linux (they actually mess up my system). I installed Ubuntu + Beryl and can run Windows XP (virtually) with no problems, all at once. Now, I have the Wireless adapter HP w450 (BCM 4306), I have followed various instructions found on-line to enable it. It works at first, but it stop working PERMANENTLY upon re-booting, with no way to restore it with any of the methods mentioned here, except if I re-install Ubuntu and go trough the process all over again. Any ideas as to what am I doing wrong? None of the instructions above seem to provide a permanent solution. Any ways I can download the required components and save them to a removable disk and run them from there? The new Ubuntu (7.04) doesn't fix this, nor the "Mint" distro. I tried others that claim to have better compatibility with the same results.
Help!!
Thank You!

---

### Post by Ayuthia on 2007-06-24
Did you try:
sudo modprobe ndiswrapper

If that works, you will need to add ndiswrapper to /etc/modules so that it will start up automatically on reboot.

If it does not work, does anything show up in dmesg?

---

