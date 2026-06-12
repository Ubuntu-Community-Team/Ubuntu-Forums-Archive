---
title: "New HP RAID and NIC woes"
date: 2008-05-29
forum: Hardware
---

### Post by sgt.sargent on 2008-05-29
I've never really used Linux before (well... I did type in a couple of complex commands like cd and ls in a terminal at work once) and decided to set up Ubuntu on my brand new computer which I bought over the long weekend (there’s no way I was going to use the Vista it came with).  I thought, in my naivety, that since I've been using GIMP, Firefox (and Mozilla before that), OpenOffice, Grep, and so forth for years that the transition wouldn't be any big deal.  

In retrospect, shiny new hardware may not have been the ideal choice for my first install of Linux...

I grabbed a CD that a coworker had burned and given me and booted from it.  It came up to the install, then to the partitioner, and showed two hard drives instead of the RAID.  After some searching I found [[COLOR="Navy"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?p=3858606") that the HP I bought has fake RAID, which can be set up by following instructions [[COLOR="Navy"]here[/COLOR]]("https://help.ubuntu.com/community/FakeRaidHowto").  These looked like just the thing using a newly burned DVD ISO (8.04, I think, which gives the Start or Install Ubuntu option, while the older CD had no such option).

The next hurdle turned out to be the onboard NIC.  It installs as an r8169 when it should be an r8168 (RTL8111C/ Realtek 8168/ ICH9), yielding a NIC that looks like it should function, but can never actually communicate with the network.  So I followed the instructions [[COLOR="Navy"]here[/COLOR]]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false") in the tar for "Linux driver for kernel 2.6.x and 2.4.x (Support x86 and x64)".  Once I figured out that sudo was needed for most of the commands, the drivers were created and everything seemed fine... except for the slight detail that the NIC wasn't actually set up to *use* the driver.

Finally, I found where someone had described dmesg | tail as being akin to device manager, in that it lets you see what Linux thinks of the device you just tried to set up.  Apparently, it thinks "failed with error -22" or more precisely "r8168: probe of 0000:02:00.0 failed with error -22"... and unfortunately, "-22" in a google search (with the quotes) turns up results with 22, rather than -22... <melodramatics> and here I lie, broken and battered on the floor. </melodramatics>

I was able to install to one of the drives using the live CD, though even then the NIC didn't work (and of course it hadn't recognized the RAID).  I realize that the fake RAID isn't going to garner the same performance benefits as a proper hardware striped RAID, and that a simple striped RAID isn't the best thing either, but I would like to be able to get Linux install there (and make it see the RAID as a RAID).

I'm not at that computer right now but its a: new HP using an Asus IPIBL-LB / Benicia-GL8E socket 775 motherboard which has an Intel G33 chipset, Realtech 8111C on motherboard NIC, with 2 340GB SATA drives which are *supposed* to show up as a single 680GB via the fake RAID.  A fairly comprehensive listing for the motherboard is [[COLOR="Navy"]here[/COLOR]]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01324212&lc=en&cc=ca&dlc=en&product=3691066").

I have a copy of the Terminal session text, but was unsure what would be most appropriate for the ettiquette in these forums (paste it all in, paste snippets, attach the text, etc.).  If someone can let me know, I'll be happy to include anything that may be useful.

---

### Post by sgt.sargent on 2008-05-30
Looking around, it appears that including data such as error output or terminal steps is acceptable, so here is exactly what I did in the terminal in the live DVD session to try to get the r8168 NIC driver working.
```
ubuntu@ubuntu:~$ lsmod | grep r8169
r8169                  32260  0 
ubuntu@ubuntu:~$ sudo rmmod r8169
ubuntu@ubuntu:~$ cd ..
ubuntu@ubuntu:/home$ cd ..
ubuntu@ubuntu:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.7G   16M  1.6G   1% /lib/modules/2.6.22-14-generic/volatile
tmpfs                 1.7G   16M  1.6G   1% /lib/modules/2.6.22-14-generic/volatile
varrun                1.7G   84K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  108K  1.7G   1% /dev
devshm                1.7G     0  1.7G   0% /dev/shm
tmpfs                 1.7G   12K  1.7G   1% /tmp
/dev/sdg1              62M  218K   62M   1% /media/64M
ubuntu@ubuntu:/$ cd /media/64M
ubuntu@ubuntu:/media/64M$ cd r8168-8.006.00
ubuntu@ubuntu:/media/64M/r8168-8.006.00$ sudo make clean modules
make -C src/ clean
make[1]: Entering directory `/media/64M/r8168-8.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/media/64M/r8168-8.006.00/src'
make -C src/ modules
make[1]: Entering directory `/media/64M/r8168-8.006.00/src'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/media/64M/r8168-8.006.00/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /media/64M/r8168-8.006.00/src/r8168_n.o
/media/64M/r8168-8.006.00/src/r8168_n.c:2266: warning: ‘rtl8168_phy_power_down’ defined but not used
  LD [M]  /media/64M/r8168-8.006.00/src/r8168.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /media/64M/r8168-8.006.00/src/r8168.mod.o
  LD [M]  /media/64M/r8168-8.006.00/src/r8168.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
strip --strip-debug r8168.ko
make[1]: Leaving directory `/media/64M/r8168-8.006.00/src'
ubuntu@ubuntu:/media/64M/r8168-8.006.00$ sudo make install
make -C src/ install
make[1]: Entering directory `/media/64M/r8168-8.006.00/src'
install -m 744 -c r8168.ko /lib/modules/2.6.22-14-generic/kernel/drivers/net/
make[1]: Leaving directory `/media/64M/r8168-8.006.00/src'
ubuntu@ubuntu:/media/64M/r8168-8.006.00$ sudo depmod -a
ubuntu@ubuntu:/media/64M/r8168-8.006.00$ sudo insmod ./src/r8168.ko
ubuntu@ubuntu:/media/64M/r8168-8.006.00$ lsmod | grep r8168
r8168                  34704  0 
ubuntu@ubuntu:/media/64M/r8168-8.006.00$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

ubuntu@ubuntu:/media/64M/r8168-8.006.00$ ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
ubuntu@ubuntu:/media/64M/r8168-8.006.00$ dmesg | tail
[  498.363127] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[  498.363131]  sdg: sdg1
[  498.370171] sd 7:0:0:0: [sdg] Attached SCSI removable disk
[  498.370208] sd 7:0:0:0: Attached scsi generic sg7 type 0
[ 1270.019726] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[ 1670.196822] r8168 Gigabit Ethernet driver 8.006.00-NAPI loaded
[ 1670.196843] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[ 1670.196853] PCI: cache line size of 32 is not supported by device 0000:02:00.0
[ 1670.196859] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[ 1670.196864] r8168: probe of 0000:02:00.0 failed with error -22
ubuntu@ubuntu:/media/64M/r8168-8.006.00$ 
```

---

### Post by igitur on 2012-03-14
> **sgt.sargent said:**
> [ 1670.196864] r8168: probe of 0000:02:00.0 failed with error -22
ubuntu@ubuntu:/media/64M/r8168-8.006.00$ [/CODE]

I get this exact same error with r8168. Ever managed to solve it?

---

