---
title: "ndiswrapper doesn't work after upgrade to 12.04"
date: 2012-04-28
forum: Hardware
---

### Post by IdanSuper on 2012-04-28
after upgrade to lubuntu 12.04 every time I run the command modprobe ndiswrapper it says: Fatal: module ndiswrapper not found.. what can I do thanks..

---

### Post by pdk on 2012-04-28
lspci|grep 2500
00:09.0 Network controller: Ralink corp. RT2500 Wireless 802.11bg (rev 01)
drivers in /lib/modules/"uname -r"
./kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
./kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
ndisgtk installs driver
ndiswrapper -m  creates alias wlan0
modprobe ndiswrapper 
fatal ndiswrapper not found.
root@peter:/etc/modprobe.d# ndiswrapper -v
ERROR: modinfo: could not find module ndiswrapper
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
ERROR: modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
The tar version at sourceforge is ndiswrapper-1.57.tar.gz (199.0 kB)
which is the latest version listed in 12.04

Same problem
Peter

---

### Post by chili555 on 2012-04-28
Or you could get an ethernet connection and do:```
sudo apt-get install --reinstall ndiswrapper-common ndiswrapper-utils-1.9
```

---

### Post by pdk on 2012-04-28
done that :)
Also if you run network from dash you get a message  "system network services not compatible with this version.
The old file from before the update /etc/udev/rules.d/70-persistent-net.rules had an entry for wlan0
I deleted the lines in the file and rebooted, this time the wlan0 line was not generated.
****************************************************************************************************
SOLVED
I can connect via a 30 meter cable downstairs with my eth0 card :)
used synaptic and installed ndiswrapper source for the kernel module.
The module assistant hung up in the details window.
Ran it by hand . Compiled it and then installed it.
Now modprobe ndiswrapper works.
Have to run  route add default gw 10.0.0.2 to get my gateway running, but that,s just a small problem
(with 12.04 the default wireless does not work at all. With 11.01 it worked badly. ndiswrapper was better, still not perfect.)

---

### Post by soneedu on 2012-04-30
> **pdk said:**
> done that :)
Also if you run network from dash you get a message  "system network services not compatible with this version.
The old file from before the update /etc/udev/rules.d/70-persistent-net.rules had an entry for wlan0
I deleted the lines in the file and rebooted, this time the wlan0 line was not generated.
****************************************************************************************************
SOLVED
I can connect via a 30 meter cable downstairs with my eth0 card :)
used synaptic and installed ndiswrapper source for the kernel module.
The module assistant hung up in the details window.
Ran it by hand . Compiled it and then installed it.
Now modprobe ndiswrapper works.
Have to run  route add default gw 10.0.0.2 to get my gateway running, but that,s just a small problem
(with 12.04 the default wireless does not work at all. With 11.01 it worked badly. ndiswrapper was better, still not perfect.)

could you explain how to use ndiswrapper source to solve the problem.
i installed the source, but do not know the next step.
pls give some advise, many thanks!

---

### Post by MetCom45 on 2012-05-02
I am also having problems with ndiswrapper in 12.04. When I try to compile from tar.gz I get "No such file or directory" and the /configure command is not found... I followed a compiling guide and created the directory /usr/local/src in which I pasted the unpacked ndiswrapper-1.57.tar.gz file.

I think that if I could successfully compile the tar.gz for ndiswrapper that it would solve my issue.

---

### Post by chili555 on 2012-05-02
When you opened the terminal to compile, did you navigate to the location of the files?```
cd /usr/local/src/ndiswrapper-1.57  <--or whatever the folder is named
```Now verify:```
ls
```Do you see the files you put there? Do you see the configure and Makfiles? If so, please proceed.

---

### Post by MetCom45 on 2012-05-02
Thank you for the response, I will try this after work tonight!

---

### Post by MetCom45 on 2012-05-03
> **chili555 said:**
> When you opened the terminal to compile, did you navigate to the location of the files?```
cd /usr/local/src/ndiswrapper-1.57  <--or whatever the folder is named
```Now verify:```
ls
```Do you see the files you put there? Do you see the configure and Makfiles? If so, please proceed.

```
tyler@tyler-Inspiron-1000:~$ cd /usr/local/src/ndiswrapper-1.57
tyler@tyler-Inspiron-1000:/usr/local/src/ndiswrapper-1.57$ ./configure
bash: ./configure: No such file or directory
tyler@tyler-Inspiron-1000:/usr/local/src/ndiswrapper-1.57$ ls
AUTHORS    driver   loadndisdriver.8  ndiswrapper.8     README
ChangeLog  INSTALL  Makefile          ndiswrapper.spec  utils
tyler@tyler-Inspiron-1000:/usr/local/src/ndiswrapper-1.57$ 

```

I did indeed cd to the correct directory the first time I attempted this. That^ is the output. If I am simply compiling incorrectly just say so. Do not feel obligated to teach me how to compile a tar.gz haha :tongue:

---

### Post by chili555 on 2012-05-03
> If I am simply compiling incorrectly just say so. Do not feel obligated to teach meI do feel obligated to teach you and others. You will learn much better and faster if you get some tips from a kindly old stranger.> tyler@tyler-Inspiron-1000:/usr/local/src/ndiswrapper-1.57$ ls
AUTHORS    driver   loadndisdriver.8  ndiswrapper.8     [COLOR="Red"]README[/COLOR]
ChangeLog  INSTALL  Makefile          ndiswrapper.spec  utilsYou are definitely in the correct folder now. Look at what I highlighted. Did you?```
less README
```In some cases the README file is a thanks to the contributors who helped write the code; in some cases, it's a change log and in some cases, it gives instructions about how to build and install the package. In any case, it is always helpful to read the README. The 'less' command allows you to scroll back and forth with the arrow keys. Get out of less with q.

Another candidate is the INSTALL file:```
less INSTALL
```One of these will tell you the process to build and install the package. In Ubuntu, the most usual, but not exclusive process is:```
make
sudo make install
```If the 'make' ends in an error, stop, find out what is wrong and fix it before you proceed. All further steps are futile.

Note that to compile (not just ndiswrapper), you need to have installed build-essential and linux-headers-generic.

---

### Post by MetCom45 on 2012-05-03
> I do feel obligated to teach you and others. You will learn much better and faster if you get some tips from a kindly old stranger.

A teacher is more efficient than trial and error, I really do appreciate your time and kindness!

> ```
tyler@tyler-Inspiron-1000:/usr/local/src/ndiswrapper-1.57$ ls
AUTHORS driver loadndisdriver.8 ndiswrapper.8 README
ChangeLog INSTALL Makefile ndiswrapper.spec utils
```

You are definitely in the correct folder now. Look at what I highlighted. Did you?

```
less README
```

In some cases the README file is a thanks to the contributors who helped write the code; in some cases, it's a change log and in some cases, it gives instructions about how to build and install the package. In any case, it is always helpful to read the README. The 'less' command allows you to scroll back and forth with the arrow keys. Get out of less with q.

Yes I did, and I now understand the 'less' command. There is both a "README" and "INSTALL" document. I will read through them both.

> If the 'make' ends in an error, stop, find out what is wrong and fix it before you proceed. All further steps are futile.

It seems to have run the 'make' command successfully, here is the output:

[http://freetexthost.com/sabiqqrlrz]("http://freetexthost.com/sabiqqrlrz") **<I have not moved beyond this point.**

> Note that to compile (not just ndiswrapper), you need to have installed build-essential and linux-headers-generic.

I understand, and I believe that I have completed those steps [>here<]("https://help.ubuntu.com/community/CompilingEasyHowTo") in step 1. Note, I have not done anything else to prepare for compiling aside from what is in this tutorial.

---

### Post by chili555 on 2012-05-03
Looks perfect so far, not even a warning! Next, I suggest:```
sudo make install
```See if the later version installed correctly:```
sudo modprobe ndiswrapper
```It should return to the command prompt; that's Linux-speak for 'command executed as requested and there are no errors or warnings to report.' That's what you want to see.

Now proceed with the installation of the .inf file. Post back any errors and I'll be happy to help.

---

### Post by MetCom45 on 2012-05-04
> **chili555 said:**
> Looks perfect so far, not even a warning! Next, I suggest:```
sudo make install
```See if the later version installed correctly:```
sudo modprobe ndiswrapper
```It should return to the command prompt; that's Linux-speak for 'command executed as requested and there are no errors or warnings to report.' That's what you want to see.

Now proceed with the installation of the .inf file. Post back any errors and I'll be happy to help.

I just followed the "INSTALL" file's directions and the rest went great, I am using Wi-Fi right now!

Thanks again for your help, you're very generous.

---

### Post by chili555 on 2012-05-04
Excellent! Glad it's working. Have fun!

---

