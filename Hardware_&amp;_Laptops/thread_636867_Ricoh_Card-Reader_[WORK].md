---
title: "Ricoh Card-Reader [WORK]"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by smileone on 2007-12-10
Hi everyone,
If  you have a Ricoh card reader and you can't work with it, try my suggestion.

```
lspci | grep Ricoh
```I will see any like this
```
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```First of all you must unload sdhci module with this code

```
sudo modprobe -rv sdhci mmc_core mmc_block
```(-v parameter it is verbose mode)

Now we can work on sdhci module.
```
sudo setpci -s 07:09.2 0xCA=0x57
sudo setcpi -s 07:09.1 0xCB=0x02
sudo setpci -s 07:09.1 0xCA=0x00

```
It is possibile that your Rioch's adress it is different of mine.
Check your lspci output and  insert the correcting adress (like 03:01.1 instead 07.09.1).
```
sudo modprobe -v sdhci mmc_core mmc_blcok
```
Now when insert your card.:popcorn:

My Ubuntu machine is FJ Amilo Si1520 and my Ubuntu version is 7.10 stable release.
P.S.: If you want try sdricoh-cs go to this web site
[http://sourceforge.net/projects/sdricohcs/](http://sourceforge.net/projects/sdricohcs/)
(Read before installation README file,  if have any problem to install sdricoh-cs contact me)

---

### Post by ldalcaraz on 2007-12-28
I can not make the XD reader work on my card reader (Dell inspiron 6400) here is the output of my lspci:

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


sudo modprobe -v sdhci mmc_core mmc_blcok

insmod /lib/modules/2.6.22-14-generic/kernel/drivers/mmc/host/sdhci.ko mmc_core mmc_blcok
FATAL: Error inserting sdhci (/lib/modules/2.6.22-14-generic/kernel/drivers/mmc/host/sdhci.ko): Unknown symbol in module, or unknown parameter (see dmesg)


Thank you ;) :confused:

---

### Post by kidcharles on 2007-12-29
> **ldalcaraz said:**
> I can not make the XD reader work on my card reader (Dell inspiron 6400) here is the output of my lspci:

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


sudo modprobe -v sdhci mmc_core mmc_blcok

insmod /lib/modules/2.6.22-14-generic/kernel/drivers/mmc/host/sdhci.ko mmc_core mmc_blcok
FATAL: Error inserting sdhci (/lib/modules/2.6.22-14-generic/kernel/drivers/mmc/host/sdhci.ko): Unknown symbol in module, or unknown parameter (see dmesg)


Thank you ;) :confused:

I had the same error message after following smileone's instructions but after restarting my computer (Dell E1505 Inspiron Notebook) it automounted an SD card (I'm running Ubuntu 7.04).

---

### Post by josin on 2007-12-29
I also had the same error message after following smileone's instructions but after restarting my computer (Lenovo 3000 N200 0769 Notebook) it unfortunately did'nt automount the SD card (I'm running Ubuntu 7.10).:(

---

### Post by d5ghost on 2008-01-07
> **ldalcaraz said:**
> I can not make the XD reader work on my card reader (Dell inspiron 6400) here is the output of my lspci:

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


sudo modprobe -v sdhci mmc_core mmc_blcok

insmod /lib/modules/2.6.22-14-generic/kernel/drivers/mmc/host/sdhci.ko mmc_core mmc_blcok
FATAL: Error inserting sdhci (/lib/modules/2.6.22-14-generic/kernel/drivers/mmc/host/sdhci.ko): Unknown symbol in module, or unknown parameter (see dmesg)


Thank you ;) :confused:

derek@ubuntu:~$ sudo modprobe -v sdhci mmc_core mmc_blcok
insmod /lib/modules/2.6.20-16-generic/kernel/drivers/mmc/core/mmc_core.ko 
insmod /lib/modules/2.6.20-16-generic/kernel/drivers/mmc/host/sdhci.ko mmc_core mmc_blcok
FATAL: Error inserting sdhci (/lib/modules/2.6.20-16-generic/kernel/drivers/mmc/host/sdhci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
derek@ubuntu:~$ sudo modprobe -v sdhci 
insmod /lib/modules/2.6.20-16-generic/kernel/drivers/mmc/host/sdhci.ko 
derek@ubuntu:~$

---

### Post by Ras1982hun on 2008-01-29
try
```
sudo modprobe -v sdhci
``` 
that should work

---

### Post by smileone on 2008-02-10
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/111089](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/111089)

---

### Post by djz88 on 2008-04-17
I got the same error like u 

I did commands one by one


```
 sudo modprobe -v sdhci
 sudo modprobe -v sdhci mmc_core
 sudo modprobe -v sdhci mmc_blcok
```

and after card plugged as well.

---

### Post by chunchengch on 2008-04-20
[http://ubuntuforums.org/showthread.php?p=4751191#post4751191](http://ubuntuforums.org/showthread.php?p=4751191#post4751191)

---

### Post by emaxx on 2008-05-01
ehmm, what if you try mm_block instead of mm_blcok ...

:lolflag:

---

### Post by chunchengch on 2008-05-01
I make a new deb for Ricoh Card-Reader, it will check and install necessary dependencies, so it may be available for models R5C552 and RL5c476 etc, you can find it in my thread [http://ubuntuforums.org/showthread.php?t=760357](http://ubuntuforums.org/showthread.php?t=760357)

---

