---
title: "Want to build a new PC for my Ubuntu"
date: 2014-03-09
forum: Hardware
---

### Post by nemesis345crew on 2014-03-09
Good evening from Greece.

I am a web developer & designer.
Because of a hardware problem on my current setup i am about to buy a few parts in order to build a new one!

So currently i am looking at these main parts:
Motherboard: Gigabyte - H87-HD3 (1150/H87/DDR3) 
CPU: INTEL CORE I5-4670 3.40GHZ LGA1150 - BOX 
RAM: KINGSTON KHX1600C9D3K2/8GX 8GB (2X4GB) PC12800 HYPERX GENESIS XMP DUAL CHANNEL KIT 
HDD: WESTERN DIGITAL WD2500AAKX 250GB CAVIAR BLUE SATA3 
Case: COOLERMASTER RC-610-KKN1 CENTURION 6 BLACK 

I already have these parts which are still working great, so i will still use them:
Keyboard/mouse Logitech EX110 wireless set 
HDDs: SATA WDC WD1600AAJS-00WAA0 160GB  ||  SATA WDC WD1001FALS-00J7B1 1T  ||  EXTERNAL WD MYPASSPORT 1T
Sound Card: SOUND BLASTER AUDIGY PLATINUM (&#960;&#953;&#952;&#945;&#957;&#972;&#957; &#957;&#945; &#960;&#945;&#961;&#959;&#960;&#955;&#953;&#963;&#964;&#949;&#943;)
Power Supply: THERMALTAKE TR2-420 (if the final build requires more power then i will change it of course)

I do have also 2 ide HDD back i will propably use them as external backup tools.

Programs i use: Apache (with PHP), MySQL Server, MySQL Workbench, Netbeans or Eclipse. As an old user of windows i still use Photoshop through WINE and i wish i could use After Effects too. After Effects is less primary for my workflow(maximum estimated usage is about 2 to 3 times in a whole year). Also i am using OracleVM Virtualbox to run Windows XP under Ubuntu. The Photoshop also runs through the VM inthe XP setup!

I have to tell you that the past 2 days i am thinking about change the intel i5 with an i7, so please pay attention to that too.


I will appreciate comments, suggestions and thoughts about my set up.


Yours friendly,
Konstantinos P. Moschovis (nemesis345crew)

---

### Post by oldfred on 2014-03-09
With a 4 series Intel chip (Haswell) you will have a motherboard that is both UEFI or BIOS.
Windows only boot from gpt drives with UEFI or with UEFI only boots from gpt partitioned drives.
Both Windows & Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.
But Ubuntu will boot from gpt partitioned drives with either BIOS or UEFI.

So I suggest all new drives or any you can reformat, use gpt. And include an efi partition at beginning of drive for UEFI or future use with UEFI if using BIOS. If BIOS you will need a 1 or 2MB unformatted partition with the bios_grub flag.

XP will not read gpt partitioned drives, but XP is obsolete in April.

Some older Gigabyte boards had these issues, not sure if newer are similar or not.
 Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www](http://www).[rod]("http://www.rodsbooks.com/gb-hybrid-efi/")sbooks.com/gb-hybrid-efi/
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off.and nomodeset
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

---

### Post by andrew.46 on 2014-03-09
If you decide to change the PSU perhaps consider a *modular* PSU. This was the only regret I had when I built my last computer...

---

### Post by CJ_Hudson on 2014-03-09
Fwiw I just built an AMD based machine, spec here: 

Gigabyte 78LMT-USB3 AM3+ 
ATX case 
ASUS VE247 Monitor 
 Corsair MX-3 DDR3 1600 4GBx4 RAM 
 OCZ Core XStream 500W PSU 
Asus BC12D1ST 5.25" blu ray ROM DVD/CD R/RW drive 
 Seagate Barracuda 2 Tb HDD 
 GT610 NVidia 1 Gb graphics card 
 TP Link TL-WN781ND PCI-E Wireless adapter 
 AMD FX4130 3.8 GHz 'Bulldozer' 
 TP Link 56k TM-IP5600 PCI datafax modem 
 Windows 8 64 bit pr

 Now it's stable I'm thinking of installing Ubuntu too.
:-)

---

### Post by nemesis345crew on 2014-03-09
@oldfred 
So you would suggest an other board eg. ASUS?
Sorry but didn't understand the thing with the UEFI, if you could give me a better explanation!

Thanks!

---

### Post by oldfred on 2014-03-09
I do not know what motherboard may be best or not.

UEFI is the new replacement for BIOS. Current UEFI offer CSM.
       UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

But now when you install or boot repair tools you need to know which way you are booting UEFI or BIOS as that is how it installs.

I think all of these had various issues.
      
 Gigabyte's ASPM Motherboard Fix: Use Windows
[http://www.phoronix.com/scan.php?page=news_item&px=MTAwMjg](http://www.phoronix.com/scan.php?page=news_item&px=MTAwMjg)
Gigabyte GA-Z87X-UD3H, Ubuntu 13.10, and Intermittent External USB Drive Failure 
[http://ubuntuforums.org/showthread.php?t=2194155](http://ubuntuforums.org/showthread.php?t=2194155)

 biostar A960D+ motherboard -MSI quirk detected
[http://ubuntuforums.org/showthread.php?t=2202279](http://ubuntuforums.org/showthread.php?t=2202279)
Some have issues with Asrock.
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
ASUS Rampage IV Extreme motherboard
[http://ubuntuforums.org/showthread.php?t=2063073](http://ubuntuforums.org/showthread.php?t=2063073)

---

### Post by Yellow Pasque on 2014-03-09
It looks pretty good to me. The RAM is on the Qualified Vendor List, so that's good.

- The PSU only has 2 SATA connectors, but it's not a problem, as you can plug a Molex connector directly into the WD1600AAJS (make sure NOT to plug a Molex AND a SATA power connector in the drive at the same time unless you like the smell of burnt electronics..)

- The PSU only has a 4-pin connector for the CPU power. You can try and plug this into the 8-pin connector, but don't be surprised if it can't deliver enough power under full load. You may want to consider a cheap adapter : [http://www.newegg.com/Product/Product.aspx?Item=N82E16812706003](http://www.newegg.com/Product/Product.aspx?Item=N82E16812706003)

> CPU: INTEL CORE I5-4670 3.40GHZ LGA1150 - BOX 
I'd personally rather go for a CPU with a little better graphics (like 4400 or 4600) [https://en.wikipedia.org/wiki/Intel_HD_Graphics#Haswell](https://en.wikipedia.org/wiki/Intel_HD_Graphics#Haswell)

---

