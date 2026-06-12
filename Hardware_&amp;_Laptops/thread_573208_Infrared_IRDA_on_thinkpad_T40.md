---
title: "Infrared IRDA on thinkpad T40"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by bliffle on 2007-10-11
I'm trying to get IR running on my T40. So I found these references:

[http://ubuntuforums.org/showpost.php?p=1753177&postcount=4](http://ubuntuforums.org/showpost.php?p=1753177&postcount=4)
[http://tuxmobil.org/Infrared-HOWTO/Infrared-HOWTO.html](http://tuxmobil.org/Infrared-HOWTO/Infrared-HOWTO.html)

I did a findchip:

```
sudo findchip -d -v -l
SMC
NSC
WINBOND

```

And followed instructions to edit:

```
sudo gedit /modutils/irda-utils

```

I get this error msg when I try to SAVE:

esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-0/socket
This socket already exists indicating esd is already running.
Exiting...

** (gedit:28438): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

So I put the edited file aside.

I don't know what to try next.

---

### Post by Lil on 2007-10-22
Hiya,

I have set this up before now on Feisty but I've since moved to Gutsy.

But it did work; I'll find my notes and reply this evening,

Vicky

---

### Post by bliffle on 2007-11-17
bump.

---

### Post by bliffle on 2007-11-23
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

### Post by bliffle on 2007-11-23
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

