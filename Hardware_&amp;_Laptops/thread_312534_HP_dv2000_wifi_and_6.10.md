---
title: "HP dv2000 wifi and 6.10"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by Mefistofeles on 2006-12-04
Hey,

Bought myself a HP dv2003ea. Installed kubuntu 6.10. Now.. at first the wifi card showed up under network devices but i coulnt enable it. Clicking on enabeling enabled it for 2 seconds after what it turned off again.

got this from dmesg:

bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed. 

Googled abit and found:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

Everything seemed to have gone right.. But.. Wifi still not working. **It shows networks but I still cant connect!**

Starting wlassistan from console shows me these errors:

X Error: BadDevice, invalid or uninitializer input device l66
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device

And when trying to connect:

send_packet: Network is unreachable
send_packet: please consult README
CONNECTION FAILED
==>stderr: Thers is already a pid file /var/run/dhclient.pid with pid 5798864

Now.. wifi-radar from console.

X Error: BadDevice, invalid or uninitializer input device l66
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device

and DHCP connecting..

eth1 Interface doesn't support scanning : No such device

---

### Post by johnmxg12 on 2006-12-05
it doesnt look like your wireless driver has been installed.  

i'm guessing you have a broad com wireless card??

follow this thread, it helped me. go straight to process for dapper and edgyhttp://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper

---

