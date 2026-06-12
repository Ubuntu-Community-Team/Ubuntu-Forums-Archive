---
title: "Bluetooth Broadcom BCM2035 issue !"
date: 2010-12-02
forum: Hardware
---

### Post by rshinde70 on 2010-12-02
HELLO FRIENDS,

To inform you,
[COLOR=Red]This is my forth time that, I'm asking for help about this issue about my bluetooth dongle.[/COLOR]

Since the installation of Ubuntu 10.04 LTS, My Bluetooth doesn't works anymore.
When I plug it, only notification comes that, I've plugged the bluetooth dongle.
But, If I go and want to "set up new device", It keeps searching and doesn't shows any of results.

I checked all my devices. All are set to "visibility shown".

And one thing is that, this bluetooth chip was working correctly, when I was using Ubuntu 8.04 Version.
[SIZE=2][COLOR=Red]
It was working fine in Ubuntu 8.04 LTS.[/COLOR][/SIZE]
[COLOR=Blue]
If Ubuntu 10.04 doesn't supports to this bluetooth chip, then, is there any way that, I can get supporting drivers from Ubuntu 8.04 Version?[/COLOR]

Please Help me as I'm asking for it, forth time..

---

### Post by searchfgold6789 on 2010-12-02
First go into a terminal and type in "lsusb"; you should see a line like this somewhere in there.```

Bus 002 Device 003: ID 0a5c:2033 Broadcom Corp. BCM2033 Bluetooth
```
If it is recognized, extract and install [_**this file**_]("http://www.kernel.org/pub/linux/bluetooth/bluez-4.80.tar.gz").

---

### Post by rshinde70 on 2010-12-02
> **searchfgold6789 said:**
> First go into a terminal and type in "lsusb"; you should see a line like this somewhere in there.```

Bus 002 Device 003: ID 0a5c:2033 Broadcom Corp. BCM2033 Bluetooth
```If it is recognized, extract and install [_**this file**_]("http://www.kernel.org/pub/linux/bluetooth/bluez-4.80.tar.gz").

Actually it is showing:
Bus 004 Device 003: ID 0a5c:2035 Broadcom Corp. BCM2035 Bluetooth
But I think if this solution is working for BCM2033, then may be it will work for 2035.

Actually, I'm new to linux. And I don't know how to install this software which you've given from this link.

Could you tell me, how to install this?

Thanks for the help :)

---

### Post by pricetech on 2010-12-02
Check out the README within the archive.  It gives instructions.

You might check first and make sure bluez is installed to begin with.  The 4.6 version is in the repos, which is just a matter of checking and installing if it's not already there.

Not sure which Broadcom chip mine uses since it's not here, but I've had zero problems with mine.

I use bluetooth, installed via Synaptic by the way.

---

### Post by rshinde70 on 2010-12-02
> **pricetech said:**
> Check out the README within the archive.  It gives instructions.

You might check first and make sure bluez is installed to begin with.  The 4.6 version is in the repos, which is just a matter of checking and installing if it's not already there.

Not sure which Broadcom chip mine uses since it's not here, but I've had zero problems with mine.

I use bluetooth, installed via Synaptic by the way.


BlueZ 4.66 is the version we got by default in Ubuntu 10.04 LTS.
Now,  [searchfgold6789]("http://ubuntuforums.org/member.php?u=926949") gave the link for the version 4.8
I think it was the version which was coming with ubuntu 8.04.
Actually, my Broadcom chip is old. So, I've to downgrade to that version.

I tried to install that version,
now I got following error:

```
checking for DBUS... no
configure: error: D-Bus library is required
```

then I googled link for installation of D-Bus library.
I found it, I d/w it and while installing it, I got following error:

```
checking for XML_ParserCreate_MM in -lexpat... no
configure: error: Could not find expat.h, check config.log for failed attempts
```

Now, for dbus library, expat.h is required.
I downloaded it but its corrupted. I tried lot of times but its coming in corrupted state.
So, I can't install this.

for expat.h I used following link:
[http://downloads.sourceforge.net/expat/expat-2.0.1.tar.gz](http://downloads.sourceforge.net/expat/expat-2.0.1.tar.gz)

Help!

---

### Post by rshinde70 on 2010-12-02
Friends,
[SIZE=3]I installed that software but [COLOR=Red]" NO CHANGE "[/COLOR] in the problem.[/SIZE]

I gave a command in terminal:
```
hcitool dev
```
to check my device, but, the result is:

```
rohit@rohit-desktop:~$ hcitool dev
Devices:
    hci0    00:00:00:00:00:00
```

Now, what to do?

---

### Post by Apis_I on 2011-03-10
I had the same problem, this never version seems to help a bit. I can scan for devices and so on, but the gnome bluetooth applet crashes and doesn't want to send/recieve any files from my phone. Im guessing it will be fixed in future version of ubuntu with newer bluetooth applet. If anyone else wants to try (might work with other devices):

[http://www.kernel.org/pub/linux/bluetooth/bluez-4.89.tar.gz](http://www.kernel.org/pub/linux/bluetooth/bluez-4.89.tar.gz)

([http://www.bluez.org/](http://www.bluez.org/) for more info)

cd to where you downloaded the file and run:
$ tar -xzf bluez-4.89.tar.gz
$ cd bluez-4.89
$ ./configure --prefix=/usr --mandir=/usr/share/man --sysconfdir=/etc --localstatedir=/var --libexecdir=/lib
$ make
$ sudo make install

(ie just do what the README file says) then reboot.

---

### Post by Kamen-rider on 2012-01-09
Hi, thank you the information of all upper ground.

I also have broadcom 2035 adapter. I have installed the latest bluez 4.97 it still can't send any files. But it is better than bluez 4.6 (come with 10.04 repos). Because bluez 4.6 can't scan any device. :P

---

