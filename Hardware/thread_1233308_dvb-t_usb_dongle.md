---
title: "dvb-t usb dongle"
date: 2009-08-06
forum: Hardware
---

### Post by madman100 on 2009-08-06
Hi all i have just been given a dvb-t usb dongle and trying to get it to work but have installed the lates vl4-dvb drivers and configure as describe on the forum but the dvb-t usb dongle is not showing up here is i picture of the usb dvb-t i do not know what make it is so can any one tell me from the picture what make it is and  if it will work in ubuntu 

Thanks 
madman100

---

### Post by Kubunteando on 2009-08-06
Not all the DVB-T will work.
First you have to find out which is the model. I cannot say from the picture. To find out this may help:

[http://www.linuxtv.org/wiki/index.php/Supported_Hardware#The_V4L-DVB_Wiki](http://www.linuxtv.org/wiki/index.php/Supported_Hardware#The_V4L-DVB_Wiki)

Also there you can find whether it is supported at this point.

---

### Post by sanderj on 2009-08-06
Plug in it your Ubuntu system, and then run 'lsusb' (or maybe 'sudo lsusb', and maybe some extra options). You can then find which USB hardware is found on the DVB-T stick, and then check whether it's supported.

HTH

---

### Post by madman100 on 2009-08-06
hi i have just done a sudo lsusb and all my other USB hardware show up but not the dvb-t USB dongle so i can not get any info from that to see if it is supported 

Thanks 
madman100

---

### Post by Kubunteando on 2009-08-06
Include the output of the lsusb when the dongle is unplugged and the output of the lsusb when the dongle is plugged in.

If there is no difference it maybe that the USB port has not enough power to power up the usb dongle. Type dmesg when you have just plugged the dongle and check the last lines of the output it maybe give some hints.

---

### Post by madman100 on 2009-08-06
hi this is  the new hardware when i do sudo lsusb Bus 001 Device 008: ID 18b4:1689
  
18b4  e3C Technologies
	1001  DUTV007
	1689  DUTV009

Thanks 
madman100

---

### Post by madman100 on 2009-08-06
Hi all got it now all up and running found this Tutorial and it works now my dvb-t usb dongle is working 

My WandTV has the EC168 chipset and now works under Ubuntu!

I did this on a Ubuntu system (9.04 x86_64)

First install Mercurial:

sudo apt-get install mercurial

Then get the source for the driver and the v4l and dvb-system with mercurial:

hg clone [http://linuxtv.org/hg/~anttip/ec168/](http://linuxtv.org/hg/~anttip/ec168/)

When it completes downloading, go into the folder ~/ec168/ and run make
and sudo make install

Hopefully the compiling goes well, then you will have a lot of modules in the ~/ec168/v4l/ subfolder.

Then you have to download the firmware from [http://palosaari.fi/linux/v4l-dvb/firmware/ec168/dvb-usb-ec168.fw](http://palosaari.fi/linux/v4l-dvb/firmware/ec168/dvb-usb-ec168.fw)

( This file can also be found on your driver CD, called EC168BDA.bin. This has to be renamed to dvb-usb-ec168.fw )

Put this file in /lib/firmware/

Then load the following modules from the ~/ec168-2/v4l/ folder:

sudo insmod dvb-core.ko
sudo insmod dvb-usb.ko
sudo insmod ec100.ko
sudo insmod mxl5005s.ko
sudo insmod dvb-usb-ec168.ko

Thanks To all For The Help
Madman100

---

### Post by johann_p on 2009-08-14
I tried this with Ubuntu 9.04 (2.6.28-14-generic) and get an error when I try to load module  dvb-usb-ec168.ko: 
```

insmod: error inserting 'dvb-usb-ec168.ko': -1 Unknown symbol in module
> dmesg
[ 4954.131403] dvb_usb_ec168: disagrees about version of symbol dvb_usb_device_init
[ 4954.131411] dvb_usb_ec168: Unknown symbol dvb_usb_device_init

```

Any ideas?

---

### Post by madman100 on 2009-08-14
hi did you do this first 

First install Mercurial:

sudo apt-get install mercurial

Then get the source for the driver and the v4l and dvb-system with mercurial:

hg clone [http://linuxtv.org/hg/~anttip/ec168/](http://linuxtv.org/hg/~anttip/ec168/)

cd ~/ec168/ 

make

sudo make install

Hopefully the compiling goes well, then you will have a lot of modules in the ~/ec168/v4l/ subfolder

CP your firmware file in to this folder  /lib/firmware/

Then load the following modules from the ~/ec168-2/v4l/ folder:

cd ~/ec168-2/v4l/

sudo insmod dvb-core.ko
sudo insmod dvb-usb.ko
sudo insmod ec100.ko
sudo insmod mxl5005s.ko
sudo insmod dvb-usb-ec168.ko 

then reboot 
madman100

---

### Post by johann_p on 2009-08-14
I tried this again in the meantime and it seems that now it worked. The problem probably was that when I tried it the first time, I had already plugged in a different USB/DVBT stick earlier and obviously this somehow messed things up. I did a reboot in the meantime and now the new DVBT stick somewhat works with kaffeine (although much worse as the other one which is a Pinnacle Systems stick.
Also, in the lsusb list, there is still no description for this device.

---

### Post by madman100 on 2009-08-14
Hi m8 in what way worse in install all of mine in newly install system in xubunt 9.4 64bit and ubuntu 9.4 64 bit and they run fine try install ubuntu to a spare harddrive then boot from it then install and configure your dvb-t again and see if you get those problems again with your dvb-t and see what the play back is like in kaffeine with your usb-dvb-t 

Thanks 
Madman100

---

### Post by johann_p on 2009-08-14
> **madman100 said:**
> Hi m8 in what way worse in install all of mine in newly install system in xubunt 9.4 64bit and ubuntu 9.4 64 bit and they run fine try install ubuntu to a spare harddrive then boot from it then install and configure your dvb-t again and see if you get those problems again with your dvb-t and see what the play back is like in kaffeine with your usb-dvb-t 


The main difference is that the Pinnacle stick picks up many more channels than this one. Both use a similar small antenna placed at the same spot for comparison.
Also, this one does not show the signal strength in the kaffeine tuning dialog while the Pinnacle stick does. The Pinnacle stick also was recognized by Ubuntu without any additinal installation.

---

### Post by RoyHobbs on 2009-10-16
Hi

I have followed your steps, however I don't have the directory ec168-2, only ec168?  Sorry I am a newbie, so any basic advice would be appreciated.  TIA

---

### Post by madman100 on 2009-10-16
hi did you do this first

First install Mercurial:

sudo apt-get install mercurial

Then get the source for the driver and the v4l and dvb-system with mercurial:

hg clone [http://linuxtv.org/hg/~anttip/ec168/](http://linuxtv.org/hg/~anttip/ec168/)

cd ~/ec168/

make

sudo make install

Hopefully the compiling goes well, then you will have a lot of modules in the ~/ec168/v4l/ subfolder

CP your firmware file in to this folder /lib/firmware/

Then load the following modules from the ~/ec168-2/v4l/ folder:

cd ~/ec168-2/v4l/

sudo insmod dvb-core.ko
sudo insmod dvb-usb.ko
sudo insmod ec100.ko
sudo insmod mxl5005s.ko
sudo insmod dvb-usb-ec168.ko

then reboot

---

### Post by hopefull99 on 2009-10-31
Hi
I have been using your method of getting a DVB-T USB Dongle to work on Ubuntu 9.4. It worked fine with plugging- in as required though you could not plug-in, unplug and replug in the same session, as when you replugged the dongle would not work. Rebooting to Ubuntu solved the problem and all was working again. Its been like this for a few months and no problems.

I have not used the dongle for a few weeks and now it is not recognised. 
I have checked and the firmware file is still present.
Using lsmod none of the 5 modules are present
  	 	 	 	 	 	  sudo insmod dvb-core.ko
 sudo insmod dvb-usb.ko
 sudo insmod ec100.ko
 sudo insmod mxl5005s.ko
 sudo insmod dvb-usb-ec168.ko

cp the directory where these were taken from and re insmod them and the stick works again. It even works as plug and play as many times as you like where it didnot before.

Rebooting looses the above files and you have to start again.


Has there been an update recently that is causing this ?.


What seems to be required is that the 5 files are loaded during the boot sequence. Is this possible ?


Thanks for you help


hopefull99.

---

### Post by Unkuiri on 2009-11-24
Hi, my dvb-t device used to work in Jaunty with this method, but now, on karmic I'm can't make the modules, when i use the comand "make" it creates a lot of modules in ~/ec168/v4l/ folder but not the required ones...:(...
I've discovered that some of them are present on the kernel (dvb-core.ko;dvb-usb.ko;mxl5005s.ko) but the other 2 i can't find nor create them (ec100.ko dvb-usb-ec168.ko)...can someone help me or have the same problem?

thanks

---

### Post by BenMoss11 on 2009-12-14
I would have to say that this does not work for me either unfortunately. I have tried the steps exactly twice with the same results both times.

Here is what happens. Steps up to the make go fine.  I type make and it starts compiling and creates a whole bunch of .o files... Then it starts to go bad.. as I said the same thing both times.

/home/ben/ec168/v4l/et61x251_core.c: In function 'et61x251_mmap':
/home/ben/ec168/v4l/et61x251_core.c:1567: warning: assignment discards qualifiers from pointer target type
/home/ben/ec168/v4l/et61x251_core.c: In function 'et61x251_ioctl_v4l2':
/home/ben/ec168/v4l/et61x251_core.c:2493: warning: the frame size of 1256 bytes is larger than 1024 bytes
  CC [M]  /home/ben/ec168/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/ben/ec168/v4l/firedtv-avc.o
  CC [M]  /home/ben/ec168/v4l/firedtv-ci.o
  CC [M]  /home/ben/ec168/v4l/firedtv-dvb.o
  CC [M]  /home/ben/ec168/v4l/firedtv-fe.o
  CC [M]  /home/ben/ec168/v4l/firedtv-1394.o
/home/ben/ec168/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/ben/ec168/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/ben/ec168/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/ben/ec168/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/ben/ec168/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/ben/ec168/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/ben/ec168/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/home/ben/ec168/v4l/firedtv-1394.c:37: warning: 'struct hpsb_iso' declared inside parameter list
/home/ben/ec168/v4l/firedtv-1394.c:37: warning: its scope is only this definition or declaration, which is probably not what you want
/home/ben/ec168/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/ben/ec168/v4l/firedtv-1394.c:53: error: dereferencing pointer to incomplete type
/home/ben/ec168/v4l/firedtv-1394.c:54: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/ben/ec168/v4l/firedtv-1394.c:61: error: dereferencing pointer to incomplete type
/home/ben/ec168/v4l/firedtv-1394.c:62: error: implicit declaration of function 'dma_region_i'
/home/ben/ec168/v4l/firedtv-1394.c:62: error: dereferencing pointer to incomplete type
/home/ben/ec168/v4l/firedtv-1394.c:62: error: expected expression before 'unsigned'
/home/ben/ec168/v4l/firedtv-1394.c:63: warning: assignment makes pointer from integer without a cast
/home/ben/ec168/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/home/ben/ec168/v4l/firedtv-1394.c:68: error: dereferencing pointer to incomplete type
/home/ben/ec168/v4l/firedtv-1394.c:82: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/ben/ec168/v4l/firedtv-1394.c: In function 'node_of':
/home/ben/ec168/v4l/firedtv-1394.c:87: error: dereferencing pointer to incomplete type
/home/ben/ec168/v4l/firedtv-1394.c:87: warning: type defaults to 'int' in declaration of '__mptr'
/home/ben/ec168/v4l/firedtv-1394.c:87: warning: initialization from incompatible pointer type
/home/ben/ec168/v4l/firedtv-1394.c:87: error: invalid use of undefined type 'struct unit_directory'
/home/ben/ec168/v4l/firedtv-1394.c: In function 'node_lock':
/home/ben/ec168/v4l/firedtv-1394.c:92: error: implicit declaration of function 'hpsb_node_lock'
/home/ben/ec168/v4l/firedtv-1394.c:92: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/ben/ec168/v4l/firedtv-1394.c:92: error: (Each undeclared identifier is reported only once
/home/ben/ec168/v4l/firedtv-1394.c:92: error: for each function it appears in.)
/home/ben/ec168/v4l/firedtv-1394.c:93: error: 'quadlet_t' undeclared (first use in this function)
/home/ben/ec168/v4l/firedtv-1394.c:93: error: expected ')' before 'arg'
/home/ben/ec168/v4l/firedtv-1394.c: In function 'node_read':
/home/ben/ec168/v4l/firedtv-1394.c:98: error: implicit declaration of function 'hpsb_node_read'
/home/ben/ec168/v4l/firedtv-1394.c: In function 'node_write':
/home/ben/ec168/v4l/firedtv-1394.c:103: error: implicit declaration of function 'hpsb_node_write'
/home/ben/ec168/v4l/firedtv-1394.c: In function 'start_iso':
/home/ben/ec168/v4l/firedtv-1394.c:114: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/ben/ec168/v4l/firedtv-1394.c:114: error: dereferencing pointer to incomplete type
/home/ben/ec168/v4l/firedtv-1394.c:116: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/ben/ec168/v4l/firedtv-1394.c:118: warning: assignment makes pointer from integer without a cast
/home/ben/ec168/v4l/firedtv-1394.c:125: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/ben/ec168/v4l/firedtv-1394.c:128: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/ben/ec168/v4l/firedtv-1394.c: In function 'stop_iso':
/home/ben/ec168/v4l/firedtv-1394.c:139: error: implicit declaration of function 'hpsb_iso_stop'
/home/ben/ec168/v4l/firedtv-1394.c: At top level:
/home/ben/ec168/v4l/firedtv-1394.c:154: warning: 'struct hpsb_host' declared inside parameter list
/home/ben/ec168/v4l/firedtv-1394.c: In function 'fcp_request':
/home/ben/ec168/v4l/firedtv-1394.c:167: error: dereferencing pointer to incomplete type
/home/ben/ec168/v4l/firedtv-1394.c:168: error: dereferencing pointer to incomplete type
/home/ben/ec168/v4l/firedtv-1394.c: In function 'node_probe':
/home/ben/ec168/v4l/firedtv-1394.c:182: error: dereferencing pointer to incomplete type
/home/ben/ec168/v4l/firedtv-1394.c:182: warning: type defaults to 'int' in declaration of '__mptr'
/home/ben/ec168/v4l/firedtv-1394.c:182: warning: initialization from incompatible pointer type
/home/ben/ec168/v4l/firedtv-1394.c:182: error: invalid use of undefined type 'struct unit_directory'
/home/ben/ec168/v4l/firedtv-1394.c:187: error: dereferencing pointer to incomplete type
/home/ben/ec168/v4l/firedtv-1394.c:187: error: 'quadlet_t' undeclared (first use in this function)
/home/ben/ec168/v4l/firedtv-1394.c:188: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/ben/ec168/v4l/firedtv-1394.c:188: error: dereferencing pointer to incomplete type
/home/ben/ec168/v4l/firedtv-1394.c:188: warning: assignment makes pointer from integer without a cast
/home/ben/ec168/v4l/firedtv-1394.c: At top level:
/home/ben/ec168/v4l/firedtv-1394.c:243: warning: 'struct unit_directory' declared inside parameter list
/home/ben/ec168/v4l/firedtv-1394.c: In function 'node_update':
/home/ben/ec168/v4l/firedtv-1394.c:245: error: dereferencing pointer to incomplete type
/home/ben/ec168/v4l/firedtv-1394.c: At top level:
/home/ben/ec168/v4l/firedtv-1394.c:253: error: variable 'fdtv_driver' has initializer but incomplete type
/home/ben/ec168/v4l/firedtv-1394.c:254: error: unknown field 'name' specified in initializer
/home/ben/ec168/v4l/firedtv-1394.c:254: warning: excess elements in struct initializer
/home/ben/ec168/v4l/firedtv-1394.c:254: warning: (near initialization for 'fdtv_driver')
/home/ben/ec168/v4l/firedtv-1394.c:255: error: unknown field 'update' specified in initializer
/home/ben/ec168/v4l/firedtv-1394.c:255: warning: excess elements in struct initializer
/home/ben/ec168/v4l/firedtv-1394.c:255: warning: (near initialization for 'fdtv_driver')
/home/ben/ec168/v4l/firedtv-1394.c:256: error: unknown field 'driver' specified in initializer
/home/ben/ec168/v4l/firedtv-1394.c:256: error: extra brace group at end of initializer
/home/ben/ec168/v4l/firedtv-1394.c:256: error: (near initialization for 'fdtv_driver')
/home/ben/ec168/v4l/firedtv-1394.c:259: warning: excess elements in struct initializer
/home/ben/ec168/v4l/firedtv-1394.c:259: warning: (near initialization for 'fdtv_driver')
/home/ben/ec168/v4l/firedtv-1394.c:262: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/ben/ec168/v4l/firedtv-1394.c:263: error: unknown field 'name' specified in initializer
/home/ben/ec168/v4l/firedtv-1394.c:263: warning: excess elements in struct initializer
/home/ben/ec168/v4l/firedtv-1394.c:263: warning: (near initialization for 'fdtv_highlevel')
/home/ben/ec168/v4l/firedtv-1394.c:264: error: unknown field 'fcp_request' specified in initializer
/home/ben/ec168/v4l/firedtv-1394.c:264: warning: excess elements in struct initializer
/home/ben/ec168/v4l/firedtv-1394.c:264: warning: (near initialization for 'fdtv_highlevel')
/home/ben/ec168/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/ben/ec168/v4l/firedtv-1394.c:271: error: implicit declaration of function 'hpsb_register_highlevel'
/home/ben/ec168/v4l/firedtv-1394.c:272: error: invalid use of undefined type 'struct hpsb_protocol_driver'
/home/ben/ec168/v4l/firedtv-1394.c:273: error: implicit declaration of function 'hpsb_register_protocol'
/home/ben/ec168/v4l/firedtv-1394.c:276: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/ben/ec168/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/ben/ec168/v4l/firedtv-1394.c:283: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/ben/ec168/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/ben/ec168/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/ben/ec168/v4l'
make: *** [all] Error 2


Any Ideas on what to do from here?

Ben

---

### Post by sanderj on 2009-12-15
Only errors in compiling firedtv-1394.c, so that's good. Some googling:

From [http://www.mail-archive.com/ubuntu-devel-discuss@lists.ubuntu.com/msg09422.html](http://www.mail-archive.com/ubuntu-devel-discuss@lists.ubuntu.com/msg09422.html)

> Basically the Firedtv driver needs the entire kernel source to compile - not
just the headers. They said they are aware of the problem and will address
it at some point.

So a quick work around is to disable the firedtv driver by modifying the
./v4l/.config file and changing '=m' to '=n' on the firedtv line.

The longer solution is to install the kernel source and then modify the
makefile configuration options to use that instead of the headers (it will
default to using the headers still if not configured correctly). If you're
not using firedtv, this is not worth it.


HTH

---

### Post by BenMoss11 on 2009-12-26
Thanks SANDERJ.

This has worked. This is now working. I am using METV right now with 2 usb dvb-t tuners. I may even have a go at setting up mythtv when I get a chance as this new usb dvb-t tuner is showing better signal strength on three channels that mythtv refuses to lock on. They old usb tuner shows a signal strength of 70%, which is plenty for metv but not for mythtv it seems. Anyhow, the new one shows about 89% signal strength.. So I live in hope.. lol

Thanks again.

---

### Post by andlinux on 2009-12-28
I was able to use my usb dvb-t stick in Ubuntu 9.04, yesterday I upgraded to 9.10 and today I discovered that my dvb-t stick didn't worked. So I tried to compile but I received an error message.
Now I get this when I want to compile:

```
andy@ubuntu-laptop:~/ec168$ make
make -C /home/andy/ec168/v4l 
make[1]: Map '/home/andy/ec168/v4l' wordt binnengegaan
creating symbolic links...
Kernel build directory is /lib/modules/2.6.31-17-generic/build
make -C /lib/modules/2.6.31-17-generic/build SUBDIRS=/home/andy/ec168/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/andy/ec168/v4l/tuner-xc2028.o
/home/andy/ec168/v4l/tuner-xc2028.c:55: error: 'FIRMWARE_NAME_MAX' undeclared here (not in a function)
make[3]: *** [/home/andy/ec168/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/andy/ec168/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make[1]: *** [default] Fout 2
make[1]: Map '/home/andy/ec168/v4l' wordt verlaten
make: *** [all] Fout 2
andy@ubuntu-laptop:~/ec168$ 

```

Who knows what this problem is and who can fix this ?

---

### Post by Unkuiri on 2009-12-29
> **sanderj said:**
> Only errors in compiling firedtv-1394.c, so that's good. Some googling:

From [http://www.mail-archive.com/ubuntu-devel-discuss@lists.ubuntu.com/msg09422.html](http://www.mail-archive.com/ubuntu-devel-discuss@lists.ubuntu.com/msg09422.html)




HTH

I tried your solution, it now compiles all modules and now I can load all of them when the usb dongle is unplugged but when i plug it and open MeTV it doesn't work..:(...anyone knows what to do?

thanks

---

### Post by ibeardslee on 2010-03-17
sanderj: heh .. I ended up doing a grep -i for 'firewire' and 'fired' and deleted a bunch of files and commented out a few files .. going from 'm' to 'n' would have been easier.

Thanks, learn a bit more each day.  Sometimes it is hard to know what to google for!

---

### Post by EmuTear on 2010-06-18
Hi guys, I'm having some trouble getting the thing to compile in mint 9. I get the following error:

```
/home/dan/ec168/v4l/videobuf-dma-contig.c: In function 'videobuf_dma_contig_user_get':
/home/dan/ec168/v4l/videobuf-dma-contig.c:140: error: dereferencing pointer to incomplete type
/home/dan/ec168/v4l/videobuf-dma-contig.c:185: error: dereferencing pointer to incomplete type
make[3]: *** [/home/dan/ec168/v4l/videobuf-dma-contig.o] Error 1
make[2]: *** [_module_/home/dan/ec168/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dan/ec168/v4l'
make: *** [all] Error 2

```Any ideas what the problem is?

EDIT: Someone else has [solved the problem ]("http://translate.google.co.uk/translate?hl=en&sl=fi&u=http://forum.ubuntu-fi.org/index.php%3Ftopic%3D16329.msg247053&ei=pYAbTKiqE5Or4QbKvJSeCg&sa=X&oi=translate&ct=result&resnum=3&ved=0CCoQ7gEwAg&prev=/search%3Fq%3Ddutv007%2B%2Berror:%2Bdereferencing%2Bpointer%2Bto%2Bincomplete%2Btype%26hl%3Den%26sa%3DG")here, but I'm not clear what exactly they've done (it's translated from Finnish).

Cheers!

---

### Post by Unkuiri on 2010-06-18
It's easy to solve your problem...
do this in the terminal:
> sudo gedit /home/you_user_name/ec168/v4l/.config
and then search in the text file for the entry:
> CONFIG_VIDEOBUF_DMA_CONTIG=m
and change to:
> CONFIG_VIDEOBUF_DMA_CONTIG=n

save the file and do the make command again, and then the sudo make install...

Hope this helps

(P.S.:I think this problem is somewhat related with some driver's kernel incompatibility.)

---

### Post by EmuTear on 2010-06-19
> **Unkuiri said:**
> It's easy to solve your problem...
Excellent, thanks ever so much!

---

