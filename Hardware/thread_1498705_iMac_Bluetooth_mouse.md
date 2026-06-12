---
title: "iMac: Bluetooth mouse"
date: 2010-06-01
forum: Hardware
---

### Post by jorgecachoh on 2010-06-01
Hi all,

I have an iMac and I have installed an Ubuntu (dual boot). All has gone fine but I have problems trying to use Bluetooth mouse.

I have been searching on Google and trying some solutions but I'm not able to fix it. I think it not a mouse related issue but that bluetooth is not started.

Please find below some command's outputs just in case this helps:

I have installed "blueman" but when I execute it I get this error
"bluez daemon is not running"


Executing "hcitool scan" I get: "Device is not available: No such device"


and executing "sudo bluetoothd -nd" I get:

bluetoothd[2031]: Bluetooth daemon 4.60
bluetoothd[2031]: Enabling debug information
bluetoothd[2031]: parsing main.conf
bluetoothd[2031]: discovto=0
bluetoothd[2031]: pairto=0
bluetoothd[2031]: pageto=8192
bluetoothd[2031]: name=%h-%d
bluetoothd[2031]: class=0x000100
bluetoothd[2031]: discov_interval=0
bluetoothd[2031]: Key file does not have key 'DeviceID'
bluetoothd[2031]: Starting SDP server
bluetoothd[2031]: Loading builtin plugins
bluetoothd[2031]: Loading audio plugin
bluetoothd[2031]: Loading input plugin
bluetoothd[2031]: Loading serial plugin
bluetoothd[2031]: Loading network plugin
bluetoothd[2031]: Loading service plugin
bluetoothd[2031]: Loading hciops plugin
bluetoothd[2031]: Loading storage plugin
bluetoothd[2031]: Loading plugins /usr/lib/bluetooth/plugins
bluetoothd[2031]: Loading netlink plugin
bluetoothd[2031]: register_interface: path /org/bluez/2031/any
bluetoothd[2031]: Registered interface org.bluez.Service on path /org/bluez/2031/any
bluetoothd[2031]: Starting experimental netlink support
bluetoothd[2031]: Failed to find Bluetooth netlink family
bluetoothd[2031]: Failed to init netlink plugin
bluetoothd[2031]: /etc/bluetooth/network.conf: Key file does not have key 'Disable'
bluetoothd[2031]: /etc/bluetooth/network.conf: Key file does not have key 'DisableSecurity'
bluetoothd[2031]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[2031]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[2031]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[2031]: Config options: InterfacePrefix=bnep%d, PANU_Script=(null), GN_Script=(null), NAP_Script=(null), GN_Interface=pan0, NAP_Interface=pan1, Security=true
bluetoothd[2031]: bridge pan0 created
bluetoothd[2031]: input.conf: Key file does not have key 'IdleTimeout'
bluetoothd[2031]: Unix socket created: 9
bluetoothd[2031]: audio.conf: Key file does not have key 'AutoConnect'
bluetoothd[2031]: Telephony plugin initialized
bluetoothd[2031]: HFP AG features: "Ability to reject a call" "Enhanced call status" "Extended Error Result Codes" 
bluetoothd[2031]: Entering main loop
bluetoothd[2031]: RFKILL event idx 0 type 1 op 0 soft 0 hard 0

(and here it gets hanged .....)


I'd very gratefull if someone could help me

Thanks!

Jorge

---

### Post by khelben1979 on 2010-06-01
[Bluetooth Setup - Ubuntu documentation]("https://help.ubuntu.com/community/BluetoothSetup")

Have you read it and followed it's instructions?

---

### Post by jorgecachoh on 2010-06-01
Yes, I have tried it.

1.- I have run "sudo apt-get install bluez && sudo apt-get install bluez-utils" without erros.

2.- I have run "sudo /etc/init.d/bluetooth restart" without errors

Here I see wrong things because if I type  "sudo /etc/init.d/bluetooth status" I always get "bluetooth is not running"

I also can see bluetooth icon but I everything is disabled on it (I can only click on "Exit" and on "About".

Anyway, I am running Kubuntu, not Ubuntu, does it make any difference on Bluetooth?

THANKS!

               Jorge

---

### Post by jorgecachoh on 2010-06-02
Now it works. It was not a mouse-related issue, but Ubuntu didn't recognized iMac integrated bluetooth adapter.

I have added an USB-Bluetooth adapter and now everything is ok.

---

### Post by khelben1979 on 2010-06-02
Okay, nice to see you got it resolved!

---

