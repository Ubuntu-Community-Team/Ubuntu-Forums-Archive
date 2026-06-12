---
title: "Download - Intel537ep Modem Driver Module Package"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by Sepero on 2007-09-16
.










For the latest releases, please visit-
[http://groups.google.com/group/ubuntu-modems](http://groups.google.com/group/ubuntu-modems)















Latest Hardy Heron 8.04 download:
[http://www.mediafire.com/?yqzmixwlbim](http://www.mediafire.com/?yqzmixwlbim)


-Jul 14 07-
This latest release should address problems with newer kernels. Please uninstall the previous Hardy driver before installing this newer version.
Intel537ep Driver for Hardy Heron Ubuntu Release 1:
[http://www.mediafire.com/?yqzmixwlbim](http://www.mediafire.com/?yqzmixwlbim)

-May 05 08-
chuckman78 has been real busy lately. Here's is the first release for Hardy.
Intel537ep Driver for Hardy Heron Ubuntu Release 1:
[http://www.mediafire.com/?zyzluyzbocm](http://www.mediafire.com/?zyzluyzbocm)




Latest Gutsy Gibbon 7.10 download:
[http://www.mediafire.com/?d2tomgrgpye](http://www.mediafire.com/?d2tomgrgpye)

-Nov 11 07-
Thanks chuckman78 for getting this driver compiled timely. I hope this release works out good for everyone. As always, write in if you experience any problems.
Intel537ep Driver for Gutsy Gibbon Ubuntu Release 1:
[http://www.mediafire.com/?d2tomgrgpye](http://www.mediafire.com/?d2tomgrgpye)




Latest Feisty Fawn 7.04 download:
[http://www.mediafire.com/?cxnm1xynxs4](http://www.mediafire.com/?cxnm1xynxs4)


-Sep 16 07-
Hello folks. After successfully releasing prepackaged drivers for the [Intel 536ep modems]("http://ubuntuforums.org/showthread.php?t=471503"), I set my sights on it's cousin, the 537ep. With good help from chuckman78, we are proud to announce the first public release of the new prepackaged driver for Intel 537ep modems on Ubuntu Feisty. Please note that this driver has only been tested privately. If there are any problems, please report them immediatly. For anyone curious about Gutsy. Gutsy drivers will be created only after Gutsy has been officially released. I would like to invite you to join the team if you are interested in helping, please contact me.

If you use another 537* modem and want to test this driver, PLEASE PLEASE PLEASE let us know what happens for you.
I am interested in releasing drivers for the other 537* modems, but only if there is a desire for them.

Intel537ep Driver for Feisty Fawn Ubuntu Release 1:
[http://www.mediafire.com/?cxnm1xynxs4](http://www.mediafire.com/?cxnm1xynxs4)



keywords:
ubuntu feisty 7.04 7.10 software soft softmodem win winmodem lin linmodem compile precompiled 537 ep

---

### Post by micocoulier on 2007-10-20
Hi,
Very pleased to hear of availability of Intel 537EP driver for Ubuntu 7.04.  Will it also work for Kubuntu 7.04?
Mike

---

### Post by chuckman78 on 2007-10-20
Hi.

I believe it will surely work for Kubuntu as long as it is 7.04. Give it a try!

Regards,

Carlos.

---

### Post by Sepero on 2007-10-22
What chuck said. ;)

---

### Post by imran saeed on 2007-11-17
hello! nice to see driver for 537 ep for 7.10, i have 536 ep and just installed 7.10 along with win xp dual boot. which driver i should download to get connected?

---

### Post by chuckman78 on 2007-11-18
Hi imran saeed.

 I am sorry to tell you that this driver wont work with the 536EP. I compile the 537EP drivers and Sepero the 536EP. He will compile it at any moment and will post about it at:


[http://ubuntuforums.org/showthread.php?t=471503]("http://ubuntuforums.org/showthread.php?t=471503")


Regards, 

Carlos.

---

### Post by luka78 on 2007-12-16
Hi...

I did everything like you said here:

Installing on 7.04

Next, just issue the following commands:

sudo apt-get install build-essential
export MODEM_TYPE=537EP
sudo make clean
sudo make 537
sudo make install

but i always get this:

 Module precompile check
   Current running kernel is: 2.6.20-15-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.20-15-generic
make[1]: Entering directory `/home/luci/.Trash/intel/coredrv'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/luci/.Trash/intel/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/luci/.Trash/intel/coredrv/coredrv.o
/home/luci/.Trash/intel/coredrv/coredrv.c:70: warning: data definition has no type or storage class
/home/luci/.Trash/intel/coredrv/coredrv.c:70: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
/home/luci/.Trash/intel/coredrv/coredrv.c:70: warning: parameter names (without types) in function declaration
/home/luci/.Trash/intel/coredrv/coredrv.c: In function ‘power_callback’:
/home/luci/.Trash/intel/coredrv/coredrv.c:295: error: ‘PM_SAVE_STATE’ undeclared (first use in this function)
/home/luci/.Trash/intel/coredrv/coredrv.c:295: error: (Each undeclared identifier is reported only once
/home/luci/.Trash/intel/coredrv/coredrv.c:295: error: for each function it appears in.)
/home/luci/.Trash/intel/coredrv/coredrv.c: In function ‘softcore_init_struct’:
/home/luci/.Trash/intel/coredrv/coredrv.c:336: warning: assignment from incompatible pointer type
/home/luci/.Trash/intel/coredrv/coredrv.c: In function ‘open’:
/home/luci/.Trash/intel/coredrv/coredrv.c:384: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/luci/.Trash/intel/coredrv/coredrv.c:394: warning: implicit declaration of function ‘pm_register’
/home/luci/.Trash/intel/coredrv/coredrv.c:395: warning: assignment makes pointer from integer without a cast
/home/luci/.Trash/intel/coredrv/coredrv.c: In function ‘close’:
/home/luci/.Trash/intel/coredrv/coredrv.c:416: warning: implicit declaration of function ‘pm_unregister’
/home/luci/.Trash/intel/coredrv/coredrv.c: In function ‘send_data_to_user’:
/home/luci/.Trash/intel/coredrv/coredrv.c:563: error: ‘struct tty_struct’ has no member named ‘flip’
/home/luci/.Trash/intel/coredrv/coredrv.c:568: error: ‘struct tty_struct’ has no member named ‘flip’
/home/luci/.Trash/intel/coredrv/coredrv.c:569: error: ‘struct tty_struct’ has no member named ‘flip’
/home/luci/.Trash/intel/coredrv/coredrv.c:571: error: ‘struct tty_struct’ has no member named ‘flip’
/home/luci/.Trash/intel/coredrv/coredrv.c:572: error: ‘struct tty_struct’ has no member named ‘flip’
/home/luci/.Trash/intel/coredrv/coredrv.c:573: error: ‘struct tty_struct’ has no member named ‘flip’
/home/luci/.Trash/intel/coredrv/coredrv.c: At top level:
/home/luci/.Trash/intel/coredrv/coredrv.c:641: error: expected ‘)’ before string constant
/home/luci/.Trash/intel/coredrv/coredrv.c:754:36: error: macro "DECLARE_WORK" passed 3 arguments, but takes just 2
/home/luci/.Trash/intel/coredrv/coredrv.c:754: warning: data definition has no type or storage class
/home/luci/.Trash/intel/coredrv/coredrv.c:754: warning: type defaults to ‘int’ in declaration of ‘DECLARE_WORK’
/home/luci/.Trash/intel/coredrv/coredrv.c:755:34: error: macro "DECLARE_WORK" passed 3 arguments, but takes just 2
/home/luci/.Trash/intel/coredrv/coredrv.c:755: warning: data definition has no type or storage class
/home/luci/.Trash/intel/coredrv/coredrv.c:755: warning: type defaults to ‘int’ in declaration of ‘DECLARE_WORK’
/home/luci/.Trash/intel/coredrv/coredrv.c: In function ‘wake_up_interruptible_persistReadQ’:
/home/luci/.Trash/intel/coredrv/coredrv.c:769: error: ‘wait_wq’ undeclared (first use in this function)
/home/luci/.Trash/intel/coredrv/coredrv.c: In function ‘interruptible_sleep_on_timeout_persistReadQ’:
/home/luci/.Trash/intel/coredrv/coredrv.c:803: error: ‘wait_wq2’ undeclared (first use in this function)
/home/luci/.Trash/intel/coredrv/coredrv.c: In function ‘kScheduleDPC’:
/home/luci/.Trash/intel/coredrv/coredrv.c:861: warning: implicit declaration of function ‘pm_access’
/home/luci/.Trash/intel/coredrv/coredrv.c: In function ‘dspdrv_CommRamISR’:
/home/luci/.Trash/intel/coredrv/coredrv.c:877: warning: function declaration isn’t a prototype
make[3]: *** [/home/luci/.Trash/intel/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/luci/.Trash/intel/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [537core_26] Error 2
make[1]: Leaving directory `/home/luci/.Trash/intel/coredrv'
2.6.20-15-generic
Failed to build driver
root@luci:/home/luci/Desktop/intel#


so, what is wrong with installation?

thx

---

### Post by luka78 on 2007-12-17
Ok, this is my modem Hardware Information:

[[IMG]http://img412.imageshack.us/img412/5249/modemfk9.th.png[/IMG]](http://img412.imageshack.us/my.php?image=modemfk9.png)

---

### Post by Sepero on 2007-12-17
> **luka78 said:**
> ...
so, what is wrong with installation?
You're not using the prepackaged driver listed at the top of this thread.

Download this:
[Driver for Feisty]("http://www.mediafire.com/?cxnm1xynxs4")

Carlos and I don't make any profit or return for producing these drivers.
Install it, and go on with your life.

---

### Post by luka78 on 2007-12-17
ok, thx i installed it and i have this:

uci@luci:~$ wvdial
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
ATZ
OK
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
luci@luci:~$

but when i try  to edit wvdial, it said:

luci@luci:~$ sudo wvdialconf /etc/wvdial.conf
Password:
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- &#65533;&#65533;
ttyS0<*1>: failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS4<Info>: Inappropriate ioctl for device
Modem Port Scan<*1>: S4   
ttyS5<Info>: Inappropriate ioctl for device
Modem Port Scan<*1>: S5   
ttyS6<Info>: Inappropriate ioctl for device
Modem Port Scan<*1>: S6   
ttyS7<Info>: Inappropriate ioctl for device
Modem Port Scan<*1>: S7   
ttyS8<Info>: Inappropriate ioctl for device
Modem Port Scan<*1>: S8   
ttyS9<Info>: Inappropriate ioctl for device
Modem Port Scan<*1>: S9   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
luci@luci:~$ sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- &#65533;
ttyS0<*1>: failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS4<Info>: Inappropriate ioctl for device
Modem Port Scan<*1>: S4   
ttyS5<Info>: Inappropriate ioctl for device
Modem Port Scan<*1>: S5   
ttyS6<Info>: Inappropriate ioctl for device
Modem Port Scan<*1>: S6   
ttyS7<Info>: Inappropriate ioctl for device
Modem Port Scan<*1>: S7   
ttyS8<Info>: Inappropriate ioctl for device
Modem Port Scan<*1>: S8   
ttyS9<Info>: Inappropriate ioctl for device
Modem Port Scan<*1>: S9   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
luci@luci:~$

---

### Post by luka78 on 2007-12-17
Well, it would be great if someone can help me about this ...

---

### Post by chuckman78 on 2007-12-17
Hi.

It looks to me you are having problem setting up right wvdial. Please, in a terminal box type and execute this:

```
gedit /usr/share/doc/intel537ep-feisty/success.txt
```


Follow the instructions there.

Regards,

Carlos.

---

### Post by Sepero on 2007-12-17
Carlos is right. The driver is installed and working correctly. You now need to setup your internet connection. Phone# Name Password
/etc/wvdial.conf

When you finish setting it up, then you can use 'wvdial'.

---

### Post by luka78 on 2007-12-18
Great, it works perfectly... funny thing is that, when i use Gnome ppp and under setup press Detect modem, it said No modem found, but it works and connect without problems on internet. :-), but who care for that, it's important that works ....

Thank you very much

---

### Post by garydale on 2007-12-21
No luck with the install. I'm running 7.10 (dist-upgraded from 7.04). Here is the output from an install attempt. I get the same thing if I install directly from the download.

cynthia@Thornbird:~/Downloads$ sudo dpkg -i intel537ep-gutsy_1.0_i386.deb 
[sudo] password for cynthia:
(Reading database ... 157094 files and directories currently installed.)
Preparing to replace intel537ep-gutsy 1.0 (using intel537ep-gutsy_1.0_i386.deb) ...
Unpacking replacement intel537ep-gutsy ...
 Removing any system startup links for /etc/init.d/537_boot ...
   /etc/rc2.d/S99537_boot
   /etc/rc3.d/S99537_boot
   /etc/rc4.d/S99537_boot
   /etc/rc5.d/S99537_boot
Setting up intel537ep-gutsy (1.0) ...
Intel537EP Modem Driver and Boot Scripts copied successfully
Updating modules (/sbin/depmod)
Installing boot scripts
 Adding system startup for /etc/init.d/537_boot ...
   /etc/rc2.d/S99537_boot -> ../init.d/537_boot
   /etc/rc3.d/S99537_boot -> ../init.d/537_boot
   /etc/rc4.d/S99537_boot -> ../init.d/537_boot
   /etc/rc5.d/S99537_boot -> ../init.d/537_boot
Loading 537EP driver
FATAL: Module Intel537 not found.
insmod: can't read 'Intel537': No such file or directory
error loading Intel537
ERROR: Module Intel537 does not exist in /proc/modules


Please Now read the file: /usr/share/doc/intel537ep-feisty/success.txt


Also, a find on Intel537* returns:

/lib/modules/2.6.22-15-generic/kernel/drivers/char/Intel537.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/char/Intel537.ko
/lib/modules/2.6.22-16-generic/kernel/drivers/char/Intel537.ko
/lib/modules/Intel537EPDriverForGutsy.ko
/lib/modules/2.6.22-18-generic/kernel/drivers/char/Intel537.ko
/lib/modules/2.6.22-12-generic/kernel/drivers/char/Intel537.ko
/lib/modules/2.6.22-13-generic/kernel/drivers/char/Intel537.ko
/lib/modules/2.6.22-17-generic/kernel/drivers/char/Intel537.ko


Any ideas on how to track down the problem?

---

### Post by Sepero on 2007-12-22
Hi, there garydale. Reasonable concern you have there. Considering that you appear to have done almost everything correctly, I can only guess one problem here: non-default kernel.

Your 'find' search is correct. The module should work correctly if you are using a default Ubuntu kernel, with one of the following suffixes:
2.6.22-13-generic
2.6.22-14-generic

(I don't believe 2.6.22-15 through 18 have been released yet.)

Since you dist-upgraded, my guess is that you are still probably using the Feisty 7.04 kernel. If you are, then the Feisty driver should still work fine for you.

---

### Post by garydale on 2007-12-22
Thanks. I am running the 2.6.22-14 kernel. I got it to work finally. I needed to do a pile of apt-get installs for the kernel headers and source then did a manual install from the driver source.

gppp refused to work on a permissions issue, so I tried running it as root, which worked. The network configuration tool doesn't seem to need it however and seems to do a better job configuring the network.

---

### Post by Sepero on 2007-12-23
Interesting story... If you need any other help, I'll be around. :)

---

### Post by jdogzilla on 2008-01-03
Hi, I was using this fine on Kubuntu Feisty.  After upgrade to Gutsy and the new precompiled driver pkg, it is not working anymore.  Here is what I get in messages on doing a Modem Detect in KPPP

Jan  3 00:35:52 gutsy kernel: [23936.756299] *****************open entry*******************
Jan  3 00:35:52 gutsy kernel: [23936.756382] 537: Loaded
Jan  3 00:35:52 gutsy kernel: [23936.756383] open: clm_configure CALL
Jan  3 00:35:52 gutsy kernel: [23936.756385] open: UART_init CALL
Jan  3 00:35:52 gutsy kernel: [23936.756386] open: dspdrv_clear_dsp_interrupt CALL
Jan  3 00:35:52 gutsy kernel: [23936.756388] open: dspdrv_SetCramISRCallBack CALL
Jan  3 00:35:52 gutsy kernel: [23936.756389] open: request_irq CALL
Jan  3 00:35:52 gutsy kernel: [23936.756393] open: clm_initialize CALL
Jan  3 00:35:52 gutsy kernel: [23936.756398] UKR b2 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756399] UVA 19 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756400] NLA 7c = b5
Jan  3 00:35:52 gutsy kernel: [23936.756401] MAC 6a = b5
Jan  3 00:35:52 gutsy kernel: [23936.756402] FPO 3e = b5
Jan  3 00:35:52 gutsy kernel: [23936.756403] BRU 1a = b5
Jan  3 00:35:52 gutsy kernel: [23936.756404] ARU ee = b5
Jan  3 00:35:52 gutsy kernel: [23936.756405] AAB 6 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756406] SRL a1 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756407] LIT f7 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756408] LAT f8 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756409] CRO fa = b5
Jan  3 00:35:52 gutsy kernel: [23936.756409] BUL 1b = b5
Jan  3 00:35:52 gutsy kernel: [23936.756410] GUF e1 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756411] ZAF 9f = b5
Jan  3 00:35:52 gutsy kernel: [23936.756412] CZE 2e = b5
Jan  3 00:35:52 gutsy kernel: [23936.756413] EGY 36 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756414] POL 8a = b5
Jan  3 00:35:52 gutsy kernel: [23936.756415] GIB 45 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756416] GMB 41 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756416] SLV 37 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756417] DOM 33 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756418] CRI 2b = b5
Jan  3 00:35:52 gutsy kernel: [23936.756419] CAN 20 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756420] SVK fb = b5
Jan  3 00:35:52 gutsy kernel: [23936.756421] ARE b3 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756422] SVN fc = b5
Jan  3 00:35:52 gutsy kernel: [23936.756422] HUN 51 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756423] EST f9 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756424] GUY 4d = b5
Jan  3 00:35:52 gutsy kernel: [23936.756425] ZWE c4 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756426] VEN bb = b5
Jan  3 00:35:52 gutsy kernel: [23936.756427] URY b7 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756428] TTO ac = b5
Jan  3 00:35:52 gutsy kernel: [23936.756429] SUR a3 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756429] PRI 8c = b5
Jan  3 00:35:52 gutsy kernel: [23936.756430] PRY 87 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756431] NIC 7f = b5
Jan  3 00:35:52 gutsy kernel: [23936.756432] JAM 5b = b5
Jan  3 00:35:52 gutsy kernel: [23936.756433] HND 4f = b5
Jan  3 00:35:52 gutsy kernel: [23936.756434] HTI 4e = b5
Jan  3 00:35:52 gutsy kernel: [23936.756435] GTM 49 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756435] BMU 12 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756436] BRB e = b5
Jan  3 00:35:52 gutsy kernel: [23936.756437] BHS b = b5
Jan  3 00:35:52 gutsy kernel: [23936.756438] IDN 54 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756439] PHL 89 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756440] IND 53 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756441] TWN fe = b5
Jan  3 00:35:52 gutsy kernel: [23936.756442] MEX 73 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756442] BRA 16 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756443] ARG 7 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756444] NZL 7e = b5
Jan  3 00:35:52 gutsy kernel: [23936.756445] SGP 9c = b5
Jan  3 00:35:52 gutsy kernel: [23936.756446] HKG 50 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756447] CHN 26 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756448] MYS 6c = b5
Jan  3 00:35:52 gutsy kernel: [23936.756449] AUS 9 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756449] RUS b8 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756450] JPN 0 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756451] PAK 84 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756452] PRT 8b = b5
Jan  3 00:35:52 gutsy kernel: [23936.756453] FRA 3d = b5
Jan  3 00:35:52 gutsy kernel: [23936.756454] BEL f = b5
Jan  3 00:35:52 gutsy kernel: [23936.756455] GBR b4 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756456] NLD 7b = b5
Jan  3 00:35:52 gutsy kernel: [23936.756456] LUX 69 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756457] ITA 59 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756458] GRC 46 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756459] CYP 2d = b5
Jan  3 00:35:52 gutsy kernel: [23936.756460] CHE a6 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756461] AUT a = b5
Jan  3 00:35:52 gutsy kernel: [23936.756462] DEU 4 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756463] TUR ae = b5
Jan  3 00:35:52 gutsy kernel: [23936.756463] ESP a0 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756464] LIE 68 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756465] ISR 58 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756466] IRL 57 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756467] ISL 52 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756468] NOR 82 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756469] FIN 3c = b5
Jan  3 00:35:52 gutsy kernel: [23936.756469] DEN 31 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756470] SWE a5 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756471] VNM bc = b5
Jan  3 00:35:52 gutsy kernel: [23936.756472] THA a9 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756473] SAU 98 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756474] PER 88 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756475] PAN 85 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756476] COL 27 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756476] CHL 25 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756477] BOL 14 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756478] ECU 35 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756479] KOR 61 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756480] USA b5 = b5
Jan  3 00:35:52 gutsy kernel: [23936.756481] found
Jan  3 00:35:52 gutsy kernel: [23936.756483] HaM: Read_ProductStrings
Jan  3 00:35:52 gutsy kernel: [23936.756484] exec linux persist
Jan  3 00:35:52 gutsy kernel: [23936.756485] ham ELP: switch 6
Jan  3 00:35:52 gutsy kernel: [23936.756489] ham[hamregistry]: hamproc_read 6
Jan  3 00:35:52 gutsy kernel: [23936.756510] ham[hamregistry]: proc_write 6
Jan  3 00:35:52 gutsy kernel: [23936.756519] ham[hamregistry]: hamproc_read...
Jan  3 00:35:52 gutsy kernel: [23937.154632] ham ELP: end
Jan  3 00:35:52 gutsy kernel: [23937.154635] exec linux persist
Jan  3 00:35:52 gutsy kernel: [23937.154636] ham ELP: switch 11
Jan  3 00:35:52 gutsy kernel: [23937.154767] ham[hamregistry]: hamproc_read 11
Jan  3 00:35:52 gutsy kernel: [23937.154790] ham[hamregistry]: proc_write 11
Jan  3 00:35:52 gutsy kernel: [23937.154798] ham[hamregistry]: hamproc_read...
Jan  3 00:35:52 gutsy kernel: [23937.554067] ham ELP: end
Jan  3 00:35:52 gutsy kernel: [23937.554070] exec linux persist
Jan  3 00:35:52 gutsy kernel: [23937.554072] ham ELP: switch 13
Jan  3 00:35:52 gutsy kernel: [23937.554190] ham[hamregistry]: hamproc_read 13
Jan  3 00:35:52 gutsy kernel: [23937.554212] ham[hamregistry]: proc_write 13
Jan  3 00:35:52 gutsy kernel: [23937.554221] ham[hamregistry]: hamproc_read...
Jan  3 00:35:53 gutsy kernel: [23937.953502] ham ELP: end
Jan  3 00:35:53 gutsy kernel: [23937.953505] Read_EEPROM
Jan  3 00:35:53 gutsy kernel: [23937.953506] exec linux persist
Jan  3 00:35:53 gutsy kernel: [23937.953507] ham ELP: switch 2
Jan  3 00:35:53 gutsy kernel: [23937.953653] ham[hamregistry]: hamproc_read 2
Jan  3 00:35:53 gutsy kernel: [23937.953677] ham[hamregistry]: proc_write 2
Jan  3 00:35:53 gutsy kernel: [23937.953687] ham[hamregistry]: hamproc_read...
Jan  3 00:35:53 gutsy kernel: [23938.352937] ham ELP: end
Jan  3 00:35:53 gutsy kernel: [23938.352941] HaM: Read_CountryList
Jan  3 00:35:53 gutsy kernel: [23938.352943] HaM Read_CurrentCountry
Jan  3 00:35:53 gutsy kernel: [23938.352944] exec linux persist
Jan  3 00:35:53 gutsy kernel: [23938.352945] ham ELP: switch 4
Jan  3 00:35:53 gutsy kernel: [23938.353142] ham[hamregistry]: hamproc_read 4
Jan  3 00:35:53 gutsy kernel: [23938.353164] ham[hamregistry]: proc_write 4
Jan  3 00:35:53 gutsy kernel: [23938.353173] ham[hamregistry]: hamproc_read...
Jan  3 00:35:54 gutsy kernel: [23938.752374] ham ELP: end
Jan  3 00:35:54 gutsy kernel: [23938.752377] got CurrentCountry
Jan  3 00:35:54 gutsy kernel: [23938.752393] open: ModemCardStart CALL
Jan  3 00:35:54 gutsy kernel: [23938.752434] *****************open exit*********************
Jan  3 00:35:54 gutsy kernel: [23938.756385] Read_EEPROM
Jan  3 00:35:54 gutsy kernel: [23938.756387] exec linux persist
Jan  3 00:35:54 gutsy kernel: [23938.756388] ham ELP: switch 2
Jan  3 00:35:54 gutsy kernel: [23938.756497] ham[hamregistry]: hamproc_read 2
Jan  3 00:35:54 gutsy kernel: [23938.756521] ham[hamregistry]: proc_write 2
Jan  3 00:35:54 gutsy kernel: [23938.756530] ham[hamregistry]: hamproc_read...
Jan  3 00:35:54 gutsy kernel: [23939.155802] ham ELP: end
Jan  3 00:35:54 gutsy kernel: [23939.155805] HaM: Read_ProductStrings
Jan  3 00:35:54 gutsy kernel: [23939.155807] exec linux persist
Jan  3 00:35:54 gutsy kernel: [23939.155808] ham ELP: switch 6
Jan  3 00:35:54 gutsy kernel: [23939.155965] ham[hamregistry]: hamproc_read 6
Jan  3 00:35:54 gutsy kernel: [23939.155989] ham[hamregistry]: proc_write 6
Jan  3 00:35:54 gutsy kernel: [23939.155999] ham[hamregistry]: hamproc_read...
Jan  3 00:35:54 gutsy kernel: [23939.555238] ham ELP: end
Jan  3 00:35:54 gutsy kernel: [23939.555240] exec linux persist
Jan  3 00:35:54 gutsy kernel: [23939.555241] ham ELP: switch 11
Jan  3 00:35:54 gutsy kernel: [23939.555362] ham[hamregistry]: hamproc_read 11
Jan  3 00:35:54 gutsy kernel: [23939.555385] ham[hamregistry]: proc_write 11
Jan  3 00:35:54 gutsy kernel: [23939.555394] ham[hamregistry]: hamproc_read...
Jan  3 00:35:55 gutsy kernel: [23939.954672] ham ELP: end
Jan  3 00:35:55 gutsy kernel: [23939.954675] exec linux persist
Jan  3 00:35:55 gutsy kernel: [23939.954676] ham ELP: switch 13
Jan  3 00:35:55 gutsy kernel: [23939.954849] ham[hamregistry]: hamproc_read 13
Jan  3 00:35:55 gutsy kernel: [23939.954873] ham[hamregistry]: proc_write 13
Jan  3 00:35:55 gutsy kernel: [23939.954882] ham[hamregistry]: hamproc_read...
Jan  3 00:35:55 gutsy kernel: [23940.354107] ham ELP: end
Jan  3 00:35:55 gutsy kernel: [23940.354113] HaM: Read_CountryList
Jan  3 00:35:55 gutsy kernel: [23940.354115] HaM Read_CurrentCountry
Jan  3 00:35:55 gutsy kernel: [23940.354116] exec linux persist
Jan  3 00:35:55 gutsy kernel: [23940.354117] ham ELP: switch 4
Jan  3 00:35:55 gutsy kernel: [23940.354316] ham[hamregistry]: hamproc_read 4
Jan  3 00:35:55 gutsy kernel: [23940.354341] ham[hamregistry]: proc_write 4
Jan  3 00:35:55 gutsy kernel: [23940.354350] ham[hamregistry]: hamproc_read...
Jan  3 00:35:56 gutsy kernel: [23940.753543] ham ELP: end
Jan  3 00:35:56 gutsy kernel: [23940.753548] got CurrentCountry
Jan  3 00:35:56 gutsy kernel: [23940.753561] HaM: ReadHookFlashMethod
Jan  3 00:35:56 gutsy kernel: [23940.753562] exec linux persist
Jan  3 00:35:56 gutsy kernel: [23940.753563] ham ELP: switch 9
Jan  3 00:35:56 gutsy kernel: [23940.753760] ham[hamregistry]: hamproc_read 9
Jan  3 00:35:56 gutsy kernel: [23940.753783] ham[hamregistry]: proc_write 9
Jan  3 00:35:56 gutsy kernel: [23940.753792] ham[hamregistry]: hamproc_read...
Jan  3 00:35:56 gutsy kernel: [23941.152978] ham ELP: end
Jan  3 00:35:57 gutsy kernel: [23941.797831] HaM: ReadQuickConnectData
Jan  3 00:35:57 gutsy kernel: [23941.797836] exec linux persist
Jan  3 00:35:57 gutsy kernel: [23941.797837] ham ELP: switch 7
Jan  3 00:35:57 gutsy kernel: [23941.798099] ham[hamregistry]: hamproc_read 7
Jan  3 00:35:57 gutsy kernel: [23941.798127] ham[hamregistry]: proc_write 7
Jan  3 00:35:57 gutsy kernel: [23941.798138] ham[hamregistry]: hamproc_read...
Jan  3 00:35:57 gutsy kernel: [23942.195503] ham ELP: end
                                                                            

and then it just hangs on the window in KPPP ... same thing with eFax, which is what I primarily want to use it for. 

ANY HELP will be appreciated

---

### Post by Sepero on 2008-01-04
The problem doesn't look like anything I've ever seen. I haven't much time right now, but my first suspect in a case like this would be the Linux kernel, and verifying that a proper version of it is being used. Hopefully Carlos can help you out before I get back.

---

### Post by Sepero on 2008-01-11
Ever get your problem fixed, jdogzilla?

Don't bother using a 'detect' with KPPP. Just set the modem to /dev/modem

---

### Post by jdogzilla on 2008-01-13
No luck yet.  This is the message I get in the efax window, along with the rest of the stuff under /var/log/messages .... 

efax-0.9a: 15:57:24 Warning: unexpected response "ATQ0V1"
efax-0.9a: 15:57:24 Warning: unexpected response "OK"

Any help will be appreciated.

---

### Post by Sepero on 2008-01-13
Still all unrecognized to me. :(

Often "warning" in Linux means that the operation still worked correctly. Are you able to send faxes?

Perhaps you could try creating a new account, and see if you can fax from that account?

Perhaps, try making a backup of your /etc/efax.rc file, delete the original, then reinstall the program?

---

### Post by chuckman78 on 2008-01-14
Hi, jdogzilla.

Sorry for being late on this. Could you try to use wvdial instead of kppp for your conection? Here is a wvdial.conf example content:

```
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
SetVolume = 3
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+GCI=14
Init3 = ATM1L3
Init4 = ATS11 = 20
Carrier Check = no
FlowControl = CRTSCTS
Stupid Mode = yes
Username = ###
Password = ###
Phone = ###
Auto DNS = yes
Check DNS = yes
Auto Reconnect = yes
Idle Seconds = 0
Abort on Busy = no
Abort on No Dialtone = no
Dial Attempts = 0
New PPPD = yes
```

Regards,

Carlos.

---

### Post by jdogzilla on 2008-01-16
I uninstalled efax, removed all config files and reinstalled, and it is still giving me the same problem. 

I don't have a dial-up account.  I only want to use the modem to send and receive fax.  Now, I did try the wvdial config posted above and made it dial up to my cell number ... my cell did ring. 

So I then tried to fax something to my cell just to see if efax even could connect to my cell, and that didn't work.  In efax, my init param is "Z &FE&D2S7=120 &C0 M1L0" and reset param is "Z" and nothing else.  

Any suggestions?  Thanks again for helping.

---

### Post by Sepero on 2008-01-16
> **jdogzilla said:**
> I don't have a dial-up account.  I only want to use the modem to send and receive fax.  Now, I did try the wvdial config posted above and made it dial up to my cell number ... my cell did ring.

Either the modem driver works, OR it doesn't work. It is just that simple.

Your quote above leads me to believe that the driver does in fact work.

If the driver works, then the problem is with efax.

Unfortunately, that's as much as I can tell you, because I hardly ever use (gfax) efax. I tried searching for a little info based on the efax error you gave us, but I wasn't able to find anything of value. I wish I could help more. The solution now appears to be up to you.

---

### Post by chuckman78 on 2008-01-17
The problem is that I am almost sure that this driver WON'T work with fax capabilities. I will try to contact Mr. Vouters (the master brain behind the driver code) about this issue but I cant assure anything because he is fairly hard to contact. Nevertheless I would put my money in the not functionality for fax use.

Regards,

Carlos.

---

### Post by Sepero on 2008-01-18
He said it was working with Feisty before he upgraded to Gutsy. If that is true, then I think it is safe to assume that it is possible to use the driver for faxing.

With that, I really am out of advice for jdogzilla. Unfortunately, Ubuntu Linux is far from perfect.

Anyway, it's always good to hear from you, Carlos. :)

---

### Post by SoDanishWasLike on 2008-01-18
Hi,

I am trying to get my modem working and I am not sure if I have a Intel 537ep modem or not.

My laptop has a Intel 855pm chipset, does this mean I can use this driver or not?

---

### Post by chuckman78 on 2008-01-18
Hi.

Please do this: in a terminal box execute:

```
lspci | grep 537
```

Post back what you get. Also execute this:

```
lspci | grep 536
```

Also, post what you get.

Regards, 

Carlos.

P.S: **Stephen**: sorry for not being around lately, work had been awful. I will like to retake the project that we were talking about last year, what do you think? (you could answer privately if you want to).

---

### Post by SoDanishWasLike on 2008-01-19
Carlos,

I did as you said in the terminal box and it was weird, after I put in the command, it would simply act as if nothing happened. I guess I don't have either a intel 537 or intel 536 modem.

```
danish@danish-laptop:~$ lspci | grep 537
danish@danish-laptop:~$ lspci | grep 536
danish@danish-laptop:~$ 
```

---

### Post by chuckman78 on 2008-01-21
Yes, it looks like the case.  Please visit this site:

[http://132.68.73.235/linmodems/index.html#scanmodem]("http://132.68.73.235/linmodems/index.html#scanmodem")

There you will find a nice utility and a great linmodems mailing list that will help you to make your modem work under linux.

Regards,

Carlos.

---

### Post by SoDanishWasLike on 2008-01-23
Thanks Carlos for your help

---

### Post by chuckman78 on 2008-01-23
My pleasure. Please post back with the results.

Regards,

Carlos.

---

### Post by go_beep_yourself on 2008-01-28
I just ran scanModem on a Dell laptop with an internal software modem. I need help on what to do next. Here are the results.

ModemData.txt:
```
 Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.22-14-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Your contry's local Linux experts
 can be found through: http://www.linux.org/groups/index.html. 
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007
 scanModem update of:  2008_01_22


 There are no blacklisted modem drivers in /etc/modprobe*  files 

The Advanced Linux Sound Architecture (ALSA) packages providing audio support, 
also includes drivers for some modems. The ALSA diagnostics are written during 
bootup to /proc/asound/ folders.

 The /proc/asound/ audio+modem diagostics are being copied.
 Finished copy to Modem/ALSAroot.tgz

The ALSA verion is 1.0.14
The modem cards detected by "aplay -l"  are:


The /proc/asound/pcm file reports:
-----------------------
00-04: Intel ICH - IEC958 : Intel 82801DB-ICH4 - IEC958 : playback 1
00-03: Intel ICH - ADC2 : Intel 82801DB-ICH4 - ADC2 : capture 1
00-02: Intel ICH - MIC2 ADC : Intel 82801DB-ICH4 - MIC2 ADC : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801DB-ICH4 - MIC ADC : capture 1
00-00: Intel ICH : Intel 82801DB-ICH4 : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with STAC9750,51 at irq 7

USB modem not detected by lsusb

For candidate card in slot 00:1f.6, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1f.6	8086:24c6	14e4:4d64	Modem: Intel Corporation 82801DB/DBL/DBM 

 Modem interrupt assignment and sharing: 
  7:        394    XT-PIC-XT        eth0, Intel 82801DB-ICH4
 --- Bootup diagnostics for card in PCI slot 00:1f.6 ----
[    9.308318] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[    9.308329] ACPI: PCI interrupt for device 0000:00:1f.6 disabled

 The PCI slot 00:1f.6 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to discuss@linmodems.org
 if help is needed.
 


 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

```


scanout.00:1f.6:
```
PCIDEV=8086:24c6
CLASS="Class 0703: 8086:24c6"
NAME="Modem: Intel Corporation 82801DB/DBL/DBM "
Vendor=8086
Device=24c6
SUBSYS=14e4:4d64
SUBNAME=" Broadcom Corporation Unknown device 4d64"
SUBven=14e4
IRQ=7
Test="./scanModem test 8086:24c6 14e4:4d64"
```

dmesg.txt:
```
           CPU0       
  0:     117088    XT-PIC-XT        timer
  1:        366    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  7:        394    XT-PIC-XT        eth0, Intel 82801DB-ICH4
  8:          3    XT-PIC-XT        rtc
  9:          1    XT-PIC-XT        acpi
 11:     128415    XT-PIC-XT        uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, ehci_hcd:usb4, yenta, i915@pci:0000:00:02.0
 12:     142666    XT-PIC-XT        i8042
 14:      10388    XT-PIC-XT        libata
 15:       9733    XT-PIC-XT        libata
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fec9000 (usable)
[    0.000000]  BIOS-e820: 000000001fec9000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 130761) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130761
[    0.000000]   HighMem    130761 ->   130761
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130761
[    0.000000] On node 0 totalpages: 130761
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125676 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FDF00 checksum 0
[    0.000000] ACPI: RSDP 000FDF00, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 1FEF0000, 0028 (r1 DELL    CPi R   27D40814 ASL        61)
[    0.000000] ACPI: FACP 1FEF0400, 0074 (r1 DELL    CPi R   27D40814 ASL        61)
[    0.000000] ACPI: DSDT 1FEF0C00, 2586 (r1 INT430 SYSFexxx     1001 MSFT  100000E)
[    0.000000] ACPI: FACS 1FEFF800, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec10000)
[    0.000000] Built 1 zonelists.  Total pages: 129740
[    0.000000] Kernel command line: root=UUID=745c93e4-5055-40ab-a438-0ba8063ade80 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0140d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2597.816 MHz processor.
[    7.497686] Console: colour VGA+ 80x25
[    7.498021] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.498563] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.509254] Memory: 506764k/523044k available (2015k kernel code, 15720k reserved, 916k data, 364k init, 0k highmem)
[    7.509265] virtual kernel memory layout:
[    7.509266]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    7.509267]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.509268]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[    7.509269]     lowmem  : 0xc0000000 - 0xdfec9000   ( 510 MB)
[    7.509270]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    7.509271]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    7.509273]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    7.509276] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.509317] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    7.589308] Calibrating delay using timer specific routine.. 5200.10 BogoMIPS (lpj=10400204)
[    7.589342] Security Framework v1.0.0 initialized
[    7.589351] SELinux:  Disabled at boot.
[    7.589366] Mount-cache hash table entries: 512
[    7.589558] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[    7.589574] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    7.589579] CPU: L2 cache: 128K
[    7.589582] CPU: Hyper-Threading is disabled
[    7.589586] CPU: After all inits, caps: bfebf9ff 00000000 00000000 0000b080 00004400 00000000 00000000
[    7.589603] Compat vDSO mapped to ffffe000.
[    7.589622] Checking 'hlt' instruction... OK.
[    7.605440] SMP alternatives: switching to UP code
[    7.605812] Freeing SMP alternatives: 11k freed
[    7.606184] Early unpacking initramfs... done
[    7.956992] ACPI: Core revision 20070126
[    7.957062] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    7.958197] ACPI: setting ELCR to 0200 (from 0800)
[    7.959694] CPU0: Intel(R) Celeron(R) CPU 2.60GHz stepping 09
[    7.959702] SMP motherboard not detected.
[    7.959704] Local APIC not detected. Using dummy APIC emulation.
[    7.959762] Brought up 1 CPUs
[    7.959962] Booting paravirtualized kernel on bare hardware
[    7.960048] Time: 20:49:47  Date: 00/28/108
[    7.960090] NET: Registered protocol family 16
[    7.960278] EISA bus registered
[    7.960300] ACPI: bus type pci registered
[    8.009610] PCI: PCI BIOS revision 2.10 entry at 0xfcfae, last bus=2
[    8.009613] PCI: Using configuration type 1
[    8.009615] Setting up standard PCI resources
[    8.012136] ACPI: EC: Look up EC in DSDT
[    8.015259] ACPI: Interpreter enabled
[    8.015267] ACPI: (supports S0 S1 S3 S4 S5)
[    8.015294] ACPI: Using PIC for interrupt routing
[    8.027043] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.027067] PCI: Probing PCI hardware (bus 00)
[    8.027714] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    8.027719] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[    8.028140] PCI: Transparent bridge - 0000:00:1e.0
[    8.028296] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.028643] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    8.040435] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    8.040574] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    8.040704] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    8.040831] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    8.040946] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.041079] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    8.041399] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.041426] pnp: PnP ACPI init
[    8.041449] ACPI: bus type pnp registered
[    8.053325] pnp: PnP ACPI: found 12 devices
[    8.053331] ACPI: ACPI bus type pnp unregistered
[    8.053338] PnPBIOS: Disabled by ACPI PNP
[    8.053459] PCI: Using ACPI for IRQ routing
[    8.053464] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.062229] NET: Registered protocol family 8
[    8.062233] NET: Registered protocol family 20
[    8.062419] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
[    8.062424] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    8.062426] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    8.062429] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    8.062439] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    8.062442] pnp: 00:02: ioport range 0x800-0x805 has been reserved
[    8.062444] pnp: 00:02: ioport range 0x808-0x80f has been reserved
[    8.062453] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    8.062456] pnp: 00:03: ioport range 0x806-0x807 has been reserved
[    8.062459] pnp: 00:03: ioport range 0x810-0x85f has been reserved
[    8.062461] pnp: 00:03: ioport range 0x860-0x87f has been reserved
[    8.062464] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
[    8.062467] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
[    8.062477] pnp: 00:08: ioport range 0x900-0x97f has been reserved
[    8.062486] pnp: 00:0b: ioport range 0x7b0-0x7bb has been reserved
[    8.062488] pnp: 00:0b: ioport range 0x7c0-0x7df has been reserved
[    8.062491] pnp: 00:0b: ioport range 0xbb0-0xbbb has been reserved
[    8.062493] pnp: 00:0b: ioport range 0xbc0-0xbdf has been reserved
[    8.062496] pnp: 00:0b: ioport range 0xfb0-0xfbb has been reserved
[    8.062498] pnp: 00:0b: ioport range 0xfc0-0xfdf has been reserved
[    8.062501] pnp: 00:0b: ioport range 0x13b0-0x13bb has been reserved
[    8.062509] pnp: 00:0b: ioport range 0x13c0-0x13df has been reserved
[    8.065124] Time: tsc clocksource has been installed.
[    8.093546] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[    8.093550]   IO window: 0000d000-0000d0ff
[    8.093554]   IO window: 0000d400-0000d4ff
[    8.093559]   PREFETCH window: 30000000-33ffffff
[    8.093563]   MEM window: f8000000-fbffffff
[    8.093568] PCI: Bridge: 0000:00:1e.0
[    8.093571]   IO window: d000-efff
[    8.093576]   MEM window: f8000000-fdffffff
[    8.093582]   PREFETCH window: 30000000-35ffffff
[    8.093597] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.093614] PCI: Enabling device 0000:02:04.0 (0000 -> 0003)
[    8.093823] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    8.093828] PCI: setting IRQ 11 as level-triggered
[    8.093832] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    8.093860] NET: Registered protocol family 2
[    8.133159] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    8.133247] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[    8.133459] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    8.133646] TCP: Hash tables configured (established 16384 bind 16384)
[    8.133654] TCP reno registered
[    8.145284] checking if image is initramfs... it is
[    8.596947] Switched to high resolution mode on CPU 0
[    8.814146] Freeing initrd memory: 7343k freed
[    8.814800] audit: initializing netlink socket (disabled)
[    8.814821] audit(1201553387.060:1): initialized
[    8.820505] VFS: Disk quotas dquot_6.5.1
[    8.820660] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    8.820946] io scheduler noop registered
[    8.820950] io scheduler anticipatory registered
[    8.820952] io scheduler deadline registered
[    8.820998] io scheduler cfq registered (default)
[    8.821018] Boot video device is 0000:00:02.0
[    8.821488] isapnp: Scanning for PnP cards...
[    9.175084] isapnp: No Plug & Play device found
[    9.305825] Real Time Clock Driver v1.12ac
[    9.306064] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.308307] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[    9.308314] PCI: setting IRQ 7 as level-triggered
[    9.308318] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[    9.308329] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    9.310118] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.310472] input: Macintosh mouse button emulation as /class/input/input0
[    9.310710] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.310917] i8042.c: Warning: Keylock active.
[    9.313527] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.313536] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.314075] mice: PS/2 mouse device common for all mice
[    9.314471] EISA: Probing bus 0 at eisa.0
[    9.314504] EISA: Detected 0 cards.
[    9.314652] TCP cubic registered
[    9.314682] NET: Registered protocol family 1
[    9.314719] Using IPI No-Shortcut mode
[    9.315059]   Magic number: 8:981:852
[    9.315195]   hash matches device ptyv4
[    9.315768] Freeing unused kernel memory: 364k freed
[    9.316624] input: AT Translated Set 2 keyboard as /class/input/input1
[   10.679699] AppArmor: AppArmor initialized<5>audit(1201553389.060:2):  type=1505 info="AppArmor initialized" pid=1193
[   10.693578] fuse init (API version 7.8)
[   10.702630] Failure registering capabilities with primary security module.
[   10.722881] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   10.722889] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.726697] ACPI: Thermal Zone [THM] (40 C)
[   11.800621] usbcore: registered new interface driver usbfs
[   11.800673] usbcore: registered new interface driver hub
[   11.800739] usbcore: registered new device driver usb
[   11.801946] USB Universal Host Controller Interface driver v3.0
[   11.802054] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   11.802072] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.802076] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.802325] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.802360] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[   11.802590] usb usb1: configuration #1 chosen from 1 choice
[   11.802641] hub 1-0:1.0: USB hub found
[   11.802656] hub 1-0:1.0: 2 ports detected
[   11.903627] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   11.903634] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   11.903651] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.903655] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.903713] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.903742] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[   11.903925] usb usb2: configuration #1 chosen from 1 choice
[   11.903976] hub 2-0:1.0: USB hub found
[   11.903991] hub 2-0:1.0: 2 ports detected
[   11.920406] SCSI subsystem initialized
[   11.968858] libata version 2.21 loaded.
[   12.007592] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   12.007599] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   12.007616] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.007621] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.007690] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   12.007720] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[   12.007887] usb usb3: configuration #1 chosen from 1 choice
[   12.007935] hub 3-0:1.0: USB hub found
[   12.007953] hub 3-0:1.0: 2 ports detected
[   12.116388] ata_piix 0000:00:1f.1: version 2.11
[   12.116408] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   12.116421] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   12.116476] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.116635] scsi0 : ata_piix
[   12.116738] scsi1 : ata_piix
[   12.116938] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[   12.116943] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    4.872000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.876000] Time: acpi_pm clocksource has been installed.
[    4.932000] ata1.00: ATAPI: QSI CD-RW/DVD-ROM SBW242U, UD25, max UDMA/33
[    5.104000] ata1.00: configured for UDMA/33
[    5.268000] ata2.00: ATA-6: IC25N030ATMR04-0, MOAOAD0A, max UDMA/100
[    5.268000] ata2.00: 58605120 sectors, multi 8: LBA48 
[    5.284000] ata2.00: configured for UDMA/100
[    5.288000] scsi 0:0:0:0: CD-ROM            QSI      CDRW/DVD SBW242U UD25 PQ: 0 ANSI: 5
[    5.288000] scsi 1:0:0:0: Direct-Access     ATA      IC25N030ATMR04-0 MOAO PQ: 0 ANSI: 5
[    5.288000] b44.c:v1.01 (Jun 16, 2006)
[    5.288000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[    5.292000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0f:1f:26:00:5a
[    5.292000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    5.292000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[    5.292000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    5.292000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.296000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    5.296000] ehci_hcd 0000:00:1d.7: debug port 1
[    5.296000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    5.296000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf6effc00
[    5.300000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.300000] usb usb4: configuration #1 chosen from 1 choice
[    5.300000] hub 4-0:1.0: USB hub found
[    5.300000] hub 4-0:1.0: 6 ports detected
[    5.332000] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    5.332000] Uniform CD-ROM driver Revision: 3.20
[    5.332000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.340000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    5.340000] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    5.360000] sd 1:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[    5.360000] sd 1:0:0:0: [sda] Write Protect is off
[    5.360000] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.360000] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.360000] sd 1:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[    5.360000] sd 1:0:0:0: [sda] Write Protect is off
[    5.360000] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.360000] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.360000]  sda: sda1 sda2
[    5.408000] sd 1:0:0:0: [sda] Attached SCSI disk
[    5.732000] Attempting manual resume
[    5.732000] swsusp: Resume From Partition 8:1
[    5.732000] PM: Checking swsusp image.
[    5.736000] PM: Resume from disk failed.
[    5.760000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.760000] EXT3-fs: write access will be enabled during recovery.
[    7.848000] kjournald starting.  Commit interval 5 seconds
[    7.848000] EXT3-fs: recovery complete.
[    7.848000] EXT3-fs: mounted filesystem with ordered data mode.
[   19.484000] NET: Registered protocol family 17
[   20.056000] Linux agpgart interface v0.102 (c) Dave Jones
[   20.084000] agpgart: Detected an Intel 855GM Chipset.
[   20.084000] agpgart: Detected 892K stolen memory.
[   20.096000] agpgart: AGP aperture is 128M @ 0xe8000000
[   20.116000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.164000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.200000] intel_rng: FWH not detected
[   20.252000] iTCO_vendor_support: vendor-support=0
[   20.252000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   20.252000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)
[   20.252000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.732000] ieee80211_crypt: registered algorithm 'NULL'
[   20.780000] Yenta: CardBus bridge found at 0000:02:04.0 [1028:017f]
[   20.780000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.780000] Yenta: Routing CardBus interrupts to PCI
[   20.780000] Yenta TI: socket 0000:02:04.0, mfunc 0x00001002, devctl 0x64
[   21.012000] Yenta: ISA IRQ mask 0x0478, PCI irq 11
[   21.012000] Socket status: 30000007
[   21.012000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   21.012000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   21.012000] cs: IO port probe 0xd000-0xefff: clean.
[   21.012000] pcmcia: parent PCI bridge Memory window: 0xf8000000 - 0xfdffffff
[   21.012000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x35ffffff
[   21.360000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.360000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.420000] input: PC Speaker as /class/input/input2
[   21.532000] bcm43xx driver
[   21.532000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   21.832000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[   21.832000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   21.888000] cs: IO port probe 0x100-0x3af: clean.
[   21.892000] cs: IO port probe 0x3e0-0x4ff: clean.
[   21.892000] cs: IO port probe 0x820-0x8ff: clean.
[   21.892000] cs: IO port probe 0xc00-0xcf7: clean.
[   21.892000] cs: IO port probe 0xa00-0xaff: clean.
[   22.052000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x256eb1, caps: 0x804713/0x0
[   22.092000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   22.660000] intel8x0_measure_ac97_clock: measured 55326 usecs
[   22.660000] intel8x0: clocking to 48000
[   23.484000] lp: driver loaded but no devices found
[   23.564000] Adding 996020k swap on /dev/sda1.  Priority:-1 extents:1 across:996020k
[   24.000000] EXT3 FS on sda2, internal journal
[   25.548000] ACPI: AC Adapter [AC] (off-line)
[   25.596000] No dock devices found.
[   25.908000] ACPI: Battery Slot [BAT0] (battery present)
[   25.932000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   25.932000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   26.000000] input: Lid Switch as /class/input/input4
[   26.004000] ACPI: Lid Switch [LID]
[   26.048000] input: Power Button (CM) as /class/input/input5
[   26.052000] ACPI: Power Button (CM) [PBTN]
[   26.096000] input: Sleep Button (CM) as /class/input/input6
[   26.100000] ACPI: Sleep Button (CM) [SBTN]
[   26.496000] ACPI: Invalid _PSS data: freq is zero
[   27.832000] ppdev: user-space parallel port driver
[   28.136000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   28.292000] audit(1201553414.627:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4581 profile="/usr/sbin/cupsd"
[   28.436000] apm: BIOS not found.
[   28.816000] Failure registering capabilities with primary security module.
[   29.300000] Bluetooth: Core ver 2.11
[   29.300000] NET: Registered protocol family 31
[   29.300000] Bluetooth: HCI device and connection manager initialized
[   29.300000] Bluetooth: HCI socket layer initialized
[   29.348000] Bluetooth: L2CAP ver 2.8
[   29.348000] Bluetooth: L2CAP socket layer initialized
[   29.436000] Bluetooth: RFCOMM socket layer initialized
[   29.436000] Bluetooth: RFCOMM TTY layer initialized
[   29.436000] Bluetooth: RFCOMM ver 1.8
[   30.280000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   32.512000] [drm] Initialized drm 1.1.0 20060810
[   32.516000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   32.520000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   32.524000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   52.336000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   62.972000] NET: Registered protocol family 10
[   62.972000] lo: Disabled Privacy Extensions
[   62.972000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   74.452000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   96.516000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  118.572000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  140.636000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  162.704000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  284.820000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  406.880000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  528.940000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  622.324000] end_request: I/O error, dev sr0, sector 52392
[  622.324000] Buffer I/O error on device sr0, logical block 6549
[  622.480000] end_request: I/O error, dev sr0, sector 52392
[  622.480000] Buffer I/O error on device sr0, logical block 6549
[  622.628000] end_request: I/O error, dev sr0, sector 52408
[  622.628000] Buffer I/O error on device sr0, logical block 6551
[  622.784000] end_request: I/O error, dev sr0, sector 52408
[  622.784000] Buffer I/O error on device sr0, logical block 6551
[  622.972000] end_request: I/O error, dev sr0, sector 52408
[  622.972000] Buffer I/O error on device sr0, logical block 6551
[  623.128000] end_request: I/O error, dev sr0, sector 52408
[  623.128000] Buffer I/O error on device sr0, logical block 6551
[  623.284000] end_request: I/O error, dev sr0, sector 52408
[  623.284000] Buffer I/O error on device sr0, logical block 6551
[  623.476000] end_request: I/O error, dev sr0, sector 52408
[  623.476000] Buffer I/O error on device sr0, logical block 6551
[  623.628000] end_request: I/O error, dev sr0, sector 52408
[  623.628000] Buffer I/O error on device sr0, logical block 6551
[  623.784000] end_request: I/O error, dev sr0, sector 52408
[  623.784000] Buffer I/O error on device sr0, logical block 6551
[  624.272000] UDF-fs: No VRS found
[  624.300000] ISO 9660 Extensions: Microsoft Joliet Level 3
[  624.312000] ISOFS: changing to secondary root
[  651.000000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  773.084000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  895.232000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1017.312000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1139.380000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1261.436000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1383.508000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1505.640000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1627.700000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1749.776000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
```


Bootup.txt:
```

 A modem device/card may be disabled at bootup, due to a variety of causes.
 Look at the bootup diagnostics record dmesg.txt  written out through:
 $ dmesg > dmesg.txt
 and try to garner some understanding from it.  Possibilities therein are too
 diverse to be automagically processed by scanModem. A line including the PCI
 bus slot 00:1f.6 of your modem, and "disable" or "disabling" predicts problems,
 though sometimes corrected later in the bootup.  Similarly a line with "@"
 in the interrupt (IRQ) for your 00:1f.6 slot is predictive of problems. 

 Possible corrections are:
 0) Get unloading.gz from http://phep2.technion.ac.il/linmodems/packages/
 This script unloads excess drivers which may be competing for resources. 
 Before trying to set up the modem, do:
 $ gunzip unloading.gz
 $ chmod +x unloading
 $ su - root 
 # ./unloading
 Or for Ubuntu related Distros
 $ sudo ./unloading
 
 1) Within the boot up BIOS, change from a Windows to a non-PNP/Other Operating System type.
 Instructions for accessing BIOS are at:
 http://linmodems.technion.ac.il/resources.html within:  Additional Resourcces.
 2a) Add an option "pci=routeirq" to the kernel boot up line.
 Here is an example paragraph from  /boot/grub/menu.lst :
       title           Ubuntu, kernel 2.6.15-26-686
       root            (hd0,6)
       kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda7 ro pci=routeirq
       initrd          /boot/initrd.img-2.6.15-26-686
       savedefault
 2b) Same as above, but use "pollirq" instead of "pci=routeirq".
 3) Within some BIOS setups, IRQ assignments can be changed.
 4) On non-laptop systems, moving the modem card to another slot has helped.
 5) Sometimes upgrading the kernel solves the problem.
 6) Sometimes downgrading the kernel solves the problem.
 7) Sometimes changing the Linux distribution solves the problem.

```

---

### Post by Sepero on 2008-01-29
This device seems to be your modem:
00:1f.6	8086:24c6	14e4:4d64	Modem: Intel Corporation 82801DB/DBL/DBM


The driver listed in this thread will not help you. Please refer to the following page to resolve getting your modem working:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by go_beep_yourself on 2008-01-29
> **Sepero said:**
> This device seems to be your modem:
00:1f.6	8086:24c6	14e4:4d64	Modem: Intel Corporation 82801DB/DBL/DBM


The driver listed in this thread will not help you. Please refer to the following page to resolve getting your modem working:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

I had already been there several times, but it hasn't been obvious which driver I need. That's why I'm here asking for help.

---

### Post by chuckman78 on 2008-01-29
Hi.

I would suggest to you to go to **_[http://linmodems.org/]("http://linmodems.org/")_** and read the info on subscribing to their mailing list and send them the info you showed to us. There is a big knowledge base of fixes for most modems and you will get an answer (either positive or negative). This post should be used only for Intel 537EP based modems, sorry.

Regards,

Carlos.

---

### Post by imac_89 on 2008-02-06
Alright, i have just downloaded and installed the .deb file. It has run and I have read the "success.txt" file to a "T". I even rebooted my laptop before testing the dial-up connection. When I rebooted the Restricted Driver utility popped up saying that it found new hardware. That is all good and fun, but I am still getting this error:
```

will@will-laptop:~$ sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Err>: Cannot open /dev/modem: No such file or directory
WvDial<Err>: Cannot open /dev/modem: No such file or directory
WvDial<Err>: Cannot open /dev/modem: No such file or directory
will@will-laptop:~$ 

```I am unsure whether this has been covered, but after reading this thread, I still haven't thought of a solution, I am looking for your input please.

---

### Post by twin_57103 on 2008-02-07
I'm trying to set up an Intel 537ep modem on an Ubuntu 7.10 machine (P3, 500 MHz, definitely not a speed demon but functional).  It's been quite a headache.  I've posted it separately: [http://ubuntuforums.org/showthread.php?t=683315]("http://ubuntuforums.org/showthread.php?t=683315"), but I'm still stuck.  I have ethernet access on the computer through my DSL, but the end user has only dial-up.  I have a couple other PCI modems laying around, but this one seemed the best place to start.

  I've installed the driver as per this thread and its links.  When I  try to connect via the integrated connection manager, it simply does nothing.  I have also installed GnomePPP, which gives in its logs
/home/leroy/.wvdial.conf<Warn>: Ignoring malformed input line: ";Do NOT edit this file by hand!"
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Err>: Cannot open /dev/modem: Device or resource busy
WvDial<Err>: Cannot open /dev/modem: Device or resource busy
WvDial<Err>: Cannot open /dev/modem: Device or resource busy

I've also had this one once:
home/leroy/.wvdial.conf<Warn>: Ignoring malformed input line: ";Do NOT edit this file by hand!"
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0
WvDial<*1>: Re-Sending: ATZ
WvDial<Err>: Modem not responding.

My roommate picked up the phone to modem noise once, but I have never heard any modem sounds directly, and I'm not sure when or how it activated.

lspci | grep 537 gives 01:0a.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
lspci | grep 536 gives nothing

wvdial.conf
[Dialer Defaults]
Phone =
Username =
Password =
New PPPD = yes

Obviously wvdial.conf is not yet set up.  Can I manually edit this file or how should I configure it?  I'm not 100% sure of the end-user's password (he wasn't last time I asked, either), but it can be retrieved somehow.  If I could get to the point of having the password refused, I could return it to the user and let him figure it out (the connection is set up properly in the integrated connection manager, but not wvdial).

I'd appreciate any help that you can give - thanks for your time.

---

### Post by chuckman78 on 2008-02-13
Guys, this is a tipycal wvdial.conf file:

```
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
SetVolume = 3
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+GCI=14
Init3 = ATM1L3
Init4 = ATS11 = 20
Carrier Check = no
FlowControl = CRTSCTS
Stupid Mode = yes
Username = ###
Password = ###
Phone = ###
Auto DNS = yes
Check DNS = yes
Auto Reconnect = yes
Idle Seconds = 0
Abort on Busy = no
Abort on No Dialtone = no
Dial Attempts = 0
New PPPD = yes
```

You can edit wvdial.conf by doing this:

Execute in a terminal box:

```
sudo gedit /etc/wvdial.conf
```

Keep in mind that I am taking for granted you are using Gnome. In case you are using KDE then substitute gedit for kate in the previous line.

Copy, paste and complete the info on the wvdial.conf file (username, password and phone). Save and exit.

Execute:

```
sudo wvdial
```

Regards,

Carlos.

---

### Post by steve457 on 2008-03-26
I was able to successfully install the driver using the .deb install package and everything seemed to work great.  I tested the callerID function using the NCID program and it worked.  The problem is that the driver does not seem to work after I reboot the machine.  If I do a lsmod I can see the driver is loaded, but for some reason the NCID program will no longer be able to find the modem.  Has anyone else experienced this problem?  Any ideas on what may be causing this to happen?  The only way I have been able to get the driver to work again is to re-install it using the .deb package everytime I reboot.

---

### Post by Sepero on 2008-03-26
Hi Steve457,
Is it possible that you or someone has manually modified the way your system boots?
Possibly your /etc/rc* directories?


The reason I ask is because, the installer places a file in your startup scripts-
/etc/init.d/537_boot

The above file is linked to from all the /etc/rc* startup directories.

After the installer runs, it simply loads the module by executing this command-
/etc/init.d/537_boot restart

If the module itself is not deleted from your system, the installer package should Not have to be reinstalled. The actual module is located here-
/lib/modules/Intel537EPDriverForGutsy.ko



On reboot, try this-
/etc/init.d/537_boot restart

If that works, then your /etc/rc* directories may have been inappropriately modified.

---

### Post by steve457 on 2008-03-26
I haven't modified  the way the system boots as far as I am aware.  I verified and do see liniks from most of the rc.X directories.  The link is from S99537_boot --> /etc/init.d/537_boot.   The only rc directories that do not have this entry are rc.0.d, rc.1.d, and rc6.d.  

I ran /etc/init.d/537_boot restart and let it complete.  It didn't print out any messages, and simply returned the prompt.  This still did not seem to fix things.  Here is output from ncidd, which tries to access the modem.

```

Verbose level: 3
Telephone Line Identifier: -
CID logfile: /var/log/cidcall.log
CID logfile maximum size: 110000 bytes
Data logfile: /var/log/ciddata.log
TTY port opened: /dev/modem
TTY port speed: 19200
TTY lock file: /var/lock/LCK..modem
TTY port control signals enabled
No Modem Response
Try 1 to init modem: return = 2.
AT
Try 2 to init modem: return = 2.
 Z S0=0 E1 V1 Q0
Try 3 to init modem: return = 2.
No Modem Response
Try 4 to init modem: return = 2.
AT
Try 5 to init modem: return = 2.
 Z S0=0 E1 V1 Q0
Try 6 to init modem: return = 2.
No modem found: /dev/modem
Terminated:  03/26/2008 12:05

```

So, it was still unable to find the modem or access it.  I then reinstalled the drivers and re-ran the same command.

```
Verbose level: 3
Telephone Line Identifier: -
CID logfile: /var/log/cidcall.log
CID logfile maximum size: 110000 bytes
Data logfile: /var/log/ciddata.log
TTY port opened: /dev/modem
TTY port speed: 19200
TTY lock file: /var/lock/LCK..modem
TTY port control signals enabled
AT Z S0=0 E1 V1 Q0
Try 1 to init modem: return = 2.

OK
Try 2 to init modem: return = 0.
Modem initialized.
AT+VCID=1
OK
Modem set for CallerID.
Network Port: 3333
Wrote pid 1585 in pidfile: /var/run/ncidd.pid
```

Now the modem was found.  If I reboot, however, the modem will not be found.  Any other suggestions?  Btw, this is on the gutsy release.

---

### Post by Sepero on 2008-03-26
> **steve457 said:**
> The only rc directories that do not have this entry are rc.0.d, rc.1.d, and rc6.d.
That's corrent.

Are any of these files deleted after reboot?
/lib/modules/Intel537EPDriverForGutsy.ko
/lib/modules/2.6.22-12-generic/kernel/drivers/char/Intel537.ko
/lib/modules/2.6.22-13-generic/kernel/drivers/char/Intel537.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/char/Intel537.ko
/lib/modules/2.6.22-15-generic/kernel/drivers/char/Intel537.ko

(The last four are only symbolic links to the first file.)

If those files all still exist, then you might want to check the permissions on all the files (including startup scripts) before and after reboot.

Other than that, I'm not really sure what could be causing the problem. Perhaps it could be your ncidd program? Check to see if the module is loaded after reboot by running:
lsmod | grep 537

If it prints something like 'Intel537', then the module is loaded and the ncidd program could be at fault.

---

### Post by steve457 on 2008-03-27
I checked and all the *.ko do still exist after reboot.  I also did

lsmod | grep 537

which returned

Intel537             4148880  0

So it looks like the driver is installed correctly.  It's strange though that the ncidd program still does not recognize the modem until after I re-install the modem driver package.  Is there another program I could test with to see if the modem is recognized?  Are there any additional commands I could try to re-start the modem drivers?

Thanks.

---

### Post by Sepero on 2008-03-27
It's appears that there may be an error in you ncidd program. You can test the modem with any regular dialing app: Kppp, pppd, minicom-


I don't really understand why it works after reinstall.

Rather than un/reinstall, you can try simply removing and reinserting the module, like this:
sudo rmmod Intel537
sudo modprobe Intel537


I hope that helps.

---

### Post by steve457 on 2008-03-27
Ok, very strange.  I reinstalled the module using the commands you mentioned:

sudo rmmod Intel537
sudo modprobe Intel537

And after that, ncidd worked fine and was able to find the modem.  It would appear that somehow the module is not installing correctly on the initial reboot, even though lsmod showed it as running.  I am stumped on how I could resolve this..  Would it be bad to try and hack rc.local to do those two commands?  Does rc.local get executed at the end of the boot process?  any other suggestions?

Thanks again for your help.

---

### Post by Sepero on 2008-03-27
The package sets the Intel537 module to be one of the absolutely last things loaded at priority 99 (Startup scripts range from 00-99).

So you could try putting the two "sudo" module lines in your /etc/rc.local file, but I wouldn't have much hope of it working.

Have you tried testing the module with Kppp?

---

### Post by i2k on 2008-04-30
Will this driver work with Ubuntu 8.04?

---

### Post by chuckman78 on 2008-05-01
Probably. We will try to release a package updated for 8.04 for this weekend.

Regards,

Carlos.

---

### Post by i2k on 2008-05-01
Thanks man, I need that driver so i don't need to boot Windoze to get on the internet anymore.

---

### Post by O_Planeta on 2008-05-10
Hello, 
I install ubuntu 8.04 on PC and has the modem 537-ep.

Unhappy, the package offers dont install via synaptic because the newer kernel (2.64. The package kernel is 2.62). I can force the install this version via dpkg? How?

I too try make the drive.... I do it in ubuntu 6.06. But don't know when look it. (Please, can you send me link for source?).

Thanks... (Sorry my poor English)...

---

### Post by luka78 on 2008-05-11
I am trying to install this driver on Xubuntu 8.04 but i always have same problem:

root@luka:/home/luka/Desktop/intel537EP# make 537
Module precompile check
Current running kernel is: 2.6.24-16-generic
/lib/modules... autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
version.h matches running kernel
2.6.24-16-generic
make[1]: Entering directory `/home/luka/Desktop/intel537EP/coredrv'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/luka/Desktop/intel537EP/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/luka/Desktop/intel537EP/coredrv/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[2]: *** [_module_/home/luka/Desktop/intel537EP/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [537core_26] Error 2
make[1]: Leaving directory `/home/luka/Desktop/intel537EP/coredrv'
2.6.24-16-generic
Failed to build driver 


What am I doing wrong?

Thank you

---

### Post by Sepero on 2008-05-12
chuckman78-
I've sent you an email and a private message about creating a new driver. I don't know if you've gotten either of them. Just send me the new compiled driver if you've got it.

---

### Post by Sepero on 2008-05-14
[COLOR="Red"]MODERATORS- please delete this post[/COLOR]

---

### Post by Sepero on 2008-05-15
The first Hardy release is now ready for download! See the start of the thread.

---

### Post by swoll1980 on 2008-05-15
when you click the hardy link you get a driver for fiesty and when you click the 537 link you get a 536 driver

---

### Post by Sepero on 2008-05-16
Thanks swoll111980. I fixed the Hardy link, but I'm not sure what you mean by "537 link to 536 driver".

---

### Post by Barakk on 2008-05-29
I tried installing  the file intel537ep-hardy_1-Philippe.Vouters_i386.deb on Ubuntu 8.04, which was installed using Wubi, but it fails and this is the output from the terminal:

```
(Reading database ... 98100 files and directories currently installed.)
Preparing to replace intel537ep-hardy 1.0 (using .../intel537ep-hardy_1-Philippe.Vouters_i386.deb) ...
Unpacking replacement intel537ep-hardy ...
 Removing any system startup links for /etc/init.d/537_boot ...
     /etc/rc2.d/S99536_boot
     /etc/rc3.d/S99536_boot
     /etc/rc4.d/S99536_boot
     /etc/rc5.d/S99536_boot
Setting up intel537ep-hardy (1.0) ...
Intel536EP Modem Driver and Boot Scripts copied successfully
Updating modules (/sbin/depmod)
Installing boot scripts
 Adding system startup for /etc/init.d/537_boot ...
     /etc/rc2.d/S99537_boot -> ../init.d/537_boot
     /etc/rc3.d/S99537_boot -> ../init.d/537_boot
     /etc/rc4.d/S99537_boot -> ../init.d/537_boot
     /etc/rc5.d/S99537_boot -> ../init.d/537_boot
Loading 537EP driver
mknod: missing operand after `1'
Try `mknod --help' for more information.
chgrp: cannot access `/dev/537': No such file or directory
chmod: cannot access `/dev/537': No such file or directory
```

I have no idea how to fix this problem and I would appreciate any ideas on how to fix it.

Thanks.

---

### Post by krcabrer on 2008-05-29
Hi ubuntu gurus:

I got the same problem with the compilation of an INTEL 537
modem card.

When I type sudo make 537, I obtain the error:

scripts/Makefile.build:46: *** CFLAGS was changed in "/home/kenneth/downloads/modem/intel-537EP_secure-2.60.80.0/coredrv/Makefile". Fix it to use EXTRA_CFLAGS. 

What can I do?

Thank you for your help.

Kenneth.

PS: When I type sudo make check, I obtain:
  Module precompile check
   Current running kernel is: 2.6.24-16-rt
   /lib/modules...   autoconf.h exists
   autoconf.h matches running kernel
   version.h matches running kernel

---

### Post by chuckman78 on 2008-05-30
Hi Barakk.

This looks like a packing issue. I will try to contact Sepero who is the expert in the area.

Regards,

Carlos.

---

### Post by chuckman78 on 2008-05-30
> **krcabrer said:**
> Hi ubuntu gurus:

I got the same problem with the compilation of an INTEL 537
modem card.

When I type sudo make 537, I obtain the error:

scripts/Makefile.build:46: *** CFLAGS was changed in "/home/kenneth/downloads/modem/intel-537EP_secure-2.60.80.0/coredrv/Makefile". Fix it to use EXTRA_CFLAGS. 

What can I do?

Thank you for your help.

Kenneth.

PS: When I type sudo make check, I obtain:
  Module precompile check
   Current running kernel is: 2.6.24-16-rt
   /lib/modules...   autoconf.h exists
   autoconf.h matches running kernel
   version.h matches running kernel

Hi Kenneth.

Have you instead tried to use the binary package from the first post of this thread. Please let us know about your progress.

Regards,

Carlos.

---

### Post by krcabrer on 2008-05-30
> **chuckman78 said:**
> Hi Kenneth.

Have you instead tried to use the binary package from the first post of this thread. Please let us know about your progress.

Regards,

Carlos.

Thank you for your help, but I have an AMD64 and the .deb is
for a 386 system.

Would you help me with the AMD64 .deb version? 
Where can I find it?

Thank you for your help.

Kenneth

---

### Post by chuckman78 on 2008-05-30
> **krcabrer said:**
> Thank you for your help, but I have an AMD64 and the .deb is
for a 386 system.

Would you help me with the AMD64 .deb version? 
Where can I find it?

Thank you for your help.

Kenneth

That would be a problem Kenneth. The source driver from Intel does not support 64 bit. Sorry.

Regards,

Carlos.

---

### Post by Sepero on 2008-05-31
To krcabrer:
Unfortunately, chuckman78 is right. You must run your system in 32bit mode for you to operate your modem with Ubuntu.



To Barakk:
The problem appears to be in either the file /etc/init.d/537_boot or your copy of the program 'mknod'.

I don't make the file /etc/init.d/537_boot so I don't know a lot about it.

My suggestion is to uninstall and reinstall the package 'coreutils'. (coreutils contains the program mknod) If you don't have an internet connection download the latest coreutils from here-
[http://mirrors.kernel.org/ubuntu/pool/main/c/coreutils/](http://mirrors.kernel.org/ubuntu/pool/main/c/coreutils/)

Download coreutils_ (6.10 or higher) ubuntu*_i386.deb

Then click on it to reinstall the package. Last, make sure you have the modem driver installed, and reboot.

That is the most simple solution, so hopefully that will clear it up for you.

---

### Post by paxon01 on 2008-05-31
Hi, everyone!
I'm new here...And I'm glad to be with you folks...

To Barrakk:
Problem is indeed in /etc/init.d/537_boot !
Try to change this line in file:

 mknod $devnode c $major 1

with:

 mknod $devnode c $major 240 1

Goodbye!

---

### Post by Barakk on 2008-06-02
I downloaded and reinstalled coreutils_6.10-3ubuntu2_i386.deb, reinstalled intel537ep-hardy_1-Philippe.Vouters_i386.deb, and then rebooted, but still no luck.It gives me the exact same message in the terminal as before, but this time it says that the package was installed successfully.

When I changed the line 

mknod $devnode c $major 1

to 

mknod $devnode c $major 240 1

and saved the file /etc/init.d/537_boot, it reverted back to the old one once I reinstalled intel537ep-hardy_1-Philippe.Vouters_i386.deb.

I think the problem is getting mknod line to stay changed after I reinstall the driver. Does anyone have a solution to this?

Thanks for all your help,

Barakk. :)

---

### Post by Sepero on 2008-06-02
Thanks for the input paxon01.

To Barakk:
Try this:
1. Modify /etc/init.d/537_boot as root (sudo) like paxon01 said
2. Reboot

See if the modem works for you then.

---

### Post by Barakk on 2008-06-03
To Sepero:

I modified /etc/init.d/537_boot as paxon01 said, but when I install the driver it reverts 

mknod $devnode c $major 240 1

back to

mknod $devnode c $major 1

, and then gives the same message. I do not know why it is doing this. Do you have any ideas?

Thank you, 

Barakk.

---

### Post by Sepero on 2008-06-04
Barakk, I think you made a mistake. I didn't say "re-install the driver" the second time. Do what I said again, but don't re-install the driver.

Best of Luck

---

### Post by Barakk on 2008-06-07
I did what you said Sepero, and I can dial now with wvdial. Thankyou Sepero and paxon01! 

:D

---

### Post by Sepero on 2008-06-18
Ubuntu Forums was a great place for me to start releasing these drivers, but now the thread is becoming long. There are posts that should be deleted to speed finding answers, and I cannot do this because I do not have the privileges.

In an effort to increase benefit to the users, I have created a google group where I should start posting future releases. On this group I wish to maintain a FAQ, which members may help edit. If you wish to find future help, or possibly help others, please join the group.

[http://groups.google.com/group/ubuntu-modems](http://groups.google.com/group/ubuntu-modems)

---

### Post by jdogzilla on 2008-06-18
with new kernel (v19), this is the error I get on reinstall

Loading 537EP driver
FATAL: Error inserting Intel537 (/lib/modules/2.6.24-19-generic/kernel/drivers/char/Intel537.ko): Invalid module format
insmod: can't read 'Intel537': No such file or directory
error loading Intel537
ERROR: Module Intel537 does not exist in /proc/modules

any suggestions?

---

### Post by Sepero on 2008-06-19
Thanks for reporting jdogzilla.

When we package these drivers, we make them in -hopes- that they will work with future Linux Kernels. It was unanticipated that Ubuntu Hardy would release so many kernels.

Try this command:
```
sudo ln -s /lib/modules/Intel537EPDriverForHardy.ko /lib/modules/2.6.24-19-generic/kernel/drivers/char/Intel537.ko
```


ln -s
 *Make a symbolic link.

/lib/modules/Intel537EPDriverForHardy.ko
 *Link to this file.

/lib/modules/2.6.24-19-generic/kernel/drivers/char/Intel537.ko
 *Link from this location.



Let us know how it works out.


sep

---

### Post by jdogzilla on 2008-06-19
No dice guys, still get the same error. Actually I had already tried that. 


% sudo /sbin/insmod /lib/modules/2.6.24-19-generic/kernel/drivers/char/Intel537.ko
insmod: error inserting '/lib/modules/2.6.24-19-generic/kernel/drivers/char/Intel537.ko': -1 Invalid module format

% sudo /etc/init.d/537_boot start
FATAL: Error inserting Intel537 (/lib/modules/2.6.24-19-generic/kernel/drivers/char/Intel537.ko): Invalid module format
insmod: can't read 'Intel537': No such file or directory
error loading Intel537
ERROR: Module Intel537 does not exist in /proc/modules

It worked when I had 2.6.24-16-generic, but does not work with 19.  Anyone else having problems with this?  Any suggestions?

---

### Post by Sepero on 2008-06-20
Thanks jodogzilla. We will look into releasing a new driver.

---

### Post by jdogzilla on 2008-06-26
Any luck building this driver for the new kernel?

---

### Post by medya on 2008-07-13
isn't it a shame which there is NO way to make it work for 64bit ubuntus ?

---

### Post by chuckman78 on 2008-07-13
jdogzilla:

We have just compiled the new driver. Packaging will be ready soon. We need beta testers as we HAVEN'T done too much testing ourself (time constraints). Keep visiting [http://groups.google.com/group/ubuntu-modems]("http://groups.google.com/group/ubuntu-modems") for the updates.

Regards, 

Carlos
aka chuckman78
aka Carlos :)

---

### Post by Sepero on 2008-07-14
Updated Hardy driver is now available.

---

