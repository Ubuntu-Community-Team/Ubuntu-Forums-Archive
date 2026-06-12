---
title: "where is the pcf8574 kernel module?"
date: 2009-06-07
forum: Hardware
---

### Post by stairwayoflight on 2009-06-07
Hi,

I am trying to use the pcf8574 chip. The kernel from (feisty I believe) has the module, but when I try "modprobe pcf8574" on jaunty it says there is no such module.

I am building a kernel today (for something else) but for kicks I thought I'd see if I could build support for the chip. I'm following the directions [here]("http://ubuntuforums.org/showthread.php?t=56835").

So I installed linux-source, started with the old config, and did a make menuconfig. When I poked inside drivers->i2c->chips (I can't remember the exact location, but some i2c chips were there) there was no option to build a module for the pcf8574 that I could see. Also there were so few options, there was no way to "scroll down" to find it, etc.

I suppose it is really not on my system (I had a stock kernel at this point):
```

me@home:~$ ls /lib/modules/2.6.28-11-generic/kernel/drivers/i2c/chips
at24.ko  ds1682.ko  eeprom.ko  max6875.ko  pcf8591.ko  tps65010.ko  tsl2550.ko
```

Also, while my new kernel was compiling, I did a
```
find / -iname "pcf8574*"
``` and got ```
/usr/src/linux-source-2.6.28/drivers/i2c/chips/pcf8574.c
```so I know its at least in the kernel source tree. Pardon me if I have missed the obvious, but what do I do to build this module for my kernel?

Regards,
Timothy

---

### Post by tonuonu on 2009-11-18
I have same question for next, 9.10 Ubuntu and no answer after extensive Googling yet.

---

### Post by tonuonu on 2009-11-18
Found something. Those modules are moved to GPIO and named pcf857x. So I did 

[FONT=Courier New] sudo modprobe pcf857x[/FONT]

PCF8574 were not autodetected in my case. Looked further and found:

[http://www.mjmwired.net/kernel/Documentation/i2c/instantiating-devices](http://www.mjmwired.net/kernel/Documentation/i2c/instantiating-devices) 

In my case PCF8574-s are 0x38 and 0x39 on bus 0:

[FONT=Courier New]root@Unknown-00-10-dc-61-9e-47:~# i2cdetect 0
WARNING! This program can confuse your I2C bus, cause data loss and worse!
I will probe file /dev/i2c-0.
I will probe address range 0x03-0x77.
Continue? [Y/n] 
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: 20 -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- 38 39 -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- UU -- -- -- -- -- -- -- 
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
70: -- -- -- -- -- -- -- --                         
root@Unknown-00-10-dc-61-9e-47:~# 

[FONT=Arial] Actually this is Velleman K8000 board.[/FONT]

root@Unknown-00-10-dc-61-9e-47:~# echo pcf8574 0x38 > /sys/class/i2c-adapter/i2c-0/new_device 
root@Unknown-00-10-dc-61-9e-47:~# echo pcf8574 0x39 > /sys/class/i2c-adapter/i2c-0/new_device 
root@Unknown-00-10-dc-61-9e-47:~# 

[FONT=Arial] They did appear:[/FONT]

root@Unknown-00-10-dc-61-9e-47:~# ls -la /sys/bus/i2c/devices/0-0038/
total 0
drwxr-xr-x 3 root root    0 2009-11-18 21:40 .
drwxr-xr-x 7 root root    0 2009-11-18 21:40 ..
-r--r--r-- 1 root root 4096 2009-11-18 21:40 modalias
-r--r--r-- 1 root root 4096 2009-11-18 21:40 name
drwxr-xr-x 2 root root    0 2009-11-18 21:40 power
lrwxrwxrwx 1 root root    0 2009-11-18 21:40 subsystem -> ../../../../../../bus/i2c
-rw-r--r-- 1 root root 4096 2009-11-18 21:40 uevent
root@Unknown-00-10-dc-61-9e-47:~# [/FONT]    

unsure what to do next. Still no input-output controls. I see error in dmesg:

[FONT=Courier New][33420.468728] i2c-adapter i2c-0: The new_device interface is still experimental and may change in a near future
[33420.468910] pcf857x: probe of 0-0038 failed with error -22
[33420.468919] i2c-adapter i2c-0: new_device: Instantiated device pcf8574 at 0x38
[33439.724806] i2c-adapter i2c-0: The new_device interface is still experimental and may change in a near future
[33439.724996] pcf857x: probe of 0-0039 failed with error -22
[33439.725006] i2c-adapter i2c-0: new_device: Instantiated device pcf8574 at 0x39[/FONT]

error 22 is 

[FONT=Courier New] #define EINVAL          22      /* Invalid argument */

[FONT=Arial] Error seems to come from dd.c:[/FONT]

root@Unknown-00-10-dc-61-9e-47:~/linux-2.6.31/drivers# grep "probe of" */*
ata/sata_mv.c: *      mv_platform_probe - handle a positive probe of an soc Marvell
ata/sata_mv.c: *      mv_pci_init_one - handle a positive probe of a PCI Marvell host
**_base/dd.c:               "%s: probe of %s failed with error %d\n",_**
ieee1394/nodemgr.c:        HPSB_DEBUG("Speed probe of node " NODE_BUS_FMT " yields %s",
scsi/ultrastor.c:/* ??? A probe of address 0x310 screws up NE2000 cards */
root@Unknown-00-10-dc-61-9e-47:~/linux-2.6.31/drivers# 

[/FONT]

---

