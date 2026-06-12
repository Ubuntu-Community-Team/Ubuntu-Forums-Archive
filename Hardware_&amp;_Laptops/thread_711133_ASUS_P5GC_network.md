---
title: "ASUS P5GC network"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by luria on 2008-02-29
Hi.  If you have the Asus P5GC motherboard (not the p5gc-xx) with 6 pci slots and no onboard video chances are that Ubuntu 7.10 will fail to recognice your onboard network properly

to check:
lspci  (look for r8168 or r8169)
ethtool -i eth0

if you, like me, find that lspci lists r8168 but ethtool list r8169 and you have no working network connection do:

1 - Download the newest r8168-xxxx driver from : [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168/RTL8111C](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168/RTL8111C)
2 - Unpack on the Desktop
3 - $ sudo mv r8168-xxxx /usr/src
4 - $ cd /usr/src/r8168-xxx
5 - $ sudo make clean modules
6 - $ sudo make install
7 - $ sudo depmod -a
8 - $ sudo insmod ./src/r8168.ko
9 - $ lsmod -a | grep 8168 #just to check it is there
10 - $ cd /etc/modprobe.d
11 - $ sudo touch blacklist-network
12 - $ nano blacklist-network # add 'blacklist r8169' without the quotes
13 - $ sudo update-initramfs -u #to make the change permanent
14 - reboot
15 - ethtool -i eth0 #to see new driver assigned

Most of this stolen from [http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-81118168-issue-615047/#post3029998](http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-81118168-issue-615047/#post3029998)
regards,
Lasse

---

### Post by banewman on 2008-02-29
Should maybe call this a howto???

---

### Post by cudjoe on 2008-03-10
Any chance to get it working with Hardy ?

---

### Post by jarlethorsen on 2008-04-16
> **luria said:**
> Hi.  If you have the Asus P5GC motherboard (not the p5gc-xx) with 6 pci slots and no onboard video chances are that Ubuntu 7.10 will fail to recognice your onboard network properly

to check:
lspci  (look for r8168 or r1869)


The last line here should obviously be "lspci  (look for r8168 or r8169)"
                                                                                                     ^^^^^^
> 
12 - $ nano blacklist-network # add 'blacklist r1869' without the quotes

Another typo, should be 'blacklist r8169'

---

### Post by natureca on 2008-04-22
Would this work for a DFI Lanparty UT NF3 250gb? Same problem different flavour :(

---

