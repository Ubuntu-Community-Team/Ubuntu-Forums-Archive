---
title: "lirc and IrDA on IBM Thinkpad T42"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by tdn on 2007-11-19
How do I get lirc and IrDA to work on my IBM Thinkpad T42?
I have aptitude installed lirc and I have found a config file for lirc containing the codes for my remote.

But how do I get it to work?
I think that I should probably install some modules for this, but do I really have to compile my own? If so, why?

---

### Post by bliffle on 2007-11-23
I'm having a problem with IR on mt T40.

I tried uninstalling 'irda-utils' and then reinstalling, but got a problem with the postinstall script:

```
john@JHT40UUU:~$ sudo apt-get install irda-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java gappletviewer-4.1 libkbanking1 libcairo-jni
  libgwenhywfar38 libflac++5c2 liboggflac3 libpostproc0d libqbanking4
  libktoblzcheck1c2a libgtk-jni libavformat0d libaqbanking16 libcairo-java
  libglib-jni cdw libbcprov-java libglib-java gcjwebplugin-4.1 libavcodec0d
  libmal1 libgtk-java libgwenhywfar-data libaqbanking-data linux-source-2.6.20
Use 'apt-get autoremove' to remove them.
Suggested packages:
  libgsmme1c102 liblinc1 obexftp
The following NEW packages will be installed:
  irda-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/99.7kB of archives.
After unpacking 336kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package irda-utils.
(Reading database ... 182048 files and directories currently installed.)
Unpacking irda-utils (from .../irda-utils_0.9.18-6ubuntu1_i386.deb) ...
Setting up irda-utils (0.9.18-6ubuntu1) ...
udev active, devices will be created in /dev/.static/dev/
udev active, devices will be created in /dev/.static/dev/
Starting IrDA service: irattachUsage: irattach <dev> [-d dongle] [-s] [-b] [-v] [-h]
       <dev> is tty name, device name or module name
Dongles supported :
        esi
        tekram
        actisys
        actisys+
        girbil
        litelink
        airport
        old_belkin
        ep7211
        mcp2120
        act200l
        ma600
        toim3232

invoke-rc.d: initscript irda-utils, action "start" failed.
dpkg: error processing irda-utils (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 irda-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

