---
title: "Reliance ZTE CDMA 1X Modem MG880 with Ubuntu 8.04"
date: 2008-08-14
forum: General Help
---

### Post by SantoUbu21 on 2008-08-14
I tried steps as given below to make my USB modem to work with my HP Notebook in which I installed Ubuntu 8.04 as dual boot in a separate partition. (I am new to Ubuntu) Please help me to make this work.

santo@santo-notebook:~$ cat/proc/bus/usb/devices
bash: cat/proc/bus/usb/devices: No such file or directory

So I tried sudo gedit /etc/init.d/mountdevsubfs.sh
and made changes like

# Magic to make /proc/bus/usb work
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

santo@santo-notebook:~$ sudo /etc/init.d/mountdevsubfs.sh start

sudo: unable to resolve host santo-notebook
/etc/init.d/mountdevsubfs.sh: 67: -obusmode=0700,devmode=0600,listmode=0644: not found
ln: 
creating symbolic link `/dev/bus/usb/devices': File exists

After this I restarted my HP notebook.

santo@santo-notebook:~$ cat/proc/bus/usb/devices
bash: cat/proc/bus/usb/devices: No such file or directory

santo@santo-notebook:~$ sudo wvdialconf
sudo: unable to resolve host santo-notebook 
Editing `/etc/wvdial.conf'.
Scanning your serial ports for a modem.
Modem Port Scan<*1>: S0   S1   S2   S3   

Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to.....
santo@santo-notebook:~$ 

I followed the steps given here
[http://prithisd.blogspot.com/2007/12/reliance-zte-cdma-1x-mg880-working-with.html](http://prithisd.blogspot.com/2007/12/reliance-zte-cdma-1x-mg880-working-with.html)
and
[http://nandz.blogspot.com/2007/11/how-to-get-reliance-zte-mg880-working.html](http://nandz.blogspot.com/2007/11/how-to-get-reliance-zte-mg880-working.html)

Please help me to resolve this. 
Thank you
Santosh

---

### Post by SantoUbu21 on 2008-08-15
Here is the updated one...

When I tried lsusb command it is listed as 
Bus xxx Device 013: ID 19d2:fffd

I even checked in Administration > Network as given here [http://ubuntuforums.org/showthread.php?p=4929133#post4929133](http://ubuntuforums.org/showthread.php?p=4929133#post4929133)

It looks like the USB modem is not even getting detected by Ubuntu. The same modem works in Vista.

I as made changes to wvdial.conf

Here another update == please help me

santo@santo-notebook:~$ sudo gedit /etc/wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = #777
Password = <have entered correct no.>
Username = <have entered correct pw>
ISDN = 0
Setvolume = 0
FlowControl = Hardware (CRTSCTS)
Modem = /dev/ttyUSB0
Dial Command = ATDT
Baud = 460800
Stupid Mode = 1

Please help me to resolve this. 
Thank you
Santosh

---

