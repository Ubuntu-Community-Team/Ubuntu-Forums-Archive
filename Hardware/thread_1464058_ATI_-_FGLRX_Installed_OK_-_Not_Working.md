---
title: "ATI - FGLRX Installed OK - Not Working"
date: 2010-04-27
forum: Hardware
---

### Post by Brandon168 on 2010-04-27
Quick Background:

Everything worked great on Ubuntu Karmic.  This is my first non-server linux install in years.  I got the itch to install Lucid-Lynx, as an X beginner, and the trouble started with my ATI Driver.

Key Points:
* Sony VGN-SR390
* ATI Technologies Inc Mobility Radeon HD 3400 Series
* Lucid Lynx w/ 2.6.32-21-generic running 64 bit
* System -> Administration -> Hardware Drivers shows ATI FIRE GL installed and activated
* Missing menu options to configure amd/ati card, not under Applications, not under System (menu option was present under 9.10)
* System cannot find aticonfig, amdcccle, etc.  BUT I can change directory to /usr/lib/fglrx/bin and the commands are there
 
root@belliott-laptop:/usr/lib/fglrx/bin# ./aticonfig
Unable to open /etc/ati/control, please reinstall the driver.
./aticonfig: No supported adapters detected

root@belliott-laptop:/usr/lib/fglrx/bin# dmesg |grep fglrx
[   14.152416] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   14.199148] [fglrx] Maximum main memory to use for locked dma buffers: 3770 MBytes.
[   14.199379] [fglrx]   vendor: 1002 device: 95c4 count: 1
[   14.199720] [fglrx] ioport: bar 1, base 0x9000, size: 0x100
[   14.199866] [fglrx] Kernel PAT support is enabled
[   14.199887] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors

I've read everything regard fglrx here and over at launchpad.  I've tried removing, purging, and manually deleting all things ati and fglrx, rebooting in between steps, the re-installing.

A few re-installs ago I was able to issue /usr/lib/fglrx/bin/aticonfig --initial -f and generate an X config; however, Ubuntu prompted me with errors and I have to run in low graphics mode.  I no longer get this far though as aticonfig does not find the adapter.

I ran /usr/src/fgrlx-8.723.1/make.sh, the log is attached which shows a warning but no errors.

What other information do I need to provide?

I've tried for weeks to get this right and I've read and tried everything I can think of.  Any thoughts?

Thanks,

Brandon

---

