---
title: "Can't compile driver for modem"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by nnnn on 2005-10-26
I am trued but i can't compile driver for the intel 537 modem.

root@nnn:~ # sudo apt-get install build-essential linux-headers-386
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
linux-headers-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up isdnlog (3.6.2005-01-03-4ubuntu1) ...

Setting up isdnutils (3.6.2005-01-03-4ubuntu1) ...

root@nnn:~/n # cd intel-537EP_secure-2.60.80.1
root@nnn:~/n/intel-537EP_secure-2.60.80.1 # make clean
cd coredrv; make clean
make[1]: Entering directory `/root/n/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/root/n/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.o *.ko

root@nnn:~/n/intel-537EP_secure-2.60.80.1 # make 537
   Module precompile check
   Current running kernel is: 2.6.10-5-386
   /lib/modules...   autoconf.h does not exist
   please install kernel source
make: *** [check] Error 1
root@nnn:~/n/intel-537EP_secure-2.60.80.1 # make install
rm -f /etc/hamregistry.bin
bash 537_inst
running kernel 2.6.10-5-386
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
installing 537 module
install: cannot stat `Intel537.ko': No such file or directory
make: *** [install] Error 1


root@nnn:~/n/intel-537EP_secure-2.60.80.1 #

---

### Post by [pl]ice on 2005-10-30
/lib/modules... autoconf.h does not exist
please install kernel source

have u done that? 

and a check if u got automake installed, cose looks like it's asking for it...

---

### Post by az on 2005-10-30
Usually, the source package is smart enough to know to use the headers instead of just the kernel source.  This seems to not be the case here.   There may be distribution-specific information in the readme?

---

### Post by az on 2005-10-30
I am running Breezy, and it seems to find everything it needs.  It does not seem to want to compile because of gcc-4.0.  You are using Hoary and are using gcc-3.3  The readme of the driver says that the precompiled part was compiled with gcc-3.2, so I do not know if this will be a problem for you.  I do not know why it is not finding the headers for you, though....

The sl-modem drivers often work for intel chipsets....


emma@ubuntu:~/Desktop/intel-537EP_secure-2.60.80.0$ make 537
   Module precompile check
   Current running kernel is: 2.6.12-9-686
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.12-9-686
make[1]: Entering directory `/home/emma/Desktop/intel-537EP_secure-2.60.80.0/coredrv'
make -C /lib/modules/2.6.12-9-686/build SUBDIRS=/home/emma/Desktop/intel-537EP_secure-2.60.80.0/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-686'
  CC [M]  /home/emma/Desktop/intel-537EP_secure-2.60.80.0/coredrv/coredrv.o
/home/emma/Desktop/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:70: warning: type defaults to `int' in declaration of `EXPORT_SYMBOL_NOVERS'
etcetc...

---

### Post by mtron on 2005-10-31
azz, or any other helpful person...

 i'm currently on holidays at my parents house (with a 56k modem connection, and only a ubuntu install, cd. so i can't download the required build tools to make my module for the 536 EP softmodem.

The card shows up in the ubuntu device manager, but it's not detected by gnomeppp...

running scanmodem, i got:

Providing detail for device at PCI_bus 0000:00:0a.0  
Communication controller: Intel Corp. 536EP Data Fax Modem
SubSystem 16be:1040   Creatix Polymedia GmbH V.9X DSP Data Fax 
Modem 0000:00:0a.0 0780: 8086:1040
Flags: bus master, medium devsel, latency 32, IRQ 9
Memory at e2000000 (32-bit, non-prefetchable) [size=4M]
Capabilities: [e0] Power Management version 2 

so, the necessary driver source for my ubuntu standard kernel, version 2.6.12-9-386, would be: [http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=39&OSFullName=Linux*&lang=eng)

Could someone please compile the source (make 536) and upload the binary to rapidshare or send me the binary by mail?

Many thanks! 

mtron

---

### Post by az on 2005-11-01
If you are running Hoary, just install build-essential and linux-headers-2.6.10-5-386 (or 686 or k7, depending on what youa re running) and you are good to go to compile the driver.  All of that is on your cd!

If you are running Breezy, you need linux-headers-2.6.12-9-386 (or 686, k7...)  In Breezy, build-essential brings in gcc4.0 but the kernel was built with gcc-3.4 So you need to download that, too ([http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgcc-3.4%2Fgcc-3.4_3.4.4-6ubuntu8_i386.deb&md5sum=c18fd6635e3e01ad22c1aaa5d857d23a&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgcc-3.4%2Fgcc-3.4_3.4.4-6ubuntu8_i386.deb&md5sum=c18fd6635e3e01ad22c1aaa5d857d23a&arch=i386&type=main))
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=gcc-3.4-base&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=gcc-3.4-base&version=breezy&arch=i386)
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=cpp-3.4&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=cpp-3.4&version=breezy&arch=i386)


(All of that is less than one meg)
cd to the place where you saved it (floppy or usb drive)
sudo dpkg -i *.deb

and then make your driver....

---

### Post by dc419 on 2005-11-24
azz,
thanks for the help, but i'm still stuck.  i installed a fresh copy, standard install, of breezy kubuntu.  i got build-essential, linux-headers-2.6.10-5-386, and then gcc-3.4.  the compile process on stelp 2 (make 537) gets further than it did before, but still gives an error.  I also tried "sudo make 537" and that also did not work.  I've been using Linux for quite a while but still consider myself a novice, so any help is much appreciated.
Thanks,
dc

---

### Post by mtron on 2005-11-28
can you specify the error message? it worked for me perfectly. 

only the provided bootscript is crap and i load the driver with modprobe, symlink the device to /dev/modem, chmod /dev/modem to 666, and then every user can use the modem with gnome-ppp, but funny thing, when i put this commands in a boot scrpt it does not work...

---

### Post by carlmccall on 2006-01-30
[QUOTE='[pl]ice']/lib/modules... autoconf.h does not exist
please install kernel source

have u done that? 

and a check if u got automake installed, cose looks like it's asking for it...[/QUOTE]


That's the error I Keep getting: autoconf.h does not exist
please install kernel source
 How Do I do that? this wasn't Covered in the Help Wiki.

---

### Post by mtron on 2006-01-31
sudo apt-get install linux-source-*your kernel version* 
(e.g. 2.6.12)

---

