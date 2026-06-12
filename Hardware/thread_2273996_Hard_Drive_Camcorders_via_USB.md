---
title: "Hard Drive Camcorders via USB?"
date: 2015-04-17
forum: Hardware
---

### Post by BikerBro on 2015-04-17
Hello Folks,

I am New to Ubuntu and am really trying to get my hands dirty and learn the ins-and-out of it. I do work with unix at work, still somewhat of an novice/intermediate at it, but can get around. I am a bit stumped with a couple of things. I am not sure if I can, or how I can connect to my hard drive camcorder (canon vixia hf r52), and my action hard drive camcorder (Contour 2). They are both usb to mini usb. I also have my cel phone plugged in, which is charging, but is not being noticed.

Here is all I see:

me@machine:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 1b1c:0c04 Corsair 
Bus 004 Device 003: ID 046d:c030 Logitech, Inc. iFeel Mouse
Bus 004 Device 002: ID 04b3:3025 IBM Corp. NetVista Full Width Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
me@machine:~$

From what I can tell, the OS is only picking up on the keyboard, mouse, and speakers-power.

Am I effed on my efforts to connect to hard-drive video cameras? I am not finding much on the subject, and what I am seeing is pretty grim.

Knowledge or direction please?

---

### Post by coldraven on 2015-04-17
Plug the camera in and then look at the end of dmesg log. (Make the terminal window fullscreen to see the results more easily)
```
dmesg | tail -20
```

FYI some more use cases here: [http://www.tecmint.com/dmesg-commands/](http://www.tecmint.com/dmesg-commands/)

---

### Post by BikerBro on 2015-04-17
Thank you for your assist with this coldraven!

Here's what dmesg gave me:

```
samurai@BigBox:~$ dmesg | tail -20
[   40.323172] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   40.936603] audit_printk_skb: 168 callbacks suppressed
[   40.936606] audit: type=1400 audit(1429222931.146:68): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1307 comm="nm-dhcp-client." lport=44028 family="inet" sock_type="dgram" protocol=17
[   40.936614] audit: type=1400 audit(1429222931.146:69): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1307 comm="nm-dhcp-client." lport=38308 family="inet6" sock_type="dgram" protocol=17
[   40.952495] audit: type=1400 audit(1429222931.158:70): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1309 comm="nm-dhcp-client." lport=44028 family="inet" sock_type="dgram" protocol=17
[   40.952502] audit: type=1400 audit(1429222931.158:71): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1309 comm="nm-dhcp-client." lport=38308 family="inet6" sock_type="dgram" protocol=17
[   45.600898] [drm:btc_dpm_set_power_state] *ERROR* rv770_restrict_performance_levels_before_switch failed
[   45.710382] init: plymouth-upstart-bridge main process ended, respawning
[   45.715071] init: plymouth-upstart-bridge main process (1774) terminated with status 1
[   45.715080] init: plymouth-upstart-bridge main process ended, respawning
[   66.609339] audit: type=1400 audit(1429222954.282:72): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2720 comm="apparmor_parser"
[   66.609348] audit: type=1400 audit(1429222954.282:73): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2720 comm="apparmor_parser"
[   66.609660] audit: type=1400 audit(1429222954.282:74): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2720 comm="apparmor_parser"
[15868.925746] systemd-hostnamed[3210]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[22364.531403] systemd-udevd[4686]: starting version 204
[23134.708261] systemd-hostnamed[7435]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[23971.818359] systemd-hostnamed[9580]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[25806.698641] systemd-hostnamed[17415]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[35453.223657] audit: type=1400 audit(1429258369.072:75): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=18699 comm="nm-dhcp-client." lport=44028 family="inet" sock_type="dgram" protocol=17
[35453.223666] audit: type=1400 audit(1429258369.072:76): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=18699 comm="nm-dhcp-client." lport=38308 family="inet6" sock_type="dgram" protocol=17
samurai@BigBox:~$
```


I am seeing some sort of DHCP errors, which I am not too concerned with, since I am here on this site. As for the rest, I am a bit clueless. Any thoughts on what you see here?

BikerBro

---

### Post by Vladlenin5000 on 2015-04-17
For the Canon VIXIA-R5x wouldn't be easier just to use the built-in WiFi? -> [http://www.usa.canon.com/CUSA/assets/app/pdf/wireless/vixia/VIXIA-R50-Connecting-via-Wi-Fi.pdf](http://www.usa.canon.com/CUSA/assets/app/pdf/wireless/vixia/VIXIA-R50-Connecting-via-Wi-Fi.pdf) 
Also for CONTOUR +2 there are better solutions, even Bluetooth or just using a microSD adapter - [http://cdn.shopify.com/s/files/1/0303/8453/files/US_User_Manual_Contour_Plus2.pdf?2787](http://cdn.shopify.com/s/files/1/0303/8453/files/US_User_Manual_Contour_Plus2.pdf?2787) - as the USB connection may require proprietary drivers/software which is only available for Windows/Mac.
Regarding your cell phone, which one? An Android smartphone behaves differently depending on the Android version. Others vary a lot. So, which one, exactly? Make/model.

---

### Post by BikerBro on 2015-04-18
I wanted to check in here and thank you both, Coldraven, Vladlenin. I will have to return to issue in the future. 

With great power (in for form of sudo), comes great responsibility, and in this case bigger issues. Even though I am using the desktop version, I have 4x1TB hard drives in raid 5 (software raid) which ended up being ~3TB, as you both would have probably guessed. Anyhow, I kept getting a message that that there wasn't a valid partition for the array drive, and so I decided to use 'parted' on it. I am not real savvy on file systems, but I had previously created the array with ext4, and ended up using ext2 while running parted. Long story short, it ended up screwing up a few things, so I removed the partition. But one of those things was that the disks seem to be stuck in GPT which fdisk likes to flag, and which I am not sure if it is a good thing or a bad. Also, sudo wouldn't let me go to root, "The program 'root' is currently not installed.  You can install it by typing:". I downloaded some weird version of root, and then uninstalled it, which ended up fixing the normal root problem... Now, my biggest annoyance is that my machine, completely Ubuntu, keeps booting to grub... Errr...At this point I am frustrated with the learning curve, but Hate MS-Anything enough to stick it out and learn. Oh, plus I was digging up some dirt to pore concrete... 

Again, I wanted to check in and thank you two for feedback, and I will be returning to these issues very soon, I hope.

---

### Post by coldraven on 2015-04-23
> systemd-hostnamed[7435]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

This is not what I was expecting, are you using Ubuntu 15.04? If so I would recommend using the stable LTS version 14.04.

The reason for using dmesg was to see if the system had recognized the camera, you might have seen a message saying something like this:
```
[43396.532156] usb 1-3: new high-speed USB device number 15 using ehci-pci
[43396.666094] usb 1-3: New USB device found, idVendor=22b8, idProduct=2e83
[43396.666110] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[43396.666118] usb 1-3: Product: XT1032
[43396.666125] usb 1-3: Manufacturer: motorola
[43396.666131] usb 1-3: SerialNumber: 12345678


```

---

### Post by BikerBro on 2015-04-29
Hmmm... I am showing 14.04 LTS when I pull up 'about this computer'. I did just do a fresh install, so much different from Windows... Learning...

---

### Post by BikerBro on 2015-04-29
I am loving the change over, but this little issue is bumming me out. I know that I can use the wireless function, for the canon, but the contour is great to just be able to plug in. I am wondering if there is any sort of plug-and-play setting that may not be picking up the usb device. Any assistance would be great.

---

### Post by BikerBro on 2015-05-06
OK, I tried the wireless function on the canon, that didn't work. Any other ideas out there.

---

