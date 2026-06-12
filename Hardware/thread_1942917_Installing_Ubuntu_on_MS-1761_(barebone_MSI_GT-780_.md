---
title: "Installing Ubuntu on MS-1761 (barebone MSI GT-780 DX/DXR)"
date: 2012-03-18
forum: Hardware
---

### Post by akuhon on 2012-03-18
The version that really work the 1st time I install is Ubuntu 10.10 (Maverick Meerkat). I've tried 11.04 and 11.10 (All 64bit version) but they always stop at bootscreen (some errors about the USB -> MSI EPF USB). 

However, this not happened with old version. So I use, Ubuntu ver 10.10 (Maverick Meerkat) 64-bit. As for 32bit vers., I notice it can't detect my ram size correctly. Currently I'm running 16GB but it only detects around 4GB while on 64 bit, no problem (detect 15GB but that's just fine with me). 

Almost all device parts install successfully. 
Only 2 things don't work properly i.e. : **the graphics card** (Nvidia GTX 570M) and **the wifi** (Intel brand).

So, I'd like to share, how do I solve these 2 problems. 

**I. Graphics card** (Nvidia GTX 570M)
To activate the features of this, I download the driver from official Nvidia download page [[COLOR="Red"]here[/COLOR]]("http://www.nvidia.com/object/linux-display-amd64-295.20-driver.html"). 
This is the latest driver as of this day. (Mar 19, 2012). You can extract it.
Just follow all the instruction and if it says you have to stop Xserver to install, just do the following :

```
Press Ctrl-Alt-F2
Login with your account 
Type : sudo service gdm stop
Go to the directory where your downloaded nvidia driver has been extracted. 
Type : sudo sh ./<your-nvidia-driver-for-linux>
```

Follow the process. There'll be some error statement but you can neglect them, until you choose "Yes" for using nvidia-xconfig to configure your display.

After that, reboot, and during some splashscreen, Nvidia Logo will appear. That means, you have successfully install the Nvidia driver on the notebook.

Remember, **if you update the kernel, you have to repeat the installation proses** as this driver always build directly inside each kernel. Otherwise, it will go to command line (not in GUI)

**II. The Wifi**
I've found out that activating the key or press Fn+F8 doesn't wake up the WLAN.  

running command : lshw -C Network will show :
```
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 6c:62:6d:36:77:b4
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:d000(size=256) memory:ec104000-ec104fff memory:ec100000-ec103fff
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f6200000-f6201fff
  *-network
       description: Wireless interface
       physical id: 6
       bus info: usb@2:1.4
       logical name: wlan0
       serial: 74:ea:3a:89:fe:6d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ar9170usb driverversion=2.6.35-28-generic firmware=N/A ip=192.168.1.103 link=yes multicast=yes wireless=IEEE 802.11bgn
```

So all I do is to download this [[COLOR="red"]file[/COLOR]]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-03-17.tar.bz2").
Then do :
```
1. Go to the directory where you download the file
2. sudo apt-get install build-essential
3. tar -xjvf compat-wireless*
4. cd compat-wireless*
5. ./scripts/driver-select intel
6. make
7. sudo make unload 
8. sudo modprobe iwlwifi
```

Press the Wireless button (or Fn+F8 keys), then network manager will activate the wifi ...

That's all. Hope it helps.

Rgds,
Arthur

---

### Post by Basher101 on 2012-03-18
i got the full version of your video card, so here is what i did to make it work:

open up synaptics package manager and search for the 3 packages: nvidia-common, nvidia-settings, nvidia-current and then install them. Once done so, go to additional drivers and run it. After a reboot everything should work

regards

---

### Post by akuhon on 2012-03-18
I see, thanks for the nvidia explanation.
I did that (installing right away from nvidia) because when I click additional driver, it showed nothing... 
Usually there's driver for Nvidia. 

Maybe, it's because the Wifi problem during 1st installation. I couldn't connect, that's why no updates during installation. 

But everything detected during 1st installation ... touchpad, bluetooth, camera ... 
Only the eject button, I have to go to terminal and execute "eject" so the dvdrom will open ... 

I still have to find the key to bind this eject function.

---

