---
title: "5 in 1 memory card reader not working"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by davebell on 2007-12-21
hey ppl
ive checked the forums repeatedly but nothing has worked that ive read so far...
ive got a toshiba satellite m100 notebook with a  Texas Instruments 5-in-1 Multimedia Card Reader which does not work... HELP! lol
heres the output to lspci:


```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
**05:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)**
05:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```


im fairly sure its the device which i have bolded....any help or suggestions to fix this would b much appreciated!

thanks in advance guys!!!

---

### Post by davebell on 2007-12-23
bump...
surely someone must hav some idea...

---

### Post by davebell on 2007-12-23
bumpedy bump bump BUMP...
HELP! please!

---

### Post by scxtt on 2007-12-23
i have 1 of those in my laptop too - there's a driver (or a few of them) for it but it still doesn't seem to work ... i really wouldn't hold your breath on getting it working.

edit: drivers are "tifm"

---

### Post by richardjennings on 2007-12-23
Does the output from lspci change if you enter a sd card?

maybe you can try manually mounting the device

something like:

mkdir /media/temp
sudo mount /proc/bus/pci/05/06.2 /media/temp

---

### Post by davebell on 2007-12-23
well i actually wanted to use it for an xD card and my memory card out of my psp which is a memory stick duo... but i use an adapter for it.... which i think makes it a memory stick pro due or something... i dno...
thanks for ur help!

no lspci output does not change...

and upon trying: sudo mount /proc/bus/pci/05/06.2/media/temp       i got the following error:
mount: /proc/bus/pci/05/06.2 is not a block device (maybe try `-o loop'?)

so i dno...where do i find the drivers for it? and how do i install them?
 thanks!

---

### Post by scxtt on 2007-12-23
do **modprobe -l | grep tifm** -- that should give you a listing of ones that are available ... then you could do **sudo modprobe <module_name>** to load them into the kernel ...

---

### Post by davebell on 2007-12-23
that did wrk... it returner an error saying module not found...
doesnt matter now... well not as much...
i discovered that my psp does in fact now wrk wen i plug it into my laptop via the usb port from memory it never used to...
oh well...
thanks for ur help!!

---

### Post by zarg@henrikke on 2007-12-28
It works fine for me, out of the box on 7.10, I get

# lsmod | grep tifm
tifm_7xx1               8576  0
tifm_core              11268  1 tifm_7xx1

and load the missing module, without any problems:

# modprobe tifm_sd
# lsmod | grep tifm
tifm_sd                12808  0
tifm_7xx1               8576  0
tifm_core              11268  2 tifm_sd,tifm_7xx1
mmc_core               28420  2 tifm_sd,sdhci

but I don't have a card to test with...

---

### Post by scxtt on 2007-12-28
yeah, i didn't have any problems w/ the modules, but when i plug the mini-SD card into the reader, nothing happens (aside from error messages from **dmesg**)

---

### Post by dapaintballer331 on 2007-12-29
I have a similar problem. If I insert a SD card, it gets mounted, but I can't successfully write to it.

---

### Post by jimmy the saint on 2007-12-29
dapaintballer33, the first time I tried to write to an SD card the same thing happened.  I figured out that you have to be sure to unmount it first before removing it otherwise nothing gets removed.  It spent quite a while writing the data before it said it was succesfully removed.  

I still cant get a memory stick pro to mount though.

---

### Post by cathectic on 2007-12-30
tifmxx only supports MMC/ SD in mainline kernels.

The developer has some experimental work to support MemoryStick and MemoryStick Pro in the projects Subversion tree.

xD support is still quite some way off.

Unfortunately, this is a completely closed, proprietary chip (TI have refused to release the specs for it), and all development work on it is coming through the efforts of just one person reverse engineering the Windows drivers.

---

### Post by Timokl on 2008-01-06
I've found some information in the Ubuntu Wiki:

[https://wiki.ubuntu.com/ticardreader]("https://wiki.ubuntu.com/ticardreader?highlight=%28card%29%7C%28reader%29")

According to this, you have to set an interrupt to activate the kernel modules.

Some who can give me an idea on how to find out the needed busid?

Thanks!

---

### Post by scxtt on 2008-01-06
should be the 1st column in the lspci output, from the example in the 1st post it would be "05:06.2":

sudo setpci -s 05:06.2 4c.b=0x02

i'd check myself, but for some reason Arch isn't seeing my card reader at all :(
edit: oh yeah, starting HAL would help ;)

---

