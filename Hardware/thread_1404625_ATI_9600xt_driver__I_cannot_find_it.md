---
title: "ATI 9600xt driver ?? I cannot find it"
date: 2010-02-11
forum: Hardware
---

### Post by Natty Dreed on 2010-02-11
hello all,

I have a desktop with ATI Readon 9600XT 256 Mb card

I tried every thing to install the driver with no luck

is there any thing i can to install it ?

I have fresh install Karmic 9.10

plz help

---

### Post by Natty Dreed on 2010-02-11
I followed this how-to [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I got higher res but the driver didn't installed 

is my card not supported ?

---

### Post by lidex on 2010-02-11
If you go to this page:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English")
You can download the catalyst driver that supports this gpu. The installation instructions are there as well (pdf download).

---

### Post by Natty Dreed on 2010-02-11
I download it and do exact as it says but nothing work

i will try the open source driver

---

### Post by Natty Dreed on 2010-02-11
open source didn't work also

:@

anyone ?

---

### Post by lidex on 2010-02-11
You have to make sure other drivers are removed, then reboot, install new drivers, reboot and configure. Post the output of these commands please:
```
lspci -nn | grep VGA
```
```
LIBGL_DEBUG=verbose glxinfo | head
```
```
cat /etc/X11/xorg.conf
```
```
fglrxinfo
```

What do you see in "Hardware Drivers"(jockey)? Also, the 9.10 catalyst driver does not support Radeon 9600. Check the version in synaptic. Looks like 9.12 doesn't support it either.

---

### Post by Natty Dreed on 2010-02-16
```
$ [COLOR=Red]lspci -nn | grep VGA[/COLOR]
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 330 [Xabre] PCI/AGP VGA Display Adapter [1039:0330] (rev 01)01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 330 [Xabre] PCI/AGP VGA Display Adapter [1039:0330] (rev 01)

```

```
$ [COLOR=Red]LIBGL_DEBUG=verbose glxinfo | head[/COLOR]
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
name of display: :0.0
```


```
$[COLOR=Red] cat /etc/X11/xorg.conf[/COLOR]
cat: /etc/X11/xorg.conf: No such file or directory
```

```
$ [COLOR=Red]fglrxinfo[/COLOR]
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
```

sorry for delay i was far from home

---

### Post by JerichoKru on 2010-02-16
> **Natty Dreed said:**
> ```
$ [COLOR=Red]lspci -nn | grep VGA[/COLOR]
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 330 [Xabre] PCI/AGP VGA Display Adapter [1039:0330] (rev 01)01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 330 [Xabre] PCI/AGP VGA Display Adapter [1039:0330] (rev 01)

```

That is not an ATi card.

You need SiS drivers.

---

### Post by Natty Dreed on 2010-02-16
> **JerichoKru said:**
> That is not an ATi card.

You need SiS drivers.

I know this but he ask for the output and here it's

and from where i can get the "SiS" driver ?

thanks in advance

---

### Post by JerichoKru on 2010-02-16
> **Natty Dreed said:**
> I know this but he ask for the output and here it's

and from where i can get the "SiS" driver ?

thanks in advance

Well, It's supposed to be installed already.  Did you open up the "Hardware Drivers" application and see if it shows up?

If not, go into synaptic, search sis, and re-install ```
xserver-xorg-video-sis
```

---

### Post by Natty Dreed on 2010-02-16
My friend I have interged sis card but I don't want it

I want The ATI Driver not the sis one

should i uninstall all xorg driver and keep the ati one ?

---

### Post by lidex on 2010-02-16
You'll need to disable onboard graphics in the bios setup. Reboot your PC and at the bios boot screen press the appropriate key - mine is delete - your's may differ. It should say somewhere on the screen. Navigate the setup screens until you find the onboard or on-chip video and change the option to disabled. Save the settings, usually F10, and confirm.

Power down the PC and unplug the power cord at the power supply. Switch your vga/monitor connector to the output on the ATI card, plug the power cord back in and power up.

[COLOR="Red"]You do have the ATI card installed, correct??[/COLOR]

---

### Post by Natty Dreed on 2010-02-16
i didn't find any option in the bios

and i installed my ati card and plugged it's show every thing fine

until i reach Ubuntu and the screen looks dark but u can see and it's wooby not sure how to describe it

---

### Post by Natty Dreed on 2010-02-16
[[IMG]http://img534.imageshack.us/img534/5558/20100217035.th.jpg[/IMG]](http://img534.imageshack.us/my.php?image=20100217035.jpg)

[[IMG]http://img198.imageshack.us/img198/6055/20100217037.th.jpg[/IMG]](http://img198.imageshack.us/my.php?image=20100217037.jpg)

Maybe this will help :)

---

### Post by lidex on 2010-02-16
Cool. Can you post the results of the previous commands with the new setup please?

---

### Post by Natty Dreed on 2010-02-16
```
$ [COLOR=Red]lspci -nn | grep VGA[/COLOR]
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 330 [Xabre] PCI/AGP VGA Display Adapter [1039:0330] (rev 01)
```
```


$ [COLOR=Red]LIBGL_DEBUG=verbose glxinfo | head[/COLOR]
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
name of display: :0.0
```

```
$ [COLOR=Red]cat /etc/X11/xorg.conf[/COLOR]
cat: /etc/X11/xorg.conf: No such file or directory
```

```
$ [COLOR=Red]fglrxinfo[/COLOR]
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
```


same thing right ? Nothing change

I just want to thank u for helping me

---

### Post by StonedSidney on 2010-05-25
I have the same problem with a Radeon 5800 series card.
When  I check Hardware Drivers it says I am running ATI Fire GL.
Catalyst Control Center runs happily and says: Driver packaging version: 8.723.1-100408a-098580C-ATI

Performance is awful - dragging windows is very choppy. Can't enable desktop effects (no driver found).
[PHP]sid@sid-beast:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  20
  Current serial number in output stream:  20

sid@sid-beast:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  20
  Current serial number in output stream:  20[/PHP]

I have installed fglrx from Synapic, and tried the Catlyst drivers from ATI's website.

OK, solved this while replying!

Solution here: [http://ubuntuforums.org/showthread.php?p=9355822#post9355822](http://ubuntuforums.org/showthread.php?p=9355822#post9355822)

---

