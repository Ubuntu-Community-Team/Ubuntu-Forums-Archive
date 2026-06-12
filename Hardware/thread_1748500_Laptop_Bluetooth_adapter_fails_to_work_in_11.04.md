---
title: "Laptop Bluetooth adapter fails to work in 11.04"
date: 2011-05-03
forum: Hardware
---

### Post by Lateralis on 2011-05-03
Hello all.  

I have Bluetooth problem on a Fujitsu laptop.  The internal hard drive of the laptop has had Ubuntu 9.04 -> 10.04 on it and with each version the inbuilt Bluetooth adapter has worked great.  However, the adapter refuses to work in 11.04.  I did, for one session, manage to get the Bluetooth working on Sunday.  For the life of me I can't work out what I did to make it work, but hoped it would work indefinitely.  No such luck; it has failed to work since I rebooted after that.  

My problem: Essentially, the Bluetooth adapter refuses to turn on and work.  The Bluetooth icon in the notification area is visible but greyed out.  Clicking on it, I see it says "Bluetooth: On" in dark grey, "Turn off Bluetooth" in white with Preferences underneath.  If I click on Preferences I get a box which essentially says nothing except: 

1) Bluetooth is disabled
2) Turn on Bluetooth in a big clickable button box. 

I have no clue how to actually "enable" the bluetooth adapter, or even why it is showing as disabled in 11.04 (when I've never had any such issues before).  

Here are the outputs of some commands which may be of use:

```

$ hciconfig -a
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:22:5F:00:6D:78  ACL MTU: 310:10  SCO MTU: 64:8
	DOWN 
	RX bytes:362 acl:0 sco:0 events:14 errors:0
	TX bytes:56 acl:0 sco:0 commands:14 errors:0
	Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
	Packet type: DM1 DH1 HV1 
	Link policy: 
	Link mode: SLAVE ACCEPT

```
```

$ sudo lsusb -v | grep Blue
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
  bDeviceProtocol         1 Bluetooth
  idProduct          0x0001 Bluetooth Dongle (HCI mode)
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth

```

```

$ dmesg | grep Blue
[   16.706558] Bluetooth: Core ver 2.15
[   16.707185] Bluetooth: HCI device and connection manager initialized
[   16.707188] Bluetooth: HCI socket layer initialized
[   16.873664] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   17.937748] Bluetooth: L2CAP ver 2.15
[   17.937751] Bluetooth: L2CAP socket layer initialized
[   17.945929] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.945932] Bluetooth: BNEP filters: protocol multicast
[   17.949795] Bluetooth: SCO (Voice Link) ver 0.6
[   17.949797] Bluetooth: SCO socket layer initialized

```
```

$ lsmod | grep blue
bluetooth              72448  8 sco,bnep,l2cap,btusb

```

I hope to get this working as Bluetooth on this laptop is pretty important to me.  So any help, advice or suggestions will be gratefully received!  

Thanks,
Lat

---

### Post by compuguy1088 on 2011-05-13
Having the same problems with a HP Mini 110-3000. Same usb/chipset as your bluetooth adapter. I have not gotten it to recognize any bluetooth devices.

I've posted a bug report mentioning these issues: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782359](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782359)

---

### Post by Lateralis on 2011-05-14
Thanks for your reply.  I did mean to post back in here a little while ago, but every time I have booted into 11.04 recently (which, admittedly, is only a handful of times) the Bluetooth has worked fine.  

I did find some people having success by doing the following:

```

sudo killall bluetoothd
sudo bluetoothd

```

When I went to try that though, my Bluetooth was already working!  

As for your link, it seems to point to this thread.  There is however a bug on [here]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/762964") on Launchpad.

---

### Post by compuguy1088 on 2011-05-24
> **Lateralis said:**
> Thanks for your reply.  I did mean to post back in here a little while ago, but every time I have booted into 11.04 recently (which, admittedly, is only a handful of times) the Bluetooth has worked fine.  

I did find some people having success by doing the following:

```

sudo killall bluetoothd
sudo bluetoothd

```

When I went to try that though, my Bluetooth was already working!  

As for your link, it seems to point to this thread.  There is however a bug on [here]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/762964") on Launchpad.

Tried that, no dice.....

---

### Post by Lateralis on 2011-05-25
> **compuguy1088 said:**
> Tried that, no dice.....

Yeah. This doesn't seem to work for everyone.  The launchpad bug does have a lot of comments from a lot of people who are quoting different things to try with variable success.  

For me, I did actually start to get this trouble again after I booted into 11.04 a few times.  For me, the commands I mentioned did the trick.

---

