---
title: "Can configure NVIDIA settings"
date: 2010-04-08
forum: Hardware
---

### Post by zoomiest on 2010-04-08
I have xubuntu on a HP laptop, and just got the Nvidia driver installed. I am trying to configure a second monitor.

However, everytime I try to edit the settings, through the GUI, I get ```
Failed to parse existing X config file /etc/X11/xorg.conf !
```

I have followed various suggestions made in these forums, like ```
$ chmod 777 xorg.conf
```

and also 

```
$ sudo nvidia-settings
```

and also

```
$ gksudo gedit /etc/X11/xorg.conf
``` and copying the contents to another file...

but I get the same errors.

when I do the sudo nvidia-settings, I get:

```
allan@xu:~$ sudo nvidia-settings
[sudo] password for allan: 

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

Segmentation fault
```

Any thoughts? What am I missing?

My xorg.conf reads:
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```


Further... 
I took another suggestion, and deleted my existing xorg.conf file, and let Nvidia recreate it... and the new one definitely had more info, and settings (sounds good), but it isn't loading... I even chomod 777 it... still isn't loading.

---

### Post by zoomiest on 2010-04-08
Resolved.

The fix had to do with deleting the xorg.conf file, and letting Nvidia create the new file with the command line 

```
$ sudo nvidia-xconfig
``` ...(instead of nvidia-settings). This time the new file that was created was successfully loaded.

Then, when I went in to configure the twin screen with the gui with gksudo nvidia-settings, then, my systems's edits WERE finally saved... 

all is well, I now have twin screens on xubuntu.

---

### Post by stilling on 2010-04-08
just select you choice in gui then when you save them click preview copy all and paste in xorg.conf log out log in and that is it off course back-up old xorg configuration 
that is how i do 



hope it helps you to

---

