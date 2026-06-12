---
title: "ATI 2600xt fan speed"
date: 2009-11-04
forum: Hardware
---

### Post by infinity217 on 2009-11-04
Hi guys, i use Ubuntu 9.10 and my graphic card (ATI HD 2600xt) fan is driving me crazy it works at full speed all the time even when i'm reading Ebooks... i tried 

(aticonfig --pplib-cmd "set fanspeed 0 40") 

but i get  

"No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again."

i do what i'm told and then i get

"Found fglrx primary device section
 Unable to find any supported Screen sections"

here is my Xorg.conf file


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection




any help would be great....

---

### Post by riturkki on 2009-11-19
I'm having same kind of problems with aticonfig. (Karmic 64bit)

My graphic card:

    VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3450

    $ sudo aticonfig --list-adapters 
    * 0. 08:00.0 ATI Radeon HD 3400 Series


$ sudo aticonfig --list-adapters
* 0. 08:00.0 ATI Radeon HD 3400 Series

* - Default adapter


$ cat /etc/X11/xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection



But when I try for instance check GPU's temperature 

$ aticonfig --adapter=0 --od-gettemperature
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
aticonfig: parsing the command-line failed.



ANY IDEAS, thanks.

---

### Post by riturkki on 2009-11-19
and 'aticonfig --initial' says:

$ aticonfig --initial
Found fglrx primary device section
 Unable to find any supported Screen sections

---

### Post by Yellow Pasque on 2009-11-19
aticonfig is looking for a more traditional xorg.conf

Try:
```
sudo aticonfig --initial -f
```

---

