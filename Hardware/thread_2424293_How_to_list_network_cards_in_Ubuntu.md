---
title: "How to list network cards in Ubuntu"
date: 2019-08-06
forum: Hardware
---

### Post by engrpeterjohn on 2019-08-06
Hi, 

I am looking for command to run in Ubuntu which shows the network adapter cards connected in the computer.

---

### Post by sevendogs1337 on 2019-08-06
From a terminal, run ```
ip link show
```. That should get you what you need.

---

### Post by TheFu on 2019-08-06
Also, **sudo lshw -C network**
This will show devices that don't have drivers.

And there are lspci commands and lsusb commands.  It depends on which bus a NIC is connected.

---

### Post by backspin on 2019-08-06
I've always used ifconfig

---

### Post by Skaperen on 2019-08-06
ifconfig lists interfaces, not cards.  but maybe that is what OP wants.  maybe "inxi -F" will be helpful.

---

### Post by #&amp;thj^% on 2019-08-06
One more to add:
```
sudo lshw -class network -short
H/W path                   Device      Class          Description
=================================================================
/0/100/19                  enp0s25     network        82579LM Gigabit Network Connection (Lewisville)
/0/100/1c.1/0              wlp3s0      network        Centrino Advanced-N 6205 [Taylor Peak]


```

---

### Post by deadflowr on 2019-08-06
> **Skaperen said:**
> ifconfig lists interfaces, not cards.  but maybe that is what OP wants.  maybe "inxi -F" will be helpful.

Switch it out with -N 
```
inxi -N
```

---

### Post by TheFu on 2019-08-06
inxi -N (or any inxi) doesn't show all network devices, unfortunately.

---

### Post by engrpeterjohn on 2019-08-07
Hi,

I get the following in terminal. How do I know which card is D-Link DGE-530T Gigabit PCI Adapter ? How to change IP address ? 

```

user---:~$ sudo lshw -class network -short
H/W path         Device      Class          Description
=======================================================
/0/100/19        eno1        network        82579LM Gigabit Network Connection
/0/100/1e/2      enp4s2      network        Gigabit Ethernet Adapter

```

It shows both network cards. The  buildin mother board network card and also additional D-Link card. But  when I connect the network cable to the D-Link card, the Ubuntu does not  logged in. Any idea how to fix it ?

---

### Post by backspin on 2019-08-09
One of the easiest ways is to use the Gui, and go to "settings" and then "Network".  Find the Network interface card you want to configure, and click the configure "cog".  The rest is pretty straight forward in those configurations.

---

### Post by TheFu on 2019-08-09
a)  [B]sudo lshw -class network -short
[/B]doesn't show the device driver, but it does list the devices. May or may not be important.  I would assume that because you are having issues that the driver is very important.

b) how to setup any network device is different based on the release, the GUI, the DE.  
Desktop [https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)
Server [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)
Just be certain that you are reading for the correct release and correct GUI.

If those methods don't work, we'll need more information to help.  It looks like an Intel GigE adapter.  If you use the correct device, eno1, then any of the normal network tools for the release should work. Over the last few years, which tools are primary have changed.  We used to use a ifupdown *interfaces* config file.  Since 17.10, netplan config files are used.

---

### Post by him610 on 2019-08-10
If TheFu says that all network devices are not always shown using *inxi -N* , it is probably true; however, I have never experienced any issues displaying any/all of my network devices (and drivers.)

```

hugh@G4560:~$ sudo lshw -class network -short && inxi -N
H/W path                 Device      Class          Description
===============================================================
/0/100/1c.5/0            enp3s0      network        I211 Gigabit Network Connection
/0/100/1c.6/0            wlp4s0      network        Wireless 3160
/0/100/1f.6              enp0s31f6   network        Ethernet Connection (2) I219-V
Network:   Card-1: Intel Ethernet Connection (2) I219-V driver: e1000e
           Card-2: Intel I211 Gigabit Network Connection driver: igb
           Card-3: Intel Wireless 3160 driver: iwlwifi


```

---

### Post by TheFu on 2019-08-10
```
$ sudo lshw -class network -short && inxi -N
H/W path       Device           Class          Description
==========================================================
/0/100/1c.5/0  wlp2s0           network        Wireless 8265 / 8275
/1             enx000ec6c76418  network        Ethernet interface
/2             veth7K5FY0       network        Ethernet interface
/3             virbr0-nic       network        Ethernet interface
Network:   Card: Intel Wireless 8265 / 8275 driver: iwlwifi
```

inxi output is missing 2 interfaces and 1 NIC.  I'd call that proof.

The veth and vir ... devices are virtual, so don't really matter. Missing the enx000ec6c76418 device **is** a huge problem.  BTW, I'm actively using that device right now and seldom use the wlp2s0 device.

---

