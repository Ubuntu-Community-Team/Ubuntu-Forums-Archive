---
title: "ARTEC E+ 48 &amp; Ubuntu 9.10"
date: 2010-03-05
forum: Hardware
---

### Post by arashiko28 on 2010-03-05
Hello, I need to install the scanner with Ubuntu 9.10, I have tried a couple of thing but nothing seems to work, when I Use the XSane, a window opens and then closes again. The scanner is an ARTEC E+ 48 and I have only Ubuntu 9.10 64-bits as OS.
Any ideas? Please help!

---

### Post by Bachstelze on 2010-03-05
Your scanner should be supported. Please open a terminal, run the command

```
lsusb
```

and paste the output.

---

### Post by arashiko28 on 2010-03-06
It does know it's there, but when I run XSane and choose it, shows an error about invalid argument and then closes.
> :~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 007: ID 05d8:4003 Ultima Electronics Corp. Artec E+ 48U
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b105 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by arashiko28 on 2010-03-13
[SIZE="7"][COLOR="Red"]***_BUMP!!!!_***[/COLOR][/SIZE]

Please, anyone?? I need this!!!!

---

### Post by arashiko28 on 2010-03-14
Pretty please! Does anyone knows anything?? I'm now desperate!

---

### Post by arashiko28 on 2010-03-14
This is what I have so far. I have the driver CD, from the beggining I was told it's useless and so far it is. After "successfully instaled" it does nothing, when I try to run ScanPanel from the Apllications>Others menu, it does nothing. When I do it from terminal, I get this:

> ScnPanel.exe
ScnPanel.exe: command not found
> sudo ScnPanel.exe
sudo: ScnPanel.exe: command not found


So, going on from here, what do I do next?

---

### Post by arashiko28 on 2010-03-14
It is supported by SANE, but I don't find the way to run it.

I also downloaded the scantwain-1.12.tar.gz but it doesn't have any configure file nor compile... so I'm pretty much where I started.

---

### Post by arashiko28 on 2010-03-15
I already managed to make it work, just copied the file Artec48.usb to usr/share/artec_eplus48u folder and then check or change the direction on the etc/sane.d/artec_eplus48u.conf file. problem solved.

---

