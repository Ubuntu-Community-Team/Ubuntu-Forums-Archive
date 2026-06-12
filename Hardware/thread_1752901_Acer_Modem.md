---
title: "Acer Modem"
date: 2011-05-08
forum: Hardware
---

### Post by coljohnhannibalsmith on 2011-05-08
Hello,

I have been trying since Gutsy to get the Winmodem on my Laptop to work; but have been unsucessful.  This is unfortunate since in many rural parts of the world a dial-up connection is the only available or economical option.  This would include rural parts of Latin-American, Africa and Oceania.  Since I am a world traveler, this option is very important to me.  I am sure this includes part of Asia as well.

I'm aware of the following website, which has gotten me closer than any other to at least identifying the type of modem I have and offering some potential solutions.  Since I have the time, I'm now going to give it another try, and at least document my efforts, so that others more knowledgeable may be better able to assist.  The last time I tried to install drivers suggested by this site, they killed my sound-card; since the 64 bit drivers were not compatible with ALSA:

[http://linmodems.org/](http://linmodems.org/)




Hannibal

---

### Post by coljohnhannibalsmith on 2011-05-08
I found the scanModem utility here:

[http://132.68.73.235/linmodems/packages/scanModem.gz](http://132.68.73.235/linmodems/packages/scanModem.gz)

and it produced the following output:

sophie@sophie-laptop:~/Downloads$ sudo ./scanModem
UPDATE=2011_02_04

 There are weekly updates of scanModem.  Your copy is more than
    14  weeks old!!
 If decisive guidance is not provided by this scanModem of 2011_02_04, 
 download an update from  [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il)

 Continuing in 10 seconds.

DISTRIB_ID=Ubuntu
Identifying PCI bus slots with candidate modems.
Running PCIbus cases
Analysing card in PCI bus 00:14.2, writing to scanout.00:14.2
Using scanout.00:14.2 data, and writing guidance to ModemData.txt
Writing DOCs/Conexant.txt

 Writing residual guidance customized to your System.
   A subfolder Modem/  has been written,  containing these files with more detailed Information: 
 ------------------------------------------------------------------------------------------
 1stRead.txt  Bootup.txt  dmesg.txt  DOCs  ModemData.txt  scanout.00:14.2  tmp
    and in the DOCs subfolder:
 Conexant.txt    DriverCompiling.txt  InfoGeneral.txt  Rational.txt
SoftModem.txt    Testing.txt         UNSUBSCRIBE.txt  wvdial.txt
YourSystem.txt
-------------------------------------------------------------------------------------------
       Please read 1stRead.txt first for Guidance.


sophie@sophie-laptop:~/Downloads$ 


Guess I've got some reading to do...

---

### Post by coljohnhannibalsmith on 2011-05-08
I was able to obtain the following relevant information from the file ModemData.txt:

--------------------------  System information ----------------------------
CPU=x86_64,  Ubuntu ,  ALSA_version=1.0.23
Linux version 2.6.38-9-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #43-Ubuntu SMP Thu Apr 28 15:23:06 UTC 2011
 scanModem update of:  2011_02_04

Distrib_ID=Ubuntu
DistribCodeName=natty
AptRepositoryStem=http://us.archive.ubuntu.com/ubuntu/

Presently install your Linux Distributions dkms package. It provides for automated driver updates, following upgrade of your kernel.  For details see [http://linux.dell.com/projects.shtml#dkms](http://linux.dell.com/projects.shtml#dkms)

There are no blacklisted modem drivers in /etc/modprobe*  files 

Potentially useful modem drivers now loaded are:

      [B][I] snd_hda_intel           

[/I][/B]Candidate PCI devices with modem chips are:
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
High Definition Audio cards can host modem chips.

For candidate card in slot 00:14.2, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 00:14.2    1002:437b    1025:009f    Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller 

 Modem interrupt assignment and sharing: 
 16:       1185        456   IO-APIC-fasteoi   hda_intel
 --- Bootup diagnostics for card in PCI slot 00:14.2 ----
[    0.514914] pci 0000:00:14.2: [1002:437b] type 0 class 0x000403
[    0.514950] pci 0000:00:14.2: reg 10: [mem 0xf0400000-0xf0403fff 64bit]
[    0.515044] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.515050] pci 0000:00:14.2: PME# disabled
[   33.627322] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16

 The PCI slot 00:14.2 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [EMAIL="discuss@linmodems.org"]discuss@linmodems.org[/EMAIL]
 if help is needed.

===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 1
00-01: ALC883 Digital : ALC883 Digital : playback 1
00-02: ALC883 Analog : ALC883 Analog : capture 1
01-00: USB Audio : USB Audio : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf0400000 irq 16
 1 [TigerJet       ]: USB-Audio - USB Internet Phone by TigerJet
                      TigerJet Network, Inc. USB Internet Phone by TigerJet at usb-0000:00:13.0-3, fu

 PCI slot 00:14.2 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.35-29-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.38-9-generic/kernel/sound/pci/hda/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: Conexant ID 2bfa
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x14f12bfa
Subsystem Id: 0x1025009f
Revision Id: 0x90000
Modem Function Group: 0x2

 The audio card hosts a softmodem chip:  0x14f12bfa

 14f1 is the Conexant Vendor ID, and 0x14f12bfa a softmodem chipset.
 Get a hsfmodem package through [http://www.linuxant.com](http://www.linuxant.com)

If not a Conexant modem, the driver hsfmodem-drivers with its dependent drivers:

----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips. 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:14.2:
    Modem chipset  detected on
NAME="Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller "
CLASS=0403
PCIDEV=1002:437b
SUBSYS=1025:009f
IRQ=16
HDA2=00:14.2
SOFT=1002:437b.HDA
CodecDiagnosed=Conexant_
HDAchipVendorID=14f1
CHIP=0x14f12bfa
CodecClass=14f1
IDENT=hsfmodem
Driver=hsfmodem-drivers

 For candidate modem in:  00:14.2
   0403 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller 
      Primary device ID:  1002:437b
    Subsystem PCI_id  1025:009f 
    Softmodem codec or chipset from diagnostics: Conexant_0x14f12bfa
                               from    Archives: 
                        The HDA card softmodem chip is 0x14f12bfa
      
***Support type needed or chipset:    hsfmodem***

Completed candidate modem analyses.

The base of the UDEV device file system is: /dev/.udev

Versions adequately match for the compiler installed: 4.5.2
             and the compiler used in kernel assembly: 4.5.2

***linux-headers-2.6.38-9-generic resources needed for compiling are not manifestly ready!***

 If compiling is necessary packages must be installed, providing:

     [B][I]linux-headers-2.6.38-9-generic
[/I][/B]
Compressed files at: /usr/src/lzma.tar.bz2 /usr/src/open-vm.tar.bz2 /usr/src/vloopback.tar.bz2

Checking pppd properties:
    -rwsr-xr-- 1 root dip 325744 2011-02-04 04:42 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
    $ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
    sudo chmod a+x /usr/sbin/pppd

Checking settings of:    /etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
lcp-echo-interval 30
lcp-echo-failure 4
noipx


***As Rodney Dangerfield (John Cohen) once said...  This is a Messerschmitt!!!!!***



I need a break now....





Hannibal

---

### Post by coljohnhannibalsmith on 2011-05-22
Hello,

I just read about a package in Synaptic that might present an easier way to get my modem to work than relying on kernel modules.  This package is:

**sl-modem-daemon**

Description:

The SmartLink modem daemon is the application part of the
driver for recent modems produced by Smart Link Ltd.

This package replaces (along with hardware access drivers) the old
driver generation (2.7.x) which consisted of kernel modules only.

It needs a kernel driver to access the hardware. This can be either
recent ALSA (shipped with a newer kernel (>=2.6.4) with ALSA support
and snd-intel8x0m module) which is sufficient for basic operation and
data/Internet connection, or the SmartLink kernel driver which is
provided by separate packages which you can build using the source from
the sl-modem-source package.

[COLOR=Blue]***Will this module only work with Smartlink Modems, or will it work with any Generic Softmodem???***[/COLOR]

---

