---
title: "Fn-F5 turn wireless radio on/off doesn't work"
date: 2007-03-28
forum: Hardware &amp; Laptops
---

### Post by dr_d12 on 2007-03-28
Hi all,

I'm trying to get Fn-F5 to turn my wireless radio power on and off (for airplanes and battery life). The default setup in Feisty is for Fn-F5 to execute ibm-wireless.sh to toggle between bluetooth, wireless, or neither. My thinkpad X40 doesn't have bluetooth and I'd like to change ibm-wireless.sh to switch between wireless on and off. Right now, Fn-F5 doesn't do anything on my X40 except exit with status 0.

Here is the output from /var/log/acpid and the contents of ibm-wireless.sh and wireless.sh. Can you help me fix it? Maybe Fn-F5 event should execute wireless.sh instead of ibm-wireless.sh?

Thanks!!
Dave

```

$ tail /var/log/acpid
[Wed Mar 28 13:12:57 2007] client connected from 4662[0:0]
[Wed Mar 28 13:12:57 2007] 1 client rule loaded
[Wed Mar 28 13:20:59 2007] received event "ibm/hotkey HKEY 00000080 00001005"
[Wed Mar 28 13:20:59 2007] notifying client 4513[107:112]
[Wed Mar 28 13:20:59 2007] notifying client 4662[0:0]
[Wed Mar 28 13:20:59 2007] executing action "/etc/acpi/ibm-wireless.sh"
[Wed Mar 28 13:20:59 2007] BEGIN HANDLER MESSAGES
[Wed Mar 28 13:20:59 2007] END HANDLER MESSAGES
[Wed Mar 28 13:20:59 2007] action exited with status 0
[Wed Mar 28 13:20:59 2007] completed event "ibm/hotkey HKEY 00000080 00001005"

```


ibm_wireless.sh

```

#!/bin/sh
# Find and enable/disable wireless devices

BLUETOOTH=/proc/acpi/ibm/bluetooth

# Note that this alters the state of the wireless!
wireless_state=`. /etc/acpi/wireless.sh`

if [ -r $BLUETOOTH ]; then
    grep -q disabled $BLUETOOTH
    bluetooth_state=$?
fi

# Sequence is Both on, Bluetooth only, Wireless only, Both off
if [ "$wireless_state" = 0 ]; then
    # Wireless was turned off
    if [ -w /proc/acpi/ibm/bluetooth ]; then
        if [ "$bluetooth_state" = 0 ]; then
            echo enable > $BLUETOOTH;
        else
            echo disable > $BLUETOOTH
        fi
    fi
fi

```

wireless.sh:

```

#!/bin/sh
# Find and enable/disable wireless devices

ON=0
OFF=1  # 1 for rf_kill, 2 for power/state

for DEVICE in /sys/class/net/* ; do
    if [ -d $DEVICE/wireless ] ; then
	# $DEVICE is a wireless device. Check if it's powered on:
	for CONTROL in $DEVICE/device/rf_kill $DEVICE/device/power/state ; do
	    if [ -w $CONTROL ] ; then
		# We have a way of controlling the device, lets try
	        if [ `cat $CONTROL` = 0 ] ; then
		    # It's powered on. Switch it off.
		    if echo -n $OFF > $CONTROL ; then 
			echo 0
			break
		    else
			OFF=2 # for power/state, second time around
		    fi
		else
		    # It's powered off. Switch it on.
		    if echo -n $ON > $CONTROL ; then
			echo 1
			break
		    fi
		fi
	    fi
	done
    fi
done	

```

---

### Post by Hookheathen on 2007-05-30
Hello Dave,

I have the same IBM X40 Thinkpad and cannot turn on the wireless (it functions fine in XP) but will not work at all with Ubuntu. My Atheros chipset is AR 5212. Any suggestions? Help gratefully appreciated.
Thanks.

---

### Post by Kidchaos on 2007-10-01
<code>
wget [http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb](http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb)
sudo dpkg -i ./bcm43xx-firmware_1.3-1ubuntu2_all.deb
sudo rm ./bcm43xx-firmware_1.3-1ubuntu2_all.deb 
</code>

Worked for me with Deisty and on an Dell Inspiron 8k and Asus wl-100g (4306 b/g)

---

### Post by shimojimatto on 2008-01-31
having the same problem with the Atheros b/g chipset 5211 on my x40... but I'm not even sure that the wireless is on in the first place... I think its not working and I think by messing with ndiswrapper and madwifi I broke it even more...

does your wifi status light turn on when you boot up ubuntu Hookheathen and dr_d12? 

using 7.10 over here...

---

### Post by Pekkalainen on 2008-03-31
My X40 has the atheros chip and I have the same problem. The card works fine but I cannot modify it in any way. It is always turned on and it is my only issue with this laptop. If anyone can lend a hand it would be deeply appreciated :)

This solution worked to turn on the LED indicator first time I tried it but upon 2 reboots it does not work anymore: [http://madwifi.org/wiki/UserDocs/EnableLEDs](http://madwifi.org/wiki/UserDocs/EnableLEDs)

Thats as far as I have gotten. I am prepared to place a bounty of 100 SEK given to the one who shows me a solution that makes the LEDs light up and the card to be able to be turned on and off with the Fn-F5 keyboard combo! :)

---

### Post by ntrl on 2008-07-04
Hi All.

I am happy user of Thinkpad X40 with Atheros WiFi. And some problem. But i solve it.

[Here solve.]("http://forums.gentoo.org/viewtopic-t-432495-highlight-tpb.html?sid=433119cf860e0c013d34aa0d47d87614") But
in ubuntu not work. 

Here my patched scripts /etc/acpi/ibm-wireless2.sh 
```

#!/bin/bash
# Find and toggle wireless of bluetooth devices on ThinkPads

state=$( /sbin/iwconfig | awk '/ath*/ { print $1 }' )
#state=$( /sbin/ifconfig | grep  ath0 )
if [[ $state == "" ]] ;
then
        cmd="enable"
        /sbin/modprobe ath_pci
        /sbin/ifconfig ath0 up
else
        cmd="disable"
        /sbin/ifconfig ath0 down
        /sbin/rmmod ath_pci wlan ath_hal
fi

logger "[ACPI] $cmd wireless LAN adapter"

```

here /etc/acpi/events/ibm-wireless:
```

# /etc/acpi/events/ibmwireless
# This is called when the user presses the wireless button and calls
# /etc/acpi/wireless.sh for further processing.

event=ibm/hotkey HKEY 00000080 00001005
#action=/etc/acpi/wireless.sh
action=/etc/acpi/ibm-wireless2.sh



```

---

