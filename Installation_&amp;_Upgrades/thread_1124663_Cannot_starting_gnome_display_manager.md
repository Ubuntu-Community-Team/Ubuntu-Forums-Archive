---
title: "Cannot starting gnome display manager"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by aglejberman on 2009-04-13
Hi, 

I had my ubuntu 8 working perfectly untill today, when I did some upgrades.

When reboot the pc I cannot access the graphic interface.

Executing /etc/init.d/gdm start gives me fail.

I see the error log of the gdm and this messages appear:
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
           No such file or directory.

....

Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!

The mysqld is also not starting!!!

Any help?
Thanks in advance.

---

### Post by antikristian on 2009-04-13
Try to search for the wacom device:
```
find /dev -name wacom
```

If you find it do a 

```
ln -s /dev/where/wacom/device/really/is /dev/wacom
```

If you could not find it

```
lsmod | grep wacom
```

if that returned nothing then try to 

```
modprobe wacom
```

If that was an utter success, add it to /etc/modules with
```
echo wacom >> /etc/modules
```

and reboot

If the lsmod command did return wacom something, then do a 
```
dmesg | grep wacom
```

Hopefully that returned something like "ttyS0" or similar, and you can then run 
```
ln -s /dev/ttyS0 /dev/wacom
```
 
and reboot

---

### Post by aglejberman on 2009-04-14
Hi antikristian, 

thanks for answering. I have no luck with your instructions.

I did:

$ find /dev -name wacom
nothing appears.

$ lsmod | grep wacom
nothing

$ modprobe wacom
$ echo wacom >> /etc/modules
$ reboot

But still the same problem, no graphical interface appears, and the error still remains the same.

Thanks for any other help.

Alejandro.

---

### Post by Slim Odds on 2009-04-14
> **antikristian said:**
> ```
lsmod | grep wacom
```if that returned nothing then try to 

```
modprobe wacom
```If that was an utter success, add it to /etc/modules with
```
echo wacom >> /etc/modules
```and reboot


if modprobe works, it will load the module... there is NO NEED to reboot....

Putting it in the /etc/modules files is fine, as that will make sure that it gets loaded the NEXT reboot.

---

### Post by antikristian on 2009-04-14
do you have a wacom tablet, or a tablet pc at all?

if you don't, then you could allways just run 
```
sudo cp /etc/X11/xorg.conf /etc/X11/corg.conf.old
sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by aglejberman on 2009-04-14
I tried this:
$ sudo dpkg-reconfigure -phigh xserver-xorg

this is the result:
$ xserver-xorg postinst warning: overwriting possibly customised configuration file; backup in /etc/X11/xorg.conf.datetime

But nothing happened.

I don't know if I have a wacom tablet, but I guess not (in fact, I have no idea what is a wacom tablet).

Thanks again.
Alejandro

---

### Post by antikristian on 2009-04-14
do a 
```
sudo /etc/init.d/gdm restart

```

---

### Post by Slim Odds on 2009-04-14
> **aglejberman said:**
> I don't know if I have a wacom tablet, but I guess not (in fact, I have no idea what is a wacom tablet).

LOL

I'd guess that you don't have one...

---

### Post by antikristian on 2009-04-14
I think I'll ask that question first next time;-)

---

### Post by aglejberman on 2009-04-14
I did the gdm restart many times, and the message is always the same:

```

* Stopping GNOME Display Manager...         [ OK ]
* Starting GNOME Display Manager...         [fail]

```

Thanks anyway

---

