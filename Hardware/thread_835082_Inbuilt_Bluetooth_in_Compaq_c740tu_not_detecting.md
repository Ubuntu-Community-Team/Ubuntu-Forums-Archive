---
title: "Inbuilt Bluetooth in Compaq c740tu not detecting"
date: 2008-06-20
forum: Hardware
---

### Post by sarada on 2008-06-20
I have a problem with bluetooth not working on my Compaq c740tu laptop. I've installed all the relevant packages (bluez-* and bluetooth, etc) but I still get the same basic problem: my inbuilt bluetooth adapter doesn't seem to show up. Could I have it disabled somewhere? Here is the output of some basic commands:

$ sudo /etc/init.d/bluetooth restart
* Restarting bluetooth [ OK ]

$ sudo hciconfig
< no output >

$ sudo hciconfig hci0 up
Can't get device info: No such device

$ sudo hciconfig hci0 restart
Can't get device info: No such device

$ lsmod | grep blue
bluetooth 61156 4 rfcomm,l2cap

$ sudo hcitool scan
Device is not available: No such device

$ sudo hcitool dev
Devices:

I have made the wireless switch on (it controls both Bluetooth and wifi, and I'm connecting through LAN).

If any suggestion plz reply or mail me at [email]sarada.sahoo@gmail.com[/email]

thanks!

---

### Post by ukripper on 2008-06-20
> **sarada said:**
> I have a problem with bluetooth not working on my Compaq c740tu laptop. I've installed all the relevant packages (bluez-* and bluetooth, etc) but I still get the same basic problem: my inbuilt bluetooth adapter doesn't seem to show up. Could I have it disabled somewhere? Here is the output of some basic commands:

$ sudo /etc/init.d/bluetooth restart
* Restarting bluetooth [ OK ]

$ sudo hciconfig
< no output >

$ sudo hciconfig hci0 up
Can't get device info: No such device

$ sudo hciconfig hci0 restart
Can't get device info: No such device

$ lsmod | grep blue
bluetooth 61156 4 rfcomm,l2cap

$ sudo hcitool scan
Device is not available: No such device

$ sudo hcitool dev
Devices:

I have made the wireless switch on (it controls both Bluetooth and wifi, and I'm connecting through LAN).

If any suggestion plz reply or mail me at [email]sarada.sahoo@gmail.com[/email]

thanks!

Found a bug reported in regards to your device on launchpad -
[https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/206549](https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/206549)

---

