---
title: "Nvidia GeForce 9300M GS"
date: 2008-06-26
forum: Hardware
---

### Post by cozadaman on 2008-06-26
Im thinking of buying a laptop that has a "Nvidia GeForce 9300M GS" graphics device. I've been on the nvidia website, but i couldnt see drivers with this EXACT chip. Is there other drivers that will support this graphics card?

Cheers in advance.

---

### Post by cozadaman on 2008-11-21
Just incase anyone wants to follow up this post, the 9300M G Graphics card is supported by ubuntu and the drivers will be automatically installed via the restricted drivers. :)

---

### Post by Superpapi on 2008-12-06
Hello,
I am new to this forum and the only thing I know about Linux & Co is the spelling and at the age of 72 I may never become a real specialist.
I have a question related to this subject. I tried to install with the help of a friend of mine Sus 11.0 on my new Asus N10J laptop and had to face the same problem. The 9300M GS cannot be found on the NVIDIA site. Then I found this thread telling me that it is provided with UBUNTU. This means that it may exist somewhere and I suppose, but I amnot an expert at all, that the same driver could be used in the Suse environment as well.
Question? is there now way to get that Driver from the Ubunto team???

I than you in advance for your suggestions.

Superpapi

---

### Post by cozadaman on 2008-12-24
The version of drivers that support the 9300M G are version 177. So search the nvidia site for the Nvidia Drivers version 177, thats the version that supports the chip reguardless of linux flavour.

Post back, hope this helps.

---

### Post by gjoellee on 2008-12-24
Support for this came with the latest kernels and drivers...


If you buy a computer with totally new hardware support should come for that hardware within 6 months.

---

### Post by Superpapi on 2008-12-25
This is just to thank you all for the help you provided.
Now let me wish you all a merry Christmas and a Happy new Year.
Superpapi

---

### Post by cozadaman on 2008-12-26
For anyone chasing the drivers for this (9300M G/GS) chipset outside of the Ubuntu flavour, the driver version is 177, and can be found on the Nvidia webpage. :)

---

### Post by bwzriccio on 2009-02-02
Hi all,
I just installed ubuntu 8.10 on my new vaio cs with VIDIA GEFORCE 9300M GS 128MB and after the installation as ubuntu reccomended I selected nvidia Drivers version 177.
The following probz occurred to me: The fan goes always turned on during video playing, i experience framedrop and the video quality (using totem or surfing with firefox) is not that good as it has to be.
did anyone experience smthing like that?

I also tried with the driver from nvidia site (NVIDIA-Linux-x86-180.22-pkg1.run).... Now i cannot even boot the server x

---

### Post by avilella on 2009-04-05
Since you have access to a laptop with hybrid graphics and have tried to run Linux, please take a moment to provide the DSDT information for the laptop in this link:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

DSDT is an acronym for Differentiated System Description Table. This table contains the Differentiated Definition Block, which supplies the information and configuration information about the base system. It is always inserted into the ACPI Namespace by the OS at boot time.

If you've got a laptop with a IGP and a hybrid Nvidia or ATi card, and you have tried to use Linux on it, you may have noticed that there are issues with the hybrid graphics setup. To help improve the Linux hybrid graphics support for this laptop, please attach your DSDT information to this Launchpad bug report specifying your laptop model:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.


> **bwzriccio said:**
> Hi all,
I just installed ubuntu 8.10 on my new vaio cs with VIDIA GEFORCE 9300M GS 128MB and after the installation as ubuntu reccomended I selected nvidia Drivers version 177.
The following probz occurred to me: The fan goes always turned on during video playing, i experience framedrop and the video quality (using totem or surfing with firefox) is not that good as it has to be.
did anyone experience smthing like that?

I also tried with the driver from nvidia site (NVIDIA-Linux-x86-180.22-pkg1.run).... Now i cannot even boot the server x

---

### Post by Ubuntization on 2009-10-09
I just bought a laptop (**MSI EX630**) that has the video card **Nvidia GeForce 9300M GS.**
I installed Ubuntu 9.4 and when I tried hardware Drivers it did not recognized my video card. 

However I went to update manager and did all the 250+ updates, then rebooted the pc and tried Hardware Drivers again and this time **IT DID** both recognize and install the drivers.

Now it is working perfectly.

---

### Post by Ubuntization on 2009-10-09
Hey Superpapi 
First of all I have to admit , I admire you being 72 and using UBUNTU :D

please read my reply, I was able to fix this problem on my own PC 

Good luck

---

