---
title: "format sandisk cruzer 4.0gb password protected"
date: 2009-01-12
forum: Hardware
---

### Post by slothbotkiller on 2009-01-12
Okay heres the deal folks I dug out an old USB stick of mine that was hidden in a drawer of mine and cannot remember the password (AT ALL). Now that was still back in the days when I used windows as a main operating system (I was using XP). about two years ago. My question is: is there any way at all to format the stick so I can use it again (I consider myself still to be a beginner user of UBUNTU). Right now I am using UBUNTU 8.10 Intrepid Ibex 8.10, if needed I will post more information about this issue. I want to create a USB startup disk.

Oh the only information I have retrieved so far was the following:

brian@brian:~$ lsusb
Bus 003 Device 008: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 003 Device 003: ID 090c:c371 Feiya Technology Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
brian@brian:~$ 


Thanks to all those who will hopefully be helpful on this epic project!
- Brian -

---

### Post by blazemore on 2009-01-12
It's very straightforward, luckily!
Run the following command in a terminal:
```
sudo apt-get install gparted -y && sudo gparted
```

Making sure the drive is plugged in, select it from the drop down menu on the right (I accept no responsibility for you selecting the wrong one).
A list of partitions is in the main areas, you can delete them and create new, or you can just format the ones which are there.

The filesystem to use is FAT32, as this can easily be accessed by almost all versions of Linux and Windows.

Hope this helps :)

---

### Post by slothbotkiller on 2009-01-12
> **blazemore said:**
> It's very straightforward, luckily!
Run the following command in a terminal:
```
sudo apt-get install gparted -y && sudo gparted
```

Making sure the drive is plugged in, select it from the drop down menu on the right (I accept no responsibility for you selecting the wrong one).
A list of partitions is in the main areas, you can delete them and create new, or you can just format the ones which are there.

The filesystem to use is FAT32, as this can easily be accessed by almost all versions of Linux and Windows.

Hope this helps :)
okay strangely enough my cruzer doesn't show up in gparted is there anything to force it to show up on gparted?

I must go to school now so i cannot give you much more information. I do have Windows as well on this box but I cannot remember what app I used to encrypt the USB stick. 

-Brian-

---

