---
title: "nForce 590 chipset and ubuntu 7.04"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by Naike on 2007-08-27
It just doesnt work and i havnt found a solution yet, I hope that someone helpful can help me!
The built-in ethernet card doesnt work, it does recognice it ang gets the ip and stuff, but just no connection.
It didnt even work on 6.06 lts

---

### Post by eokorie on 2007-08-27
strange, my copy works very well.  I have the GA-M59SLI-S5 motherboard and Ubuntu starts up pretty well.  Are you having problems with installing it?

---

### Post by Naike on 2007-08-27
oh man cant believe it lol i forgot to mention the actual problem.
I cant get the built-in ethernet card to work.

---

### Post by dougfractal on 2007-08-27
can you post this

> uname -r
sudo lshw -businfo
ifconfig -a

---

### Post by Naike on 2007-08-27
Yeah sure.
[http://koti.mbnet.fi/memleak/aaa.txt](http://koti.mbnet.fi/memleak/aaa.txt)

or here:


> 2.6.20-15-generic
> Bus info        Device     Class          Description
=====================================================
                           system         System Product Name
                           bus            CROSSHAIR
                           memory         BIOS
cpu@0                      processor      AMD Athlon(tm) 64 X2 Dual Core Process
                           memory         L1 cache
                           memory         L2 cache
                           memory         System Memory
                           memory         None
                           memory         None
                           memory         None
                           memory         None
pci@00:00.0                memory         C51 Host Bridge
pci@00:00.1                memory         C51 Memory Controller 0
pci@00:00.2                memory         C51 Memory Controller 1
pci@00:00.3                memory         C51 Memory Controller 5
pci@00:00.4                memory         C51 Memory Controller 4
pci@00:00.5                memory         C51 Host Bridge
pci@00:00.6                memory         C51 Memory Controller 3
pci@00:00.7                memory         C51 Memory Controller 2
pci@00:04.0                bridge         C51 PCI Express Bridge
pci@01:00.0                display        nVidia Corporation
pci@00:08.0                memory         MCP55 Memory Controller
pci@00:09.0                bridge         MCP55 LPC Bridge
pci@00:09.1                bus            MCP55 SMBus
pci@00:09.2                memory         MCP55 Memory Controller
pci@00:0a.0                bus            MCP55 USB Controller
usb@1           usb1       bus            OHCI Host Controller
usb@1:1                    printer        DeskJet 920C
usb@1:3                    bus            G11 Keyboard
usb@1:3.1                  input          Gaming Keyboard
usb@1:3.2                  generic        Generic USB device
usb@1:3.4                  input          G11 Keyboard
usb@1:4                    input          USB Receiver
usb@1:8                    communication  Bluetooth wireless interface
pci@00:0a.1                bus            MCP55 USB Controller
usb@2           usb2       bus            EHCI Host Controller
usb@2:5         scsi8      storage        Flash Disk
scsi@8:0.0.0    /dev/sdb   disk           Flash Disk
                /dev/sdb   disk
                /dev/sdb1  disk           FAT16 partition
pci@00:0c.0                storage        MCP55 IDE
ide@0           ide0       bus            IDE Channel 0
ide@0.0         /dev/hda   disk           TSSTcorpCD/DVDW SH-S182D
                /dev/hda   disk
pci@00:0d.0     scsi0      storage        MCP55 SATA Controller
scsi@0:0.0.0    /dev/sda   disk           ST3250620AS
scsi@0:0.0.0,1  /dev/sda1  disk           HPFS/NTFS partition
scsi@0:0.0.0,2  /dev/sda2  disk           Extended partition
                /dev/sda5  disk           HPFS/NTFS partition
                /dev/sda6  disk           Linux swap / Solaris partition
                /dev/sda7  disk           Linux filesystem partition
pci@00:0d.1     scsi2      storage        MCP55 SATA Controller
pci@00:0d.2     scsi4      storage        MCP55 SATA Controller
pci@00:0e.0                bridge         MCP55 PCI bridge
pci@02:0b.0                bus            TSB43AB22/A IEEE-1394a-2000 Controller
pci@00:0e.1                multimedia     MCP55 High Definition Audio
pci@00:10.0     eth0       bridge         MCP55 Ethernet
pci@00:11.0     eth1       bridge         MCP55 Ethernet
pci@00:12.0                bridge         MCP55 PCI Express bridge
pci@00:16.0                bridge         MCP55 PCI Express bridge
pci@04:00.0     scsi6      storage        SiI 3132 Serial ATA Raid II Controller
pci@00:17.0                bridge         MCP55 PCI Express bridge
pci@00:18.0                bridge         K8 [Athlon64/Opteron] HyperTransport T
pci@00:18.1                bridge         K8 [Athlon64/Opteron] Address Map
pci@00:18.2                bridge         K8 [Athlon64/Opteron] DRAM Controller
pci@00:18.3                bridge         K8 [Athlon64/Opteron] Miscellaneous Co
> eth0      Link encap:Ethernet  HWaddr 00:1A:92:98:8E:A8
          inet6 addr: fe80::21a:92ff:fe98:8ea8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:585566 (571.8 KiB)  TX bytes:7478 (7.3 KiB)
          Interrupt:17 Base address:0x6000

eth1      Link encap:Ethernet  HWaddr 00:1A:92:98:90:6C
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x8000

eth0:avah Link encap:Ethernet  HWaddr 00:1A:92:98:8E:A8
          inet addr:169.254.8.135  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x6000

eth1:avah Link encap:Ethernet  HWaddr 00:1A:92:98:90:6C
          inet addr:169.254.7.99  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3696 (3.6 KiB)  TX bytes:3696 (3.6 KiB)

---

### Post by dougfractal on 2007-08-27
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/131737](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/131737)
> network device (nVidia MCP55, forcedeth) stops sending packets

Affecting: 	linux-source-2.6.15 (Ubuntu)

There's a kernel bug.
Try to update the kernel.

sudo ifdown eth0
sudo ifdown eth1
sudo ifup eth1

hopefully you get somesort of ethernet.
ping -c 4 google.com

sudo apt-get update
sudo aptitude upgrade linux-generic

reboot

sudo apt-get upgrade

---

### Post by Naike on 2007-08-27
I couldnt get a connection.
what can i do,  and does ubuntu (i use kubuntu) have a working kernel?

---

### Post by dougfractal on 2007-08-27
Either use a usb device and manually install kernel new kernel

[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux_2.6.20.16.28.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux_2.6.20.16.28.1_i386.deb)


move to package location
> sudo dpkg -i linux_2.6.20.16.28.1_i386.deb

or try and install Gusty Tribe 5. A pretty stable pre-release. There will be constant upgrades until final release.

---

### Post by Naike on 2007-08-27
I saved that file on my usb, and then copied to my home folder.
And in the command line:

cd --

and that command you gave me, it loaded but it didnt help either.

---

### Post by dougfractal on 2007-08-27
To run the the new kernel you would have  to reboot.  Of course  if you are on a live CD you will lose the changes.  (Unless you have a persistent mode usbsitck)  

```
uname -r
```

---

### Post by Naike on 2007-08-28
I did reboot, and i dont use a live CD.

Weird is that the command " cd /home/naike/" didnt work.
Ill post my kerler ver. now.

---

### Post by Naike on 2007-08-28
This is what happens.
> nikke@nikke-crosshair:~$ cd /home/nikke/Kernel
nikke@nikke-crosshair:~/Kernel$ sudo dpkg -i linux_2.6.20.16.28.1_i386.deb
Password:
(Reading database ... 75265 files and directories currently installed.)
Preparing to replace linux 2.6.20.16.28.1 (using linux_2.6.20.16.28.1_i386.deb)
...
Unpacking replacement linux ...
Setting up linux (2.6.20.16.28.1) ...

But still the kernel version is the old one even after i reboot.

---

### Post by dougfractal on 2007-08-28
**grub**


> sudo gedit /boot/grub/menu.lst


copy YOUR 
> title           Ubuntu, kernel 2.6.15-generic 
root            XXXXX
kernel          /boot/vmlinuz-2.6.XXXXXXXXXX
root=UUID=XXXXXXXXXXXXXXXXXXX ro quiet splash
initrd         /boot/initrd.img-2.6.XXX-generic
quiet

> ls /boot   # to list the new kernel
paste and add the new kernel values
> title         Ubuntu, kernel 2.6.20.***


If the networking works for the new kernel then > sudo apt-get update &&  sudo apt-get upgrade

---

### Post by Naike on 2007-08-28
I run that first command i get something like:
sudo: gedit: command not found

And i didnt quite get your instructions but ill try when you correct that first command.

---

### Post by Marat Galiev on 2007-08-28
use nano  editor.
like this:
**sudo nano /boot/grub/menu.lst**

---

### Post by Naike on 2007-08-28
I dont know what to do.

so first i use nano editor (works)

Then i copy that first quote.

this is how far i get and then i dont get what to do.
I'm really sorry that I'm pretty newb at this.
And how can i save the list?

---

### Post by dougfractal on 2007-08-28
can you post
> 
ls /boot

cat /boot/grub/menu.lst

then I can show you

---

### Post by Naike on 2007-08-28
Well, umm I installed Ubuntu gutsy, but in the live cd the ethernet didnt work either.
Now i installed XP again and it overwrote the boot list thing so i cant get on ubuntu now.
How can i fix this?

---

### Post by dougfractal on 2007-08-28
**Grub**
[http://ubuntuforums.org/showpost.php?p=3181703&postcount=6](http://ubuntuforums.org/showpost.php?p=3181703&postcount=6)
> Restoring GRUB
You will either need a Super GRUB Disk or your Ubuntu disc, and as long as your drive references are fine everywhere, it will only take a couple of commands to fix things. You will need to decide if GRUB is going in the MBR (master boot record of the drive) or on the partition. If Ubuntu is sharing a drive with Windows, choosing MBR will get back the GRUB menu and let you boot either. If Ubuntu is installed on another drive, and you use a boot manager to boot your partitions, then choosing to install GRUB on the partition may be better. If one doesn't work, then try the other. Simply enter the first command followed by the other. To get to the command prompt on the Super GRUB Disk, type C; to get to the grub> prompt on your Ubuntu CD, go to command line and enter the following before entering the GRUB restore commands:

grub

Restore GRUB to the Master Boot Record (eg: 1st partition on 2nd drive)
root (hd1,0)
setup (hd1)

Restore GRUB to a Partition (eg: 1st partition on 2nd drive)
root (hd1,0)
setup (hd1,0)

Note sure? Find the Partition where GRUB is
At the grub> prompt enter:
find /boot/grub/stage1

[B]
Networking[/B] 
from what I understand is, you have an active network but no dhcp connection from ubuntu.
If you used a static ip (ie the same values from XP) can you ping your hub.
If so  add the hub's ip to the dns section in  NetworkManager
> gksu network-admin

---

### Post by Naike on 2007-08-28
I'll try.

---

### Post by Naike on 2007-08-28
I copied my ips and stuff form XP 100% right.
But still i get no connection.
And this has the new kernel...

---

### Post by dougfractal on 2007-08-29
please attach hard data

> ifconfig > network.txt
route >>  network.txt
cat /etc/resolv.conf >> network.txt
ping -c2 64.233.183.104   >> network.txt #  [www.google.com](www.google.com) 
ping -c2 [www.google.com](www.google.com)  >> network.txt 
cat network.txt

---

### Post by Shin_Gouki2501 on 2007-08-29
Dns?

---

### Post by Naike on 2007-08-29
I did put the 2 dns adresses as in windows, ill try that command in a couple of minutes.
[http://koti.mbnet.fi/memleak/abc.txt](http://koti.mbnet.fi/memleak/abc.txt)

> naike@naike-desktop:~$ ifconfig > network.txt
naike@naike-desktop:~$ route >> network.txt
naike@naike-desktop:~$ cat /etc/resolv.conf >> network.txt
naike@naike-desktop:~$ ping -c2 64.233.183.104 >> network.txt # [www.google.com](www.google.com)
connect: Network is unreachable
naike@naike-desktop:~$ ping -c2 [www.google.com](www.google.com) >> network.txt
ping: unknown host [www.google.com](www.google.com)
naike@naike-desktop:~$ cat network.txt
eth0      Link encap:Ethernet  HWaddr 00:1A:92:98:8E:A8  
          inet addr:62.178.160.120  Bcast:62.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21a:92ff:fe98:8ea8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:424315 (414.3 KB)  TX bytes:4648 (4.5 KB)
          Interrupt:17 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:1A:92:98:90:6C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x4000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1536 (1.5 KB)  TX bytes:1536 (1.5 KB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
62.0.0.0        *               255.0.0.0       U     0      0        0 eth0
nameserver 195.34.133.21
nameserver 195.34.133.22

---

### Post by swappa on 2007-08-31
Got the exact same thing with GB tribe 5....works fine in Feisty

---

### Post by dougfractal on 2007-08-31
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
62.0.0.0 * 255.0.0.0 U 0 0 0 eth0
nameserver 195.34.133.21
nameserver 195.34.133.22


It looks as if your ifconfig and route are wrong, no default.

the netmask means the nameserver must look like 62.34.133.21 which it ain't.
(I'm no nework expert) but I think you need to Bcast:255.255.255.255 Mask:0.0.0.0 

and your route
default         XXX.XXX.XXX.XXX    0.0.0.0         UG    0      0        0 eth0

to help you more you need to tell me if you have a network hub with dhcpd server or DSL via pppoe . If tell me you ISP and I can help.
If hub what is its IP.

Your nForce is fine just misconfigured.

my route example (do not use)
```
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.62.0    *               255.255.255.0   U     0      0        0 eth2
link-local      *               255.255.0.0     U     1000   0        0 eth2
default         192.168.62.1    0.0.0.0         UG    0      0        0 eth2
```

---

### Post by Naike on 2007-09-12
Well I dont use a hub, my cable is directly connected to the wall.
ISP?? Isnt it the internet provider or something?
If so its Chello Austria or with the other name UPC Telekabel.

Can you specify some more, i know 0 about networking...

---

### Post by dougfractal on 2007-09-12
Looking at the posts, You have had quite a journey.

> sudo ifdown eth0
sudo dhcpd eth0
ifconfig
route

Will probally not work, but test anyway
> sudo ifdown eth1
sudo dhcpd eth1
ifconfig
route

please post the outputs

---

