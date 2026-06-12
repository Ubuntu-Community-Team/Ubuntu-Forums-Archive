---
title: "Constant Xubuntu crashes on an old PC"
date: 2014-01-25
forum: Hardware
---

### Post by michael99 on 2014-01-25
Hello all!
I have a very old custom build pc that is on its way to graveyard. I had WinXP on it but due to a malware I had to reformat. I installed Xubuntu wishing it will last a few more months before I build a new one. Just a note, I didn't have any hardware problems, it's just the age problem.

I installed Xubuntu after overcoming some difficulties, like a locking up gpu (solved with nomodeset setting) and an unrecognized wireless card. I *think* I solved the problem with the wireless drivers by using ndiswrapper and a windows driver (netani.inf).

The problem now is that after making the wireless card to work, the computer is extremely unstable. Each time that I boot the computer, it's going to either freeze while booting or boot and after a few minutes freeze. By freeze I mean a total lock down, I get no response by keyboard / mouse / SYSRQ. It's just the screen showing my applications (or the boot process if it freezes while booting) and I have to cold reboot.

My GPU is a nvidia geforce2 mx 200 and my wireless card is a AGN100. My cpu is an intel pentium 4
Attached is boot.log kern.log dmesg and syslog

Can anybody help?
Thank you

---

### Post by sudodus on 2014-01-25
Welcome to the Ubuntu Forums :-)

My experiences of ndiswrapper are not good, so I would suggest that you use either a wired connection or a wireless adapter or card, that works out of the box with linux (xubuntu).

When you search the internet for ***linux wifi*** you find a lot, for example this link [http://wireless.kernel.org/en/users/Devices](http://wireless.kernel.org/en/users/Devices) where you can check what can be expected to work with linux.

---

### Post by michael99 on 2014-01-25
Hey!
Unfortunately this computer doesn't have an ethernet card, just a wireless one and I'm not spending any money to buy anything for it as it will be a waste of money.
Isn't there a work around with the existing hardware?

---

### Post by sudodus on 2014-01-25
Searching for ***agn100 linux driver*** finds for example this link

[http://sourceforge.net/projects/agnx80211driver/](http://sourceforge.net/projects/agnx80211driver/)

Maybe it can solve your problem.

---

### Post by michael99 on 2014-01-25
I tried it but when i run make it outputs these errors and stops: > neofyta@neofytapc:~/Desktop/agnx$ sudo make make -C /lib/modules/3.11.0-12-generic/build M=/home/neofyta/Desktop/agnx modules make[1]: Entering directory `/usr/src/linux-headers-3.11.0-12-generic'   CC [M]  /home/neofyta/Desktop/agnx/rf.o In file included from /home/neofyta/Desktop/agnx/rf.c:17:0: /home/neofyta/Desktop/agnx/debug.h: In function ‘dump_ieee80211_hdr’: /home/neofyta/Desktop/agnx/debug.h:315:2: error: implicit declaration of function ‘DECLARE_MAC_BUF’ [-Werror=implicit-function-declaration]   DECLARE_MAC_BUF(mac);   ^ /home/neofyta/Desktop/agnx/debug.h:315:18: error: ‘mac’ undeclared (first use in this function)   DECLARE_MAC_BUF(mac);                   ^ /home/neofyta/Desktop/agnx/debug.h:315:18: note: each undeclared identifier is reported only once for each function it appears in /home/neofyta/Desktop/agnx/debug.h:372:9: error: implicit declaration of function ‘ieee80211_get_hdrlen’ [-Werror=implicit-function-declaration]          hdrlen = ieee80211_get_hdrlen(fctl);          ^ /home/neofyta/Desktop/agnx/debug.h:378:3: error: implicit declaration of function ‘print_mac’ [-Werror=implicit-function-declaration]    printk(" A1=%s", print_mac(mac, hdr->addr1));    ^ cc1: some warnings being treated as errors make[2]: *** [/home/neofyta/Desktop/agnx/rf.o] Error 1 make[1]: *** [_module_/home/neofyta/Desktop/agnx] Error 2 make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-12-generic' make: *** [modules] Error 2   I guess I'm missing something to install but I don't know what. It's a fresh xubuntu 13.10 install. Do you have any idea how can these errors be solved?  Thank you

---

### Post by sudodus on 2014-01-25
Did you install the compiler and the repositories for source code?

Start ***Synaptic***. Select

Settings -- Repositories

And tick the entries for ***source code***

'Reread' and install ***gcc***

-o-

Try to run the make script again

---

### Post by michael99 on 2014-01-27
Hey!
gcc is installed at its newest version already and the repositories for source code are ticked. Note that I don't have internet on that computer until I get the wireless card working.
Anything else to try?

---

### Post by sudodus on 2014-01-27
An alternative would be to try some other version of Ubuntu or some other linux distro, that might work out of the box without any special wifi driver.

I'm not very good at understanding compiler errors and debugging the compiling process. With some luck someone who knows better will read this and start helping you.

---

