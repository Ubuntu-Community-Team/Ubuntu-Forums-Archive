---
title: "Shutdown/Restart and WiFi"
date: 2009-01-18
forum: Hardware
---

### Post by lowteq on 2009-01-18
Hello.

I just installed Ubuntu 8.10 on a Toshiba Portege R100 (model PPR10C-04M8Z).

The one problem I haven't been able to solve is a hang on shutdown and restart.  The OS does properly shut itself down, I've confirmed this by disabling the splash screen and watching the messages, however after the shutdown process is complete the laptop never actually turns off or restarts.  The screen blanks (back light turns off) but the fans and hard drive continue to spin.  I've left it for along time in this state to see what happens and nothing does.  Holding the power button down for the usual 4 seconds turns the laptop off.

I've been poking at this problem and here is what I've found.

The laptop has a switch to disable the WiFi (an Intel Pro/Wireless 2100).  If I turn that off then the laptop does shutdown or restart properly.  Only when that switch is on does the problem occur.  I've tried manually taking down the wireless interface (ifconfig eth1 down) and then doing a reboot or shutdown and the problem still occurs.  I've noticed that whether or not I boot with the wireless turned on the module for the WiFi card is loaded (ipw2100).  I've done some research and some people mentioned an interaction with the ALSA-UTILS system, that didn't turn out to be the case.  If I use the wired ethernet connectoin these problems do not occur.

I have not installed any third party applications or kernel modules yet.  I did modify my xorg.conf to use the Trident X server.  I also added vga=791 to my boot parameters to fix a problem when going to or from battery power.  However this shutdown/restart problem was occurring before I made those changes.

I'd appreciate any insights people here might have.

Craig.

---

