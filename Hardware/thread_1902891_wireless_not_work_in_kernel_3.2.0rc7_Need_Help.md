---
title: "wireless not work in kernel 3.2.0rc7? Need Help"
date: 2012-01-01
forum: Hardware
---

### Post by upin on 2012-01-01
after installed kernel3.2.0Rc7 for my Ubuntu 11.10 and then i restart Ubuntu, wireless doesn't work. How to fix this problem? Thank you

---

### Post by fdrake on 2012-01-01
3.2.0Rc7 is not considered a stable kernel yet why did you bother installing it? I doubt you will find a lot of help if it's a module-kernel related problem! before we proceed, can you boot into an older kernel at the grub menu time? is the wifi working with the old one? if not check this commands and post here the results:
```

lshw -c network
ifconfig
iwconfig
rfkill list all

```

---

### Post by upin on 2012-01-01
> **fdrake said:**
> 3.2.0Rc7 is not considered a stable kernel yet why did you bother installing it? I doubt you will find a lot of help if it's a module-kernel related problem! before we proceed, can you boot into an older kernel at the grub menu time? is the wifi working with the old one? if not check this commands and post here the results:
```

lshw -c network
ifconfig
iwconfig
rfkill list all

```Thanks for your helping! this is my result 
```
tux@tux-pc:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: b8:ac:6f:79:68:ec
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:5000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff memory:f0420000-f043ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
tux@tux-pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:79:68:ec  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17496 (17.4 KB)  TX bytes:17496 (17.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:171.243.213.232  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1037 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:790316 (790.3 KB)  TX bytes:101080 (101.0 KB)

tux@tux-pc:~$ iwconfig
ppp0      no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

tux@tux-pc:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes

```

---

### Post by fdrake on 2012-01-01
> 
tux@tux-pc:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes


check the wifi switch , it must be off. Do you have a wireless option int the bios to turn it on?

also try this command :
```

sudo ifconfig wlan0 up
rfkill list all

```
and post here the output

---

### Post by upin on 2012-01-01
i turned it off!
```
tux@tux-pc:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
tux@tux-pc:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
tux@tux-pc:~$ 

```

---

### Post by fdrake on 2012-01-01
can you post again the results of "ifconfig" and "iwconfig" . Now the device is hardware-active! we just need to enable it with the system.

---

### Post by upin on 2012-01-01
> **fdrake said:**
> can you post again the results of "ifconfig" and "iwconfig" . Now the device is hardware-active! we just need to enable it with the system.

```
tux@tux-pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:79:68:ec  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::baac:6fff:fe79:68ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7195955 (7.1 MB)  TX bytes:6448980 (6.4 MB)
          Interrupt:42 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70595 (70.5 KB)  TX bytes:70595 (70.5 KB)

tux@tux-pc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tux@tux-pc:~$ 

```

---

### Post by fdrake on 2012-01-01
```

sudo rfkill unblock all
rfkill list all
ifconfig
iwconfig

```
any changes?

---

### Post by upin on 2012-01-01
> **fdrake said:**
> ```

sudo rfkill unblock all
rfkill list all
ifconfig
iwconfig

```
any changes?
```
[sudo] password for tux: 
tux@tux-pc:~$ sudo rfkill unblock all
tux@tux-pc:~$ rfkill list all
0: dell-wifi: Wireless LAN
	[COLOR="Red"]Soft blocked: no[/COLOR]
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
tux@tux-pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:79:68:ec  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::baac:6fff:fe79:68ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78805 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56004367 (56.0 MB)  TX bytes:38124134 (38.1 MB)
          Interrupt:42 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1827 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70798 (70.7 KB)  TX bytes:70798 (70.7 KB)

tux@tux-pc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tux@tux-pc:~$ 

```

---

### Post by fdrake on 2012-01-01
you will need also to load the right driver for your card. question: was the driver working with your previous kernel or not?

anyway the instructions to install your driver are here:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

download the zip file and follow the directions. if you have any problem let us know.

zip file:[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by upin on 2012-01-01
> **fdrake said:**
> you will need also to load the right driver for your card. question: was the driver working with your previous kernel or not?

anyway the instructions to install your driver are here:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

it work fine with old kernel 3.0! i tried to install but it show me the command 
```
tux@tux-pc:~$ sudo apt-get --reinstall install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-evolution python-numpy liblapack3gf python-tz libblas3gf libgfortran3
  python-beautifulsoup
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,155 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 331155 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu4 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu4_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu4) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 3.2.0-030200rc7-generic
Building for architecture x86_64
Building initial module for 3.2.0-030200rc7-generic
Error! Bad return status for module build on kernel: 3.2.0-030200rc7-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-030200rc7-generic
[COLOR="Red"]W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-1.fw for module r8169[/COLOR]

```

---

### Post by fdrake on 2012-01-01
did you install these pckgs before installing :
```

sudo apt-get install dkms linux-libc-dev libc6-dev linux-headers-generic linux-headers

```

also what does the log says?
```
less /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log
```

---

### Post by upin on 2012-01-01
> **fdrake said:**
> did you install these pckgs before installing :
```

sudo apt-get install dkms linux-libc-dev libc6-dev linux-headers-generic linux-headers

```

also what does the log says?
```
less /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log
```
i installed linux-headers-3.2.0-030200rc7-generic and linux-headers-3.2.0-030200rc7
Log:
```
DKMS make.log for bcmwl-5.100.82.38+bdcom for kernel 3.2.0-030200rc7-generic (x86_64)
Mon Jan  2 00:17:17 ICT 2012
make: Entering directory `/usr/src/linux-headers-3.2.0-030200rc7-generic'
  LD      /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.c:332:2: error: unknown field ‘ndo_set_multicast_list’ specified in initializer
/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.c:332:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.c:332:2: warning: (near initialization for ‘wl_netdev_ops.ndo_validate_addr’) [enabled by default]
make[1]: *** [/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.2.0-030200rc7-generic'
~
~
~
(END)

```

---

### Post by genbell on 2012-01-08
Download this for i386 architecture

[https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu5/+build/2945147/+files/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu5_i386.deb](https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu5/+build/2945147/+files/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu5_i386.deb)

or this for amd64

[https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu5/+build/2945146/+files/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu5_amd64.deb](https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu5/+build/2945146/+files/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu5_amd64.deb)

---

### Post by finomeno on 2012-02-21
> **genbell said:**
> Download this for i386 architecture

[https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu5/+build/2945147/+files/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu5_i386.deb](https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu5/+build/2945147/+files/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu5_i386.deb)

or this for amd64

[https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu5/+build/2945146/+files/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu5_amd64.deb](https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu5/+build/2945146/+files/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu5_amd64.deb)

Thanks a million, genbell!
This helped me with the final 3.2.0.17.16 kernel installed from [http://ppa.launchpad.net/francisbrwn9/kernels/ubuntu](http://ppa.launchpad.net/francisbrwn9/kernels/ubuntu) PPA.

It all works together great now on Kubuntu 11.10

---

