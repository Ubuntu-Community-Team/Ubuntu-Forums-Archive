---
title: "install rt2870 dirvers"
date: 2009-09-22
forum: Hardware
---

### Post by joelsolar on 2009-09-22
I was trying to install rt2870 driver for my  buffalo WLI-UC-GN, the Smallest Wifi N USB Dongle on Earth.
When I executed the command MAKE, the issue is:


joel@compaq:~/Documents/2009$ make
make -C tools
make[1]: Entering directory `/home/joel/Documents/2009/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/joel/Documents/2009/tools'
/home/joel/Documents/2009/tools/bin2h
cp -f os/linux/Makefile.6 /home/joel/Documents/2009/os/linux/Makefile
make  -C  /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/joel/Documents/2009/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/joel/Documents/2009/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/joel/Documents/2009/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/joel/Documents/2009/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
cp -f /home/joel/Documents/2009/os/linux/rt2870sta.ko /tftpboot
cp: cannot remove `/tftpboot': Permission denied
make: *** [LINUX] Error 1


There is a error,
can someone tell me what's going on?

When I try the command sudo make install:

joel@compaq:~/Documents/2009$ sudo make install
[sudo] password for joel: 
make -C /home/joel/Documents/2009/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/joel/Documents/2009/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/joel/Documents/2009/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.28-11-generic
make[1]: Leaving directory `/home/joel/Documents/2009/os/linux'

When I try iwconfig:

joel@compaq:~/Documents/2009$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


When I try ifconfig:

joel@compaq:~/Documents/2009$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:94:34:a7  
          inet addr:192.168.1.17  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe94:34a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51708757 (51.7 MB)  TX bytes:1595748 (1.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

How do I configure my adpater?
I tried too ndiswrapper:

[IMG]file:///tmp/moz-screenshot.jpg[/IMG]
[IMG]http://ubuntuforums.org/home/joel/pic.png[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

System can see my adapter
but I could not install it

What kind of configuration tool may I use?

[IMG]http://ubuntuforums.org/home/joel/pic2.png[/IMG]




Please  I need help
I will appreciate it.

Thanks friends.

---

