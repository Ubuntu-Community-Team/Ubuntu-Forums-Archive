---
title: "Help uninstalling a driver"
date: 2008-04-27
forum: Hardware
---

### Post by GepettoBR on 2008-04-27
I have a D-Link USB wireless receiver that, up until Gutsy, wasn't supported out of the box. I managed to make it work perfectly with [this tutorial](http://blog.ox.cx/2006/11/16/dwl-g122-rev-c1-and-ubuntu/) under Gutsy. After upgrading to Hardy, it still worked under the 2.6.22-14-generic kernel, but not under the new 2.6.24-16-generic kernel. I tried repeating the process under the new kernel but it still did not work. Using a Hardy LiveCD on another computer, I found out that my receiver works OOTB (with Network Manager, even). So I want to undo everything I did and make it work under the new kernel.

Since I'm not sure what exactly all those commands did, I'm unsure as to how I should undo all this (unload and uninstall the kernel modules and undo the changes to my configuration files). The driver is listed in  the Hardware Manager (ex-restricted drivers manager), by the way.

Finally, in case Google fishes this thread up, **RT73 USB WIRELESS CARDS WORK OUT OF THE BOX WITH UBUNTU 8.04 HARDY HERON**

---

### Post by ljonesj on 2008-04-27
what is the specific name of the D-link usb wireless u have

---

### Post by GepettoBR on 2008-04-27
It's a DWL-G122, revision C1, firmware version 3.00

---

### Post by GepettoBR on 2008-04-27
**ALMOST SOLVED** (see next post). I decided to take the risk of breaking something and it turns out the most obvious solution is the right one (Occam's Razor strikes once more).

Here's what I did:
(1) Remove the /etc/Wireless/RT73STA folder (backing it up to ~/BACKUP_WLAN_DRIVER just in case)
```
mkdir ~/BACKUP_WLAN_DRIVER
sudo mv /etc/Wireless/RT73STA ~/BACKUP_WLAN_DRIVER/RT73STA
```
(2) Remove rt73usb from the blacklist
```
gksudo gedit /etc/modprobe.d/blacklist

#Comment out the line that reads "blacklist rt73usb"
```
At this point, Network Manager was once again trying to connect to the internet, but unsuccessfully since the correct drivers weren't loaded. Before doing that, however, we need to remove the faulty module to avoid conflict:

(3) Removed the custom driver from the system folder by copying it into the backup folder
```
 mkdir /home/paulo/BACKUP_WLAN_DRIVER/Kernel_Module
sudo mv /lib/modules/2.6.24-16-generic/kernel/drivers/usb/net/rt73.ko ~/BACKUP_WLAN_DRIVER/Kernel_Module/rt73.ko
```
(4) Now it's time to load the correct default driver by executing ```
sudo modprobe rt73usb
```
(5)We need to make the driver autoload on every boot, otherwise we'll have to modprobe rt73usb whenever we want to go online.
```
sudo echo "rt73usb" >> /etc/modules
```
(6) Activate the Wireless Connection in Network Manager, choose an Access Point, and we're done.

How much better than Windows is this: No restarting the computer at all.

---

### Post by GepettoBR on 2008-04-27
Actually, problems arose after restarting, as now the keyring manager asks for my password after every login for nm-applet to connect me to the wireless network. Anyone know a workaround for this?

---

### Post by Kiefer Rodriguez on 2008-04-27
> **GepettoBR said:**
> I have a D-Link USB wireless receiver that, up until Gutsy, wasn't supported out of the box. I managed to make it work perfectly with [this tutorial]("http://blog.ox.cx/2006/11/16/dwl-g122-rev-c1-and-ubuntu/") under Gutsy. After upgrading to Hardy, it still worked under the 2.6.22-14-generic kernel, but not under the new 2.6.24-16-generic kernel. I tried repeating the process under the new kernel but it still did not work. Using a Hardy LiveCD on another computer, I found out that my receiver works OOTB (with Network Manager, even). So I want to undo everything I did and make it work under the new kernel.

Since I'm not sure what exactly all those commands did, I'm unsure as to how I should undo all this (unload and uninstall the kernel modules and undo the changes to my configuration files). The driver is listed in  the Hardware Manager (ex-restricted drivers manager), by the way.

Finally, in case Google fishes this thread up, **RT73 USB WIRELESS CARDS WORK OUT OF THE BOX WITH UBUNTU 8.04 HARDY HERON**

DWL-G122 Revision C1, Using RT73 [Ralink] Chipset;
-[Script to install and configure it automatically]("http://ubuntuforums.org/showthread.php?t=757607")
-[URL="http://ubuntuforums.org/showthread.php?p=4730903"]Guide that does the above

[/URL]
Hope that helps - Kindest regards,
[I]Kiefer
[COLOR=Red]
**[COLOR=Black]Edit:[/COLOR]** Whoops, I only just noticed you need to uninstall it, not install it - My apologies :\[/COLOR]
[/I]

---

