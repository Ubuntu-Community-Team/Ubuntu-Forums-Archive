---
title: "Bluetooth enabled and visible but not Working (HP Touchsmart TM2)"
date: 2011-05-08
forum: Hardware
---

### Post by vharishankar on 2011-05-08
On my HP Touchsmart TM2 2102tu laptop I have not been able to get Bluetooth to work properly. I am currently using Ubuntu 10.10.

The bluetooth adaptor is enabled and the icon shows the preferences dialog. However, scanning for devices is not showing any devices in spite of the fact that my Nokia x2-01 phone is nearby and has bluetooth enabled. Neither is the phone able to detect my laptop when scanning.

Here's hciconfig:
> hci0:	Type: BR/EDR  Bus: USB
	BD Address: 70:F3:95:74:7D:CE  ACL MTU: 310:10  SCO MTU: 64:8
	UP RUNNING PSCAN ISCAN 
	RX bytes:1579 acl:0 sco:0 events:79 errors:0
	TX bytes:1051 acl:0 sco:0 commands:70 errors:1


One more thing. The bluetooth/wireless LED is always blinking between red and blue state when enabled and red when disabled. But the wireless connects perfectly. In windows, the LED is white when enabled and red when disabled (no blinking).

If any other info is needed, please let me know.

---

### Post by Zingam on 2011-05-08
After you've logged in, try this in the console:

sudo service bluetooth restart




Then if you have Raink device like me: RT3090 WiFi card combined with a Ralink bluetooth and you have installed the RT3090 driver from here [https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090) and the wireless works but bluetooth still cannot find any devices, somebody has suggested to log into Windows. Press the Wifi button to switch wireless off and then reboot and log into Ubuntu... and it works for me like that too.

---

### Post by vharishankar on 2011-05-08
That doesn't work still.

I don't have the RT 3090 driver, but it uses the 2800 driver.

lsmod | grep rt 
```
parport_pc             36959  0 
rt2860sta             543010  0 
rt2800pci              18535  0 
rt2800lib              45181  1 rt2800pci
crc_ccitt              12667  2 rt2860sta,rt2800lib
rt2x00pci              14322  1 rt2800pci
rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178528  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
parport                46458  3 parport_pc,ppdev,lp

```

---

### Post by vharishankar on 2011-05-08
I'm sorry. Clarification in order. I'm using 11.04 Natty, not 10.10. I wsa a bit confused.

/proc/version
```
Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011

```

---

### Post by vharishankar on 2011-05-10
Still not working.

Have absolutely no idea why. The adapter is recognized. The scanning takes place, but no devices are found even if bluetooth is set to "visible" on the phone. And the other device is also not finding the computer.

By the way it works perfectly in Windows 7.

---

### Post by android272 on 2011-05-16
I am having the same trouble with my tablet. scans for devices but never finds any.

---

### Post by zztoninho on 2011-06-17
i have me same problem in my hp dv5 2115 br !! and i change from rt2800 !!!

any suggestions ??? it's the same bug in various distros ! like debian, ubuntu and mint !!!

---

