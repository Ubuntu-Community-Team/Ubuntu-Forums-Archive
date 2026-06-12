---
title: "Canon Pixma iP100 driver 12.04"
date: 2013-04-14
forum: Hardware
---

### Post by toopho on 2013-04-14
I have followed the instructions in this page:

[http://askubuntu.com/questions/186267/how-can-i-install-canon-pixma-ip100-driver-for-ubuntu-12-04lts-64bit](http://askubuntu.com/questions/186267/how-can-i-install-canon-pixma-ip100-driver-for-ubuntu-12-04lts-64bit)

Now the printer seems to be properly installed and I get the message "printing" and "Page printed" but the printer doesn't actually do anything. Maybe the problem is that I am using the 32bit version of the driver and that's the only one they have in the [canon web page]("http://es.software.canon-europe.com/products/0010626.asp").
 
I have been able to find more information about the iP100 in the forums but it was always involving another version of ubuntu or another similar printer of Canon. Apparently there were some problems with some files of the driver not being in the right directory or not having enough permitions. I can't not follow those instructions because I have a different version of ubuntu.

This is my output of uname -a
```
Linux Ferrari-1100 3.2.0-40-generic #64-Ubuntu SMP Mon Mar 25 21:22:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

$cat /var/log/cups/error_log
```
E [14/Apr/2013:15:14:24 +0200] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [14/Apr/2013:15:14:25 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'iP100-series-Gray..' already exists
W [14/Apr/2013:15:14:25 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'iP100-series-RGB..' already exists
W [14/Apr/2013:15:14:25 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-iP100-series' already exists
E [14/Apr/2013:15:29:24 +0200] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [14/Apr/2013:15:29:30 +0200] failed to CreateProfile: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

---

### Post by toopho on 2013-04-14
I went to System Configuration -> Printers -> Printer Options and where it says "allowed users" I typed in my username in a new line as it is spelled.

$lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 04a9:10b9 Canon, Inc. 
Bus 001 Device 004: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 005 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
```

The following commands do not have any output:
$dmesg | grep canon
$dmesg | grep ip100

I took a look at the FAQ file that comes with the driver and it says:

Q - Printing does not start.

A- The printer registered to the spooler may have stopped.
Open the CUPS Web interface ([http://localhost:631/](http://localhost:631/)), and check the status of the printer.
If the status is [stopped], click [Start Printer] to restart the printer.

So with firefox, clicking, I go to localhost:631/printers/ and where it says Status I can read...   ...well I have seen it change from Idle to Stopped and now says: Idle - "Rejecting Jobs". So I click on "iP100-series" and on "Maintanance" I click on "Accept jobs" and reboot the printer.  Then I click on "print test page" and it says something like <Error in the printer "connecting to printer">. On "completed jobs" it tells there are six completed jobs. Where it says "Administration" I click on "Set as server default".

Don't really know what I am doing. Going for reboot now...

---

### Post by pdc on 2013-04-14
I guess if we see if the drivers were installed as you planned 

If you copy and paste

> [COLOR="#FF0000"]sudo dpkg -l | grep cnijfilter[/COLOR] into a terminal........use the Menu...........Edit.......paste functions of the terminal.........

Canon supply a driver package directly

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100119002.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100119002.html)

You say

> Maybe the problem is that I am using the 32bit version of the driver

.........if that is so, perhaps best you delete what you have installed...........go to synaptic and look for cnij and delete what is listed .....

this site supplies a 64bit package

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100119002.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100119002.html)

the commands would be

> cd Downloads

> cnijfilter-ip100series-3.70-1-deb.tar.gz

> tar -zxvf cnijfilter-ip100series-3.70-1-deb.tar.gz

> cd cnijfilter-ip100series-3.70-1-deb

> sudo ./install.sh

...........the install script should install the appropriate drivers.......

---

### Post by toopho on 2013-04-14
```

$dmesg
...
[   38.520053] usb 1-5: new high-speed USB device number 6 using ehci_hcd
[   38.653805] hub 1-5:1.0: USB hub found
[   38.654095] hub 1-5:1.0: 4 ports detected
[  118.140086] usb 1-3: new high-speed USB device number 7 using ehci_hcd
[  118.310721] usblp0: USB Bidirectional printer dev 7 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10B9
[  118.311438] usbcore: registered new interface driver usblp
[  119.846136] usblp0: removed
[  119.867353] usblp0: USB Bidirectional printer dev 7 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10B9
[  257.503537] usblp0: removed
[  261.003377] usblp0: USB Bidirectional printer dev 7 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10B9
$lsusb
...
Bus 001 Device 007: ID 04a9:10b9 Canon, Inc. 
```

I have tried to follow the instructions in this post:
[http://ubuntuforums.org/showthread.php?t=1320222&page=2&p=11027885#post11027885](http://ubuntuforums.org/showthread.php?t=1320222&page=2&p=11027885#post11027885)

```
~$ find /usr/ -name printuiip100
/usr/bin/printuiip100
/usr/share/printuiip100
```
The following command tells me the files are now in /usr/lib32/:
$ find /usr/ -name libcnbp*

And when I go to create the symbolic links, I find out they are already there:

```
/usr/lib32$ ls -l
total 528
drwxr-xr-x 2 root root  12288 abr  9 21:25 gconv
lrwxrwxrwx 1 root root     24 abr  9 21:27 libcnbpcmcm303.so -> libcnbpcmcm303.so.7.03.1
-rw-r--r-- 1 root root  39028 jun  8  2011 libcnbpcmcm303.so.7.03.1
lrwxrwxrwx 1 root root     26 abr  9 21:27 libcnbpcnclapi303.so -> libcnbpcnclapi303.so.3.3.1
-rw-r--r-- 1 root root  15292 jun  8  2011 libcnbpcnclapi303.so.3.3.1
lrwxrwxrwx 1 root root     28 abr  9 21:27 libcnbpcnclbjcmd303.so -> libcnbpcnclbjcmd303.so.3.3.0
-rw-r--r-- 1 root root  15068 jun  8  2011 libcnbpcnclbjcmd303.so.3.3.0
lrwxrwxrwx 1 root root     25 abr  9 21:27 libcnbpcnclui303.so -> libcnbpcnclui303.so.3.3.1
-rw-r--r-- 1 root root  23388 jun  8  2011 libcnbpcnclui303.so.3.3.1
lrwxrwxrwx 1 root root     22 abr  9 21:27 libcnbpess303.so -> libcnbpess303.so.3.1.0
-rw-r--r-- 1 root root 326368 jun  8  2011 libcnbpess303.so.3.1.0
lrwxrwxrwx 1 root root     21 abr  9 21:27 libcnbpo303.so -> libcnbpo303.so.1.0.11
-rw-r--r-- 1 root root  66484 jun  8  2011 libcnbpo303.so.1.0.11
lrwxrwxrwx 1 root root     17 abr  9 21:27 libcnnet.so -> libcnnet.so.1.2.2
-rw-r--r-- 1 root root  32456 jun  8  2011 libcnnet.so.1.2.2
```
Who knows, maybe there is a problem with permissions:

```

$sudo chmod 777 libcn*

$ls /usr/bin/printuiip100 -l
-rwxr-xr-x 1 root root 455788 jun  8  2011 /usr/bin/printuiip100

$ls /usr/share/printuiip100 -l
total 1020
-rw-r--r-- 1 root root   5425 jun  8  2011 black_bar.xpm
-rw-r--r-- 1 root root    500 jun  8  2011 contrast_high.xpm
-rw-r--r-- 1 root root    514 jun  8  2011 contrast_low.xpm
-rw-r--r-- 1 root root   5424 jun  8  2011 cyan_bar.xpm
-rw-r--r-- 1 root root    470 jun  8  2011 cyan_high2.xpm
-rw-r--r-- 1 root root    471 jun  8  2011 cyan_low2.xpm
-rw-r--r-- 1 root root    499 jun  8  2011 density_dark.xpm
-rw-r--r-- 1 root root    500 jun  8  2011 density_light.xpm
-rw-r--r-- 1 root root   1633 jun  8  2011 locale-table
-rw-r--r-- 1 root root   5427 jun  8  2011 magenta_bar.xpm
-rw-r--r-- 1 root root    473 jun  8  2011 magenta_high2.xpm
-rw-r--r-- 1 root root    472 jun  8  2011 magenta_low2.xpm
-rw-r--r-- 1 root root  51708 jun  8  2011 ngptn_ip100.xpm
-rw-r--r-- 1 root root  51708 jun  8  2011 okptn_ip100.xpm
-rw-r--r-- 1 root root 823598 jun  8  2011 printui.glade
-rw-r--r-- 1 root root  32500 jun  8  2011 printui.res
-rw-r--r-- 1 root root   5426 jun  8  2011 yellow_bar.xpm
-rw-r--r-- 1 root root    472 jun  8  2011 yellow_high2.xpm
-rw-r--r-- 1 root root    471 jun  8  2011 yellow_low2.xpm

$ sudo chmod 777 /usr/share/printuiip100/*
```
Well, I think I only have to reinstall the drivers now and see what happens. But what's that "common package" mention in [that thread]("http://ubuntuforums.org/showthread.php?t=1320222")? Downloading from the Canon web page there is only the iP100 package.

---

### Post by pdc on 2013-04-14
> But what's that "common package" mention in

each Canon install has that: the link I suggest includes it: see the thumbnail

I suggest

1) delete what you have installed
2)install as I suggest
3) see how things stand after that

---

### Post by toopho on 2013-04-15
```
~$sudo dpkg -l | grep cnijfilter
ii  cnijfilter-common                      3.50-2ubuntu4                           IJ Printer Driver for Linux.
ii  cnijfilter-ip100series                 2.90-2ubuntu8                           IJ Printer Driver for Linux.

```
Synaptic is not in ubuntu! Trying with software-center, the search for cnij returns plenty of drivers for different printers of Canon. There are only two installed: cnijfilter-common 3.50-2ubuntu4 and cnijfilter-ip100series 2.90-2ubuntu8. I uninstall these two. The package cnijfilter-common:i386 shows as not installed.

```
$ tar -zxvf cnijfilter-ip100series-3.70-1-deb.tar.gz 
cnijfilter-ip100series-3.70-1-deb/
cnijfilter-ip100series-3.70-1-deb/packages/
cnijfilter-ip100series-3.70-1-deb/packages/cnijfilter-common_3.70-1_i386.deb
cnijfilter-ip100series-3.70-1-deb/packages/cnijfilter-common_3.70-1_amd64.deb
cnijfilter-ip100series-3.70-1-deb/packages/cnijfilter-ip100series_3.70-1_amd64.deb
cnijfilter-ip100series-3.70-1-deb/packages/cnijfilter-ip100series_3.70-1_i386.deb
cnijfilter-ip100series-3.70-1-deb/resources/
cnijfilter-ip100series-3.70-1-deb/resources/printer_zh_utf8.lc
cnijfilter-ip100series-3.70-1-deb/resources/printer_ja_utf8.lc
cnijfilter-ip100series-3.70-1-deb/resources/printer_fr_utf8.lc
cnijfilter-ip100series-3.70-1-deb/install.sh
pil@Ferrari-1100:~/Canon$ cd cnijfilter-ip100series-3.70-1-deb 
pil@Ferrari-1100:~/Canon/cnijfilter-ip100series-3.70-1-deb$ ./install
[sudo] password for pil:
==================================================

Canon Inkjet Printer Driver
Version 3.70
Copyright CANON INC. 2001-2012
All Rights Reserved.

==================================================
Command executed = sudo dpkg -iG ./packages/cnijfilter-common_3.70-1_amd64.deb
Seleccionando paquete cnijfilter-common previamente no seleccionado
(Leyendo la base de datos ... 230177 ficheros o directorios instalados actualmente.)
Desempaquetando cnijfilter-common (de .../cnijfilter-common_3.70-1_amd64.deb) ...
Configurando cnijfilter-common (3.70-1) ...
Procesando disparadores para libc-bin ...
ldconfig deferred processing now taking place
Command executed = sudo dpkg -iG ./packages/cnijfilter-ip100series_3.70-1_amd64.deb
Seleccionando paquete cnijfilter-ip100series previamente no seleccionado
(Leyendo la base de datos ... 230194 ficheros o directorios instalados actualmente.)
Desempaquetando cnijfilter-ip100series (de .../cnijfilter-ip100series_3.70-1_amd64.deb) ...
Configurando cnijfilter-ip100series (3.70-1) ...
Procesando disparadores para libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: No se puede crear el archivo temporal de caché /etc/ld.so.cache~: Permiso denegado
###### This last line means: Couldn't create temporary archive of cache  ...: denied permission
#=========================================================#
#  Register Printer
#=========================================================#
Next, register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
> 

Searching for printers...


#=========================================================#
#  Select Printer
#=========================================================#
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
-----------------------------------------------------------
 0) Update
-----------------------------------------------------------
Target printers detected
1) Canon iP100 series (/dev/usb/lp0)
-----------------------------------------------------------
Currently selected:[1] Canon iP100 series (/dev/usb/lp0)
Enter the value. [1]

#=========================================================#
#  Register Printer
#=========================================================#
Enter the printer name.[IP100]
Command executed = sudo /usr/sbin/lpadmin -p IP100 -m canonip100.ppd -v cnijusb:/dev/usb/lp0 -E

#=========================================================#
#  Set as Default Printer
#=========================================================#
Do you want to set this printer as the default printer?
Enter [y] for Yes or [n] for No.[y]

#=========================================================#
Installation has been completed.
Printer Name : IP100
Select this printer name for printing.
#=========================================================#

```

Note that there was a permission error just before "Register Printer". I have translated it for you.

I see now there are two printers installed (see attachment)[ATTACH=CONFIG]241416[/ATTACH]. When attemping to print the test page with any of these two, the printer ejects the paper halfway before finishing to print the page. Well, at least now the printer is doing something.

```
$ sudo apt-get purge cnij*
...
Utilice «apt-get autoremove» para eliminarlos.
Los siguientes paquetes se ELIMINARÁN:
  cnijfilter-common* cnijfilter-ip100series*
0 actualizados, 0 se instalarán, 2 para eliminar y 0 no actualizados.
Se liberarán 8.892 kB después de esta operación.
¿Desea continuar [S/n]? n
Abortado.
```

---

### Post by toopho on 2013-04-15
In System Configuration > Printers I have disabled the printer iP100-series (the first installation) and I have left the printer iP100 (the second installation) enabled. I have rebooted and now the printer has printed beautifully. It's just strange that the location of the printer is not shown in the attached picture. And that the first installation hasn't gone away. But well, I am glad it is working now, I going to do a series of tests this week, and I'll see if I have to come back here. Thanks for the support, especially to pdc.

EDIT:
I have been able to remove the first installation of the printer through the localhost:631 page.

---

### Post by pdc on 2013-04-15
> [COLOR="#EE82EE"][SIZE=5]I have rebooted and now the printer has printed beautifully[/SIZE][/COLOR].

that's great; delighted to hear that ............ eso es genial, encantado de escuchar que ........I hope my spanish is good enough......

if you click on thread tools: top-right ........you can mark it as SOLVED

.........and we can assume for anyone else following this thread ...............that the answer is that installing the driver from Canon works ............... as advised above in post #3

enjoy

---

### Post by toopho on 2013-04-17
> **pdc said:**
> 
if you click on thread tools: top-right ........you can mark it as SOLVED


Yep, I tried to do that as I wrote my above last post. But I couldn't (and still can't) find how to mark it as "Solved" so I edited the thread tittle manually. I think that's ok too.

---

