---
title: "[GRUB] How do I get hardware device for GRUB syntax in device.map"
date: 2014-01-30
forum: Hardware
---

### Post by david144 on 2014-01-30
Is there a way after the kernel has booted to get this information? 

(hd0) (fd0) etc.. etc.


grub-probe doesn't seem to tell me or I'm not using the right target type?
```

san@iSCSI-SAN:~$ grub-probe --target=device --device /dev/sdb
/dev/sdb
san@iSCSI-SAN:~$ grub-probe --target=device --device /dev/sdb1
/dev/sdb1
san@iSCSI-SAN:~$ grub-probe --target=drive --device /dev/sdb
(/dev/sdb)
san@iSCSI-SAN:~$ grub-probe --target=drive --device /dev/sdb1
custom logging function 0x7fb98e3a6250 registered
selinux=0
runtime dir '/run/udev'
calling: info
device 0x7fb98e3a62d0 has devpath '/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8:1.0/host6/target6:0:0/6:0:0:0/block/sdb/sdb1'
grub-probe: warn: disk does not exist, so falling back to partition device /dev/sdb1.
(/dev/sdb1)
san@iSCSI-SAN:~$

```

my system doesn't currently have a device.map, and I'd like to try making one but need to figure out what grub thinks my USB boot stick is?
(for additional info why I want this see: [http://ubuntuforums.org/showthread.php?t=2202219](http://ubuntuforums.org/showthread.php?t=2202219) unfortunately udev option just isn't working and I can't figure out why so I'm determined to try the device.map)

2nd question if I figure out the system hardware device name for this usb stick and make my device.map file do I need to reconfigure grub/remake it? sorry I'm a total novice at grub.

Thanks for your help :)

---

### Post by oldfred on 2014-01-30
Grub stopped using device maps many versions ago, but if you have one it may use it. Have not seen any comment on it recently.

What is issue?

BIOS checks for hardware and you boot. Or UEFI on newer systems.
But boot drive is always hd0 in grub, then the remain drives are hd1, hd2 etc.

But I find I skipped a port in my SATA drives. So if I plug in a flash drive it is sde, but if I reboot with it plugged in it is sdb and all my other drives are changed. 
But I normally boot from sdc and that always works, but it is hd0. And if refering to another drive to find something I often have to experiment as it may not always be the same.

---

### Post by Bashing-om on 2014-01-30
david144; Hi !

How about this:
You can determine what GRUB thinks your disk devices are by running:
```

sudo grub-mkdevicemap --device-map=device.map
cat device.map

```

The device.map file is located in /boot/grub/ It isn't required but can be used in Grub 2. The same command as Grub legacy: 
```

sudo grub-mkdevicemap

``` To generate the device.map file.

A while back I re-aranged my hard drives - due to a failing hard drive, and In order to get my grub booting properly I did (re-)map my drives with the grub-mkdevicemap command.

[INDENT][INDENT]sometimes, ya gotta do what ya gotta do
[/INDENT][/INDENT]

---

### Post by david144 on 2014-01-30
> **oldfred said:**
> 
What is issue?

In my other post: [http://ubuntuforums.org/showthread.php?t=2202219](http://ubuntuforums.org/showthread.php?t=2202219)

I'm trying to get my PNY 16GB Flash disk which is my boot disk to stay as a fixed /dev/sd*[COLOR=#FF0000]X[/COLOR]*

it can be /dev/sdz for all I care but I want to get all my drives into fixed positions so I know what is what based on their serial and PCI info, udev doesn't seem to be working to rearrange them (Tried all kinds of /etc/udev/rules.d/ files and even tried modifying the /lib/udev/rules.d files even though it's not recommended but can't get it back into hd0 which is where I'd prefer it be since it's my boot drive after all :)

> **Bashing-om said:**
> david144; Hi !
How about this:
You can determine what GRUB thinks your disk devices are by running:
```

sudo grub-mkdevicemap --device-map=device.map
cat device.map

```


Beautiful Thanks! :)

Turns out it is currently showing as (hd1) with only one other drive plugged in at the moment. I'll play around with it once I get home since I'm working over SSH at the moment.

---

### Post by Bashing-om on 2014-01-30
david144; Great !

Please bear in mind that linux systems now utilize UUIDs to identify devices .. While a device name (say sda) may change depending on when/where the system recognizes the device, UUIDs remain a constant.

[INDENT][INDENT]in the process of learning
[/INDENT][/INDENT]

---

### Post by david144 on 2014-01-31
> **Bashing-om said:**
> david144; Great !

Please bear in mind that linux systems now utilize UUIDs to identify devices .. While a device name (say sda) may change depending on when/where the system recognizes the device, UUIDs remain a constant.
[INDENT][INDENT]in the process of learning
[/INDENT]
[/INDENT]


Thanks again for your help :)

Stopping at the grub command line I can verify that the device.map put my USB stick before the SATA drive, but once the kernel boots it still goes back to sys to get the order so it's back to trying more udev rules with me ;)

---

### Post by Bashing-om on 2014-01-31
david144; Hey.

I wish you a good return on the effort. udev is where it all happens, but these waters can get real deep. You are now getting down to the guts and gore of the operating system.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

