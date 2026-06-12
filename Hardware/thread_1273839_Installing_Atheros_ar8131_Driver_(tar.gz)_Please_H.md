---
title: "Installing Atheros ar8131 Driver (tar.gz) Please Help"
date: 2009-09-23
forum: Hardware
---

### Post by del337er on 2009-09-23
Ok guys, I just installed Ubuntu on my Aspire 1 laptop and it wouldn't recognize my ethernet port (Atheros ar8131 PCI-E Gigabit Ethernet). I was told to download and install the driver for that product, so I did. [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (AR81Family Linux Driver) The problem is, im not sure how to install the driver. I know how to decompress tar.gz files, but beyond that I don't know much. The README file that was included isn't much help because i don't understand it.:( (I attached it, maybe you can understand it better than me.) I am somewhat a newbie to Linux, so please explain thoroughly. Thanks.

---

### Post by chris1950 on 2009-09-23
> **del337er said:**
> Ok guys, I just installed Ubuntu on my Aspire 1 laptop and it wouldn't recognize my ethernet port (Atheros ar8131 PCI-E Gigabit Ethernet). I was told to download and install the driver for that product, so I did. [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (AR81Family Linux Driver) The problem is, im not sure how to install the driver. I know how to decompress tar.gz files, but beyond that I don't know much. The README file that was included isn't much help because i don't understand it.:( (I attached it, maybe you can understand it better than me.) I am somewhat a newbie to Linux, so please explain thoroughly. Thanks.


Go here it should help as it gives a step by step. [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html) You said you know how to decompress so start with step #2.:)

---

### Post by del337er on 2009-09-23
Wow thanks so much this is just what i needed, i am dual booting Windows and Ubuntu so i cant check it right now. Lol, be right back:)

---

### Post by chris1950 on 2009-09-23
> **del337er said:**
> Wow thanks so much this is just what i needed, i am dual booting Windows and Ubuntu so i cant check it right now. Lol, be right back:)

Basically what you are doing is creating a install package from source code and installing it. Good luck

---

### Post by del337er on 2009-09-23
Ok, in the tutorial you linked me to it told me to input the following command to configure the script:
 
~/dls/pkg$ ./configure

but I got this error when I pressed enter:

bash: /home/del337er/dls/pkg$: No such file or directory


Why is there a $ after the directory pkg? What does it mean? Im sorry but im a real noob to this so please expain:confused:

---

### Post by chris1950 on 2009-09-23
> **del337er said:**
> Ok, in the tutorial you linked me to it told me to input the following command to configure the script:
 
~/dls/pkg$ ./configure

but I got this error when I pressed enter:

bash: /home/del337er/dls/pkg$: No such file or directory


Why is there a $ after the directory pkg? What does it mean? Im sorry but im a real noob to this so please expain:confused:
Refer to step 1 and reread.
What is the name of the package it created when you unpacked the file? you need to name the package
What happens after unpacking, depends on the package, but in most cases a directory with the package's name is created. The newly created directory goes under the directory where you are right now. To be sure, you can give the ls command:
         me@puter: ~/dls$ **ls**
        pkg pkg.tar.gz
        me@puter: ~/dls$

Maybe this is easier to understand

  	 	 	 	 	 	  ** How to install Linux / UNIX *.tar.gz tarball files**

  ** # 1: Uncompress tarball**

 To uncompress them, execute the following command(s) depending on the extension:
$ tar zxf file.tar.gz
$ tar zxf file.tgz
$ tar jxf file.tar.bz2
$ tar jxf file.tbz2

Now change directory
$ ls
$ cd path-to-software/
 **# 2: Build and install software**

 Generally you need to type 3 commands as follows for building and compiling software:
# ./configure
# make
# make install
 Where,
 
[LIST]
[*]./configure will configure the 	software to ensure your system has the necessary functionality and 	libraries to successfully compile the package  	
[*]make will compile all the source 	files into executable binaries.  	
[*]Finally, make install will install the binaries and any 	supporting files into the appropriate locations.  	
[/LIST]
 **# 3: Read INSTALL / README file**

 Each tarball comes with installation and build instructions. Open INSTALL or README file for more information:
$ vi INSTALL

---

### Post by NJC on 2009-09-24
del337er, which version of Ubuntu are you trying to install. I went through compiling tar files from source code for my Atheros card as well - but only on Ubuntu 8.04 LTS. After installing 9.04 it properly detected my network.

---

### Post by del337er on 2009-09-25
I have 9.04 jaunty Jackalope

---

### Post by NJC on 2009-09-25
FWIW lspci shows this as my network adapter:

01:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)

It worked "out of the box" in 9.04 but not in 9.10 Karmic (Alpha 6).

---

### Post by del337er on 2009-10-01
yes thats the thing, i figured out that my network adapter was: 
01:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)
but i have 9.04, and no "out of the box" working:(

---

### Post by northd_tech on 2009-10-27
I have installed Ultimate Ubuntu 2.3 (in both 32-bit and 64-bit versions, based on Jaunty Jackalope 9.04) on a Toshiba Satellite P505D with the Atheros AR8132 Ethernet NIC.  I never got it to work with the 64-bit OS, but a kernel update just seems to have quietly fixed the problem that I had with the older 2.6.28-13 through 2.6.28-15 kernels.

There is a "driver" available from Atheros here for the 81xx family:

[http://www.chipdrivers.com/download-get/786/191/36/](http://www.chipdrivers.com/download-get/786/191/36/)

[http://www.chipdrivers.com/chipset/netw ... 132/linux/]("http://www.chipdrivers.com/chipset/network-adapter/atheros/ar8132/linux/")

Unfortunately, I never got that to build or install- there were several errors about function calls IIRC. This Atheros AR8132 Ethernet does appear to work in the newer kernel "2.6.28-16" only though.

Actually, it looks like the Ethernet is showing up as "Attansic" rather than "Atheros" for whatever reason- the LiveDVD may have done this during install- I don't remember any messages about it.
-----------------------------------------------------------
15: PCI 400.0: 0200 Ethernet controller
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1969_1062
  Unique ID: YmUS.xQq8Ov29x34
  Parent ID: H0_h.AQdh0Ungjl1
  SysFS ID: /devices/pci0000:00/0000:00:06.0/0000:04:00.0
  SysFS BusID: 0000:04:00.0
  Hardware Class: network
  Model: "Attansic Ethernet controller"
  Vendor: pci 0x1969 "Attansic Technology Corp."
  Device: pci 0x1062 
  SubVendor: pci 0x1179 "Toshiba America Info Systems"
  SubDevice: pci 0xff50 
  Revision: 0xc0
  Memory Range: 0xf0300000-0xf033ffff (rw,non-prefetchable)
  I/O Ports: 0xb000-0xbfff (rw)
  IRQ: 5 (no events)
  Module Alias: "pci:v00001969d00001062sv00001179sd0000FF50bc02sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #37 (PCI bridge)

It was a litte strange to see an ethernet card give more trouble than the WiFi setup under Linux, so this Atheros might be one of the more "difficult" NIC's.

---

### Post by nava2 on 2009-11-13
I am also having issues with this card in 9.10, but I cannot find the package to even install it! Does anyone have a copy of this package they could host and post?
 
E: I should clarify, the website appears to be down and I need this package as my karmic installation went haywire.

---

### Post by Zuela on 2009-11-13
Someone can upload the AR81Family-linux-v1.0.0.10.tar.gz file for me? the site isn't working =(

Thanks for the help ^^

---

### Post by pawanspace on 2009-11-16
I am also not able to download the drivers from the link. I have also tried [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) Its not working can any one please please upload the driver!

---

### Post by pawanspace on 2009-11-16
I have also tried [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) Its not working can any one please please upload the driver!

---

### Post by enri2 on 2009-11-19
heeeelllllpppp the website does't work

will this driver work for g31m-es2l rev 2??;)

---

### Post by seccanj on 2009-12-07
Hi,
I had this same problem on an Acer Aspire 5739G and was able to fix it without installing these separate drivers, as the network adapter is already supported in the latest kernel.
The fix was to simply add an option to GRUB.

Read the complete procedure here:  [http://ubuntuforums.org/showpost.php?p=8446793&postcount=12](http://ubuntuforums.org/showpost.php?p=8446793&postcount=12)

Hope this helps.
Roberto

---

### Post by Slotkenov on 2009-12-21
And I'm also looking for that driver. The download page is still down. I sent them a mail telling them their download page is down. They said they would fix it, but that was two weeks ago.

Somebody who has those drivers able to post them?

That would be great.

---

### Post by deejc on 2010-01-03
> **seccanj said:**
> Hi,
I had this same problem on an Acer Aspire 5739G and was able to fix it without installing these separate drivers, as the network adapter is already supported in the latest kernel.
The fix was to simply add an option to GRUB.

Read the complete procedure here:  [http://ubuntuforums.org/showpost.php?p=8446793&postcount=12](http://ubuntuforums.org/showpost.php?p=8446793&postcount=12)

Hope this helps.
Roberto

I had this issue with a Foxconn NetBox Nt-i330
Fantastic .. one quick edit, Reboot .. working!

Thanks!

---

### Post by Bridgette on 2010-01-15
Hi
I found this the driver website really hard to get the file from but eventually did, im really new to Ubuntu so this is a big learning curve for me, even viewing files and mounting USB drives etc as well as just the basic functions I have leanrt
I have the driver file and have put in a directory i created and unpacked it, went into the src directory and did a make install (hey this is all new) and get a cannot find compiler error, did a #less Makefile and its an error comming from the makefile I think, if anyone could help me that would be great started learning command lines around one week ago, running KK 9.10 server, thnaks
 
Bree
 
Its a steep learning curve
 
:)

---

### Post by mrbox on 2010-04-13
People,
Just for future reference, I had the same problem with debian 4 etch.
I have a Gigabyte motherboard G31M-ES2L with Atheros AR8131 LAN and now it's working fine.
Here is what a did:

Got the driver:
===========
[http://partner.atheros.com/Download.aspx?id=125](http://partner.atheros.com/Download.aspx?id=125)
  detail: when I got it by Linux and tried to extract I got error. So I needed to got by Windows and extract with winrar;

then: Copy the entire extracted folder driver  to your linux (anywhere);
 and: loging with root, go to your folder driver and type:
make
make install

-reboot your system!

that's all.

---

### Post by littlebigman on 2011-07-15
> **mrbox said:**
> Got the driver

The link no longer works, and it seems like Atheros was bought by Qualcomm. Their site doesn't include a section from which to download the driver.

I googled for it, but found nothing available.

Does someone know where to find it?

Thank you.

---

### Post by Slotkenov on 2011-07-15
I still have them on my computer.

I've attached them in this post.

---

### Post by littlebigman on 2011-07-15
Thanks, but decompression fails:
> 
/var/tmp# tar xzvf ./AR81Family-linux-v1.0.1.6.tar.gz 
atl1e.7
atl1e.spec
at_osdep.h
copying
dkms.conf
ldistrib.txt
Makefile
pci.updates
readme
release_note.txt
src/
src/atl1c.h
src/atl1c_ethtool.c
src/atl1c_hw.c
src/atl1c_hw.h
src/atl1c_main.c
src/atl1c_param.c
src/atl1e.h
src/atl1e_ethtool.c
src/atl1e_hw.c
src/atl1e_hw.h
src/atl1e_main.c
src/atl1e_param.c
src/at_common.h
src/at_common_main.c
src/at_osdep.h
src/kcompat.c
src/kcompat.h
src/kcompat_ethtool.c
src/Makefile

gzip: stdin: decompression OK, trailing garbage ignored
src/Module.markers
src/Module.symvers
src/modules.order
tar: Child returned status 2
tar: Error is not recoverable: exiting now


I have another question: If I compile the module on my workstation, will it work on another distro, with a different kernel version? Are modules kernel-specific?

---

### Post by Slotkenov on 2011-07-15
Did you try unpacking it on a Windows machine?

Your last question I can't answer unfortunately, I'm not so much an expert in Linux.

Good luck!

---

### Post by littlebigman on 2011-07-15
> **Slotkenov said:**
> Did you try unpacking it on a Windows machine?

Thanks for the tip. For some reason, it did unpack OK in Windows.

---

### Post by nikkhesal on 2011-07-19
hi 
our link:[http://ftp.nluug.nl/pub/os/Linux/system/kernel/people/mcgrof/ethernet/](http://ftp.nluug.nl/pub/os/Linux/system/kernel/people/mcgrof/ethernet/)
i tested this driver .
is ok
tnx

Good luck!

---

