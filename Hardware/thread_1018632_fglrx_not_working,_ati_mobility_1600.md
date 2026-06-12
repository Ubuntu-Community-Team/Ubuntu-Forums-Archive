---
title: "fglrx not working, ati mobility 1600"
date: 2008-12-22
forum: Hardware
---

### Post by mattiask on 2008-12-22
I have some problems with my graphics, I can't get fglrx working. When I type "fglrxinfo" it returns
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

Using the latest restricted drivers and have recently updated fglrx. 

My xorgconf
```
Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth	24
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	BusID       "PCI:1:0:0"
	Driver	"fglrx"
EndSection

```

What to do? Have searched all day and haven't found anything useful. I hope I don't need to reinstall my little computer...

---

