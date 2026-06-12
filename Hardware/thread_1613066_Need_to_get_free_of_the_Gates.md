---
title: "Need to get free of the Gates"
date: 2010-11-04
forum: Hardware
---

### Post by darkknight85 on 2010-11-04
Any helpfull ideas would be great!!! I am having trouble installing Kubuntu 10.04 on my recently purchased (From pawnshop) laptop. Here are my specs 
It is a Compaq CQ50-110US and has a Nvidia board i think. With 2 AMD Turion dual-core RM-70 processors. My video card is an Nvidia GeForce 8200M G and my wireless card is a Atheros 5007. Right now I am using Vista X64 Home Premium :( because I can not get my graphics or my wireless to work right. Agian any helpfull advice would be good. If you have sucessfully installed Kubuntu 10.04 on this laptop please for love of all that is not "Microsoft" will you help me to tear down these damn "Gates" and shatter these "Windows"....Yes i know i dissed Microsoft three times Oh well I got to have some kinda fun right
:P

---

### Post by P4man on 2010-11-04
To get helpful advice, you might want to start by explaining the problem in some more detail. Saying "it doesnt work right" irsnt likely to give you an accurate solution.

---

### Post by wojox on 2010-11-04
> I can not get my graphics or my wireless to work right

Did you install the drivers?

---

### Post by darkknight85 on 2011-01-01
I have installed the Nvidia drivers for my graphics card and now that works grate. My WiFi still is a no go. I have the madWiFi packeg but i cant figure out how to install it. I am not sure what is up with my wireless card right now. I am about to say screw and stay with "Winblows"

---

### Post by ChuckyDuckster on 2011-01-01
Don't give up!

If you already have the driver files, I would install ndisgtk. because you aren't connected to the internet yet, you will need to get a few packages from a computer that is connected and then dpkg them on the laptop

You will need:
ndiswrapper-common ([http://packages.ubuntu.com/hardy/ndiswrapper-common](http://packages.ubuntu.com/hardy/ndiswrapper-common))
ndiswrapper-utils ([http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9))
ndisgtk ([http://packages.ubuntu.com/hardy/ndisgtk](http://packages.ubuntu.com/hardy/ndisgtk))

then run
```
sudo dpkg -i (ndiswrapper-common).deb
sudo dpkg -i (ndiswrapper-utils).deb
sudo dpkg -i (ndisgtk).deb
```Substituting the parenthesis with the filenames of the packages.
After that, Windows Wireless Drivers will appear in the System section of your main menu, and you will be able to install the drivers you need.

---

### Post by darkknight85 on 2011-01-02
I tried ndiswrapper with out success. That is why i am looking at madwifi.

---

### Post by IcarusR on 2011-01-02
Did you try installing the compat-wireless drivers as per this page ?

[http://wireless.kernel.org/en/users/Download#Getting_compat-wireless_on_Ubuntu]("http://wireless.kernel.org/en/users/Download#Getting_compat-wireless_on_Ubuntu")

---

### Post by darkknight85 on 2011-01-21
If it helps i ran the following and got this....
 
@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: [EMAIL="pci@0000:00:0a.0"]pci@0000:00:0a.0[/EMAIL]
       logical name: eth0
       version: a2
       serial: 00:1d:72:64:9b:41
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:42 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: [EMAIL="pci@0000:07:00.0"]pci@0000:07:00.0[/EMAIL]
       logical name: wlan0
       version: 01
       serial: 00:1f:e2:87:cc:76
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff

---

