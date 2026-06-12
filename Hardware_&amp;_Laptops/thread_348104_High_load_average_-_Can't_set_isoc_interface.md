---
title: "High load average - Can't set isoc interface"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by A*p on 2007-01-28
My laptop (HPcompaq nx7010) has had a very high load average for a while now (between 2 and 7, usual is about 5), Sadly I cannot pinpoint when it started, but i would estimate it been within the last few weeks.  It sometimes gets so bad that the laptop is unusable.  I 'think' that this is either something to do with bluetooth or wireless on my laptop as when I press the wifi button to the off position the errors stop (i think that the button enables/disables both wifi and bluetooth).  As wireless on the laptop works fine and I have never used bluetooth so am not sure as to if that is working o.k. hence why i am thinking that bluetooth may be the source of the problem.  I did read somewhere that the bluetooth device was connected via usb internally to the laptop. 

When I try and open the device manager with the wifi button in the on position the System load will go to average off at 12-14  Hdd access will be constant all my memory will be eaten up and the and the device manager window will display, but no contents will be shown (window outline all grey inside)  this will just go on until I force a quit.  If I goto another terminal (Ctrl + Alt F1 etc) where I would login just populates with an error output:  

**[COLOR="Indigo"][17184716.340000] hci_usb_probe: Can't set isoc interface settings[/COLOR]**

*(different numbers in brackets on each line though)*


Top shows the haldaemon in the 1st spot and my logs show continuous errors:

**From daemon.log**

[COLOR="Indigo"]Jan 28 11:17:54 nx7010 NetworkManager: <debug info>^I[1169983074.481624] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_49f_86_noserial'). 
Jan 28 11:17:55 nx7010 hcid[4766]: HCI dev 0 registered
Jan 28 11:17:55 nx7010 hcid[4766]: Register path:/org/bluez/hci0 fallback:0
Jan 28 11:17:55 nx7010 NetworkManager: <debug info>^I[1169983074.822347] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_49f_86_noserial_if1'). 
Jan 28 11:17:55 nx7010 NetworkManager: <debug info>^I[1169983074.836607] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jan 28 11:17:55 nx7010 hcid[4766]: HCI dev 0 unregistered
Jan 28 11:17:55 nx7010 hcid[4766]: Unregister path:/org/bluez/hci0
Jan 28 11:17:55 nx7010 hcid[4766]: Device hci0 has been removed
Jan 28 11:17:55 nx7010 hcid[14599]: Can't init device hci0: No such device (19)
Jan 28 11:17:55 nx7010 NetworkManager: <debug info>^I[1169983074.977900] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 
Jan 28 11:17:55 nx7010 NetworkManager: <debug info>^I[1169983075.047819] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jan 28 11:17:55 nx7010 NetworkManager: <debug info>^I[1169983075.250323] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_49f_86_noserial_if1'). 
Jan 28 11:17:55 nx7010 NetworkManager: <debug info>^I[1169983075.256349] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 
Jan 28 11:17:55 nx7010 NetworkManager: <debug info>^I[1169983075.256485] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_49f_86_noserial'). 
Jan 28 11:17:55 nx7010 NetworkManager: <debug info>^I[1169983075.730187] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_49f_86_noserial'). [/COLOR]


*And it just repeats...*

**From messages**

[COLOR="Indigo"]Jan 28 14:07:09 nx7010 kernel: [17186710.236000] usb 3-2: new full speed USB device using uhci_hcd and address 104
Jan 28 14:07:10 nx7010 kernel: [17186710.500000] usb 3-2: configuration #1 chosen from 1 choice
Jan 28 14:07:10 nx7010 kernel: [17186710.752000] usb 3-2: USB disconnect, address 104
[/COLOR]
*Ant it just repeats... (note that the 104 represents the 104th time it has tried will repeat with 105 etc)*  

**Output from lsusb**

[COLOR="Indigo"]ollie@nx7010:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000[/COLOR]

any suggestion or help are much appreciated.

---

### Post by A*p on 2007-05-13
As far as I can tell this is a hardware issue, and it is the bluetooth device in my laptop that is the cause for this.

---

