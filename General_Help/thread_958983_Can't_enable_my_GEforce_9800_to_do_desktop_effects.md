---
title: "Can't enable my GEforce 9800 to do desktop effects"
date: 2008-10-26
forum: General Help
---

### Post by a Dalmatian on 2008-10-26
The subject speaks for its self, my 9800 Geforce can't even do the desktop effects, and I need to know what you need me to do so people can help me better.

---

### Post by lifelesspoet on 2008-10-26
Have you enabled the latest geforce video drivers

Applications >> System >> Hardware Drivers

A dialog should pop up and allow you to enable the driver, which will download automatically.

---

### Post by a Dalmatian on 2008-10-26
> **lifelesspoet said:**
> Have you enabled the latest geforce video drivers

Applications >> System >> Hardware Drivers

A dialog should pop up and allow you to enable the driver, which will download automatically.

first things I tried, only shows HAL and LAN are being ran by proprietary drive.

---

### Post by lifelesspoet on 2008-10-26
This is how i installed my drivers.


sudo apt-get install  nvidia-glx-177 nvidia-kernel-common

---

### Post by a Dalmatian on 2008-10-26
ok after getting error message, I restarted but now I got this:

byron@byron-desktop:~$ sudo apt-get install nvidia-glx-177 nvidia-kernel-common
[sudo] password for byron:

(I can't put in the passoword and this is the Terminal program (for lack of better terms) this gets put into, right?)

---

### Post by eternalnewbee on 2008-10-26
Hi there.
I've read, somewhere in the Forums that the newest graphic cards aren't compatible yet, but that there will be much more support in the upcoming 8.10 release.
Sorry I haven't got any better news for you.
Good luck.

---

### Post by lifelesspoet on 2008-10-26
I'm using 8.10 beta with 2 8800 gts 512's and it picked up my cards right away, I don't recommend the beta at the moment as i have had issues with my video card.  Release is but a few days away.



edit 
yes, it gets typed in the terminal and the password is your login password

---

### Post by a Dalmatian on 2008-10-26
byron@byron-desktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.


ERROR: Unable to write to directory '/etc/X11'.

byron@byron-desktop:~$

---

### Post by a Dalmatian on 2008-10-26
also if this helps its a Gefocre 9800 GT

---

### Post by superbenny on 2008-11-02
> **a Dalmatian said:**
> ok after getting error message, I restarted but now I got this:

byron@byron-desktop:~$ sudo apt-get install nvidia-glx-177 nvidia-kernel-common
[sudo] password for byron:

(I can't put in the passoword and this is the Terminal program (for lack of better terms) this gets put into, right?)


even if it doesn't look like it, your password is still being entered. just type it normally, and then hit enter.


> byron@byron-desktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
Device section "Configured Video Device" must have a Driver
line.


ERROR: Unable to write to directory '/etc/X11'.

byron@byron-desktop:~$

do 
```
sudo nvidia-xconfig
```
you need to make sure you run nvidia-xconifig as super user.

---

