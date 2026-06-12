---
title: "Open source ATI driver for Radeon 3650"
date: 2016-02-28
forum: Hardware
---

### Post by daxtinator15 on 2016-02-28
Hello everyone! My dad gave me an HP Elitebook 8530p for free from his office and I'm trying to get the open source drivers for my GPU to work. I tried to play Old School RuneScape on it and it was lagging up a storm. The drivers aren't showing up in the additional drivers and when I run ubuntu-drivers list, the open source driver isn't there. I tried a few different things yesterday and I also reinstalled Ubuntu several times. I know the proprietary drivers don't support my GPU anymore and I've made sure fglrx is purged. I just want to be able to run RuneScape and Counter-Strike Source. Any help would be appreciated thanks. 

Also, the bios is locked from a former employee from his company. Trying to get a hold of him for the password so I can't mess with the bios.

---

### Post by Bashing-om on 2016-02-28
daxtinator15' Hello;

You are correct in that there is no proprietary graphic's driver available for the AMD HD3650 chip set. ATI bought out AMD some time back, and has dropped support for these legacy cards. 

However, the kernel should have picked up and loaded the 'radeon' (open source) graphic's driver.

Post back - between code tags - the outputs of terminal commands:
```

sudo lshw -C display
lsmod | grep radeon

``` 
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
to start the process of finding out what is not going on.

[INDENT][INDENT]it shudda, it wudda
[INDENT][INDENT][INDENT]it can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daxtinator15 on 2016-02-28
```
brian@hpgnome:~$ sudo lshw -C display
[sudo] password for brian: 
  *-display               
       description: VGA compatible controller
       product: RV635/M86 [Mobility Radeon HD 3650]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:30 memory:c0000000-cfffffff ioport:7000(size=256) memory:d8300000-d830ffff memory:d8320000-d833ffff
```

```
brian@hpgnome:~$ lsmod | grep radeon
radeon               1519616  5
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
drm_kms_helper        126976  1 radeon
drm                   356352  8 ttm,drm_kms_helper,radeon
```

---

### Post by Bashing-om on 2016-02-28
daxtinator15; Welll ..

What ya got is the open source driver, and it is loaded . All components are functional.

Just not going to get any better is my opinion.

Now if ya just got to get better, there remains a short time solution .. - install release 12.04.1 .. that release has the xserver and kernel that the ATI proprietary driver supports. Bad thing is that 12.04 goes end of life in April of next year and will no longer be supported .

else: upgrade the hardware.

[INDENT][INDENT]it is not so much that the bear talks so well
[INDENT][INDENT][INDENT]what is amazing is that the bear talks at all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daxtinator15 on 2016-02-29
I was afraid that'd be the case. Bummer. Thanks though! Also, it's possible to do a NVIDIA 9600m swap. Do you know if there are proprietary drivers for that?

---

### Post by Bashing-om on 2016-02-29
daxtinator15; Uh Huh ...

GeForce 9600M GT ??
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

Then yeah ! ...
You are looking at the Linux 340.* legacy driver series. It is the last to support the G8x, G9x, and GT2xx GPUs, and motherboard chipsets based on them. Support for new Linux kernels and X servers, as well as fixes for critical bugs, will be included in 340.* legacy releases through the end of 2019.

So that card has some time yet before it too ceases . Just do not expect high performance from this card either. Bear in mind, if old cards could do what the new card do, there would be no new cards.

[INDENT][INDENT]we can do that too
[/INDENT][/INDENT]

---

### Post by daxtinator15 on 2016-02-29
Ya I know the 9600 isn't killer, just as long as I can RuneScape in bed or on my couch is fine. Thanks!

---

### Post by Bashing-om on 2016-02-29
daxtinator15; Hey ...

Yeah .. no substitute for trying it and see what happens .

[INDENT][INDENT]fingers crossed
[/INDENT][/INDENT]

---

### Post by daxtinator15 on 2016-03-01
Hey thanks for all the help!

---

### Post by mastablasta on 2016-03-02
even with opensource driver the 3650 is well supported. so at best there would be a slight performance drop and maybe a bit worse power management than in windows. something else seems to be wrong. if you were messing with proprietary driver it is quite possible that you resolved the issue badly. just recently when I was testing the 15.10 I couldn't get the hardware acceleration to run. not sure why it didn't work then suddenly on reboot I loaded as it should and it was all really fast and responsive. so make sure you are not using software acceleration, but that the hardware acceleration is activated (see testing the driver: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) )

another thing - do you have desktop effects disabled when running the game? are these native games you are trying to run or are you using some sort of emulation?

furthermore, there are a couple of PPA's that hold beta version of opensource drivers (xorg edgers for example). while AMD keeps moving drivers into opensource (out of support) they at least have the descency to help developers that are developing them. so opensource drivers continue to improve with each version also with the help from AMD. still 3650 should be well supported.

---

