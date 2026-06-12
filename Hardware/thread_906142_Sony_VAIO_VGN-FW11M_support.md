---
title: "Sony VAIO VGN-FW11M support"
date: 2008-08-31
forum: Hardware
---

### Post by pscaffardi on 2008-08-31
Hi there!
I installed Hardy on my Sony VAIO VGN-FW11M.
These were the problems i encountered:

a) only 3GB of available RAM (fixed switching to server kernel)
b) Intel WiFi Link 5100 wireless adapter not working (i had to compile and install last wireless compat drivers; now the adapter works but it generate a kernel panic on shutdown)
c) many function keys dont work (brightness, lcd/ext.monitor switch, sleep, zoom in/out)
d) many multimedia keys dont work (S1, play/pause, stop, next, prev and AV mode)
e) when using an external monitor to extend the desktop i cannot set its resolution greater than the LCD (1600x900). My laptop VGA is ATI Radeon HD 3400. 

I am using last available server kernel (2.6.24-21). 

About function and multimedia keys, i have discovered some of them send valid scancodes (using 'sudo showkey -s'):
- (BLOCK SCROLL=fn+BLOCK NUM): 0x46 0xC6

I try folloing [wiki hotkey research instructions]("https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch") but no method worked.
These are DMI identification string of my laptop:

system-manufacturer: Sony Corporation
system-product-name: VGN-FW11M
system-version: C600CZSB

I attach the output of snc-dsdt.sh.

If you have suggestions i'm here to test your workarounds/fixes.

Bye bye

---

### Post by josepcoves on 2008-10-08
Hi pscaffardi,

I'm also unable to use function keys...

By the way... how did you manage to install 2.6.24-21 server kernel? Did you add new apt repositories?

Thanks

Josep

---

### Post by josepcoves on 2008-10-09
Hi pscaffardi,

I managed to install linux-kernel 2.6.24-21 by adding repositories:

deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) hardy-proposed main universe

But when I restarted with that kernel version I still had the same amount of RAM (3GB)... did you do anything else?

Thanks

Josep

---

