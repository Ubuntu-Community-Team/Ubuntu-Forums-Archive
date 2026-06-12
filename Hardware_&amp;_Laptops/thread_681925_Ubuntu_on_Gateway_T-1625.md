---
title: "Ubuntu on Gateway T-1625"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by subpar on 2008-01-29
Hi All,

I recently (last night as a matter of fact) purchased a Gateway T-1625 Laptop. It came pre installed with Vista, and I wanted to go ahead and get rid of this bloatware and go ahead and install Ubuntu on it. I've never had any problems getting Ubuntu installed on any system (even ones where XP would straight up not install) until this little machine.

The biggest problem, of course, was the wireless chipset. The live cd did not pick up the wireless card, and neither did the install. Since I don't have access to a wired connection, I could not get online to troubleshoot it. I don't know if ndiswrapper will work with it yet, since I haven't been able to find the driver online. The wireless chipset is copy and pasted from the gateway website is "Integrated Realtek 802.11b/g Wireless Networking." 

Other problems were as follows: ALSA had no sound output. The website does not specify what the sound card is, so I won't be able to figure out what the card is until I get home and actually look at the computer. Also, the restricted graphics driver would not pick up like it did on my other computers with ATI graphics cards. When I tried to enable the restricted driver it told me that I needed a package (the package name escapes me at the moment), but I'm pretty sure that I can get around this if I were able to get an internet connection up and running.

I've read that gateways aren't exactly linux friendly (after I bought it, of course), so I'm hoping I didn't just shoot myself in the foot and get stuck with Vista. Has anyone had similar problems, and if so, how did you get around it?

Thanks in advance!

---

### Post by marsmissionaries on 2008-02-17
The card is probably a rtl8185 or something similar. The card will work with NDISwrapper.

The native r818x driver in linux is not good, don;t use it.


As for sound, they tend to use realtek sound as well.

---

### Post by tomsa on 2008-02-21
Did you manage to fix it?  I just bought the same computer and find myself to be in the same boat!  Any help at all would be great!

---

### Post by Yellow Pasque on 2008-02-21
Please run this for us so we know what kind of hardware we're troubleshooting (the first command requires internet):
```
sudo update-pciids
sudo lspci
sudo lshw -C network
```

Here's a link to a good script that grabs the latest version of ALSA and that alone might fix your sound:
[http://ubuntuforums.org/showpost.php?p=4360698&postcount=6](http://ubuntuforums.org/showpost.php?p=4360698&postcount=6)

---

### Post by rookie2008 on 2008-05-06
Hi,
I just bought a Gateway t-1625 a month ago... and Vista was dragging all my resources down.  So I figured why not try something faster.  I installed the Ubuntu 8.04 AMD 64 bit desktop edition.  I am not having any of the audio problems previously mentioned.  However, the ATI drivers seem to be limited due to closed source problems.  I am trying to figure out how to install my wifi drivers.  I am very new to the whole linux scene; I guess I will try out NDISwrapper.

Here are the stats that I got back from using the commands Temüjin recommended.

sudo update-pciids

--14:26:00--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 132,393 (129K) [text/plain]

100%[====================================>] 132,393       25.82K/s    ETA 00:00

14:26:05 (25.79 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [132393/132393]


sudo lspci

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)



sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:59:1e:fa
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=66.212.73.14 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

---

### Post by Yellow Pasque on 2008-05-06
rookie,
lspci and lshw do not see a wireless device. Are you sure your card is inserted properly and the PCI slot enabled in the BIOS?

---

### Post by rookie2008 on 2008-05-07
The wifi is built in to my motherboard of my Gateway 1625 laptop with a Realtek RTL8187B 802.11b/g 54Mbps USB 2.0 Network Adapter.  I am 

I tried what **dfelix **"http://ubuntuforums.org/showthread.php?t=723975" did with Ubuntu 7.10.  But I ran into many complications and errors.

root@CENSORED:/usr/ndiswrapper-1.52# make 
make -C driver 
make[1]: Entering directory `/usr/ndiswrapper-1.52/driver' 
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/usr/ndiswrapper-1.52/driver 
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic' 
  LD      /usr/ndiswrapper-1.52/driver/built-in.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/crt.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/hal.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/iw_ndis.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/loader.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/ndis.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/ntoskernel.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/ntoskernel_io.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/pe_linker.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/pnp.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/proc.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/rtl.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/wrapmem.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/wrapndis.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/wrapper.o 
  CC [M]  /usr/ndiswrapper-1.52/driver/usb.o 
  AS [M]  /usr/ndiswrapper-1.52/driver/win2lin_stubs.o 
  LD [M]  /usr/ndiswrapper-1.52/driver/ndiswrapper.o 
  Building modules, stage 2. 
  MODPOST 1 modules 
  CC      /usr/ndiswrapper-1.52/driver/ndiswrapper.mod.o 
  LD [M]  /usr/ndiswrapper-1.52/driver/ndiswrapper.ko 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic' 
make[1]: Leaving directory `/usr/ndiswrapper-1.52/driver' 
make -C utils 
make[1]: Entering directory `/usr/ndiswrapper-1.52/utils' 
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c 
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory 
loadndisdriver.c:16:19: error: stdio.h: No such file or directory 
loadndisdriver.c:17:19: error: errno.h: No such file or directory 
loadndisdriver.c:18:20: error: string.h: No such file or directory 
loadndisdriver.c:19:20: error: libgen.h: No such file or directory 
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory 
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory 
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory 
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory 
loadndisdriver.c:26:20: error: unistd.h: No such file or directory 
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory 
In file included from /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/syslimits.h:7, 
                 from /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/limits.h:11, 
                 from loadndisdriver.c:28: 
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory 
loadndisdriver.c:29:19: error: ctype.h: No such file or directory 
loadndisdriver.c:30:20: error: dirent.h: No such file or directory 
loadndisdriver.c:31:20: error: syslog.h: No such file or directory 
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory 
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory 
In file included from loadndisdriver.c:37: 
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’ 
loadndisdriver.c: In function ‘load_file’: 
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function) 
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once 
loadndisdriver.c:67: error: for each function it appears in.) 
loadndisdriver.c:67: error: expected ‘;’ before ‘size’ 
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’ 
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast 
loadndisdriver.c:73: warning: implicit declaration of function ‘open’ 
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function) 
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’ 
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’ 
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’ 
loadndisdriver.c:81: warning: implicit declaration of function ‘close’ 
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function) 
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’ 
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function) 
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function) 
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast 
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function) 
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’ 
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:69: warning: unused variable ‘statbuf’ 
loadndisdriver.c: In function ‘parse_setting_line’: 
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’ 
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’ 
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’ 
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’ 
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’ 
loadndisdriver.c: In function ‘read_conf_file’: 
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function) 
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function) 
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’ 
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’ 
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’ 
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’ 
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’ 
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’ 
loadndisdriver.c:150: warning: unused variable ‘statbuf’ 
loadndisdriver.c: In function ‘load_bin_file’: 
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’ 
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’ 
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’ 
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’ 
loadndisdriver.c:232: error: expected expression before ‘struct’ 
loadndisdriver.c: In function ‘load_driver’: 
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function) 
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function) 
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’ 
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’ 
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’ 
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’ 
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’ 
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’ 
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast 
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:284: error: dereferencing pointer to incomplete type 
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’ 
loadndisdriver.c:287: error: dereferencing pointer to incomplete type 
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’ 
loadndisdriver.c:289: error: dereferencing pointer to incomplete type 
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’ 
loadndisdriver.c:294: error: dereferencing pointer to incomplete type 
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’ 
loadndisdriver.c:296: error: dereferencing pointer to incomplete type 
loadndisdriver.c:299: error: dereferencing pointer to incomplete type 
loadndisdriver.c:302: error: dereferencing pointer to incomplete type 
loadndisdriver.c:303: error: dereferencing pointer to incomplete type 
loadndisdriver.c:305: error: dereferencing pointer to incomplete type 
loadndisdriver.c:311: error: dereferencing pointer to incomplete type 
loadndisdriver.c:312: error: dereferencing pointer to incomplete type 
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’ 
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’ 
loadndisdriver.c:314: error: dereferencing pointer to incomplete type 
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:321: error: dereferencing pointer to incomplete type 
loadndisdriver.c:282: warning: unused variable ‘statbuf’ 
loadndisdriver.c:344: error: expected expression before ‘struct’ 
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’ 
loadndisdriver.c:348: warning: implicit declaration of function ‘free’ 
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c: In function ‘get_device’: 
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’ 
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’ 
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:367: warning: unused variable ‘statbuf’ 
loadndisdriver.c: In function ‘load_device’: 
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function) 
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function) 
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’ 
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast 
loadndisdriver.c:435: error: dereferencing pointer to incomplete type 
loadndisdriver.c:436: error: dereferencing pointer to incomplete type 
loadndisdriver.c:439: error: dereferencing pointer to incomplete type 
loadndisdriver.c:447: error: expected expression before ‘struct’ 
loadndisdriver.c: In function ‘get_ioctl_device’: 
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function) 
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function) 
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’ 
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’ 
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’ 
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’ 
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’ 
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function) 
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function) 
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function) 
loadndisdriver.c: In function ‘main’: 
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’ 
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function) 
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’ 
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’ 
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’ 
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’ 
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’ 
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’ 
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’ 
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’ 
make[1]: *** [loadndisdriver] Error 1 
make[1]: Leaving directory `/usr/ndiswrapper-1.52/utils' 
make: *** [all] Error 2 
root@CENSORED:/usr/ndiswrapper-1.52# make install 
make -C driver install 
make[1]: Entering directory `/usr/ndiswrapper-1.52/driver' 
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/usr/ndiswrapper-1.52/driver 
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic' 
  Building modules, stage 2. 
  MODPOST 1 modules 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic' 
echo /lib/modules/2.6.24-16-generic/misc 
/lib/modules/2.6.24-16-generic/misc 
mkdir -p /lib/modules/2.6.24-16-generic/misc 
install -m 0644 ndiswrapper.ko /lib/modules/2.6.24-16-generic/misc 
/sbin/depmod -a 2.6.24-16-generic -b / 
make[1]: Leaving directory `/usr/ndiswrapper-1.52/driver' 
make -C utils install 
make[1]: Entering directory `/usr/ndiswrapper-1.52/utils' 
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c 
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory 
loadndisdriver.c:16:19: error: stdio.h: No such file or directory 
loadndisdriver.c:17:19: error: errno.h: No such file or directory 
loadndisdriver.c:18:20: error: string.h: No such file or directory 
loadndisdriver.c:19:20: error: libgen.h: No such file or directory 
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory 
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory 
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory 
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory 
loadndisdriver.c:26:20: error: unistd.h: No such file or directory 
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory 
In file included from /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/syslimits.h:7, 
                 from /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/limits.h:11, 
                 from loadndisdriver.c:28: 
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory 
loadndisdriver.c:29:19: error: ctype.h: No such file or directory 
loadndisdriver.c:30:20: error: dirent.h: No such file or directory 
loadndisdriver.c:31:20: error: syslog.h: No such file or directory 
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory 
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory 
In file included from loadndisdriver.c:37: 
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’ 
loadndisdriver.c: In function ‘load_file’: 
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function) 
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once 
loadndisdriver.c:67: error: for each function it appears in.) 
loadndisdriver.c:67: error: expected ‘;’ before ‘size’ 
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’ 
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast 
loadndisdriver.c:73: warning: implicit declaration of function ‘open’ 
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function) 
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’ 
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’ 
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’ 
loadndisdriver.c:81: warning: implicit declaration of function ‘close’ 
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function) 
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’ 
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function) 
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function) 
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast 
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function) 
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’ 
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:69: warning: unused variable ‘statbuf’ 
loadndisdriver.c: In function ‘parse_setting_line’: 
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’ 
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’ 
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’ 
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’ 
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’ 
loadndisdriver.c: In function ‘read_conf_file’: 
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function) 
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function) 
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’ 
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’ 
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’ 
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’ 
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’ 
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’ 
loadndisdriver.c:150: warning: unused variable ‘statbuf’ 
loadndisdriver.c: In function ‘load_bin_file’: 
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’ 
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’ 
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’ 
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’ 
loadndisdriver.c:232: error: expected expression before ‘struct’ 
loadndisdriver.c: In function ‘load_driver’: 
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function) 
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function) 
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’ 
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’ 
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’ 
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’ 
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’ 
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’ 
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast 
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:284: error: dereferencing pointer to incomplete type 
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’ 
loadndisdriver.c:287: error: dereferencing pointer to incomplete type 
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’ 
loadndisdriver.c:289: error: dereferencing pointer to incomplete type 
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’ 
loadndisdriver.c:294: error: dereferencing pointer to incomplete type 
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’ 
loadndisdriver.c:296: error: dereferencing pointer to incomplete type 
loadndisdriver.c:299: error: dereferencing pointer to incomplete type 
loadndisdriver.c:302: error: dereferencing pointer to incomplete type 
loadndisdriver.c:303: error: dereferencing pointer to incomplete type 
loadndisdriver.c:305: error: dereferencing pointer to incomplete type 
loadndisdriver.c:311: error: dereferencing pointer to incomplete type 
loadndisdriver.c:312: error: dereferencing pointer to incomplete type 
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’ 
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’ 
loadndisdriver.c:314: error: dereferencing pointer to incomplete type 
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:321: error: dereferencing pointer to incomplete type 
loadndisdriver.c:282: warning: unused variable ‘statbuf’ 
loadndisdriver.c:344: error: expected expression before ‘struct’ 
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’ 
loadndisdriver.c:348: warning: implicit declaration of function ‘free’ 
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c: In function ‘get_device’: 
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’ 
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’ 
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:367: warning: unused variable ‘statbuf’ 
loadndisdriver.c: In function ‘load_device’: 
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function) 
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function) 
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’ 
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast 
loadndisdriver.c:435: error: dereferencing pointer to incomplete type 
loadndisdriver.c:436: error: dereferencing pointer to incomplete type 
loadndisdriver.c:439: error: dereferencing pointer to incomplete type 
loadndisdriver.c:447: error: expected expression before ‘struct’ 
loadndisdriver.c: In function ‘get_ioctl_device’: 
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function) 
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function) 
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’ 
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’ 
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’ 
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’ 
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’ 
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function) 
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function) 
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function) 
loadndisdriver.c: In function ‘main’: 
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’ 
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function) 
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’ 
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’ 
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’ 
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’ 
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’ 
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’ 
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’ 
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’ 
make[1]: *** [loadndisdriver] Error 1 
make[1]: Leaving directory `/usr/ndiswrapper-1.52/utils' 
make: *** [install] Error 2 


I do not know where to start with fixing the ATI radeon X1270 video drivers, or aspi drivers for my dvd playback.

---

### Post by H_a_D_3_z on 2008-05-08
Thank God!!!:guitar:
For a minute there i felt like "I AM LEGEND!"
I also have a Gateway, however it is a T-1628.  Just about the samething.  My specs are similar to yours, and i can't get on the internet either.  Subpar, Tomsa, & Rook I think maybe we should keep close tabs on each other to get updates on this Gateway mystery.  I'm new to linux also, and this is getting really frustrating.  Help me out guys.

Needing a shoulder to cry on :confused:!!!

---

### Post by darthbader on 2008-05-09
I have the T1625 Gateway with the Realtek RTL8187B 802.11b/g 54Mbps USB 2.0 Network Adapter as well.  I am running dual boot with Vista x64.  I am using Ubuntu 8.04 x86 edition so my additional ram is not recognized but I had issues running the live CD of the X64 Ubuntu.  (The screen was shaking the whole time it ran).  

Ubuntu installed perfectly except I had trouble with the wireless as you have all had issues with as well.

I downloaded the Realtek 8187b driver for windows and installed it using the windows 98 inf file with NDISWRAPPER 

I am not a total noob to ubuntu as I have used several versions before 7.10, 7.04, and 6.10 however I am not a linux genius either.  I usually dont stray away from the repositories although I am getting more brave as time goes on.  

Now my wireless works perfectly.  It detects all my networks within range and connects to my access points and stayes connected better than Vista did.  I had major issues with my wireless staying connected while using Vista 32 bit and x64 as well.

I did try to follow someones instructions for installing the NDISWrapper and the driver in Terminal but it screwed up my repositories and I couldnt fix anything so I did have to reinstall but I discovered that NDISWrapper is included in the Add Remove Programs manager.  After I installed it from there its been running great.

Would any of you be from the Pittsburgh, PA area????
I bought my T-1625 when it went on clearance at Best buy in March.

Go Penguins

---

### Post by H_a_D_3_z on 2008-05-09
Hey Darth would you mind set us up with a couple of links that help you get your feet on the ground.  By the way, I'm from Columbus, GA. 

Go Falcons (so Mike is still in jail :()

---

### Post by Geomancer626 on 2008-05-12
Hey, guys don't feel alone. I'm here with a gateway T-1623 :D

Has anyone made progress on getting the wireless working yet? Also, if you've gotten ndiswrapper to work, does it allow you to put the device in monitor mode?

---

### Post by DSMTurboAWD on 2008-05-27
> **darthbader said:**
> I have the T1625 Gateway with the Realtek RTL8187B 802.11b/g 54Mbps USB 2.0 Network Adapter as well.  I am running dual boot with Vista x64.  I am using Ubuntu 8.04 x86 edition so my additional ram is not recognized but I had issues running the live CD of the X64 Ubuntu.  (The screen was shaking the whole time it ran).  

Ubuntu installed perfectly except I had trouble with the wireless as you have all had issues with as well.

I downloaded the Realtek 8187b driver for windows and installed it using the windows 98 inf file with NDISWRAPPER 

I am not a total noob to ubuntu as I have used several versions before 7.10, 7.04, and 6.10 however I am not a linux genius either.  I usually dont stray away from the repositories although I am getting more brave as time goes on.  

Now my wireless works perfectly.  It detects all my networks within range and connects to my access points and stayes connected better than Vista did.  I had major issues with my wireless staying connected while using Vista 32 bit and x64 as well.

I did try to follow someones instructions for installing the NDISWrapper and the driver in Terminal but it screwed up my repositories and I couldnt fix anything so I did have to reinstall but I discovered that NDISWrapper is included in the Add Remove Programs manager.  After I installed it from there its been running great.

Would any of you be from the Pittsburgh, PA area????
I bought my T-1625 when it went on clearance at Best buy in March.

Go Penguins

Could you be more specific in the steps you used to get the driver to work. It would be very helpful. I would be very grateful as well.

---

### Post by rookie2008 on 2008-05-27
Hello everyone,

My wifi was working just fine using pjasnos' method ([http://ubuntuforums.org/showthread.php?t=765671&highlight=rtl8187b](http://ubuntuforums.org/showthread.php?t=765671&highlight=rtl8187b))
Also listed below -

wget [http://www.datanorth.net/~cuervo/rtl...ed-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl...ed-dist.tar.gz)

wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up

until I installed the updates that GNOME recommended I download and install earlier today. I am using Ubuntu The new updates triggered these errors due to alterations to my patch file.

notavailable@CENSORED:~$ cd rtl8187b-modified
notavailable@CENSORED:~/rtl8187b-modified$ sudo ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory
notavailable@CENSORED:~/rtl8187b-modified$ dir

2.6.24.patch install ReadMe.txt wlan0dhcp wlan0up
ieee80211 makedrv release_note wlan0down wpa_supplicant-0.5.3
ifcfg-wlan0 README.FIRST rtl8187 wlan0rmv
notavailable@CENSORED:~/rtl8187b-modified$

I found that doing the following again put my wifi back online

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up

 I thought the updates were supposed to fix problems, not create them. Maybe I should email the developers?

---

### Post by UB_Battousai on 2008-07-11
I just started using Ubuntu (Linux/Unix for that matter) a couple days ago. I got my wireless working and with WPA.

Here is what I did:

Install the X86 version of Ubuntu. (If you install the 64bit version, the wireless driver will not work)

After the install type: 
sudo apt-get update
sudo apt-get install ndisgtk (Type Y when it asks to install the other dependencies)

Download the Windows 98 version of the 8187B Driver. (All other version fail)
Extract the zip file.

Go to System > Administration > Windows Wireless Drivers

Install the driver (Browse and select the .INF file)

Close all applications and restart. (The whole computer, not just the network service)

Done, you should be able to configure your wireless settings. (BTW I'm posting from my Ubuntu laptop over Wireless w/ WPA)

Good Luck!:guitar:

---

### Post by onewithnature83 on 2008-07-20
Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---

