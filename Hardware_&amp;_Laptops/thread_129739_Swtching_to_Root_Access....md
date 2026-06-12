---
title: "Swtching to Root Access..."
date: 2006-02-14
forum: Hardware &amp; Laptops
---

### Post by caven80 on 2006-02-14
Hello People,,

i cannot switch to root access after issuing the 'su' command.
i enter in da correct password n it tell me authentication failed.

also im trying to install a Intel 537 EP modem..
when i issue the commands, make clean or make 537 or make install..

i get the message..bassh: comamnd not found..

Please help me..im trying desperately to get on da internet..

A newbie to linux..in  dire need of help

---

### Post by towsonu2003 on 2006-02-14
switch to root access with ```
sudo -i
``` su is not used in ubuntu, any root privileged command should be issued either as
```
sudo command
``` or after giving sudo -i. more info in [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

for make and make install put in install cd and ```
sudo apt-get update
sudo apt-get install build-essential
``` and try again

---

### Post by caven80 on 2006-02-15
hey...thanks for those tips..it Worked..
the 'make' commands worked too..

jus that i could not use the apt-get and insall build-essential commands..as my modem is not set up as yet..(the install cd was mounted and also i tried to issue those commands when i was in the cd directory..)

also when i use the command 'make 537' to install the modem..i get a message which says..'install kernel sources'...how do i do this..?

---

### Post by towsonu2003 on 2006-02-15
[QUOTE=caven80]hey...thanks for those tips..it Worked..
the 'make' commands worked too..

jus that i could not use the apt-get and insall build-essential commands..as my modem is not set up as yet..(the install cd was mounted and also i tried to issue those commands when i was in the cd directory..)

also when i use the command 'make 537' to install the modem..i get a message which says..'install kernel sources'...how do i do this..?[/QUOTE]
apt-get looks at two basic sources to install stuff: install cd and internet. 

if the make command worked, that means you succeeded in installing build-essential using the apt-get commands. for the kernel source, insert installation cd, make sure it is mounted, and in the terminal (copy-paste) ```
sudo apt-get update
sudo apt-get install linux-headers-`uname -r`
```
this should fix the "kernel source" problem.

One note: if you use "sudo -i", don't use sudo in front of the commands during the time you "are" root. The following is just an *illustration* for someone who installs linux-headers and then compiles something: 
```
sudo -i
apt-get update
apt-get install linux-headers-`uname -r`
exit
./configure
make
sudo make install
```

if you couldn't install the build-essential, or have problems installing linux-headers, read below. else, just ignore the stuff below
----------------------
build-essential / linux-headers should be in the install cd. after inserting the cd and making sure it is mounted, open a terminal and issue the following commands and if you get errors, please copy and paste them here.
```
sudo apt-get update
sudo apt-get install build-essential linux-headers-`uname -r`
[code]
it may also be a good idea to copy and paste the output of this command if you get errors
[code]cat /etc/apt/sources.list
```
if this last command gives a "you have no permission to do that" kinda error, then do
```
sudo cat /etc/apt/sources.list
```

---

### Post by caven80 on 2006-02-15
hey..looks like da kernel sources issue too was solved..but i did receive some error message when i issued the 'apt-get install linux-headers-`uname -r`' command..something like it cannot connect to some website..also..

when i issue da command 'make 537'  i got the message ' gcc 3.4 - command not found'....   is this missing..?

Also..

i issued the command  ' apt-get install linux-headers-`uname -r` ' after mounting da cd..it said that i have da latest kernel a also headers..


looks like im coming close to installing my modem..
please keep the assistance coming in..

u are very helpfull

---

### Post by towsonu2003 on 2006-02-15
[QUOTE=caven80]
when i issue da command 'make 537'  i got the message ' gcc 3.4 - command not found'....   is this missing..?
[/QUOTE]
again, insert install CD and ```
sudo apt-get update
sudo apt-get install gcc-3.4
```

I am not sure if this one is in the CD though. apt-get will tel you whether it installed it or couldn't find the package...

> something like it cannot connect to some website..
i issued the command ' apt-get install linux-headers-`uname -r` ' after mounting da cd..it said that i have da latest kernel a also headers..
it is probably telling you that it tried to connect to a repository when you told it to "apt-get update" but it couldn't. it saying you have the latest kernel headers means you already installed linux-headers. 

PS. I have to leave the office now -sorry / someone may pick up, or I'll reply later on :)

---

### Post by caven80 on 2006-02-15
thanks..but the same thing with gcc 3.4
says..'cannot find the file specified..'

guess its not on da computer n also on da cd.
i dont see the computer checking for da files on da cd...i mean..no sound or even da light doesnt come on..im sure its not looking for da files on da cd..

how do i install da gcc 3.4 now.??

sorry i cannot send u da exact messages as i'm dual booting with xp to connect to da internet..n that drive is formatted with NTFS..cannot write into it

if u really need da error messages..i will write them down n then type it out for u.

---

### Post by towsonu2003 on 2006-02-15
Ignore the stuff below the line and see the wiki at [https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4](https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4)

I thought of editing this post too late.....

I'm leaving the stuff below just because I wrote it ;)

--------------------------------------
[QUOTE=caven80]
how do i install da gcc 3.4 now.??
[/QUOTE]
yea I guess it's not in the CD... though when you go to ubuntu again, do me a favor: 
insert install CD
open terminal 
sudo mount /cdrom (now we can be sure it is mounted)
open synaptic and go to Settings->Repositories
and check whether "CD Ubuntu 5.10 "Breezy Badger"" is in the list (it should be)
if it's not, add it by going to Edit->"add cdrom" -follow instructions-
close synaptic
```

sudo apt-get update
sudo apt-get install build-essential linux-headers-`uname -r` binutils

```
in terminal: sudo eject (when apt-get is done) so the cd will be spit off
apt-get will tell you either you have these packages, or that it installed them. 

before going to ubuntu, go to the dialup wiki page and check out whether there is any information about installing gcc-3.4 (if there is, use thri instructions :) )
my instructions: go to packages.ubuntu.com,
search for, find, and download the packages for breezy: cpp-3.4 GCC-3.4 GCC-3.4-base
than go back to ubuntu, save these packages to your desktop, open a terminal and ```

cd
cd Desktop
sudo dpkg -i cpp-[tab] GCC-3.4_[tab] GCC-3.4-base[tab]
```
and PRAY while it is installing ;) ->> [tab] means you press the tab key so that it autocompletes the rest of the file name. ->> if it gives a dependency error ("package X is dependent on package Y, but package Y is unavailable"): 
```

sudo dpkg -r cpp-[tab] GCC-3.4_[tab] GCC-3.4-base[tab]
```
go back to packages.ubuntu.com, find and download the missing dependency (package), go back to ubuntu, and 
```

sudo dpkg -i packageY cpp-[tab] GCC-3.4_[tab] GCC-3.4-base[tab]
``` Do these until it installs everything without giving dependency errors (I know it is very frustrating). If packageY has another unmet dependency packageT, the command will be sudo dpkg -i packageT packageY cpp................ and so on.
dpkg -i means install package, dpkg -r means remove package. I make you remove packages with unmet dependencies everytime so that you won't get into weird troubles I won't be able to understand ;)

for the error messages, try copy pasting them to a text document and trasnferring he text document to windows. text files are edited using gedit in Applications>Accessories>Text Editor. Tell it to save the file with filename.*txt* extension to your desktop for ease of access. You can get rid of them later on.

---

### Post by towsonu2003 on 2006-02-15
I just saw that instructions are available in the wiki here:

[https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4](https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4)

---

### Post by caven80 on 2006-02-17
Hey...
i think i installed GCC successfully..(all 3 pakages) but had more trouble installing da modem..
i am pasting da log.  Log includes- from installing GCC to trying to issue 'make install' commands..

Please help further.

Many Thanks..

Caven
**********************************************************

root@regonet:/modem# **ls -la** 
total 2324
dr-xr-xr-x   2 root root    4096 Feb 15 23:16 .
drwxr-xr-x  26 root root    4096 Feb 17 16:40 ..
-r-xr-xr-x   1 root root 1707096 Feb 15 23:16 cpp-3.4_3.4.4-6ubuntu8_i386.deb
-r-xr-xr-x   1 root root  163028 Feb 15 23:15 gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
-r-xr-xr-x   1 root root  484408 Feb 15 23:13 gcc-3.4_3.4.4-6ubuntu8_i386.deb

root@regonet:/modem# dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb  gcc-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
Selecting previously deselected package cpp-3.4.
(Reading database ... 72542 files and directories currently installed.)
Unpacking cpp-3.4 (from cpp-3.4_3.4.4-6ubuntu8_i386.deb) ...
Selecting previously deselected package gcc-3.4.
Unpacking gcc-3.4 (from gcc-3.4_3.4.4-6ubuntu8_i386.deb) ...
Selecting previously deselected package gcc-3.4-base.
Unpacking gcc-3.4-base (from gcc-3.4-base_3.4.4-6ubuntu8_i386.deb) ...
Setting up gcc-3.4-base (3.4.4-6ubuntu8) ...
Setting up cpp-3.4 (3.4.4-6ubuntu8) ...
Setting up gcc-3.4 (3.4.4-6ubuntu8) ...

root@regonet:/modem# cd /intel*

root@regonet:/intel-537EP_secure-2.60.80.1# make clean
cd coredrv; make clean
make[1]: Entering directory `/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.o *.ko

root@regonet:/intel-537EP_secure-2.60.80.1# make 537
   Module precompile check
   Current running kernel is: 2.6.12-9-386
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.12-9-386
make[1]: Entering directory `/intel-537EP_secure-2.60.80.1/coredrv'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/intel-537EP_secure-2.60.80.1/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /intel-537EP_secure-2.60.80.1/coredrv/coredrv.o
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:70: warning: type defaults to `int' in declaration of `EXPORT_SYMBOL_NOVERS'
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:70: warning: parameter names (without types) in function declaration
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:70: warning: data definition has no type or storage class
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `open':
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:394: warning: `pm_register' is deprecated (declared at include/linux/pm.h:106)
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `close':
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:416: warning: `pm_unregister' is deprecated (declared at include/linux/pm.h:111)
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `hamproc_write':
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:660: warning: ignoring return value of `copy_from_user', declared with attribute warn_unused_result
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: At top level:
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:754: warning: initialization from incompatible pointer type
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:755: warning: initialization from incompatible pointer type
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `kScheduleDPC':
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:861: warning: implicit declaration of function `pm_access'
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `dspdrv_CommRamISR':
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:877: warning: function declaration isn't a prototype
  CC [M]  /intel-537EP_secure-2.60.80.1/coredrv/clmmain.o
  CC [M]  /intel-537EP_secure-2.60.80.1/coredrv/rts.o
  CC [M]  /intel-537EP_secure-2.60.80.1/coredrv/task.o
  CC [M]  /intel-537EP_secure-2.60.80.1/coredrv/uart.o
  CC [M]  /intel-537EP_secure-2.60.80.1/coredrv/wwh_dflt.o
  CC [M]  /intel-537EP_secure-2.60.80.1/coredrv/locks.o
  CC [M]  /intel-537EP_secure-2.60.80.1/coredrv/softserial_io.o
/intel-537EP_secure-2.60.80.1/coredrv/softserial_io.c: In function `softserial_write':
/intel-537EP_secure-2.60.80.1/coredrv/softserial_io.c:94: warning: ignoring return value of `copy_from_user', declared with attribute warn_unused_result
  CC [M]  /intel-537EP_secure-2.60.80.1/coredrv/softserial_ioctl.o
  CC [M]  /intel-537EP_secure-2.60.80.1/coredrv/softserial.o
/intel-537EP_secure-2.60.80.1/coredrv/softserial.c: In function `softserial_register_tty':
/intel-537EP_secure-2.60.80.1/coredrv/softserial.c:141: warning: assignment from incompatible pointer type
  CC [M]  /intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.o
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c:48: warning: function declaration isn't a prototype
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c:61: warning: initialization from incompatible pointer type
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c:65: warning: function declaration isn't a prototype
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c: In function `afe_Write':
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c:417: warning: ignoring return value of `copy_from_user', declared with attribute warn_unused_result
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c: In function `afe_Read':
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c:437: warning: ignoring return value of `copy_to_user', declared with attribute warn_unused_result
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c: At top level:
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c:454: warning: initialization from incompatible pointer type
  LD [M]  /intel-537EP_secure-2.60.80.1/coredrv/Intel537.o
  Building modules, stage 2.
  MODPOST
[B]Warning: could not find /intel-537EP_secure-2.60.80.1/coredrv/.537core.lib.cmd for /intel-537EP_secure-2.60.80.1/coredrv/537core.lib
*** Warning: "pm_access" [/intel-537EP_secure-2.60.80.1/coredrv/Intel537.ko] undefined!
  CC      /intel-537EP_secure-2.60.80.1/coredrv/Intel537.mod.o
  LD [M]  /intel-537EP_secure-2.60.80.1/coredrv/Intel537.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: Leaving directory `/intel-537EP_secure-2.60.80.1/coredrv'[/B]

root@regonet:/intel-537EP_secure-2.60.80.1# make install
rm -f /etc/hamregistry.bin
bash 537_inst
running kernel 2.6.12-9-386
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
installing 537 module
debian 537_boot rc2.d and rc3.d scripts
starting module and utilities
[B]error loading Intel537
ERROR: Module Intel537 does not exist in /proc/modules[/B]done
root@regonet:/intel-537EP_secure-2.60.80.1#

---

