---
title: "Major problem with Nvidia after a release upgrade, 12.04 to 14.04. Can’t access termi"
date: 2015-05-08
forum: Hardware
---

### Post by livin2chill on 2015-05-08
[COLOR=#111111][FONT=Ubuntu]After upgrading from 12.04 to 14.04 I experience a complete freeze at the login. Apparently it's caused by a missing Nvidia driver file.
I can’t use any input devices, so I can’t use Ctrl+Alt+F2 to get to the command line.
I can’t ssh in for whatever reason.
Recovery menu either freezes or doesn’t allow any input, I cannot tell.
Anything I can do?
I need this up and running ASAP, it’s an important webserver.
[/FONT][/COLOR]
Downloading a live image now, could I possibly install on the live system then copy the files over to my standard?

---

### Post by blm-ubunet on 2015-05-08
Add "nomodeset"  (not with the quotes!)  to your kernel load cmd in grub..

At least you should then get a console screen.
Could then remove nvidia packages to trigger kernel module rebuild, then reboot try without nomodeset.

Adding "nomodeset" stops the nVidia driver kernel module.
AFAIK The update process will have installed a new kernel & attempted to build-in the pre-existing DKMS kernel module(s).
That's worked just fine for me on multiple computers.
This process could fail if the linux headers package is not installed.

---

### Post by livin2chill on 2015-05-08
Well, I was able to boot into a shell, but here's the catch: all keyboard and mouse inputs are completely ignored...
I was able to dig up some stuff about this, apparently it's something with the kernel not recognizing any input at all...

EDIT: 
Apparently this driver issue affects all ethernet communications as well...could this be any worse?

---

### Post by livin2chill on 2015-05-09
Okay, ALL FIXED. I hope that anyone with this problem can see it. All I had to do was get a 12 or 14.04 live install, pick the advanced options, then go into the recovery mode. Pick drop into root shell. THEN I ran sudo dpkg --configure -a, then installed Nvidia drivers.

---

