---
title: "Agere SoftModem driver not passing incoming RING notification."
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by Gimli on 2008-02-21
I all, 
I am having some problems with installing the Agere SoftModem in my Ubuntu Server.
I am also posting this to the linmodems mailing list, but hope there is someone here that can be of help.

In short, I can install the modem driver and dial out, but the incoming ring is not detected therefore presenting problems with my Hylafax installation.

This has been keeping me going for a week now and is driving me nuts. I hope someone can help.

I give you my complete installation process, Modemdata.txt and other info.

Installation process.

I ran scanModem (output of ModemData.txt attached below) which suggested that the type is 11c1:0620 and required driver is Agere.SV2P.
I also visited the following site which suggested the chipset is SV92PP. ([http://www.pcidatabase.com/vendor_details.php?id=979](http://www.pcidatabase.com/vendor_details.php?id=979))

I downloaded the newest driver from [http://phep2.technion.ac.il/linmodems/packages/ltmodem/sv92/agrsm-20080203.tar.gz](http://phep2.technion.ac.il/linmodems/packages/ltmodem/sv92/agrsm-20080203.tar.gz)

I installed following the instructions in the readme and

Then I load the drivers using
$ sudo modprobe agrmodem
$ sudo modprobe agrserial

the following confirms that they are loaded

$ lsmod | grep agr
agrserial              13984  0
agrmodem             1188772  1 agrserial

the modem comes up on ttyAGS3

$ ls -l | grep ttyA*
crw-rw---- 1 root   dialout  62,  67 2008-02-21 21:03 ttyAGS3

Then I open minicom and change the port to ttsAGS3 using
$ sudo minicom -s

Test 1: Dialout
ATDT xxxxxxx successfully dials out and hangs up.

Test 2: Receiving
I dial the number of the modem but no RING is displayed in minicom. I can answer successfully using command ATA.

This problem translates directly to my Hylafax server installation. Faxanswer does not instruct faxgetty to answer the phone because it does not know the phone is ringing.


ModemData.txt

 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.22-14-server
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Your contry's local Linux experts
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org)
--------------------------  System information ----------------------------
CPU=i686,
Linux version 2.6.22-14-server (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 08:27:05 UTC 2008
 scanModem update of:  2008_02_10


 There are no blacklisted modem drivers in /etc/modprobe*  files

The Advanced Linux Sound Architecture (ALSA) packages providing audio support,
also includes drivers for some modems. The ALSA diagnostics are written during
bootup to /proc/asound/ folders.

USB modem not detected by lsusb
For candidate card in slot 01:01.0, firmware information and bootup diagnostics are:
 PCI slot       PCI ID          SubsystemID     Name
 ----------     ---------       ---------       --------------
 01:01.0        11c1:0620       11c1:0620       Communication controller: Agere Systems Unknown device 0620

 Modem interrupt assignment and sharing:
 --- Bootup diagnostics for card in PCI slot 01:01.0 ----


 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===




Predictive diagnostics for card in PCI bus 01:01.0:
        Modem chipset  detected on
CLASS="Class 0780: 11c1:0620"
NAME="Communication controller: Agere Systems Unknown device 0620"
PCIDEV=11c1:0620
SUBSYS=11c1:0620
SUBven=11c1
IRQ=10
IDENT=Agere.SV2P

 For candidate modem in PCI bus:  01:01.0
   Class 0780: 11c1:0620 Communication controller: Agere Systems Unknown device 0620
      Primary PCI_id  11c1:0620
 Support type needed or chipset:        Agere.SV2P


----------------end Softmodem section --------------

 Vendor 11c1 is Lucent Technologies with modem technology now under LSI Inc.
Their Linux  code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its
 continued maintenance is only initiated at the request of a major chipset buyer,
 or comparable sponsor. Several different  modem chipset types  are produced:
 with varying support under Linux.
 Device ID  Support        Name           Comment
 ---------  -------------  -----------    -----------------------------
 0480       serial drivers Venus           controller chipset 1673JV7
 0440-045d  martian        Mars/Apollo     DSP (digital signal processing) chipsets
 0462       none           56K.V90/ADSL Wildwire
 048d none                 SV2P            soft modem
 048(c or f) AGRSM         SV2P            soft modem
 0600       none           soft modem, very few in the field.
 0620       AGRSM          Pinball  soft modem, in some HP desktop PCs
 062(1-3)   none           SV92PP,Pinball  soft modem, in some HP desktop PCs

martian - At [http://linmodems.technion.ac.il/linmodems/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/linmodems/ltmodem/kernel-2.6/martian/)

AGRSM - At [http://linmodems.technion.ac.il/packages/ltmodem/sv92/](http://linmodems.technion.ac.il/packages/ltmodem/sv92/)
The  suse-10-2a.tar.gz has newer Agere/LSI code, but there are compiling problems with newer kernels/

Read Agrsm.txt
-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.3
             and the compiler used in kernel assembly: 4.1.3



 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   linuc_headers base folder /lib/modules/2.6.22-14-server/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,  linux-libc-dev). The also required headers of package libc6 are commonly installed by default.



If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed package
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
        -rwsr-xr-- 1 root dip 269256 2007-10-04 21:57 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
        $ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
        sudo chmod a+x /usr/sbin/pppd

Checking settings of:   /etc/ppp/options
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
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/YourSystem.txt concerning other COMM channels: eth0
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
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------


make and make install output

$ sudo make
make -C /lib/modules/2.6.22-14-server/build SUBDIRS=/home/clr/modem/agrsm modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-server'
  CC [M]  /home/clr/modem/agrsm/agrsoftmodem.o
objcopy --weaken-symbol=LXHardwareInfoCreate \
                --weaken-symbol=LXHardwareInfoDestroy \
                /home/clr/modem/agrsm/agrmodemlib.o /home/clr/modem/agrsm/agrsm_core.o
  CC [M]  /home/clr/modem/agrsm/lib.o
/home/clr/modem/agrsm/lib.c: In function ‘agr_pci_find_device’:
/home/clr/modem/agrsm/lib.c:134: warning: ‘pci_find_device’ is deprecated (declared at include/linux/pci.h:477)
  CC [M]  /home/clr/modem/agrsm/serial26.o
/home/clr/modem/agrsm/serial26.c: In function ‘serial8250_get_mctrl’:
/home/clr/modem/agrsm/serial26.c:1371: warning: unused variable ‘flags’
/home/clr/modem/agrsm/serial26.c: In function ‘serial8250_config_port’:
/home/clr/modem/agrsm/serial26.c:2039: warning: unused variable ‘ret’
/home/clr/modem/agrsm/serial26.c: At top level:
/home/clr/modem/agrsm/serial26.c:2131: warning: initialization from incompatible pointer type
/home/clr/modem/agrsm/serial26.c:2132: warning: initialization from incompatible pointer type
/home/clr/modem/agrsm/serial26.c:1922: warning: ‘serial8250_request_rsa_resource’ defined but not used
  LD [M]  /home/clr/modem/agrsm/agrmodem.o
  LD [M]  /home/clr/modem/agrsm/agrserial.o
  Building modules, stage 2.
  MODPOST 2 modules
WARNING: could not find /home/clr/modem/agrsm/.agrsm_core.o.cmd for /home/clr/modem/agrsm/agrsm_core.o
  CC      /home/clr/modem/agrsm/agrmodem.mod.o
  LD [M]  /home/clr/modem/agrsm/agrmodem.ko
  CC      /home/clr/modem/agrsm/agrserial.mod.o
  LD [M]  /home/clr/modem/agrsm/agrserial.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-server'


$ sudo make install
make -C /lib/modules/2.6.22-14-server/build M="/home/clr/modem/agrsm" modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-server'
  INSTALL /home/clr/modem/agrsm/agrmodem.ko
  INSTALL /home/clr/modem/agrsm/agrserial.ko
  DEPMOD  2.6.22-14-server
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-server'
if ! /sbin/modprobe -nq agrmodem.ko ; then /sbin/depmod -a; fi

---

