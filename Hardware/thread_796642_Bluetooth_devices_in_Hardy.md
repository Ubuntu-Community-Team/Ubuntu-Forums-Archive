---
title: "Bluetooth devices in Hardy"
date: 2008-05-16
forum: Hardware
---

### Post by gforster on 2008-05-16
Many of the guides in getting bluetooth to work with various devices are written for older versions, not for hardy and it seems that certain things have changed in Hardy.

My specific problem is with my apple bluetooth keyboard and mighty mouse. No, this is not the same problem as I and others have posted about in other places. When either the computer or the peripheral devices go to sleep (I'm not sure which, because when they sleep, I am away from the computer), I cannot wake the computer with those devices. Sometimes, the mouse works while the keyboard does not, but usually neither work. 

Thankfully, I am on a laptop and the normal laptop keyboard/touchpad work just fine.  Everything works correctly immediatly when I issue the folowing command int the terminal:```
sudo /etc/init.d/bluetooth restart

``` According to some things I read, if I edit the /etc/default/bluetooth file, and change HID2HCI_ENABLED=1  to this:
HID2HCI_ENABLED=0 that might possibly solve my problem.

However, I do not want to go messing with config files when I don't really understand them. I do not want to disable my laptop keyboard.  So, simply -  is this something I want to do?  Mind you, the keyboard is automatically detected when I start the computer and if I log out/in or restart bluetooth, which it seems many others have had problems with.

Let me know if I need to post other info like my xorg or whatever. Thanks for any help. One of these days, I hope to return the favor.

---

### Post by balagosa on 2008-05-16
I read forums that once you switch to HCI, it might be hard to switch it back to HID.

did you try typing ```
lsusb
```. what is the otucome of that?

---

### Post by gforster on 2008-05-17
My lsusb output is:

```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 0000:0000 
```

Is there somewhere I can learn about hci vs hid? Am I using hci since that is what the dongle mode is? Is there an advantage/disadvantage to either?

---

### Post by apehunter on 2008-05-18
First post EVER! 

I am trying to get my bluetooth device to be recognized on Hardy.

Bluetooth device: Insignia NS-BTHDP/NS-BTHDST
Compter: Dell INSPIRON 500m
OS: UBUNTU HARDY

I have tried to understand all the strings on this topic and will input the analysis of my bluetooth device, as I still have not solved this problem.

BEFORE inserting USB bluetooth device
$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

AFTER insterting USB bluetooth device
$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 007: ID 0a5c:4503 Broadcom Corp. 
Bus 002 Device 006: ID 0a5c:4502 Broadcom Corp. 
Bus 002 Device 005: ID 0a5c:4500 Broadcom Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

$ sudo hcitool scan
Device is not available: No such device
$ hcitool dev
Devices:


As you can see no devices have been found.

Questions: 
1) Could it be that insignia is not supported under linux?
2) Is there a known fix?

thanxs a million

---

