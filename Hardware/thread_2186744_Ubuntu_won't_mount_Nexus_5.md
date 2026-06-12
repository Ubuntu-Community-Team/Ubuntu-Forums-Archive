---
title: "Ubuntu won't mount Nexus 5"
date: 2013-11-08
forum: Hardware
---

### Post by Batmensch on 2013-11-08
Ubuntu 13.04 won't mount my new Nexus 5 using MTP.  My previous Nexus 4 mounted fine.

The error is:
Unable to mount Nexus 5
Unable to open MTP device '[usb:001,010]'

dmesg output:

[ 1347.327293] usb 1-1.2: new high-speed USB device number 10 using ehci-pci
[ 1347.420878] usb 1-1.2: New USB device found, idVendor=18d1, idProduct=4ee1
[ 1347.420883] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1347.420886] usb 1-1.2: Product: Nexus 5
[ 1347.420888] usb 1-1.2: Manufacturer: LGE
[ 1347.420891] usb 1-1.2: SerialNumber: 02b2eefb2161137a

I'm running on an iMac.  The device mounts fine under MacOSX.

---

### Post by Batmensch on 2013-11-08
OK, looks like it's a problem with MATE; Cinnamon seems to be able to access the Nexus 5 without a problem.

---

### Post by dave77459 on 2013-11-09
> **Batmensch said:**
> Ubuntu 13.04 won't mount my new Nexus 5 using MTP.  My previous Nexus 4 mounted fine.

The error is:
Unable to mount Nexus 5
Unable to open MTP device '[usb:001,010]'

dmesg output:

[ 1347.327293] usb 1-1.2: new high-speed USB device number 10 using ehci-pci
[ 1347.420878] usb 1-1.2: New USB device found, idVendor=18d1, idProduct=4ee1
[ 1347.420883] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1347.420886] usb 1-1.2: Product: Nexus 5
[ 1347.420888] usb 1-1.2: Manufacturer: LGE
[ 1347.420891] usb 1-1.2: SerialNumber: 02b2eefb2161137a

I'm running on an iMac.  The device mounts fine under MacOSX.
I followed instructions from [here]("http://www.omgubuntu.co.uk/2013/06/mount-nexus-4-on-ubuntu"), and you gave me the clue to make it work. I needed the right idVendor.  This is what I did:

> 1. Enable Developer options and enable USB debugging.

2. Install necessary MTP modules to your computer:
   sudo apt-get install mtp-tools mtpfs

3. Configure 51-android.rules
   sudo gedit /etc/udev/rules.d/51-android.rules
 
   paste the following at the end of the file (if the file does not exist then just paste):
   #LG – Nexus 5
   SUBSYSTEM==”usb”, ATTR{idVendor}==”18d1", MODE=”0666"

4. Make the file executable:
   sudo chmod +x /etc/udev/rules.d/51-android.rules

5. Restart udev
   sudo service udev restart


I needed the idVendor, which you supplied.  I restarted my computer and plugged in the Nexus 5, and it worked.  It might have worked without the restart, but I realized when I shutdown that another user was logged in and maybe that caused a conflict.

Thanks for the vendor ID.  I hope this works for you.

---

### Post by RomanIvanov on 2013-12-29
It did not helped me, but I found in web completely automated approach to configure (by the same approach) and do automount - [http://roman-ivanov.blogspot.com/2013/12/mount-nexus5-to-ubuntu-1204.html](http://roman-ivanov.blogspot.com/2013/12/mount-nexus5-to-ubuntu-1204.html).

---

### Post by ali34 on 2014-10-18
My issue got fixed by switching from USB 3.0 to USB 2.0

---

