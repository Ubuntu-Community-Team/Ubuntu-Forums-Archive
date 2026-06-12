---
title: "not detecting external usb/devices"
date: 2012-02-11
forum: Hardware
---

### Post by kirtesh on 2012-02-11
[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG] am new to ubuntu..i was using windows 7..i installed ubuntu 9.04(32-bit)on my external hard disk..wen i was using it with my laptop(64-bit) which has windows 7 installed in it i faced a problem.. it is not detecting any pen-drive, external devices like data card of mobile broadband attached to it..i cant even have access to internet as it is not detecting mobile broadband...i logged in as root too...but i didnt succeeded...plz help me out...Thxs

---

### Post by ahallubuntu on 2012-02-11
First of all, Ubuntu 9.04 is obsolete and no longer supported.  You should avoid installing any version earlier than 10.04 LTS unless you really know what you are doing and have a good reason to do so.  Many problems that existed in 9.04 were long fixed in the newer versions, so no one wants to help you fix things that would work in the newer versions.  You also can't get updates for software with 9.04 any longer.

Some things do not work automatically with Ubuntu - like a mobile broadband adapter.  It really depends on whether the manufacturer of that adapter has chosen to provide support for it.  If not, you may have trouble getting it to work at all, in any version of Ubuntu.  But, if you use a supported version of Ubuntu and can provide the exact make/model of your broadband adapter, there may be solutions for you to make that exact hardware work.

---

### Post by madvinegar on 2012-02-11
Open a terminal, log in as root and write

```
modprobe usb-storage
```

and hit enter.


If the USB devices are recognized and mounted, let me know and I will tell you what to do.

---

### Post by madvinegar on 2012-02-12
> **madvinegar said:**
> 

If the USB devices are recognized and mounted, let me know and I will tell you what to do.

As root (i.e. write in terminal gksudo nautilus) and navigate to /etc/modules.

Open the file "modules" and add the line


```
usb_storage
```

i.e. the file "modules" should look something like this:


```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

usb_storage
lp
lp
lp
lp
```

Save the file and exit.

From now on, the usb_storage module will be loaded at each start-up.
Check it and let me know if everything worked out fine.

---

### Post by kirtesh on 2012-02-12
> **madvinegar said:**
> Open a terminal, log in as root and write

```
modprobe usb-storage
```

and hit enter.


If the USB devices are recognized and mounted, let me know and I will tell you what to do.
@Madvinegar..i wrote modprobe usb-storage on terminal as root yet my system failed to detect external connected devices..when i tried to open /etc/modules as ROOT ,output shown was Permission Denied...system didnt allowed me to open the file..the number of times i tried it showed me the same message permission denied 

modprobe usb-storage

---

### Post by kirtesh on 2012-02-12
> **ahallubuntu said:**
> First of all, Ubuntu 9.04 is obsolete and no longer supported.  You should avoid installing any version earlier than 10.04 LTS unless you really know what you are doing and have a good reason to do so.  Many problems that existed in 9.04 were long fixed in the newer versions, so no one wants to help you fix things that would work in the newer versions.  You also can't get updates for software with 9.04 any longer.

Some things do not work automatically with Ubuntu - like a mobile broadband adapter.  It really depends on whether the manufacturer of that adapter has chosen to provide support for it.  If not, you may have trouble getting it to work at all, in any version of Ubuntu.  But, if you use a supported version of Ubuntu and can provide the exact make/model of your broadband adapter, there may be solutions for you to make that exact hardware work.
yeah am too getting fried up...can u plz explain the procedure how to uninstall ubuntu from USB bcoz i have heard that procedure for uninstalling linux is different from that of windows

---

### Post by kirtesh on 2012-02-12
> **kirtesh said:**
> @Madvinegar..i wrote modprobe usb-storage on terminal as root yet my system failed to detect external connected devices..when i tried to open /etc/modules as ROOT ,output shown was Permission Denied...system didnt allowed me to open the file..the number of times i tried it showed me the same message permission denied 

modprobe usb-storage
i did the changes..somehow..yet it isn't detecting external devices...n i registered another problem my terminal doesn't lets me directly open a file using its specified  address?? how to solve it now?

---

### Post by madvinegar on 2012-02-12
Since with modprobe usb-storage in terminal you could not get the USB drives to be mounted, there was no reason for you to proceed in the next step, i.e. in adding usb_storage in etc/modules.

On the other hand, I don't know exactly what you did with the terminal so I cannot figure out now why terminal will not let you open files.

Maybe you should consider installing a newer version of ubuntu, namely from 10.04 and later on (as ahallubuntu is suggesting). Probably all of these problems will not be present with a more updated version of ubuntu.

---

### Post by kirtesh on 2012-02-13
> **madvinegar said:**
> Since with modprobe usb-storage in terminal you could not get the USB drives to be mounted, there was no reason for you to proceed in the next step, i.e. in adding usb_storage in etc/modules.

On the other hand, I don't know exactly what you did with the terminal so I cannot figure out now why terminal will not let you open files.

Maybe you should consider installing a newer version of ubuntu, namely from 10.04 and later on (as ahallubuntu is suggesting). Probably all of these problems will not be present with a more updated version of ubuntu.
Thanks for support..i will go on for 10.04 now..

---

