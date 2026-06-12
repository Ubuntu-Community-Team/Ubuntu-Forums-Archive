---
title: "Intel I225-V 2.5Gb Ethernet driver"
date: 2020-06-19
forum: Hardware
---

### Post by yaminb on 2020-06-19
HI,

I recently upgraded my mother board: ROG STRIX B550-F GAMING
This is has the: Intel® I225-V 2.5Gb Ethernet 

I can't seem to get it to connect to my lan cable. It keeps saying it is unplugged.
Now, I do have a windows drive, and with the same setup, the lan connection works fine.

That tells me there's something wrong with my ubuntu 20.04 configuration or a driver that is needed.
It looks to me like the interface is there and ready. Something is just wrong.


 ifconfig
enp5s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether d4:5d:64:d5:6e:a4  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xfc200000-fc2fffff  




Any ideas?


I'm currently running with the boards WIFI module, which worked straight away. So that's it's not blocking me right now.
Weird world when wifi works, but standard lan does not :)

---

### Post by yaminb on 2020-06-19
umm this was weird, but now that I think about it, it makes sense.

After booting to windows and then back to linux, the lan began to work.

I believe it is because I needed to load the firmware for the networking interface as per:
[https://askubuntu.com/questions/1244745/ubuntu-20-04-intel-network-connectivity-issue-bug-in-igc](https://askubuntu.com/questions/1244745/ubuntu-20-04-intel-network-connectivity-issue-bug-in-igc)

I was just about to do that, when I noticed the lan was now working.
Most likely when I booted into windows, it loaded the firmware and now works fine in ubuntu

---

### Post by yaminb on 2020-06-19
Had to remark post as unsolved.

After some reboots, I lost the ethernet again for ubuntu, but works fine in windows.
So I'm trying the way here: [https://askubuntu.com/questions/1244...sue-bug-in-igc]("https://askubuntu.com/questions/1244745/ubuntu-20-04-intel-network-connectivity-issue-bug-in-igc")

But in my download of the lan driver 
[https://www.asus.com/ca-en/Motherboards/ROG-STRIX-B550-F-GAMING/HelpDesk_Download/](https://www.asus.com/ca-en/Motherboards/ROG-STRIX-B550-F-GAMING/HelpDesk_Download/)
[https://dlcdnets.asus.com/pub/ASUS/mb/SocketAM4/ROG_STRIX_B550-F_GAMING/Intel_I225_LAN_Driver_V1.0.1.4_WIN10_64-bit.zip?_ga=2.176041826.1986677863.1592579308-962706779.1591732659](https://dlcdnets.asus.com/pub/ASUS/mb/SocketAM4/ROG_STRIX_B550-F_GAMING/Intel_I225_LAN_Driver_V1.0.1.4_WIN10_64-bit.zip?_ga=2.176041826.1986677863.1592579308-962706779.1591732659)


There is no corresponding Bin file that I can see as per the the askubuntu link. Nothing like FXVL_15F3_ASUS.bin that I can then use with nvmupdate64e.

---

### Post by Kris_M on 2020-06-19
it's the chip. I had one once. had to get a plugin card with a different chip for internet. windows worked fine but Ubuntu kept dropping connection on me.

---

### Post by yaminb on 2020-06-20
cool. I just ordered an usb-ethernet adapter. Should get me by.

Sucks it's not supported though.

---

### Post by Kris_M on 2020-06-20
No. assuming you have a box, get a cheap card.
[https://www.microcenter.com/product/408947/tp-link-gigabit-pci-express-network-adapter](https://www.microcenter.com/product/408947/tp-link-gigabit-pci-express-network-adapter)
or some such.

---

### Post by yaminb on 2020-06-24
I ended up getting this 
[https://plugable.com/products/usb3-e1000](https://plugable.com/products/usb3-e1000)

works great, straight out of the box with ubuntu.

---

