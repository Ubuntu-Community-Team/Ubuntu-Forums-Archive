---
title: "Ubuntu 7.10 on Gateway t-1625"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by Saerone on 2008-03-14
Hi guys i need help, 
 I bought into this here Gateway T-1625 without doin enough research. Would love to get Ubuntu running, and I tried about 2 weeks ago but had to go back to Vista. Anyway Id like to know if anyone had any luck with there sound or wireless. 

Wireless
Realtek 8187b wireless

and 
all i see is 
Sigmatel high def audio codec

---

### Post by Saerone on 2008-03-14
Anyone. Please help me stay away from Vista...

---

### Post by crackerUVA on 2008-03-15
I'm having the same problem with the same computer, I tried using NDISwrapper to use the windows drivers, no success though.  Let me know if you figure out a solution.

---

### Post by dfelix on 2008-03-18
Ok, I've been through a two-week troubleshooting odyssey with my t-1625 and I've come bearing the fruits of my labor.  Let me preface this post by saying that I don't really know what I'm doing; I've just read post after post on this topic and somehow managed to put together a working configuration.

Anyhow, here are the packages/files that you'll need along with their locations:

linux-backports-modules-2.6.22-14-generic
found at [http://packages.ubuntu.com/gutsy/devel/linux-backports-modules-2.6.22-14-generic](http://packages.ubuntu.com/gutsy/devel/linux-backports-modules-2.6.22-14-generic)

linux-backports-modules-generic
[http://packages.ubuntu.com/gutsy/devel/linux-backports-modules-generic](http://packages.ubuntu.com/gutsy/devel/linux-backports-modules-generic)

ndiswrapper-1.52.tar.gz
downloadable from [http://ndiswrapper.sourceforge.net/joomla](http://ndiswrapper.sourceforge.net/joomla)

ndiswrapper-common_1.50-1ubuntu1_all.deb
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper)

ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper)

RTL8187B_driver_only.zip
This contains windows drivers for the realtek rtl8187b wireless card.  It's downloadable from the realtek site (do a google search for realtek rtl8187b).

Ok, first things first - I find it really annoying to have to type 'sudo' before every freakin command.  So let's log in as root.  To do this, log in normally and go to System > Administration > Login Window.  Click on the Security tab and check the 'Allow local system administrator login' box.  Next, open a terminal and enter
sudo passwd
This will let you set a password for root.

Now log back in as root.  First, let's take care of the sound problem because it's the easiest to fix.  Just install the linux-backports-modules-2.6.22-14-generic and linux-backports-modules-generic modules (in that order!).  Then reboot.  That's it.  You may have run alsamixer (from a terminal) to turn up your sound.

Next, we'll install ndiswrapper in the /usr directory and use the Win98 driver for the wireless card.  Open a terminal and navigate to the directory where you've put the ndiswrapper-1.52.tar.gz file.  Then enter the following commands:

cp ndiswrapper-1.52.tar.gz /usr
cd /usr
tar zxvf ndiswrapper-1.52.tar.gz 
cd ndiswrapper-1.52
make uninstall (I did this twice)
make
make install

Next, install the ndiswrapper-common and ndiswrapper-utils packages (in that order).
Here I created a directory to hold my Win98 driver:
mkdir /wireless
Now unzip the contents of RTL8187B_driver_only.zip to /wireless and navigate to the newly created directory /wireless/RTL8187B/Win98.

Here I took time out to add the following two lines to my /etc/network/interfaces file:
auto wlan0
iface wlan0 inet dhcp
I'm pretty sure that this is essential, but I don't really know when this needs to be done.  

Now return to /wireless/RTL8187B/Win98 and install the driver with the following commands:
ndiswrapper -i net8187b.inf
depmod -a
modprobe ndiswrapper

Now you can check that the driver installed correctly by typing
ndiswrapper -l
and you should be able to see available wireless networks by typing
iwlist wlan0 scan

If this looks ok, enter
ndiswrapper -m
This should return the following output:
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

Now, to get ndiswrapper to load on startup, just alter your /etc/modules file with the command
echo ndiswrapper >> /etc/modules

That's pretty much it.  I have to mention that I haven't been able to connect to any network with encryption using Network Manager.  In fact, so far as I can tell, Network Manager is a badass evil cyborg sent back in time to prevent me from getting wireless.  Don't touch it.
I was able to connect to a friend's wireless network using the following commands:

iwconfig wlan0 essid <friend's wireless network name>
iwconfig wlan0 mode managed
iwconfig wlan0 key <friend's password in hexadecimal>
dhclient wlan0

Unfortunately, I can't tell you exactly what kind of protection/encryption was on her network because she couldn't remember the administrator password to her router.  bummer.

I've been able to access my network at home, which uses WPA encryption, using wpa_supplicant.  Here's my wpa_supplicant configuration file (/etc/wpa_supplicant.conf):

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
fast_reauth=1
update_config=1

network={
        ssid="<my wireless network name>"
        proto=WPA
        key_mgmt=WPA-PSK
        #psk="<my password>"
        psk=<hexadecimal password, see below>
 }

For some reason my router wouldn't accept a plaintext password, so I used the command

wpa_passphrase <my wireless network name> <my password>

This will give you a hexadecimal equivalent of your password which you can use as I did.

Lastly, to log in to a network using WPA, use the commands:

wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -w -B
dhclient wlan0

Be sure to wait a minute for the handshake protocol stuff to take place.  
The WPA support is pretty crappy, I admit.  I would say I get ten to fifteen solid minutes of good connectivity at a time.  If anyone can figure out how to improve this, I'm all ears.

Hope this helps.

---

### Post by rookie2008 on 2008-05-07
The wifi is built in to my motherboard of my Gateway 1625 laptop with a Realtek RTL8187B 802.11b/g 54Mbps USB 2.0 Network Adapter.  

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

### Post by rookie2008 on 2008-05-07
I am running Ubuntu 8.04 AMD 64 bit desktop edition.  
The wifi is built in to my motherboard of my Gateway 1625 laptop with a Realtek RTL8187B 802.11b/g 54Mbps USB 2.0 Network Adapter.


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

