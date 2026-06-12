---
title: "Mobile Intel (r) 965 Express Chipset Family driver for Ubuntu"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by babek on 2007-11-23
Hi, 

i'm using fujitsu-siemens laptop with intel chipset. I need this vga driver for it. For Ubuntu: 

Mobile Intel (r) 965 Express Chipset Family driver for Ubuntu 

where i can download it?

---

### Post by hlmuller on 2007-11-23
You haven't given the correct information for your question.

Please post the results of this command:

```
lspci | grep vga
```

---

### Post by StrangeBrew on 2008-01-08
I have the same question. I got nothing when I entered lspci | grep vga. 
Anyone got any info for us?

thanks

---

### Post by Yellow Pasque on 2008-01-08
It probably just uses the regular intel driver. Is that what you have listed in the driver line of the "Device" section of your /etc/X11/xorg.conf ? What exactly is wrong with your video?
> I got nothing when I entered lspci | grep vga
[smartass]Me neither, but I got something when I entered lspci | grep VGA[/smartass]

---

### Post by firstc624 on 2008-01-08
i may be misunderstanding, but if you are talking of intels driver for the 695 chipset it is built into the kernel.   that said however, in gutsy the intel version doesnt support full 3d acceleration....just in case that is y u r asking...  the newest version of hardy that we r currently tsting, hardy heron, has the correct version.  if yoou look in synaptic search for video-intel  you will see the driver you r looking for already installed.

DO NOT USE HERDY ON ANT PRODUCTION MACHINES  it isnt ready yet as it is just an alpha

---

### Post by StrangeBrew on 2008-01-09
> **Temüjin said:**
> It probably just uses the regular intel driver. Is that what you have listed in the driver line of the "Device" section of your /etc/X11/xorg.conf ? What exactly is wrong with your video?
The problem I get, "Desktop effects could not be enabled". I'm just guessing that the graphic controller is the problem.

Here is what's in the file you asked for...
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

---

### Post by Yellow Pasque on 2008-01-09
The G965 & G3x have issues with Compiz and are blacklisted from running it. No eye candy for you!

---

### Post by StrangeBrew on 2008-01-09
That is so lame....but doesn't Sayabon use compiz as well? Not to sound like a complete idiot, what does compiz do?

I'm a rookie.

---

### Post by rmcnaught on 2008-02-05
I have just read this posting after trying to get advise for running Compiz on a Dell Inspiron 1525 with Ubuntu and Mobile Intel 965 Express Chipset Family.

It seems impossible on this hardware from the above to get Compiz to work?  Does that mean that it cannot be done at all, or can desktop effects be enabled from beryl and emerald?

TIA

Robert

---

### Post by Yellow Pasque on 2008-02-05
It can be done, but might be buggy, especially with video playback. If you want to try anyway, you need to un-blacklist the pci id in /usr/bin/compiz (and make sure the rest of the file is set correctly) before trying to enable desktop effects.

The first part of your /usr/bin/compiz file (after the comments) probably looks like this:
```
COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real) 
```
It needs to look like this (changes bolded):
```
COMPIZ_BIN_PATH="**/usr/bin/**" # For window decorators and compiz
PLUGIN_PATH="**/usr/lib/compiz/**" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="**compiz.real**" # Final name for compiz (compiz.real)
```
Also, go down to line 60 and comment (put a '#' sign in front of) lines 60 and 61 like so:
```
**#** T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
**#** T="$T 8086:2972" # i965 (x3000)
```
Now type compiz in a terminal. What happens?

---

### Post by Jp-Zou-Lou on 2008-07-23
Hey There, Does Anyone no Where i can download a driver update for mobile intel(R) 965 Express Chipset Family, ive tried INTEL and DELL But Dont Really Now What Is the rite one, If anyone could help, Thanks in Advance :)

---

### Post by Yellow Pasque on 2008-07-23
> **Jp-Zou-Lou said:**
> Hey There, Does Anyone no Where i can download a driver update for mobile intel(R) 965 Express Chipset Family, ive tried INTEL and DELL But Dont Really Now What Is the rite one, If anyone could help, Thanks in Advance :)
As far as I'm aware, it works with the standard "intel" driver. The version in the Ubuntu Hardy repo appears to be 2.2.1
Version 2.4.0 was released today
[http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.4.0.tar.bz2](http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.4.0.tar.bz2)

---

### Post by VicAlpha on 2008-07-23
> **Temüjin said:**
> As far as I'm aware, it works with the standard "intel" driver. The version in the Ubuntu Hardy repo appears to be 2.2.1
Version 2.4.0 was released today
[http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.4.0.tar.bz2](http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.4.0.tar.bz2)
Is there a specific method to install those driver? Whatever I've tried doesn't work :(

---

### Post by francisco_athens on 2008-07-23
What version of Ubuntu are you using? also show us the output of

$ lspci | grep Display

the intel driver is included with Ubuntu, so it should detect just fine.  If you have messed up your settings you can
```

$ sudo dpkg-reconfigure -phigh xserver-xorg
```

which will give you a fresh xorg.conf (and also backup your existing)

then 
```

$ sudo /etc/init.d/gdm restart
```

to restart your desktop (not to be confused with rebooting your system)

hope this helps

---

