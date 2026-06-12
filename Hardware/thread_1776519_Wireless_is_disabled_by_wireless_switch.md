---
title: "Wireless is disabled by wireless switch"
date: 2011-06-06
forum: Hardware
---

### Post by akshay2000 on 2011-06-06
Hello. I have Dell XPS 14 (L401x) which has (according to lspci) Intel Centrino Wireless Card. When I was using  Maverick Meerkat, WiFi worked just fine. Then I did fresh install of Natty Narwhal. Its not wubi install, its installed on separate partition. Even after doing this, wireless was fine. But now, when the wireless is switched off by F2 key before booting the computer, you just can't turn it on afterwards. If I try to turn it on, the  hardware LED indicating WiFi glows, but when I click connections icon on the panel, it says wireless id disabled by hardware switch! I fails to detect the change in state.
However, if I keep WiFi on by hardware and reboot (i.e., WiFi is enabled while the system boots) everything is fine. I can switch on and off using F2 key. Any fix to this?
I've already tried b43, no luck.

---

### Post by Bucky Ball on 2011-06-06
b43 is for Broadcom cards. Uninstall.

---

### Post by akshay2000 on 2011-06-07
> **Bucky Ball said:**
> b43 is for Broadcom cards. Uninstall.

Oh, I know that! But the thing is, within Dell's official drivers for Windows 7, there are a few from Broadcom. Moreover, b43 really seemed to solve my problem for one session at least! Would anybody throw light on this?

---

### Post by irv on 2011-06-07
I also have a Dell, but not your model. I am using the b43 driver because it is the only one that works with my Broadcom card 4311. Ubuntu and Xubuntu 11.04 has real issues with wifi cards for some reason. 10.X required installing the STA driver from "Additional Drivers" but this release won't work with that driver. I really feel it is in the kernel, because I had problem with Suse and other distros.

I think the kernel needs fixing. That's MO.

---

### Post by akshay2000 on 2011-06-08
> **irv said:**
> I also have a Dell, but not your model. I am using the b43 driver because it is the only one that works with my Broadcom card 4311. Ubuntu and Xubuntu 11.04 has real issues with wifi cards for some reason. 10.X required installing the STA driver from "Additional Drivers" but this release won't work with that driver. I really feel it is in the kernel, because I had problem with Suse and other distros.

I think the kernel needs fixing. That's MO.

I don't know why do you think so. All my hardware worked pretty well with 10.10 as well as 11.04. Its just that something has gone wrong in the course of use and I don't know how to fix it. I have 4 XPS lying around. Others work pretty well!

---

### Post by linuxnewuser2011 on 2011-06-08
> **akshay2000 said:**
> Hello. I have Dell XPS 14 (L401x) which has (according to lspci) Intel Centrino Wireless Card. When I was using  Maverick Meerkat, WiFi worked just fine. Then I did fresh install of Natty Narwhal. Its not wubi install, its installed on separate partition. Even after doing this, wireless was fine. But now, when the wireless is switched off by F2 key before booting the computer, you just can't turn it on afterwards. If I try to turn it on, the  hardware LED indicating WiFi glows, but when I click connections icon on the panel, it says wireless id disabled by hardware switch! I fails to detect the change in state.
However, if I keep WiFi on by hardware and reboot (i.e., WiFi is enabled while the system boots) everything is fine. I can switch on and off using F2 key. Any fix to this?
I've already tried b43, no luck.

same to same problem ..any solution ??????

---

### Post by selvin on 2011-06-08
Hi I have problem opposite to this one. I just installed Ubuntu 10.04 on my Dell inspiron mini 10 net book.
My wifi is running well but I cannot turn it off, its always in on state. I tried using Fn+F2 key(hardware key), but nothing happens. For Bluetooth there is an option to turn off via software, but there is none in case of wifi.
This is the first time I have installed Ubuntu, so I dont know much about it. Please help.

---

### Post by Bucky Ball on 2011-06-08
> **selvin said:**
> Hi I have problem opposite to this one. I just installed Ubuntu 10.04 on my Dell inspiron mini 10 net book.
My wifi is running well but I cannot turn it off, its always in on state. I tried using Fn+F2 key(hardware key), but nothing happens. For Bluetooth there is an option to turn off via software, but there is none in case of wifi.
This is the first time I have installed Ubuntu, so I dont know much about it. Please help.

If your problem is opposite to this one please post a new thread with a descriptive title and as much info as you can give  rather than burying a post in a thread with a description that has nothing to do with your issue. You will get more specific help. 

Welcome. ;)

---

### Post by akshay2000 on 2011-06-09
> **Bucky Ball said:**
> If your problem is opposite to this one please post a new thread with a descriptive title and as much info as you can give  rather than burying a post in a thread with a description that has nothing to do with your issue. You will get more specific help. 

Welcome. ;)

Thanks a lot Bucky Ball, he should post a new thread. But, maybe you can throw some light on the main problem. What I think is, removing driver packages completely and reinstalling them should solve the problem. But I don't know which drivers are being used. You see, I'm still having first cup!

---

### Post by Bucky Ball on 2011-06-09
akshay, open a terminal (Applications>Accessories>Terminal) and paste this in:

```
lshw -C network
```Post the result back here. That will give us the details of the chip the wireless card is using and drivers, if any, that are in use. ;)

Most Intel cards work 'out of the box'. Have you gotten online with a cable, gotten updates, and checked System>Administration>Additional Drivers? Sorry if you've answered that already.

---

### Post by akshay2000 on 2011-06-10
> **Bucky Ball said:**
> akshay, open a terminal (Applications>Accessories>Terminal) and paste this in:

```
lshw -C network
```Post the result back here. That will give us the details of the chip the wireless card is using and drivers, if any, that are in use. ;)

Most Intel cards work 'out of the box'. Have you gotten online with a cable, gotten updates, and checked System>Administration>Additional Drivers? Sorry if you've answered that already.

Never mind repeating a bit. Yeah, I know they work out of box, mine did too. But somehow, I managed to modify the 'box' and now it doesn't work. Wireless works, wireless switch doesn't! And yeah, I can always use cable connection (like I'm doing now.) All additional drivers are installed. And I like to run apt-get update && upgrade when I have nothing to do! So, its always up to date. Read first post and you'll get the problem. Its not about card, its about switch.

Heres's the output.
```
 *-network DISABLED      
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: wlan0
       version: 35
       serial: 58:94:6b:b2:49:08
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic-pae firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:fbc00000-fbc01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:16:00.0
       logical name: eth0
       version: 06
       serial: b8:ac:6f:c5:27:89
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=172.24.32.38 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:47 ioport:c000(size=256) memory:d2c04000-d2c04fff memory:d2c00000-d2c03fff

```I see it says network disabled even when its enabled and hardware LED is glowing.

Update: the first network doesn't show disabled if I leave wireless network switched on and then reboot. The line is *-network. Its expected, though. Everything works as it should, if I leave WiFi on while system is booting.

---

### Post by akshay2000 on 2011-07-03
Bump!

No solution, or its too simple to be asked here?

---

### Post by glynnk on 2012-05-08
Has there been any solution for these wireless switch problems on Dell computers yet?
I've just installed ubuntu 12.04 on an inspiron m301z and came across the problem after trying to type 'Alt F2'. Now I cannot turn the wireless back on.
I've come across many threads on this forum related to this issue, most of them failing to articulate the problem, going way off the mark and resorting to installing new drivers etc. 

The problem is that, instead of a physical wireless switch, these laptops use 'Fn+F2' to turn on/off the wireless. The wireless turns off when the keys are pressed, as expected. The wireless does not turn on when the keys are pressed again, not as expected. Windows handles it. Fedora handles it. Surely there a proper workaround?

If not, it might be a good idea to package a usability warning when using dell inspiron computers, telling the user that, if they wish to use a wireless connection, they may have to reinstall their OS everytime they hit 'Fn+F2' by accident.

---

### Post by ts3 on 2012-05-08
> **glynnk said:**
> The problem is that, instead of a physical wireless switch, these laptops use 'Fn+F2' to turn on/off the wireless. The wireless turns off when the keys are pressed, as expected. The wireless does not turn on when the keys are pressed again, not as expected.

Hi, you can always try to run in terminal 

```
sudo rfkill unblock all
```

To see where the blocks are, before that, you can run [FONT="Courier New"]rfkill list all[/FONT] (no need for sudo for that).  In my experience (mostly hp & dell) hardware switches are tricky on linux but so far sudo rfkill unblock all has proven a reliable fix.

Cheers

---

### Post by akshay2000 on 2012-05-09
> **glynnk said:**
>  If not, it might be a good idea to package a usability warning when using dell inspiron computers, telling the user that, if they wish to use a wireless connection, they may have to reinstall their OS everytime they hit 'Fn+F2' by accident.

You don't have to reinstall Ubuntu every time you hit the key. Leave the wireless turned on by the switch and reboot. Wireless should work fine. Additionally, as mentioned above, run 'rfkill list all' to see which switches are blocked and then run 'rfkill unblock <switch>' to unblock. If that seems to work fine for you, you can set a key binding to run a script which will automatically run rfkill commands - so that your wireless works just like it does on Windows. Get back with your results.

---

