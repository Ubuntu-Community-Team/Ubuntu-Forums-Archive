---
title: "Oops when Installing RocketRaid 2320 drivers in v6.10"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by Erik-NA on 2006-12-03
I am trying to use rocketraid 2320 as RAID-controller in Ubuntu 6.10 with kernel 2.6.17-10-server

I downloaded rr232x-linux-src-1.03-060710.tar from [http://www.highpoint-tech.com/USA/rr2320.htm](http://www.highpoint-tech.com/USA/rr2320.htm)

Make and make install worked (two warnings but no errors) and when I reboot, the kernel is showing an oops

```
 scsi5 : ahci
[42949381.940000]  0:0:0:0: Attached scsi generic sg0 type 0
[42949381.940000]  1:0:0:0: Attached scsi generic sg1 type 0
[42949381.950000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[42949381.950000] sda: Write Protect is off
[42949381.950000] sda: Mode Sense: 00 3a 00 00
[42949381.950000] SCSI device sda: drive cache: write back
[42949381.950000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[42949381.950000] sda: Write Protect is off
[42949381.950000] sda: Mode Sense: 00 3a 00 00
[42949381.950000] SCSI device sda: drive cache: write back
[42949381.950000]  sda: sda1 sda2 sda3 sda4
[42949381.960000] sd 0:0:0:0: Attached scsi disk sda
[42949381.960000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[42949381.960000] sdb: Write Protect is off
[42949381.960000] sdb: Mode Sense: 00 3a 00 00
[42949381.960000] SCSI device sdb: drive cache: write back
[42949381.960000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[42949381.960000] sdb: Write Protect is off
[42949381.960000] sdb: Mode Sense: 00 3a 00 00
[42949381.960000] SCSI device sdb: drive cache: write back
[42949381.960000]  sdb: sdb1 sdb2 sdb3 sdb4
[42949381.980000] sd 1:0:0:0: Attached scsi disk sdb
[42949381.990000] rr232x: module license 'Proprietary' taints kernel.
[42949381.990000] rr232x:0: RocketRAID 232x controller driver v1.03 (Dec  3 2006 15:42:42)
[42949381.990000] BUG: unable to handle kernel paging request at virtual address 63f4d288
[42949381.990000]  printing eip:
[42949381.990000] f88fcdb8
[42949381.990000] *pde = 00000000
[42949381.990000] Oops: 0000 [#1]
[42949381.990000] SMP
[42949381.990000] Modules linked in: rr232x sd_mod sg ahci ata_piix libata scsi_mod thermal processor fan fbcon til
eblit font bitblit softcursor vesafb capability commoncap
[42949381.990000] CPU:    0
[42949381.990000] EIP:    0060:[<f88fcdb8>]    Tainted: P      VLI
[42949381.990000] EFLAGS: 00010a03   (2.6.17-10-server #2)
[42949381.990000] EIP is at f8e22123f+0x18/0x50 [rr232x]
[42949381.990000] eax: 00000000   ebx: f8923580   ecx: f8923060   edx: 6b62a1c8
[42949381.990000] esi: f8923580   edi: ffffffed   ebp: 000005f0   esp: dfa13e50
[42949381.990000] ds: 007b   es: 007b   ss: 0068
[42949381.990000] Process modprobe (pid: 915, threadinfo=dfa12000 task=df81ca90)
[42949381.990000] Stack: f88faeb4 f891bb4a f8923060 f8923082 00000000 00000000 0000000f f8922fa0
[42949381.990000]        f8923100 00000000 dfa12000 c046e86c c046e870 dfa13eac c02d7a8f 00000001
[42949381.990000]        df81ca90 c011b170 00100100 00200200 df813560 df813568 00000000 f8923580
[42949381.990000] Call Trace:
[42949381.990000]  <f88faeb4> hpt_detect+0x54/0x780 [rr232x]  <c02d7a8f> wait_for_completion+0x8f/0xd0
[42949381.990000]  <c011b170> default_wake_function+0x0/0x10  <f8837041> init_this_scsi_driver+0x41/0x102 [rr232x]
[42949381.990000]  <c013bb28> sys_init_module+0x148/0x19c0  <c01e87f0> pci_bus_read_config_byte+0x0/0x80
[42949381.990000]  <c0102f8b> sysenter_past_esp+0x54/0x75
[42949381.990000] Code: 5e e9 3d c3 ff ff 8d b6 00 00 00 00 8d bc 27 00 00 00 00 8b 54 24 04 31 c0 8b 4c 24 08 3b 1
5 e8 30 92 f8 7d 32 8d 14 92 c1 e2 02 <66> 8b 82 c0 30 92 f8 66 89 01 66 8b 82 c2 30 92 f8 66 89 41 02
[42949381.990000] EIP: [<f88fcdb8>] f8e22123f+0x18/0x50 [rr232x] SS:ESP 0068:dfa13e50
```

Can anyone tell me what is wrong and what to do?

---

### Post by Erik-NA on 2006-12-06
Found that I am not alone with the problem

[http://www.justlinux.com/forum/showthread.php?t=147539]("http://www.justlinux.com/forum/showthread.php?t=147539")

Seems to be a driver issue. The post above is from October and it is strange that highpoint-tech hasn't released an updated driver.

I tried to install v6.06 but my motherboard (P5BV-V)is using the JMicron controller for the CD/DVD-rom which apparently is not supported in Drapper Drake (v6.06)

---

### Post by Erik-NA on 2006-12-10
The driver works with an updated kernel, 2.6.19, and now the driver works fine. Problem is solved

---

### Post by Erik-NA on 2006-12-26
Finnally, after a very long time I found the right way to install the driver on edgy (server-version) with 2.6.17-10 kernel.
 
On a clean install I did the following based on the guide: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
```
user@host:~$ sudo –i
password:
root@nas:~# vi /etc/apt/sources.list
```I added the following to the end:```
deb http://se.archive.ubuntu.com/ubuntu/ edgy universe 
deb-srcc http://se.archive.ubuntu.com/ubuntu/ edgy universe
```
On Ubuntu 6.10, /bin/sh is a symlink to /bin/dash by default. /bin/dash seems to make problems when you compile software from the sources, at least I had that impression. That's why I make /bin/sh a symlink to /bin/bash instead.
```
root@nas:~# rm -f /bin/sh
root@nas:~# ln -s /bin/bash /bin/sh

```Install Required Packages For Kernel Compilation
```
root@nas:~# apt-get update
root@nas:~# apt-get install kernel-package libncurses5-dev fakeroot wget bzip2 initrd-tools build-essential
```

Download The Kernel Sources:
```
root@nas:~# cd /usr/src
root@nas:~# apt-get install linux-headers-2.6.17-10-server
```
Create a symbolic link to the sources. If you do not, the driver will not work and you have also to do more when you run make.
```
root@nas:~# ln -s linux-headers-2.6.17-10-server linux
```

Donwload, compile and install the driver
```
root@nas:~# mkdir rocketraid
root@nas:~# cd rocketraid
root@nas:~# wget http://www.highpoint-tech.com/BIOS_Driver/rr232x/Linux/rr232x-linux-src-1.03-060710.tar.gz
root@nas:~# tar xfvz rr232x-linux-src-1.03-060710.tar.gz
root@nas:~# cd rr232x-linux-src-1.03/product/rr232x/linux
root@nas:~# make install

```

---

### Post by zindine on 2007-04-09
Thanks for the step by step guide. 

I was able to make my RocketRaid 2320 work on Ubuntu 7.04 following the guide and the live CD.

---

### Post by seer_tenedos on 2007-04-23
No matter what i do i can't get the drivers to work on 7.04.  I have tried it as a module but modprobe hangs when i try to load the module and the compiling the drivers into the kernel did not seem to help either.   I am using version 1.05 of the 2320 drivers.  Can anyone help with with a working module for the 7.04 kernel or give me any tips on finding and solving the problem?

Chris

---

### Post by zindine on 2007-05-12
Hey Chris,

Are you still stuck? 

Let me know, I will try to give you a hand. 

Zindine

---

### Post by seer_tenedos on 2007-05-13
I have given up for now and switched to opensuse. Maybe i will give it ago again sometime in the future but open suse will do for now.  Thanks for the offer of help.

---

### Post by zindine on 2007-05-13
Are you able to boot directly from a device on the highpoint interface? 

That's my only problem right now. I need to use a separate device (on PATA) to start the ram filesystem. 

Maybe I will try OpenSuse too...

---

### Post by seer_tenedos on 2007-05-13
no i have the system booting off disks on another controller.  The card was jsut adding an extra 8 disks to my system.  My problem was the if i loaded the drivers as a module they never worked.  I got some error compiling them too but they still compiled.  If i compiled the drivers into the kernel then my pc would no longer boot with the kernel reporting that part of my bios is writeable that should not be.

Open suse 10.2 has precompiled driver that you cna downlaod from highpoint and they work perfectly.  I wish they had the same for Ubuntu and then i may not have this problem.  Thats the only reason i switched to open suse.  I would have prefered Ubuntu because i really wanted some of the new drivers for other devices that is built into the new kernel in Ubuntu.

---

### Post by perimere on 2007-05-29
I have a 2320 running a RAID-5 array (no OS just data) under Ubuntu Dapper. The problem I'm experiencing is that I want to add two more disks to the array.  

I've got the disks physically installed fine (visible in the BIOS at boot time), but you need to expand the array through the software management console.

Has anyone managed to get the Highpoint management console working in Ubuntu?

Any ideas would be handy!

Cheers

Adam

---

### Post by Erik-NA on 2007-07-02
> **perimere said:**
> I have a 2320 running a RAID-5 array (no OS just data) under Ubuntu Dapper. The problem I'm experiencing is that I want to add two more disks to the array.  

I've got the disks physically installed fine (visible in the BIOS at boot time), but you need to expand the array through the software management console.

Has anyone managed to get the Highpoint management console working in Ubuntu?

Any ideas would be handy!

Cheers

Adam

You mean CLI htpdraidconf? Yes, I have it working

Here is what I did for installing the CLI management console

After extracting the tar.gz fil I converted the rpms into deb package with the alien command. (You may probably have to install alien). However I attached CLI-Linux-2.3-3-1214 as deb packages to this post.

Create a dir for the files
[PHP]root@nas:~# cd /usr/src/rocketraid
root@nas:/usr/src/rocketraid#mkdir cli
root@nas:/usr/src/rocketraid#cd cli[/PHP]

Download CLI management tool
[PHP]root@nas:/usr/src/rocketraid/cli# wget http://www.highpoint-tech.com/BIOS_Driver/HRM/Linux/CLI-Linux-2.3-3-1214.tgz
root@nas:/usr/src/rocketraid/cli# tar xfvz CLI-Linux-2.3-3-1214.tgz[/PHP]

Convert rpm to deb package with alien (or use attached files)
[PHP]root@nas:/usr/src/rocketraid/cli# alien --scripts hptsvr-3.13-4.i586.rpm
hptsvr_3.13-5_i386.deb generated
root@nas:/usr/src/rocketraid/cli# alien --scripts hptraidconf-2.3-3.i386.rpm
hptraidconf_2.3-4_i386.deb generated[/PHP]

Install the packages
[PHP]root@nas:/usr/src/rocketraid/cli# dpkg &#8211;i hptsvr_3.13-5_i386.deb
root@nas:/usr/src/rocketraid/cli# dpkg &#8211;i hptraidconf_2.3-4_i386.deb[/PHP]

Tell the applikation which driver to use
[PHP]root@nas:/usr/src/rocketraid/cli# echo rr232x > /etc/hptcfg[/PHP]

Start the deamon manually.
[PHP]root@nas:/usr/src/rocketraid# hptsrv[/PHP]

Done!

Now you can connect with the hptraidconf command, see the pdf for how it works.

---

