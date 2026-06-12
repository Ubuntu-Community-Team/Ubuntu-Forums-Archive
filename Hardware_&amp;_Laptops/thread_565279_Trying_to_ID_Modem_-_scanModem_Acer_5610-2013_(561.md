---
title: "Trying to ID Modem - scanModem Acer 5610-2013 (5610Z)"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by mfdc1969 on 2007-10-02
I'm trying to ID the internal modem in my Acer 5610-2013 (it's a 5610Z Build No. BL50 running Fiesty Ubuntu) and I have followed the instructions from  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_identify_Modem_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_identify_Modem_chipset) in an attempt to ID the modem chipset using scanModem. 

Here is the output of the ModemData.txt file



```
 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 7.04 kernel 2.6.20-16-386
 Occassionally reponses are blocked by an Internet Providers mail filters.
 So do in a day also check the Archived responses at DISCUSS@linmodems.org
Code updated on:  2005_April_19
------------ --------------  System information ------------------------
Ubuntu 7.04 
 on System with processor: i686
 currently under kernel:   2.6.20-16-386
 The kernel was assembled with compiler:  4.1.2
 with current System compiler GCC=4.1.2
    /usr/bin/gcc -> gcc-4.1

Checking for kernel-headers needed for compiling.

 A /dev/modem symbolic link is not set.
 Checking for USB modems
 None found
--------- lspci scan ----------------
 PCI_bus
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
-------------------------------------

 A modem was not detected among the above PCI devices.
 This indicates that the modem, if present has a non-standard or ISA bridge.
 Please follow the directions in Modem/General.txt for identifying the modem properties
 when booting under Microsoft Windows. Also access any documentation sources
 on yourchipset.  Guidance can only be provided AFTER
 the chipset and/or its drivers have been identified.

  ======= PCI_ID checking completed ====== 
 Update=2005_April_19

Analyzing information for PCMCIA device at PCI Bus 06:04.0
GREPping for an inserted PCMCIA modem with filter:        ommunication
 A PCMCIA modem is detected.
      
 The stardard ltmodem resources should suffice for modem support:
     http://ltmodem.heby.de/
 if the modem has a Lucent/Agere digital processing chipset.
 
   
For information on modem port creation under the UDEV device file system see:
   http://linmodems.technion.ac.il/archive-fourth/msg03299.html  for Conexnant modems
   http://linmodems.technion.ac.il/archive-fifth/msg01177.html  for Lucent/Agere DSP modems
   
The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases~:alias net-pf-24 pppoe
-------------------------------------
 Resident PPP support modules are properly uncompressed .
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 00:16:D4:D2:8C:9B  
wlan0     Link encap:Ethernet  HWaddr 00:19:7E:3D:CB:20  
          inet6 addr: fe80::219:7eff:fe3d:cb20/64 Scope:Link
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/General.txt
 Be sure to read the Ethernet section of Modem/General.txt 
DEVPPP=crw------- 1 root root 108, 0 2007-04-15 04:49 /dev/ppp
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[   22.224298] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 5 6 10 12 14 15) *0, disabled.
[   22.325652]   IO window: disabled.
[   22.325660]   MEM window: disabled.
[   22.325666]   PREFETCH window: disabled.
[   22.325678]   IO window: disabled.
[   22.325685]   MEM window: disabled.
[   22.325692]   PREFETCH window: disabled.
[   22.325703]   IO window: disabled.
[   22.325710]   MEM window: disabled.
[   22.325717]   PREFETCH window: disabled.
[   22.325728]   IO window: disabled.
[   22.325744]   PREFETCH window: disabled.
[   23.768744] audit: initializing netlink socket (disabled)
[   38.708000] ibm_acpi: ec object not found
[   38.824000] pcc_acpi: loading...
[   43.172000] apm: BIOS not found.
  debian is not yet providing pre-compiled drivers for WinModems
```


So, bear with me please ... I'm a noob, I believe it states:
- No USB modem found
- No modem was found amoung PCI devices
- PCMCIA modem was found and it refers me to [http://ltmodem.heby.de/](http://ltmodem.heby.de/) and I then go to the page mentioned for my 2.6.xx kernel [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/) and there is a package **agrsm-ubuntu-2.6.20-16-generic.tar.gz   **

But there is also a folder "Ubuntu" which contains packages for 2.6.10/12 kernels for the ltmodem.

Is this simply just a matter of me downloading the TAR and then finding the instructions for the installation of ltmodems in Fiesty?

Any help would be greatly appreciated!
Thanks,
Michael

---

### Post by mfdc1969 on 2007-10-12
**[COLOR="Red"]I have updated this so others may benefit.[/COLOR]**

M.

Date: Thu, 11 Oct 2007 20:18:37 -0400
> From: "Marvin Stodolsky"
> To: "M"
> Subject: Re: scanModem, Ubuntu 7.04 kernel 2.6.20-16-386
> MC
> 
> updated on:  2005_April_19
> is too ancient to analyze the modem which is likely hosted upon the
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High
> Definition Audio Controller
> 
> Get the current scanModem from  [http://limodems.technion.ac.il](http://limodems.technion.ac.il) and
> send us the new ModemData.txt if necessary.

----------------------------

New scanModem data:

```
 Only plain text email is forwarded by the  DISCUSS@linmodems.org List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry  kernel 2.6.20-16-386 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org .
 Local Linux experts can be found through: http://www.linux.org/groups/index.html
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.20-16-386 (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Sun Sep 23 19:47:10 UTC 2007
 scanModem update of:  2007_Oct_09


 There are no blacklisted modem drivers in /etc/modprobe*  files 
USB modem not detected by lsusb


Advanced Linux Sound Architecture  (ALSA) spackage providing audio support 
on your System, also includes drivers for some modems. For modems using the 
snd-hda-intel  audio+modem driver, upgrades to a new ALSA version are sometimes 
necessary to achieve function. See for example:
      http://linmodems.technion.ac.il/bigarch/archive-seventh/msg02144.html
Copying ALSA diagnostics to Modem/ALSAroot.tgz
ALSAversion = 1.0.13

Modem or candidate host audio card have firmware information and diagnostics:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:27d8	1025:0090	Audio device: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 22:       2503   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   23.900000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   23.900000] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

  The High Defintion Audio card with PCI ID 8086:27d8 may host a soft modem chip.
Bootup diagnostics lack ALSA data.
 Modem not detected though HDA card diagnostics
 For candidate modem in PCI bus:  00:1b.0
   Class 0403: 8086:27d8 Audio device: Intel Corporation 82801G
      Primary PCI_id  8086:27d8
    Subsystem PCI_id  1025:0090 
    Softmodem codec or Vendor from diagnostics: 
                              from    Archives: 14f12bfa, a Conexant type,
                        

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	hsfmodem


Writing Intel.txt

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read Conexant.txt

 The hsfmodem package serves a great variety of Conexant chipset modems. 
 From  http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php
 download hsfmodem_VersionSpec_k2.6.20_16_386_ubuntu_i386.deb.zip 
                           with 2.6.20_16_386 equivalent to 2.6.20-16-386, your kernel version.
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See Testing.txt  for details.
 
 Read Conexant.txt

Writing Conexant.txt


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   linuc_headers base folder /lib/modules/2.6.20-16-386/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,  linux-libc-dev). The also required headers of package libc6 are commonly installed by default. 

Compressed files at: /usr/src/linux-source-2.6.20.tar.bz2


If a driver compilation files with message including some lack of some FileName.h (stdio.h for example. 
Some additional kernel-header files need installation to /usr/include.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:
$ sudo apt-get -s install linux-kernel-devel
While some of the files may be on the install CD, others may have to be found through http://packages.ubuntu.com

For Ubuntu Feisty, additional packages required were:
 libc6-dev linux-libc-dev
available through http://packages.ubuntu.com/ , if not on the install CD.
Such packages may have different names for other Linux distributions.
Try installing just the libc6-dev, then test the compile again.


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269224 2007-04-04 20:41 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html

Read Modem/YourSystem.txt concerning other COMM channels: eth0 eth0:avah wlan0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------
```


------------------------------

Date: Fri, 12 Oct 2007 15:28:32 +0200
> From: [email]discuss@linmodems.org[/email]
> To: "M"
> CC: Marvin Stodolsky
> 	
> Subject: Re: M, Canada kernel 2.6.20-16-386
> 
> So all you need for your Conexant HSF modem is the Linuxant driver.
> Open again ModemData.txt, find the line starting with
> For owners of a Dell  etc...
> and read instructions from there on through
> Writing Conexant.txt

---

### Post by mfdc1969 on 2007-10-15
Followed instructions from scanModem output file ModemData.txt:

```
For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read Conexant.txt

 The hsfmodem package serves a great variety of Conexant chipset modems. 
 From  http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php
 download hsfmodem_VersionSpec_k2.6.20_16_386_ubuntu_i386.deb.zip 
                           with 2.6.20_16_386 equivalent to 2.6.20-16-386, your kernel version.
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found after a reboot
```

After reboot it was necessary to:

```
sudo hsfconfig
```

and following that I had to remove the Volume control from the panel and re-add it to enable it.

**The modem is now recognised by the Restricted Drivers and does dial out.**

I hope my posting/threads may help others.

---

### Post by ferarg on 2008-01-09
Thanks man!!

Great Help!

---

