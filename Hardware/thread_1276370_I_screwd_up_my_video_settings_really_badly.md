---
title: "I screwd up my video settings really badly"
date: 2009-09-27
forum: Hardware
---

### Post by JigglyWiggly_ on 2009-09-27
So I was using wine with the restricted hardware drivers 180, worked fine for the most part. Except jedi knight restarted x-serve,r so I tried installing the newest unsupoorted drives from nvidia 185.xx. I installed them from the cmd line...(ubuntu recovery) and then I tried too boot and it failed. So then I tried going back to the other 180 hardware restricted drivers on the ubuntu manager. And it enabled, except compiz says desktop effects  could not be enabled....

Here is the log
```
cojigglywiggly@3dslice:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity 

```

here is my xorg.conf


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

Any suggestions? I don't want to reformat...
And reformatting to solve problems sounds like i'm using windows...

Oh and I'm using an 8400mgs.

---

### Post by pastalavista on 2009-09-27
Opern a terminal and enter```
sudo apt-get purge xserver-xorg
```and then```
sudo apt-get install xserver-xorg
```This will revert back to the default installation.

---

### Post by JigglyWiggly_ on 2009-09-27
Didn't work... and when I run that stupid nvidia thing with ./NVIDIA-etcetcetc
it says that there is a previous version of 185 installed. Which is itself, because 185 is the version it installs. How can I get rid of that stupid crap?

---

### Post by JigglyWiggly_ on 2009-09-27
YES YES YES I got it...
I just had to do this in the terminal(no gui, with gdm stopped):
```
sh NVIDIA-Linux-x86_64-185.18.36-pkg2.run --uninstall
```

For the goodness of your soul, please do not install this garbage anyone :D

---

### Post by etnlIcarus on 2009-09-27
You probably also could have done a:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
As per the comments at the top of your xorg.conf.

---

### Post by Zoot7 on 2009-09-27
> **JigglyWiggly_ said:**
> YES YES YES I got it...
I just had to do this in the terminal(no gui, with gdm stopped):
```
sh NVIDIA-Linux-x86_64-185.18.36-pkg2.run --uninstall
```

For the goodness of your soul, please do not install this garbage anyone :D

I'd the same problems with that 185.18 driver, tried installing it several times only to be presented with that lovely White Screen upon bootup.
The 180.44 driver worked fine for me on my laptop (see sig), so I'd say give that a shot. ;)
**[http://www.nvidia.com/object/linux_display_ia32_180.44.html]("http://www.nvidia.com/object/linux_display_ia32_180.44.html")**

---

### Post by JigglyWiggly_ on 2009-09-27
> **etnlIcarus said:**
> You probably also could have done a:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
As per the comments at the top of your xorg.conf.

I had tried that, I read literally dozens of pages on the Internet, none of them worked.

---

