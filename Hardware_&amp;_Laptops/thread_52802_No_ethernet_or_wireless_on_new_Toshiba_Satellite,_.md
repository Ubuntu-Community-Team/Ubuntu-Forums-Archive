---
title: "No ethernet or wireless on new Toshiba Satellite, Ubuntu 5.04"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by opnickc on 2005-07-29
Hi, first post.

[Note: I'm not sure if this thread should be here or in Networking, so if an admin moves it I won't be offended]

If you just want to get to my problem, go ahead and skip this paragraph.  
A few weeks ago, I came across [this](http://www.pcworld.com/reviews/article/0,aid,120520,00.asp) article.  I had thought about trying linux before, and since I hadn't been using my desktop's secondary HD, I decided to give ubuntu a try.  I've booted to windows once since, and aside from the problems I'm about to tell you about (and ATI's poor linux support) I couldn't be happier with ubuntu.  I've grown so attached to the OS, I'vd decided to run it on my new laptop, a Toshiba Satellite M55-S135.

Here's my difficulty, ubuntu was unable to configure my NIC or wireless card during installation, and I currently can't connect to my LAN or the internet with the machine.  Now I'm still a newbie to linux, though turning on DMA on my desktop did get me some experience with the command line, and installing device drivers has proven more difficult than on windows.  Since I don't even have a wireless connection at home, right now I'm just trying to get my NIC running:

My NIC is a Marvell Yukon 88E8036 PCI-E Fast Ethernet Controller.
The wireless card is an Atheros AR5005G Wireless network adapter.

Now I've already downloaded the linux drivers for the ethernet card.  However, when I try to install them I get some failures which cause the installation to fail (sorry about how long it is).

[FONT=System][SIZE=1]root@lincecil2:/home/nick/Desktop/DriverInstall # ./install.sh


Installation script for sk98lin driver.
Version 8.23.1.3 (Jun-20-2005)
(C)Copyright 2003-2005 Marvell(R).
====================================================
Add to your trouble-report the logfile install.log
which is located in the  DriverInstall directory.
====================================================


1) installation
2) generate patch
3) exit
Choose your favorite installation method: 1










Please read this carfully!

This script will automatically compile and load the sk98lin
driver on your host system. Before performing both compilation
and loading, it is necessary to shutdown any device using the
sk98lin kernel module and to unload the old sk98lin kernel
module. This script will do this automatically per default.

Please plug a card into your machine. Without a card we aren't
able to check the full driver functionality.

Do you want proceed? (y/N) y












Create tmp dir (/tmp/Sk98IiEJPAccrVpYInMAHPbFX)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.10-5-386)                                  [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SP)                                               [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (i386)                                              [   OK   ]
Check compiler (not found)                                           [ failed ]
./install.sh: line 497: inst_failed: command not found
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check archive file (sk98lin)                                         [   OK   ]
Check kernel gcc version (3.3.5) (Kernel:3.3.5 != gcc:722:)          [ failed ]
There is a version mismatch between the compiler that was used
to build the current running kernel and the compiler which you
intend to compile the kernel module with. In most of the cases,
this is no problem, but there are cases in which this compiler-
mismatch leads to unexpected system crashes

If you know what you are doing and want to override this
check, you can do so by setting IGNORE_CC_MISMATCH system
variable:
    Example: export IGNORE_CC_MISMATCH=1
Installation of sk98lin driver module failed.
Delete temp directories (done)                                       [   OK   ]
root@lincecil2:/home/nick/Desktop/DriverInstall #[/SIZE][/FONT]

Now I'm not sure, but I think this means I'm going to have to install the gcc compiler, correct?  I've downloaded gcc, the newest version and version 3.3.5 since that's what caused the last fail.  The thing is, I really don't know how to go about installing it.  It looks a little harder than running a setup.exe file, and I really don't know what I'm doing.  Am I at least going in the right direction?  Any help would be greatly appreciated; I really like this operating system (I just need to learn how to use it fully).

Thanks in advance for your help.

---

### Post by amohanty on 2005-07-29
> If you know what you are doing and want to override this
check, you can do so by setting IGNORE_CC_MISMATCH system
variable:
Example: export IGNORE_CC_MISMATCH=1
Installation of sk98lin driver module failed.
Delete temp directories (done) [ OK ]
root@lincecil2:/home/nick/Desktop/DriverInstall # 

Ok this is just a warning. FOr the most part it will not cause any problems. So at the command prompt do what it says:
>> export IGNORE_CC_MISMATCH=1
and run your install script.

> I've downloaded gcc, the newest version and version 3.3.5 since that's what caused the last fail. The thing is, I really don't know how to go about installing it. It looks a little harder than running a setup.exe file, and I really don't know what I'm doing. Am I at least going in the right direction? Any help would be greatly appreciated; I really like this operating system (I just need to learn how to use it fully). 

Goto
System->Administration->Synaptic Package Manager
enter your password
click on search in the toolbar 
type in gcc and go wild...

HTH
AM

---

### Post by art on 2005-07-29
and for the wireless install madwifi driver. Download it from here

[http://madwifi.sourceforge.net/](http://madwifi.sourceforge.net/)

and install.

---

### Post by art on 2005-07-29
and for the wireless install madwifi driver. Download it from here

[http://madwifi.sourceforge.net/](http://madwifi.sourceforge.net/)

and install.

---

### Post by opnickc on 2005-07-29
Thanks for the help so far.  I didn't realize I could use the package manager without an internet connection.

I haven't tried the wireless yet, but I'll be sure to take a look once I get the ethernet working.

Now I get the following error in the installation;

Check kernel header files (not found)                                [ failed ]
Kernel header not found. Please install the linux header files
development package or crate a symbolic link from the
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

I would've just typed in the command they gave, but I looked in my /usr/src folder and there was no folder titled by my kernel version.  In fact, the only thing there was a folder named "rpm".  Am I supposed to have my linux source code or something installed here?  How do I know what version of the linux kernel I'm running?  

Again, thanks for all your help so far.

---

### Post by art on 2005-07-29
To know the kernel you are running type

uname -r 

in the command line. You actually for this problem do not need the kernel source, all you need is the headers, So you may download them only...

---

### Post by opnickc on 2005-07-29
[QUOTE=art]To know the kernel you are running type

uname -r 

in the command line. You actually for this problem do not need the kernel source, all you need is the headers, So you may download them only...[/QUOTE]
 I got the driver installed finally (went into the package manager and installed the kernel headers), but ubuntu still doesn't pick up the device.  I have no network connection and the device is labled unknown in the device manager.  Any suggestions?

---

### Post by amohanty on 2005-07-29
What does ifconfig return?
>> ifconfig

AM

---

### Post by opnickc on 2005-07-30
[QUOTE=amohanty]What does ifconfig return?
>> ifconfig

AM[/QUOTE]

root@lincecil2:/home/nick # ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:783 errors:0 dropped:0 overruns:0 frame:0
          TX packets:783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:70164 (68.5 KiB)  TX bytes:70164 (68.5 KiB)

---

### Post by amohanty on 2005-07-30
ok try:
>> sudo depmod -A

this will rebuild the modules.dep file. Then try:

>> modprobe <your drivername>

If it returns something, there is a problem, so please post whatever it returns.

AM

---

### Post by opnickc on 2005-07-30
root@lincecil2:/home/nick # sudo depmod -A
root@lincecil2:/home/nick # modprobe sk98lin
root@lincecil2:/home/nick # 

nothing

---

### Post by amohanty on 2005-07-30
if modprobe returned nothing it means that the driver modules were loaded. It only prints or returns something when there is trouble. Have you rebooted after installing?

AM

---

### Post by amohanty on 2005-07-30
Also, goto:
Applications->System Tools->Network Tools

Now in the drop down in the first tab do you see anything other than lo. I mean click on the drop down and see if you have anything. If you see anything else, select it and click on the 'COnfigure' btn next to it and set it up.

AM

---

### Post by opnickc on 2005-07-30
[QUOTE=amohanty]Also, goto:
Applications->System Tools->Network Tools

Now in the drop down in the first tab do you see anything other than lo. I mean click on the drop down and see if you have anything. If you see anything else, select it and click on the 'COnfigure' btn next to it and set it up.

AM[/QUOTE]


I've rebooted several times, and the only object in the Network Device dropdown menu is lo.

---

### Post by amohanty on 2005-07-30
post result of

>> cat /etc/modules

AM

---

### Post by opnickc on 2005-07-30
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the name of kernel modules that should be loaded
# at boot time, one per line.  Lines beginning with "#" are ignored

lp
mousedev
psmouse

---

### Post by amohanty on 2005-07-30
ok your modules are not loaded on reboot. this is what you need to do. Go through the install process again. dont worry it will simply overwrite the files. When you are about to do a make install, do the following instead:
>> sudo make install | tee my-install.log

This will not only output the messages onto the shell but also to the file called my-install.log.

Now after it is done, fire up gedit and open the file my-install.log and look for the .so files. there should usually only be one and it should be in /usr/lib. 

Then fire up gedit and open /etc/modules
add the name of the file WITHOUT the trailing file extension (.so in this case) at the end.

do:
>> sudo depmod -A
>> lsmod

post the output, name of the .so file and if possible the README that came with the driver.

finally reboot. It should work now. Actually it shoudl work without the rebbot also but a reboot never hurt anybody :)

AM

---

### Post by opnickc on 2005-07-30
I'm afraid there's no place in the installation where I use a make install command (the installation is fairly automated),  Is there a workaround to find the correct *.so file?

---

### Post by amohanty on 2005-07-30
Sorry forgot the first post!!!

do the following:

>> ./install.sh | tee my-install.log

HTH
AM

---

