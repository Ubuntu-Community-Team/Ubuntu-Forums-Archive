---
title: "No GUI when starting up LiveCD: only CLI"
date: 2009-02-03
forum: Hardware
---

### Post by Sonadow on 2009-02-03
Ok, i'm currently having this problem with Ubuntu (Intrepid and Jaunty Alpha 3) on my notebook.

I currently own an Acer Aspire 6530G, with the following specs:

- 16" WCG screen
- AMD Turion X2 RM-72 (2.1GHz)
- ATi Radeon 3470 x2 Hybrid Graphics (Mobility Radeon 3200 + Mobility Radeon 3470)
- 320GB Hitachi SATA HDD 
- 3GB DDR2 SDRAM
- Atheros WLAN

On POST, i entered the BIOS to set the boot sequence to strat with the DVD drive first. I then oinserted my Jaunty Alpha 3 LiveCD and was taken to the Ubuntu boot menu. I then selected 'Try Ubuntu without any changes to your computer'.

The Linux kernel loaded up and i saw the Ubuntu loading screen with the orange status indicator dancing up and down. 

After the status bar completed loading, i was thrown into a CLI instead of ths standard GNOME interface. Something was wrong, so i tried to run:

```
sudo startx
```

I got lines and lines of text which i do not understand (hey, im just starting out), but i remember seeing this line:

```
Fatal error:
No screens detected
```

So i decided to retry the process, except that this time, i selected Sage Graphics Mode on the Ubuntu boot menu. No dice: still the CLI instead of the GNOME environment with the same error as the previous when i attempted to run startx

A little help here? Would really like to try and run the LiveCD on my Aspire, since i only have 2 more semesters left in campus, and after that, i have no need for the Windows exclusive software anymore. Would like to experiment on Ubuntu on this notebook of mine, since i had some degree of luck with installing it on my desktops, be it LiveCD or actual installation.

At the same time, maybe i should point out something with my Jaunty LiveCD: when i inserted the Jaunty Cd into my desktop PCs, and selected 'Try without changing', normal graphics mode threw up a black screen (no GUI or CLI) at all after the Ubuntu status bar screen: however, Safe Graphics Mode successfully initiated the GUI. (My desktop PCs run on an old VIA P4M80 graphics and an Intel GMA 950.) And i don't think there's anything wrong my CD.

---

### Post by Crafty Kisses on 2009-02-03
Did you install any graphics drivers before hand? Try reconfiguring your X:
```
dpkg-reconfigure xserver-xorg
```

---

### Post by Sonadow on 2009-02-03
> **Codename said:**
> Did you install any graphics drivers before hand? Try reconfiguring your X:
```
dpkg-reconfigure xserver-xorg
```

By graphics drivers, do you mean drivers for Linux or Windows?

There are ATi drivers installed for Windows Vista (this notebook is currently running off Vista). No drivers installed for Linux, because im trying to experiment it from a LiveCD first.

---

### Post by Crafty Kisses on 2009-02-03
Was this 64-bit Jaunty or 32-bit Jaunty?

---

### Post by Sonadow on 2009-02-03
> **Codename said:**
> Was this 64-bit Jaunty or 32-bit Jaunty?

It's an i386 copy. So 32-bit.

Here are some snippets of the error that was thrown up when i tried to run sudo startx:

```

(==)log file: "/var/log/Xorg.0.log"
(==)using config file: "/etx/X11/xorg.conf"

Primary device is not PCI
(EE)No devices are detected

Fatal server error:
No screens found

xinit: no such file or directory (errno 2): unable to connect to X server
xinit: no such process (errno 3): server error
```

The log file was too log for me to copy down on pen and paper, but i managed to catch sight for this line:

```

multiple primary devices detected

- ATi Radeon 3470 
- Ati Radeon 3200


```

*something like that. Not accurate, but i think you get the idea.

running sudo dpkg-reconfigure xserver-xorg did not do anything useful at all.

Apparently, a quick search reveals that other users have been able to load the GUI on a Mobile Radeon 3470. I wonder what is wrong with my notebook?

(Anyway, back to Vista on the Acer, soon to install Win 7 beta. I have no ill feelings towards Microsoft, since I'll give them the credit for the wide hardware support/compatibility they have)

---

### Post by Sonadow on 2009-02-04
Quick update to the situation:

It's not just the Jaunty LiveCD that fails: even my CDs of Hardy and Intrepid fail to load into the GUI after the status bar loading splash.

Same error as the one posted in my earlier topics.

I'm starting to suspect that it may be the presence of 2 Radeon cards in my notebook, but i'm not sure.

Anyone got a workaround for this? (there's no option to disable Hybrid CrossfireX in the BIOS.)

---

### Post by Sonadow on 2009-02-18
<bump after 2 weeks>

apparently, even Kubuntu and Xubuntu LiveCDs do not work as well.

Any suggestions? Because I am quite keen to try out Linux on my notebook.

---

