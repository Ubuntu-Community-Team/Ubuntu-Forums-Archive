---
title: "Ethernet not functioning"
date: 2009-07-07
forum: Hardware
---

### Post by gabemorr on 2009-07-07
So I installed UNR on my brand new (fully hardware functional) HP Mini 110 1030NR. Everything works fine, including the wireless, but the ethenet doesn't work. Seeing as I have a wired network it would be nice to have ethernet working.

Any ideas?

---

### Post by cariboo on 2009-07-07
Could you open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

and paste the output in your next post.

---

### Post by rtb on 2009-07-11
The original poster hasn't responded, but I will.  I also have an HP Mini 110 with an ethernet port that does not work under UNR 9.04.

As I mentioned in [thread 1201415]("http://ubuntuforums.org/showthread.php?t=1201415"), the ethernet port *does* work for HP Mini Mi, HP's flavor of Ubuntu.  It uses the atl1e driver (ver. 1.0.0.6, for kernel 2.6.24-22-lpia).  However, simply modprobe'ing that module in UNR 9.04 did not work.  Nor did adding it to /etc/modules and rebooting.  Under UNR 9.04, I'm currently running kernel 2.6.13-28-generic and version 1.0.0.7-NAPI of the atl1e module.

The output of "lshw -C network" is:

```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:7b:4e:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=172.27.72.43 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:11:b7:98:df:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

I can get other information (lspci, modinfo) for both the non-functioning UNR 9.04 or the functioning HP Mini Mi if needed.

---

### Post by rtb on 2009-07-14
One (and only one) bump.

---

### Post by eighthave on 2009-07-16
I also have a new HP mini 110 1030NR running Ubuntu 9.04 Netbook Remix and all the updates and it also doesn't have functional ethernet.  Wifi works fine, sounds just like the previous posters' problem.  Here's some requested info:

```

root@viageirinho:~ > sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:25:56:7e:35:3a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=10.4.0.184 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 06:b1:3c:f8:73:5a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by Luca_turicci on 2009-08-03
My Mini 110 ethernet doesn't work, either, i can't copy/paste, because i don't have wireless connection here and i'm using another PC.

---

### Post by PhilMize on 2009-08-15
Same as the guys above me, ethernet is not working.

> phil@phil-netbook:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:26:5e:18:49:4b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.100 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d6:fc:15:ec:d5:db
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


---

### Post by rtb on 2009-08-18
A (recent?) lead from the _[hardware support pages]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks")_ references _[this solution]("http://ubuntuforums.org/showpost.php?p=7525735&postcount=2")_ which seems to work for me.  It does require compiling the driver.  I'll reproduce those instructions with a few updates/modifications here:

Retrieve AR81Family-linux-v1.0.0.10.tar.gz from _[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)_.  You'll find a link to it under the heading "AR81Family Linux Driver".  You'll have to accept the Atheros EULA.

Compile, install, and load the module.  From the command line, go to the directory where you saved the package and issue these commands:

```

tar -xvzf AR81Family-linux-v1.0.0.10.tar.gz
cd src
make
sudo make install
sudo modprobe atl1e
```

---

### Post by PhilMize on 2009-08-21
> **rtb said:**
> A (recent?) lead from the _[hardware support pages]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks")_ references _[this solution]("http://ubuntuforums.org/showpost.php?p=7525735&postcount=2")_ which seems to work for me.  It does require compiling the driver.  I'll reproduce those instructions with a few updates/modifications here:

Retrieve AR81Family-linux-v1.0.0.10.tar.gz from _[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)_.  You'll find a link to it under the heading "AR81Family Linux Driver".  You'll have to accept the Atheros EULA.

Compile, install, and load the module.  From the command line, go to the directory where you saved the package and issue these commands:

```

tar -xvzf AR81Family-linux-v1.0.0.10.tar.gz
cd src
make
sudo make install
sudo modprobe atl1e
```




This fixed it. Awesome!

---

### Post by pi4r0n on 2009-08-21
Guys

Can you help me with this please :) I have done some research on GOOGLE but could not find any solution for that :(

> 
gzip: stdin: decompression OK, trailing garbage ignored
src/Makefile
src/Module.symvers
src/modules.order
tar: Child returned status 2
tar: Error exit delayed from previous errorsCheers

pi4r0n

---

### Post by rtb on 2009-08-22
> gzip: stdin: decompression OK, trailing garbage ignoredI did get this error un-tarring the package.  That's a delayed error from an earlier file in the package with "trailing garbage" (whatever that is). In my case, at least, the module still compiled and installed successfully.  

It doesn't inspire great confidence in the vendor's package, I know.  But it seems to work.

For what it's worth, the hardware support pages indicate that the problem with the ethernet port has been resolved with UNR 9.10 (Karmic).  I haven't tried it myself, yet.

I should probably have added that if you compile the driver, you'll have to re-compile with each kernel upgrade.

---

### Post by arch0njw on 2009-09-05
This worked for me.  You're awesome!  Thank you!

Acer Aspire One AOD250-1580

---

### Post by PhilMize on 2009-09-08
I just installed 8.04 LTS and the NIC worked fine after the first boot and has been working just dandy...

Fluke?:)

---

### Post by hughh on 2009-09-29
> **rtb said:**
> A (recent?) lead from the _[hardware support pages]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks")_ references _[this solution]("http://ubuntuforums.org/showpost.php?p=7525735&postcount=2")_ which seems to work for me.  It does require compiling the driver.  I'll reproduce those instructions with a few updates/modifications here:

Retrieve AR81Family-linux-v1.0.0.10.tar.gz from _[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)_.  You'll find a link to it under the heading "AR81Family Linux Driver".  You'll have to accept the Atheros EULA.

Compile, install, and load the module.  From the command line, go to the directory where you saved the package and issue these commands:

```

tar -xvzf AR81Family-linux-v1.0.0.10.tar.gz
cd src
make
sudo make install
sudo modprobe atl1e
```
Hmmm, I'm running into a problem:

```

hugh@Aspire:~/tmp/src$ sudo make install
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/hugh/tmp/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
# remove all old versions of the driver
find /lib/modules/2.6.28-15-generic -name atl1e.ko -exec rm -f {} \; || true
find /lib/modules/2.6.28-15-generic -name atl1e.ko.gz -exec rm -f {} \; || true
install -D -m 644 atl1e.ko /lib/modules/2.6.28-15-generic/kernel/drivers/net/atl1e/atl1e.ko
/sbin/depmod -a || true
install -D -m 644 atl1e.7.gz /usr/share/man/man7/atl1e.7.gz
man -c -P'cat > /dev/null' atl1e || true
man: 
cannot write to /var/cache/man/cat7/atl1e.7.gz in catman mode
atl1e.
hugh@Aspire:~/tmp/src$ 

```Suggestions anyone?

---

### Post by arch0njw on 2009-09-29
> **hughh said:**
> Hmmm, I'm running into a problem:

... snip ...

Suggestions anyone?

Did you try running the modprobe anyway?  I think I got an error too and it worked anyway.

---

### Post by arch0njw on 2010-03-16
Oh, rock!  This has been fixed in 10.04.  I just tried the Alpha 3 of Lucid on a Live Flash and both wired and wireless worked!

---

### Post by wittrup on 2010-05-02
I get the following error for both
make
sudo make install
"Makefile:118: *** Compiler not found. Stop."

Anyone knows how to fix this without working network interface?

---

### Post by wittrup on 2010-05-07
```

sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137
sudo ln -sf /media/external /cdrom
sudo apt-cdrom -m add
sudo apt-get -f install

```
Fixed my errors.

---

### Post by arch0njw on 2010-05-07
wittrup, very nice.  And thank you for sharing your solution.  That kind of follow-up helps make these forums so useful.

---

### Post by _traq_ on 2010-09-18
> **wittrup said:**
> I get the following error for both
make
sudo make install
"Makefile:118: *** Compiler not found. Stop."

Anyone knows how to fix this without working network interface?

I got his error as well.  The commands you posted subsequently didn't work for me - can you explain what you were doing, exactly?
[quote=wittrup]```
sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137
sudo ln -sf /media/external /cdrom
sudo apt-cdrom -m add
sudo apt-get -f install
```[/quote]

or, if anybody else has any advice, please let me know.  thanks

---

