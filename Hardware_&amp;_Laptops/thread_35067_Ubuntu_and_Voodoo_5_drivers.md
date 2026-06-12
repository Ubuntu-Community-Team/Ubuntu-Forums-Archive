---
title: "Ubuntu and Voodoo 5 drivers"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by Righteous Brother on 2005-05-17
Hi there,

I currently have a Win2K/Linux dual boot.  Each OS is on it's own hard drive. Athlon T-Bird 1GHz, 512 MB PC133.

I just downloaded Ubuntu Linux and installed it this past weekend.  In trying to get it configured I am running into some snags.

First, I have a Voodoo5 64MB video card.  In Windows, I usually have it set at 1152 X 864,  True Color (32bit), and 75Hz refresh rate.  Ubuntu only shows a setting for 640 X 480 and 60Hz refresh rate.  How can I get a higher resolution?

Second, When I start up, the default settings are to boot to Linux.  Other family members use the computer also and don't care for Linux.  How can I edit the boot sequence to make Windows the default?

Thanks.

RB

---

### Post by Righteous Brother on 2005-05-18
My bad... I actually have the Hoary Hedgehog version and have re-posted over there.

 ](*,)

---

### Post by markuman on 2005-06-30
[QUOTE=Righteous Brother]My bad... I actually have the Hoary Hedgehog version and have re-posted over there.

 ](*,)[/QUOTE]


hi, on hoary with x.org , it seems there is a bug.

with my voodoo 5 it's the same here!

look in your /etc/X11/xorg.conf under >Section "Monitor"< and add following lines/edit it like that

```

Section "Monitor"
	Identifier	"YourMonitor"
        HorizSync       30-86
	VertRefresh	50-120
	Option		"DPMS"
EndSection 

```

now you can choice after restart your system/ or X-Server your resolution.
for 3D support just install " libglide3 " library and ReLink your library like that 
" ldconfig " 


so long...
markuman

---

