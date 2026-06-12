---
title: "Intel Graphics Card 945GM Problems"
date: 2010-04-26
forum: Hardware
---

### Post by soultaker0x on 2010-04-26
I'm currently using Ubuntu 9.10 on a HP Pavilion dv2000.  When I boot I get a message saying that Ubuntu is running on low-graphics mode.

After that the window displays the following message:
The following error was encountered. You may need to update your configuration to solve this.

(EE) intel(0): No modes.
(EE) Screen(s) found, but none have usable configuration.

The Graphics Card that my computer has is:
 lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

I'm new to Linux/Ubuntu, and I'd really appreciate your help.

---

### Post by klemes on 2010-04-26
I would reboot into Recovery Mode as root and try a :

```
dpkg-reconfigure xserver-xorg
```

and afterward do a fresh reboot into normal boot to test the changes(if any)...

If that does not work reboot again into Recovery Mode and this time type:

```
X -configure 
```

This will update your xorg.conf.

To test the new xserver type:

```
X -config /root/xorg.conf.new
```

If successful consider moving the new xorg.conf to /etc/X11 for the changes to become permanent:

```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```

and tehn reboot into normal mode.

:guitar:

---

### Post by soultaker0x on 2010-04-26
> **klemes said:**
> I would reboot into Recovery Mode as root and try a :

```
dpkg-reconfigure xserver-xorg
```and afterward do a fresh reboot into normal boot to test the changes(if any)...

If that does not work reboot again into Recovery Mode and this time type:

```
X -configure 
```This will update your xorg.conf.

To test the new xserver type:

```
X -config /root/xorg.conf.new
```If successful consider moving the new xorg.conf to /etc/X11 for the changes to become permanent:

```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```and tehn reboot into normal mode.

:guitar:

I just tried booting in Recovery Mode but the monitor just displayed splashes of color. I tried it several times, but with no success. 

Is there another way to do those modifications?

---

### Post by kalaka on 2010-05-17
When you encounter the error you can try pressing Ctrl+Alt+F1, then login with your username/password and try the commands from there.

---

