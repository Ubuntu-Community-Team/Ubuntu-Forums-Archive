---
title: "bluetooth mouse 2"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by mcframe on 2006-02-05
Hi, 
i recently bought a "Trust" Bluetoth mouse for my HP bluetooth Notebook and am trying to get it to work properly. Following this [http://www.ubuntuforums.org/showthread.php?t=87919&highlight=bluetooth+mouse]("http://www.ubuntuforums.org/showthread.php?t=87919&highlight=bluetooth+mouse") and other online references I "manually" get the mouse to work with ```
sudo /usr/bin/hidd --connect 00:0A:94:C1:3C:2B 
```. But strangely on every new connection an insert pin request pop ups where only "0000" is accepted - although the mouse does not requests a pin when connected under windows or knoppix. I suppose this as the reason why a ```
sudo /usr/bin/hidd --connect 00:0A:94:C1:3C:2B --server
``` command does not lead to a automatic reconnection when the mouse restarts from standby mode. 
I have no idea why a pin is requested!! 

Second issue I found out is that even with this bluez-utils init script ```
PATH=/sbin:/bin:/usr/sbin:/usr/bin
DESC="Bluetooth services"

HCID=/usr/sbin/hcid
HCIATTACH=/usr/sbin/hciattach
HCID_NAME=hcid

HID2HCI=/usr/sbin/hid2hci

UART_CONF=/etc/bluetooth/uart

RFCOMM=/usr/bin/rfcomm
RFCOMM_NAME=rfcomm
RFCOMM_CONF=/etc/bluetooth/rfcomm.conf

SDPD=/usr/sbin/sdpd
SDPD_NAME=sdpd

DUND_DAEMON=/usr/bin/dund
DUND_NAME=dund
PAND_DAEMON=/usr/bin/pand
PAND_NAME=pand
HIDD_DAEMON=/usr/bin/hidd
HIDD_NAME=hidd

DUND_ENABLED=1
PAND_ENABLED=0
HIDD_ENABLED=1
DUND_OPTIONS="--listen --persist --msdun call dun"
PAND_OPTIONS=""
#HIDD_OPTIONS="--server"
HIDD_OPTIONS="-i 00:0A:94:C1:3C:2B --server" 
 ...snipped... 
``` 
no dund and hidd processes are running if bluez-utils is started or restarted. Any clues on this?? 

THX an advance

---

### Post by mcframe on 2006-02-07
Hi all, unfortunately there was no answer to my questions. So I had no altenative than to find it out myself: 

The unusual request for a pin was caused by the *auth enable* setting in /etc/bluetooth/hcid.conf. As soon as it has been commented out the mouse has been accessible without any pin request. 

The not starting of HIDD (and as it turned out DUND) has been caused by choosing the wrong file for the configuration. Primarily I have set HIDD_ENABLE, HIDD_OPTIONS and DUND_ENABLE in /etc/init.d/bluez-utils. The right file for theese settings turned out to be /etc/default/blue-utils. Hope it helps anyone!

---

