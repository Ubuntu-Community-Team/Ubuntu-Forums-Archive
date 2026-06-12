---
title: "Linuxant down? How to get USB-FAX Modem to work"
date: 2013-11-29
forum: Hardware
---

### Post by hankoor on 2013-11-29
Hi folks,
i'm trying to get my Conexant USB-Modem to work with my Ubuntu 3.11.0-13-generic.
As far as i can see (i'm very new to Ubuntu and Unix Sys @ all) it has been detected:
[http://www.linmodems.org/](http://www.linmodems.org/) has a Prog named ScanModem which i download and executed. 
Here's some of the output:

```
 Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 3.11.0-13-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: http://www.linux.org/groups/index.html.
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu ,  ALSA_version=k3.11.
Linux version 3.11.0-13-generic (buildd@aatxe) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #20-Ubuntu SMP Wed Oct 23 17:26:33 UTC 2013
 scanModem update of:  2011_08_08

Distrib_ID=Ubuntu
DistribCodeName=saucy
AptRepositoryStem=http://de.archive.ubuntu.com/ubuntu/


The dkms driver upgrade utilities are installed,

 There are no blacklisted modem drivers in /etc/modprobe*  files 

 Potentially useful modem drivers now loaded are:
      cdc_acm            

Attached USB devices are:
 ID 03f0:7d04 Hewlett-Packard DeskJet F2100 Printer series
 ID 0572:1329 Conexant Systems (Rockwell), Inc. 
 ID 08d4:0003 Fujitsu Siemens Computers 
If a cellphone is not detected, see http://ubuntuforums.org/archive/index.php/t-878554.html
A sample report is:  http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to discuss@linmodems.org

Candidate PCI devices with modem chips are:
High Definition Audio cards can host modem chips.

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 004:
    Modem chipset  detected on
SLOT="Bus 004 Device 003:"
NAME="Conexant Systems (Rockwell), Inc. "
bus=004
USBmodemID=0572:1329
IDENT=dgcmodem
Driver=dgcmodem

For a detailed USB cellphone usage report, see http://linmodems.technion.ac.il/bigarch/archive-eighth/msg03240.html 
 For candidate modem in:  004
    Conexant Systems (Rockwell), Inc. 
      Primary device ID:  0572:1329
 Support type needed or chipset:    dgcmodem
 


For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt

 The modem requires a dgcmodem package.

Modem support packages from Linuxant include resources for compiling drivers.  
If an installer package matching your kernel_version  is not provided,
just install a generic code package.

 From  http://www.linuxant.com/drivers/dgc/downloads-ubuntu-x86.php
 download dgcmodem-7.80.02.05full_k3.11.0_13_generic_ubuntu_i386.deb.zip 
 Under Linux unpack with:
 $ unzip dgcmodem*.zip
 Then install with:
 $ sudo dpkg -i dgcmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.
 
 The directions following below need only be pursued, if the above procedures are not adequate.
004
 Read DOCs/Conexant.txt

Writing DOCs/Conexant.txt



 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.8.1
             and the compiler used in kernel assembly: 4.8

 linux-headers-3.11.0-13-generic resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
     linux-headers-3.11.0-13-generic
Compressed files at: /usr/src/linux-source-3.11.0.tar.bz2


If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through http://packages.ubuntu.com
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
    -rwsr-xr-- 1 root dip 322968 Jan 22  2013 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html

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

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html

For guidance on FAX usage, get from http://linmodems.technion.ac.il/packages/  get faxing.tar.gz
It has samples for a modem using port /dev/ttySL0, which must be changed to match your modem's port.

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------


```
It seems that the usb Modem has at least been detected...

Furthermore:

lsusb said:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 03f0:7d04 Hewlett-Packard DeskJet F2100 Printer series
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0572:1329 Conexant Systems (Rockwell), Inc. 
Bus 004 Device 002: ID 08d4:0003 Fujitsu Siemens Computers 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I don't think the Modem is properly installed because it's not listet in my Network Connections or in any other way.

I got a Vendor-CD packaged with the modem wich contains the following:
 0 -r-------- 1 henrik henrik     0 Apr 30  2007 BUGS
 1 -r-------- 1 henrik henrik   298 Jun  7  2007 CHANGES
11 -r-------- 1 henrik henrik 10601 Mai 10  2007 cnxtmodem.spec.in
 4 -r-------- 1 henrik henrik  3850 Mai  1  2007 config.mak
 2 dr-x------ 1 henrik henrik  2048 Jul  1  2011 debian
13 -r-------- 1 henrik henrik 13279 Jun  7  2007 dgcmodem.spec
 4 -r-------- 1 henrik henrik  3835 Mai  1  2007 INSTALL
 3 -r-------- 1 henrik henrik  2512 Jun  3  2007 LICENSE
14 -r-------- 1 henrik henrik 14070 Jun  3  2007 makefile
 2 dr-x------ 1 henrik henrik  2048 Jul  1  2011 modules
 2 dr-x------ 1 henrik henrik  2048 Jul  1  2011 packages
 1 -r-------- 1 henrik henrik   991 Jun  7  2007 README
 2 dr-x------ 1 henrik henrik  2048 Jul  1  2011 scripts


What can i do now? Linuxant.com seems to be offline.
Can i compile the vendor-files into my kernel? (I never ever did that before :) )

Thanks

Henrik

---

### Post by hankoor on 2013-12-05
Linuxant is no longer down.
I will try out for myself to get the Modem running.

Henrik

---

