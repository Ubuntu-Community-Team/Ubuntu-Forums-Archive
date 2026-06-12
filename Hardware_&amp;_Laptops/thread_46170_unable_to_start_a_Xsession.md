---
title: "unable to start a Xsession"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by ricardo06 on 2005-07-03
After I completed the instructions in [https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28graphic%29%7C%28acceleration%29](https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28graphic%29%7C%28acceleration%29)

I am totaly unable to restart an X session. 

after entring my login and passwd there is pop-up that says that my xsession has lasted less than 10 seconds, because it cannot finf the module 'libatk-bridge' it also says i have no ICEauthorithy file.

I have hoary on amd64 I followed the instructions according to rthis distibution. I think it attemps to install new graphics drivers. 

I would very much appreciate any indications to help me go back to the standard set-up.

Richard

---

### Post by codejunkie on 2005-07-03
[QUOTE=ricardo06]After I completed the instructions in [https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28graphic%29%7C%28acceleration%29](https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28graphic%29%7C%28acceleration%29)

I am totaly unable to restart an X session. 

after entring my login and passwd there is pop-up that says that my xsession has lasted less than 10 seconds, because it cannot finf the module 'libatk-bridge' it also says i have no ICEauthorithy file.

I have hoary on amd64 I followed the instructions according to rthis distibution. I think it attemps to install new graphics drivers. 

I would very much appreciate any indications to help me go back to the standard set-up.

Richard[/QUOTE]

first listing what type of video card you have would be useful, second if your using an nvidia card you could try switching it back to nv or vesa with 
```
sudo nano /etc/X11/xorg.conf
``` 
find this section,
```

example:
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	[COLOR=Red]Driver		"example"[/COLOR]
	BusID		"PCI:1:0:0"

``` 
in the line that says Driver "example" find and replace "example" with "nv" or "vesa"
note: the "nv"driver is for nvidia cards only do not use it with other graphics cards 
if you have an ATI or another video card you could try replacing it with the "vesa" driver or find the one for your card and using it.
you could also try this 
```
sudo dpkg-reconfigure xserver-xorg

```
in the first section it gives a list of video drivers choose the driver for your card and
hit enter and you can also just hit enter to the rest options because it usually automatically configures it for you but it gives you an option to change stuff if you want.

---

