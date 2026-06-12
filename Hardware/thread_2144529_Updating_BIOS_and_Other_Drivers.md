---
title: "Updating BIOS and Other Drivers"
date: 2013-05-12
forum: Hardware
---

### Post by NIMDog on 2013-05-12
Hi all!

I am in need of a BIOS update. However, I can't find any versions of my bios for Ubuntu! I have a Dell Optiplex 745 Mini Tower, running Ubuntu 13.04. The current bios version is 2.3.1. The latest version is 2.6.6. I tried to install the driver from Wine and it said that it was not allowed to flash the bios, so it couldn't continue. Any ideas?

---

### Post by SuperFreak on 2013-05-12
You don't flash BIOS from within the OS or at least not usually. Typically you have a copy of the new BIOS on a USB stick in your computer and you flash from within BIOS. However you do this at your own risk; if there is a power failure or something goes wrong you may bork your system.

---

### Post by grahammechanical on 2013-05-12
Motherboard makers do not support Linux users the way they support Windows users. The motherboard maker should have provided a utility for flashing the BIOS. My motherboard came with a CD of drivers and utilities. Windows based, of course. But it does include a DOS based utility that will run from floppy disk. I have never used it. But look to the motherboard maker for a means to flash the BIOS and take care. It should be possible to backup the present version so that you can re-install it.

I have found this for you

[http://www.dell.com/support/drivers/uk/en/ukbsdt1/DriverDetails/Product/optiplex-745?driverId=GRJ7T&osCode=WW1&fileId=2847999872&languageCode=en&categoryId=BI](http://www.dell.com/support/drivers/uk/en/ukbsdt1/DriverDetails/Product/optiplex-745?driverId=GRJ7T&osCode=WW1&fileId=2847999872&languageCode=en&categoryId=BI)

It says this

> [COLOR=#000000][FONT=Trebuchet MS]This file format consists of a BIOS executable file. To use it, download the file and copy it to a DOS-bootable diskette. With the diskette in the floppy drive, reboot the system and run the program.[/FONT][/COLOR]

Regards.

---

### Post by Bashing-om on 2013-05-12
NIMDog;
Best advise; If It ain't broke, don't fix it !

Possible with updating BIOS to introduce additional problems.
[INDENT=2]
regards

[/INDENT]

---

### Post by ajgreeny on 2013-05-12
But if you must update, and you can not find any other way to do it, have a look at   [FreeDos]("http://www.freedos.org/") which apparently can run the BIOS updates on many machines.

It could be that it will not work for you, but it must be worth a try, though only if you really need to update the BIOS at all; as Bashing-om says, "If it ain't broke, don't fix it!"

---

### Post by ahallubuntu on 2013-05-12
~

---

### Post by SuperFreak on 2013-05-12
I realize it is possible with some motherboards to update from Windows but I have always updated directly from the BIOS and I was led to understand that was the safest means. I have used Asus and Asrock motherboards on my custom machines. Updating BIOS is sometimes necessary for hardware changes such as new CPUs but even the manufacturers do not recommend updating a perfectly working system

---

### Post by mörgæs on 2013-05-12
On most Dells it's an easy job to upgrade BIOS. I have done many times. Just create a bootable USB stick with Freedos using Unetbootin and copy the exe file to the stick. 

Of course you should first spend some time searching for reports on the particular version you are planning to install. If noone has posted bad experiences I would consider the risk minimal.

---

### Post by Mark Phelps on 2013-05-12
IF you don't have a way to (1) save off the current WORKING BIOS version and (2) restore that if the BIOS upgrade goes badly -- then doing a BIOS update is a bad idea and asking for trouble.

---

### Post by Yellow Pasque on 2013-05-12
The changelog lists the following changes. Which of those do you need so bad that it's worth a BIOS update?
```
System: OptiPlex 745 Version: 2.6.6 Release Date: 08/24/2011 
* Add digital sign

2.4.1
* Correct Quadpack LED code when no memory is installed
* Optimize PCI Memory allocation

2.3.1
```

---

### Post by NIMDog on 2013-05-13
Ok, I was able to find a drive that had Windows 7 installed on it and update via that. Way easier!

---

