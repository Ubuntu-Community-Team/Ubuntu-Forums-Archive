---
title: "537EP internal v.92 data/fax modem"
date: 2009-01-23
forum: Hardware
---

### Post by slowlap on 2009-01-23
Can anybody please help, i'm running intrepid and trying to get Phillipe vouters drivers from linmodems, compiled and installed, but keep getting back the following from terminal:

paul@paul-desktop:~$ sudo su
[sudo] password for paul: 
root@paul-desktop:/home/paul# cd intel-537EP_secure-2.60.80.0
root@paul-desktop:/home/paul/intel-537EP_secure-2.60.80.0# make clean
cd coredrv; make clean
make[1]: Entering directory `/home/paul/intel-537EP_secure-2.60.80.0/coredrv'
rm -f *.ko *.o .*.o.cmd *.mod.c *~ core .*.ko.cmd Module.symvers
rm -rf .tmp_versions
make[1]: Leaving directory `/home/paul/intel-537EP_secure-2.60.80.0/coredrv'
rm -f *.o *.ko
root@paul-desktop:/home/paul/intel-537EP_secure-2.60.80.0# make 537
   Module precompile check
   Current running kernel is: 2.6.27-9-generic
   /lib/modules...   autoconf.h exists
   autoconf.h matches running kernel
   version.h matches running kernel
/bin/sh: [[: not found
/bin/sh: [[: not found
/bin/sh: [[: not found
/bin/sh: [[: not found
/bin/sh: /lspci: not found
Modem type not determined.
$ export MODEM_TYPE=<type>
with type=537 or 537EP or 537SP or 537EA or 537AA
root@paul-desktop:/home/paul/intel-537EP_secure-2.60.80.0# # export MODEM_TYPE=537EP
root@paul-desktop:/home/paul/intel-537EP_secure-2.60.80.0# Sudo make install
bash: Sudo: command not found
root@paul-desktop:/home/paul/intel-537EP_secure-2.60.80.0# make install
rm -f /usr/sbin/hamregistry.bin
bash 537_inst
running kernel 2.6.27-9-generic
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
installing 537 module
install: cannot stat `Intel537.ko': No such file or directory
make: *** [install] Error 1
root@paul-desktop:/home/paul/intel-537EP_secure-2.60.80.0#

Many Thanks in advance 
ps i'm a newbie, so i need help in laymens terms

---

### Post by Ursidae on 2009-01-28
I also receive a similar message when I try to install the same driver on intrepid.
I'm using the deb package installer that I found when at this page:
[https://help.ubuntu.com/community/DialupModemHowto/Intel537EP](https://help.ubuntu.com/community/DialupModemHowto/Intel537EP)

The message I receive during install is;
Fatal: Error inserting Intel537 (/lib/module/2.6.27-11-generic/kernel/drivers/char/Intel537.ko): Invalid module format.
insmod: can't read 'Intel537': No such file or directory.
error loading Inttel537
Error: Module Intel537 does not exist in /proc/modules.

Is it possible that I'm missing a step prior to installing the driver? Other than running scanModem, I haven't done anything.

Any help is greatly appreciated.

---

### Post by slowlap on 2009-01-29
sorry haven't got a clue, i'm really new to this, hopefully someone else will read the post and help us both out

---

### Post by Ursidae on 2009-02-02
All of the reading I have done states that the 537EP driver will not work with the kernel I'm using (2.6.27-11-generic). The last known kernel I have found that it works for is 2.6.27-9-generic.
I am going to try and install that kernel and try reinstalling the driver.

---

### Post by Ursidae on 2009-02-03
I installed 2.6.27-9-generic and I still cannot get the driver to install. 
I'm going to go buy a different modem.
If that doesn't work I'm going to give up and install windows. I need something working soon. My ultimate goal is to install Hylafax, but that is dependent on a working modem.

---

