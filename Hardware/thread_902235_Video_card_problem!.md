---
title: "Video card problem!"
date: 2008-08-27
forum: Hardware
---

### Post by macmoy on 2008-08-27
somebody please help me. im new to linux (ubuntu 8.04)

i cant enable the desktop effects aand the login window is not centered.

inside my xorg is:

Device
    Identifier "Configured Video Device"


when i execute: lspci | grep VGA

output: 
01:00.0 VGA compatible controller:
VIA Technologies, Inc. Chrome9 HC IGP (rev 01)

how can i install the correct driver to enable desktop effects?

what is the name of my video card? chrome9?

can somebody PLEASE HELP ME!!!

Thank you so MUCH!!

---

### Post by dsm iv tr on 2008-08-27
The driver you need is called "via". I don't know if it supports 3D acceleration yet, but I hear tell of the 2D working just fine. In any case, it should net you better performance and more resolutions than the vesa driver.

See also: [http://ubuntuforums.org/showthread.php?t=899459](http://ubuntuforums.org/showthread.php?t=899459)

Open a terminal, and run

```

$ sudo aptitude install xserver-xorg-video-via
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BACKUP
$ sudo gedit /etc/X11/xorg.conf

```

Look for a section like

```

Section "Device"
...
        Driver      "vesa"
...
EndSection

```

and change it to read

```

Section "Device"
...
        Driver      "via"
...
EndSection

```

Save the file, and reboot.

On the off chance that X refuses to work after you make the change and reboot, copy the old backup file back into place or change the line to read "vesa" again. You can do this from a text terminal using a command like

```

$ sudo nano /etc/X11/xorg.conf

```

Good luck!

---

### Post by macmoy on 2008-08-28
STILL, I cant use the Desktop Effects.
And i the login windows is still not centered.

ANY OTHER HELP PLEASE.

---

### Post by fauzie on 2008-08-28
I used an older version of that card. It just won't run under Linux. You might be out of luck here. They have a linux driver on their website, but it broke everything when installed here. You're welcome to try though :)

---

