---
title: "Wireless issue"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by brennydoogles on 2007-07-03
I have an older E-machines laptop onto which I just installed Ubuntu. It was a nightmare for several reasons, but the main one was that the alternate cd kept freezing, and would randomly "forget" to do things it told me it was doing (like setting up users, it created a full install with no users). I never got it to successfully set up networking for me, and I think that part of the problen is enabling my network adapter. In windows I had to hit Fn+F2 to enable the wireless card, but I have a sneaky suspicion that this keyboard shortcut does nothing now. Is there a way to enable the wireless adapter through terminal (bearing in mind that it was not set up during the installation)?? Any help would be greatly appreciated, and thank you in advance!!

---

### Post by Megatog615 on 2007-07-03
Post the output of ifconfig -a.
Post the output of iwconfig.
Post the output of lspci.

In Linux, you're not set to have hardware modification privileges. Only the root account can modify hardware. If you set up a hotkey to enable the card, you'd be asked for your password every time. Unless you don't care about that...

---

### Post by brennydoogles on 2007-07-03
> **Megatog615 said:**
> Post the output of ifconfig -a.
Post the output of iwconfig.
Post the output of lspci.

In Linux, you're not set to have hardware modification privileges. Only the root account can modify hardware. If you set up a hotkey to enable the card, you'd be asked for your password every time. Unless you don't care about that...

ok, ifconfig -a gave me an error, so here it is as well as ifconfig:
```
brendon@brendon-linux:~$ ifconfig -a.
ifconfig: option `-a.' not recognised.
ifconfig: `--help' gives usage information.
brendon@brendon-linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8B:63:B0:FF  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fe63:b0ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102019 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89397015 (85.2 MiB)  TX bytes:10515924 (10.0 MiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 b)  TX bytes:600 (600.0 b)

```
and iwconfig:
```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```
and lspci:
```
brendon@brendon-linux:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem
brendon@brendon-linux:~$ 


```

ps-- If I don't have to enter my password, I don't neccesarily want to, and if I can write a script to automatically turn on my wireless adapter upon boot... I would love to do that as well. Thank you for your help!!

---

### Post by Megatog615 on 2007-07-03
You put a period on the end of ifconfig -a. It doesn't matter anyway. The -a shows output for all devices that have some kind of network protocol but aren't necessarily network cards. For example, infrared adapters. Sometimes an Ethernet card can be categorized as a card that only shows up with -a.

The BCM4401 seems to be a wired Ethernet card. Are you using the laptop to post here right now?

is the wireless adapter on the motherboard or is it a PC Card that plugs in the side of the laptop? If it is built-in, and is not even detected by lspci(it can show even unsupported hardware), there is probably an option in the BIOS to enable it permanently.

What is the model number of the laptop?

---

### Post by brennydoogles on 2007-07-03
I made an idiot mistake. When I read the replies this morning, I was tired and not thinking, so I typed in the commands and posted the output here.... all from my desktop computer. Not my laptop like I should have. So..... let's try this again from the right computer shall we??


```
brendon@localhost:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:03:25:23:24:E4  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe23:24e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1041 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:936277 (914.3 KiB)  TX bytes:146012 (142.5 KiB)
          Interrupt:21 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:CB:4F:64  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x4000 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



brendon@localhost:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



brendon@localhost:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
brendon@localhost:~$ 


```

Thanks for thehelp everyone!!

---

### Post by Jacemg on 2007-07-03
you know i'm probably going to get flamed for something like this... posting with little or no expirience with UNIX but if its behaving that randomly it begs the question of some bad memory..
Just because you've never seen more random things happen until you've run into a stick of bad RAM or mixed a few incompatible sticks together.. try mem test on the live cd just for the heck of it.

---

### Post by brennydoogles on 2007-07-03
> **Jacemg said:**
> you know i'm probably going to get flamed for something like this... posting with little or no expirience with UNIX but if its behaving that randomly it begs the question of some bad memory..
Just because you've never seen more random things happen until you've run into a stick of bad RAM or mixed a few incompatible sticks together.. try mem test on the live cd just for the heck of it.

I only have 1 stick of ram (256 mb OUCH!) and it is factory installed. If it were bad, I think the laptop would not run. Thanks for the suggestion anyways!!

---

### Post by Megatog615 on 2007-07-03
Ok, it looks like you have a card that's supported under the bcm43xx driver. Unfortunately the bcm43xx driver is buggy(we'll get more into that later though).

I need you to post the output of this command:
```
cat /etc/modprobe.d/blacklist
```

If bcm43xx is not blacklisted, you should follow this guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

It gets a little technical, but from what I've heard the bcm43xx chipset works well now that firmware is supported.
Step 1.3.1.1 seems like the best way to obtain the firmware.

---

### Post by ugm6hr on 2007-07-03
Two options:
[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by brennydoogles on 2007-07-03
> **Megatog615 said:**
> Ok, it looks like you have a card that's supported under the bcm43xx driver. Unfortunately the bcm43xx driver is buggy(we'll get more into that later though).

I need you to post the output of this command:
```
cat /etc/modprobe.d/blacklist
```

If bcm43xx is not blacklisted, you should follow this guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

It gets a little technical, but from what I've heard the bcm43xx chipset works well now that firmware is supported.
Step 1.3.1.1 seems like the best way to obtain the firmware.

I don't really know what most of this means, but here it is!!
```
brendon@brendon-linux:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
brendon@brendon-linux:~$ 

```

---

### Post by Megatog615 on 2007-07-03
Everything seems to be in order. Proceed with the tutorial I posted!

---

### Post by brennydoogles on 2007-07-03
> **Megatog615 said:**
> Everything seems to be in order. Proceed with the tutorial I posted!

ok, remember that moron moment I had earlier?? I did it again. Here is the out put of cat /etc/modprobe.d/blacklist again:
```
brendon@localhost:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
brendon@localhost:~$ 

```

---

### Post by ugm6hr on 2007-07-04
> **brennydoogles said:**
> ok, remember that moron moment I had earlier?? I did it again. 

How far did you get in this?: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

This is a native fwcutter option (easier to achieve, less issues with upgrades, but apparently limited to 11Mbps).

Start at Step 1.3.1:
```
sudo apt-get install bcm43xx-fwcutter
```

PS: The second link in my previous post should achieve the same outcome (?possibly easier).

---

### Post by sargentdean on 2007-07-04
If you want 54Mbps then follow the tutorial here. 
[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306]("http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306")


I did and had my wireless up and running in no time.

There's just one more step not covered in the tutorial. You need to: 

> sudo gedit /etc/modules

Then add:

> ndiswrapper

save and reboot.

If you don't add ndiswrapper to '/etc/modules' then your boot time might slow down.

Hope this helps.

Earl

---

### Post by brennydoogles on 2007-07-06
> **sargentdean said:**
> If you want 54Mbps then follow the tutorial here. 
[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306]("http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306")


I did and had my wireless up and running in no time.

There's just one more step not covered in the tutorial. You need to: 



Then add:



save and reboot.

If you don't add ndiswrapper to '/etc/modules' then your boot time might slow down.

Hope this helps.

Earl

Ok, I am fairly certain that I have installed the driver correctly... but I am still back to my original problem... Enabling the card. My HARDWARE is set up so that you have to enable the card after every reboot (in windows you could do that by pressing Fn F2), so that the card starts out in airplane mode every time. Because my laptop is old, it doesn't have a switch of any kind, so you have to use the keyboard shortcuts to do it. How can I make this happen?? If it is a terminal type of thing, I would love to put it into a script to run at boot-time (I know I will have to put in my password every time, and I'm ok with that). Any help would be greatly appreciated!!!

---

### Post by brennydoogles on 2007-07-06
I also figured this might be helpful:
```
brendon@localhost:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by brennydoogles on 2007-07-07
*Polite Bump*

---

### Post by sargentdean on 2007-07-07
> **brennydoogles said:**
> *Polite Bump*

I don't know if this is meant for me or everyone. If meant for me you are out of luck.:p I am a complete noob at linux. I have to search the forum for almost everything I want to try. 

Sorry;

Earl

---

### Post by brennydoogles on 2007-07-07
> **sargentdean said:**
> I don't know if this is meant for me or everyone. If meant for me you are out of luck.:p I am a complete noob at linux. I have to search the forum for almost everything I want to try. 

Sorry;

Earl

Meant to help get the post where people will find it. Thanks for the help anyway!

---

### Post by fredj on 2007-07-07
What happens when you click on the network icon in the taskbar? Does it show any wireless networks. It
seems that your wireless adaptor is being recognised and does have a driver.
Open a terminal and enter lshw -class network. Post the output from that here.

---

### Post by brennydoogles on 2007-07-07
> **fredj said:**
> What happens when you click on the network icon in the taskbar? Does it show any wireless networks. It
seems that your wireless adaptor is being recognised and does have a driver.
Open a terminal and enter lshw -class network. Post the output from that here.

Bash told me that I needed to run the command as super-user, so here is the output:
```
brendon@localhost:~$ sudo lshw -class network
Password:
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:25:23:24:e4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.2.3 latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:dfffc000-dfffcfff irq:21
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:cb:4f:64
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfffa000-dfffbfff irq:17
brendon@localhost:~$ 


```

I went through the process of installing the driver, and it looks like I did it correctly (from what I can tell). I believe I just need to tell the hardware that it's ok to send and recieve information.

---

### Post by ugm6hr on 2007-07-08
If you are now using ndiswrapper (which I think you are trying now), have you blacklisted bcm43xx?

It looks like it is still using the linux native driver.  Check for bcm43xx in etc/modprobe.d/blacklist - it wasn't there last time.

If it's not there, in Terminal:
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

If you are still having problems, tell us where you got to in the tutorial before it started misbehaving.

---

### Post by taustin12 on 2007-07-08
Brenny, which eMachines laptop are you using? I am having the exact same problem with my older emachines m5310 laptop, and I have the same suspicions regarding the fn - f2 button.  Some fn buttons appear to work properly in ubuntu (screen brightness - fn f7, fn f8 ) but the fn f2 appears unresponsive.  I haven't looked in my bios yet, if I find anything out I'll post.

One noob question: I am having trouble 'unblacklisting' a device.  I don't have permissions to edit the file.  Is there a superuser account I should be familiar with?

---

### Post by brennydoogles on 2007-07-08
> **taustin12 said:**
> Brenny, which eMachines laptop are you using? I am having the exact same problem with my older emachines m5310 laptop, and I have the same suspicions regarding the fn - f2 button.  Some fn buttons appear to work properly in ubuntu (screen brightness - fn f7, fn f8 ) but the fn f2 appears unresponsive.  I haven't looked in my bios yet, if I find anything out I'll post.

One noob question: I am having trouble 'unblacklisting' a device.  I don't have permissions to edit the file.  Is there a superuser account I should be familiar with?

It is an emachines M5414, with 256 MB of ram and a 60 GB hd. It is almost 2 years old.

---

### Post by brennydoogles on 2007-07-08
> **ugm6hr said:**
> If you are now using ndiswrapper (which I think you are trying now), have you blacklisted bcm43xx?

It looks like it is still using the linux native driver.  Check for bcm43xx in etc/modprobe.d/blacklist - it wasn't there last time.

If it's not there, in Terminal:
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

If you are still having problems, tell us where you got to in the tutorial before it started misbehaving.

```
brendon@localhost:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
blacklist bcm4306
blacklist bcm43xx

```

Let's see if this works on a restart.

---

### Post by taustin12 on 2007-07-08
Got ya beat - mine's about 4 years old I think, with 512MB ram.  


Anyways, here's how I got my BCM4306 device to see the wireless networks:
 - changed the wireless radio setting in BIOS to ON.  It had been set to PRIOR.
 - did a fresh resinstall of ubuntu.  I've tried so many different things I decided I needed to start over.
 - Donlwoaded file <bcm43xx-firmware_1.3-1ubuntu2_all.deb> and installed the package.
 - Rebooted, now my wireless card can at least SEE the wlan networks available.  This was not happening before.  I'm still unable to connect, but at least I'm making progress.  

Onward......

---

### Post by brennydoogles on 2007-07-08
> **taustin12 said:**
> Got ya beat - mine's about 4 years old I think, with 512MB ram.  


Anyways, here's how I got my BCM4306 device to see the wireless networks:
 - changed the wireless radio setting in BIOS to ON.  It had been set to PRIOR.
 - did a fresh resinstall of ubuntu.  I've tried so many different things I decided I needed to start over.
 - Donlwoaded file <bcm43xx-firmware_1.3-1ubuntu2_all.deb> and installed the package.
 - Rebooted, now my wireless card can at least SEE the wlan networks available.  This was not happening before.  I'm still unable to connect, but at least I'm making progress.  

Onward......

I didn't see the wireless radio setting in my BIOS, do I need to flash it??

---

### Post by taustin12 on 2007-07-09
> **brennydoogles said:**
> I didn't see the wireless radio setting in my BIOS, do I need to flash it??

Hmmm....maybe.  Strange, considering my laptop is considerably older than yours.  I've never tried flashing to an older BIOS version, not sure if you're comfortable with that or not.  Let's hope it won't render your laptop fubar.

FYI, the setting is on the Advanced page, called Wireless Power Setting. 

My BIOS version: Phoenix 000c 1913

---

### Post by brennydoogles on 2007-07-09
> **taustin12 said:**
> Hmmm....maybe.  Strange, considering my laptop is considerably older than yours.  I've never tried flashing to an older BIOS version, not sure if you're comfortable with that or not.  Let's hope it won't render your laptop fubar.

FYI, the setting is on the Advanced page, called Wireless Power Setting. 

My BIOS version: Phoenix 000c 1913

Ok, I have enabled the wireless Power setting on my BIOS, but after my reboot I noticed that my wireless card is not being recognized (as far as I can tell). I will post the outputs from all of the commands I have been told to do in the past, and see if we can make any progress.

ifconfig -a ```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:03:25:23:24:E4  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe23:24e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1482692 (1.4 MiB)  TX bytes:169865 (165.8 KiB)
          Interrupt:21 Base address:0xd800 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

iwconfig ```
brendon@localhost:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.


```

lspci ```
brendon@localhost:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```

cat /etc/modprobe.d/blacklist: ```
 cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
blacklist bcm4306
blacklist bcm43xx

```

lshw -class network: ```
 lshw -class network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:25:23:24:e4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.2.3 latency=64 maxlatency=11 mingnt=52 multicast=yes
       resources: ioport:d800-d8ff iomemory:dfffc000-dfffcfff irq:21
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@00:0b.0
       version: 03
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
       resources: iomemory:dfffa000-dfffbfff irq:17

```

Thanks for the help!!

---

### Post by AJB2K3 on 2007-07-09
I dont know if this will be of use but after installing **NETWORK SELECTOR** my wireless is working but i need to start it before connecting.
How can i get it to auto start eg on startup.

---

### Post by taustin12 on 2007-07-09
> **brennydoogles said:**
> Ok, I have enabled the wireless Power setting on my BIOS, but after my reboot I noticed that my wireless card is not being recognized (as far as I can tell). I will post the outputs from all of the commands I have been told to do in the past, and see if we can make any progress.

Thanks for the help!!

I should point out that I am a Ubuntu noob......but it occurs to me that a fresh reinstall may be beneficial to you (see my previous post).  I know after I tried 4 or 5 things, it became unclear as to exactly what I had changed, and where I was starting from.

The one difference I see is that Ubuntu always recognized my wlan device from the start - it just would not see any available networks.  In your case it appears that Ubuntu is not seeing your device.  Perhaps with all the meddling something got changed to prevent this?

btw I still have had no luck actually connecting to my wlan in feisty, but it does see all the networks that are "available."

[soapbox]
Maybe I'll quit my job and devote all my time to this.  Or, eventually get a new laptop WITHOUT a Broadcom wlan adapter.  bcm43xx for Feisty is buggy indeed.

I really like Feisty, but the wireless issues are getting aggravating.
[/soapbox]

---

### Post by brennydoogles on 2007-07-14
> **taustin12 said:**
> I should point out that I am a Ubuntu noob......but it occurs to me that a fresh reinstall may be beneficial to you (see my previous post).  I know after I tried 4 or 5 things, it became unclear as to exactly what I had changed, and where I was starting from.

The one difference I see is that Ubuntu always recognized my wlan device from the start - it just would not see any available networks.  In your case it appears that Ubuntu is not seeing your device.  Perhaps with all the meddling something got changed to prevent this?

btw I still have had no luck actually connecting to my wlan in feisty, but it does see all the networks that are "available."

[soapbox]
Maybe I'll quit my job and devote all my time to this.  Or, eventually get a new laptop WITHOUT a Broadcom wlan adapter.  bcm43xx for Feisty is buggy indeed.

I really like Feisty, but the wireless issues are getting aggravating.
[/soapbox]

ok, time to try something new. I wasn't happy with the performance of the laptop with ubuntu, so i decided to switch to Xubuntu (wonderful BTW). What would I need to change in these instructions to get them working in Xubuntu?

---

### Post by ugm6hr on 2007-07-14
> **brennydoogles said:**
> ok, time to try something new. I wasn't happy with the performance of the laptop with ubuntu, so i decided to switch to Xubuntu (wonderful BTW). What would I need to change in these instructions to get them working in Xubuntu?

What instructions?
If the card doesn't appear in *lspci*, Xubuntu won't be able to do anything either.

---

