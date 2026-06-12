---
title: "how can i change the address of the local bluetooth device?"
date: 2008-09-20
forum: Hardware
---

### Post by paranoid_humanoid on 2008-09-20
hi

i have two desktop computers at home, and i recently purchased two usb bluetooth dongles of the same brand for them. after installation, i discovered that the two devices have the same address. and other devices get confused when between the two computers, so i can't use them both at once.

one pc is running windows and the other is running ubuntu. so i guess that the device address is stored on the chip like the MAC address with the LAN devices.

i know that it's possible to change a MAC address, is it possible to change the bluetooth address of the device on ubuntu?

thanks

---

### Post by IntuitiveNipple on 2008-09-20
What is the make and model of the dongle, and the USB device ID?
```

lsusb

```
Also what is the Bluetooth Device address being reported?
```

hciconfig -a

```
Depending on the maker of the device it may be possible to use the **bdaddr** tool from the test/ directory of the [bluez source package](http://www.kernel.org/pub/linux/bluetooth/bluez-4.6.tar.gz) to change the BD address.
> 
**bdaddr**

prints the chip manufacturer's name, and the current BD_ADDR. If the IEEE OUI index file "oui.txt" is installed on the system, the BD_ADDR owner will be displayed. If the optional [new bdaddr] argument is given, the device will be reprogrammed with that address. This can either be permanent or temporary, as specified by the -t flag. In both cases, the device must be reset before the new address will become active. This can be done with a 'soft' reset by specifying the -r flag, or a 'hard' reset by removing and replugging the device. A 'hard' reset will cause the address to revert to the current non-volatile value.

uses manufacturer specific commands to set the address, and is therefore device specific. For this reason, not all devices are supported, and not all options are supported on all devices.

Current supported manufacturers are: **Ericsson, Cambridge Silicon Radio (CSR), Texas Instruments (TI), Zeevo and ST Microelectronics (ST)**


---

### Post by paranoid_humanoid on 2008-09-20
> Bus 004 Device 002: ID 1131:1004 Integrated System Solution Corp.

> hci0:	Type: USB
	BD Address: 00:11:67:00:00:00 ACL MTU: 1021:4 SCO MTU: 48:10
	UP RUNNING PSCAN ISCAN 
	RX bytes:1203 acl:0 sco:0 events:25 errors:0
	TX bytes:596 acl:0 sco:0 commands:25 errors:0
	Features: 0xff 0xfe 0xff 0x7e 0x98 0x19 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'nimbus'
	Class: 0x180100
	Service Classes: Capturing, Object Transfer
	Device Class: Computer, Uncategorized
	HCI Ver: 2.0 (0x3) HCI Rev: 0x2da LMP Ver: 2.0 (0x3) LMP Subver: 0x2da
	Manufacturer: Integrated System Solution Corp. (57)


so i guess the make is Integrated System Solution Corp. it's a cheap chinese dongle. how can i install a compiled bdaddr to try it out?

---

### Post by IntuitiveNipple on 2008-09-20
> **paranoid_humanoid said:**
> so i guess the make is Integrated System Solution Corp. it's a cheap chinese dongle. how can i install a compiled bdaddr to try it out?
According to [this article from 2006](http://forum.openwrt.org/viewtopic.php?id=6943) the ISSC devices may be supported by bdaddr. although possibly some patching may be required.

You could try installing and building the bluez source package from the link I gave earlier. There should be instructions on building it in the package or else they might be found via a Google search.

---

### Post by paranoid_humanoid on 2008-09-20
okay, here's a stupid question since that i'm not an avid linux user yet :D
i compiled the bluez package and installed it by following the instructions, but can't find the bdaddr bin file to run it. how can i find it?

---

### Post by IntuitiveNipple on 2008-09-20
Hmmm... I'm guessing the bdaddr tools isn't installed by default, maybe not even built. Did you look in the test/ directory after building to see if a bdaddr executable has been created?

I'll take a look-see - maybe there's a Makefile target for it.

---

### Post by IntuitiveNipple on 2008-09-20
checking the help for configure shows a --enable-test option:
```

./configure --enable-test

make

 ls -l test/bdaddr
-rwxr-xr-x 1 tj tj 5136 2008-09-21 03:29 test/bdaddr

```
You can now run it from there:
```

sudo test/bdaddr

```
You'll need to know the options. Here's a way to install the man-page without anything else:
```

MANPAGE=bdaddr.8
gzip -c test/${MANPAGE} | sudo tee /usr/share/man/man${MANPAGE##*.}/${MANPAGE}.gz >/dev/null

man bdaddr

```

---

### Post by paranoid_humanoid on 2008-09-20
i looked and there was no executable files in the test directory after building. any luck with the makefile?

---

### Post by paranoid_humanoid on 2008-09-20
okay, i did everything and changed the address and it tells me to reset the device. i unplugg it and plug it back in and it's still the same address :s

> amr@nimbus:~/Desktop/bluez-4.6/test$ ./bdaddr
Manufacturer:   Integrated System Solution Corp. (57)
Device address: 00:11:67:00:00:00
amr@nimbus:~/Desktop/bluez-4.6/test$ sudo ./bdaddr 00:12:67:00:00:00
Manufacturer:   Integrated System Solution Corp. (57)
Device address: 00:11:67:00:00:00
New BD address: 00:12:67:00:00:00

Address changed - Reset device now
amr@nimbus:~/Desktop/bluez-4.6/test$ ./bdaddr
Manufacturer:   Integrated System Solution Corp. (57)
Device address: 00:11:67:00:00:00


---

### Post by IntuitiveNipple on 2008-09-20
By "reset" does it mean using the bdaddr -r option do you think?

---

### Post by paranoid_humanoid on 2008-09-20
okay, i used the -r flag for a soft reset instead of a hard one and it worked :D

looks like i'll be adding a script to do that automatically on every session start. i couldn't thank you enough right now :)

---

### Post by IntuitiveNipple on 2008-09-20
I'd suggest adding it to the bluetooth system start-up script, /etc/init.d/bluetooth - but as an include so any package updates don't wipe it out.

Create a new script - /etc/bluetooth/bdaddr for example - and source that from /etc/init.d/bluetooth:
```

--- /etc/init.d/bluetooth	2008-07-24 20:55:37.000000000 +0100
+++ /etc/init.d/bluetooth	2008-09-21 03:59:53.000000000 +0100
@@ -56,6 +56,12 @@
 
 . /lib/lsb/init-functions
 
+# set device address
+BDADDR=/etc/bluetooth/bdaddr
+if [ -f $BDADDR ]; then
+  . $BDADDR
+fi
+
 # test for essential daemons
 test -x $HCID || exit 0
 test -x $HCIATTACH || exit 0

```

---

### Post by paranoid_humanoid on 2008-09-21
i don't know why, but after changing the bdaddr, bluetooth became seriously unstable. everytime i try to bond it with my mobile phone the whole computer freezes, and i have to reset manually.

maybe it's that the new bluez test is not stable yet..

thanks for your help anyway..

---

### Post by IntuitiveNipple on 2008-09-21
> **paranoid_humanoid said:**
> 
maybe it's that the new bluez test is not stable yet..

Ahh... is the inference of that statement that you *installed* the new binaries? I never meant for you to do that - simply build them so the bdaddr executable was available.

There is an **uninstall** target so use it, then re-install the Ubuntu package.
Save your custom bluetooth bdaddr script, the bdaddr binary, and the altered /etc/init.d/bluetooth script somewhere safe first, then:
```

# get the currently installed Bluetooth packages (so they can be reinstalled)
PACKAGES="$(dpkg-query -W -f='${Package;-15} ${Version;25} ${Status}\n' 'blue*' | grep 'ok installed' | awk '{printf $1 " " }')"
echo "Bluetooth packages: $PACKAGES"

cd bluez-4.6
sudo make uninstall

sudo apt-get --purge $PACKAGES

# re-install removed packages
sudo apt-get install $PACKAGES

```
Now put your customised scripts and bdaddr back in place, and see if that improves matters.

---

