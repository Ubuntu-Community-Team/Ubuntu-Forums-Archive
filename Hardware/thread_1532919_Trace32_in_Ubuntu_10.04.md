---
title: "Trace32 in Ubuntu 10.04"
date: 2010-07-17
forum: Hardware
---

### Post by kishon on 2010-07-17
I installed trace32 from tarball to /opt/t32. Then I got this error
./bin/pc_linux/t32marm FATAL ERROR from X-windows: font not found: t32-sys-13 

So after reading some forum threads followed the following steps to solve the above error.

# cd /opt/t32/fonts
# mkfontdir .
# xset fp /opt/t32/fonts
# xset fp rehash

But I get the following error

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  45 (X_OpenFont)
  Serial number of failed request:  97
  Current serial number in output stream:  98

Any idea on how to solve this issue?

Thanks.

---

### Post by jmtarrant@gmail.com on 2011-05-19
This is how I resolved the TRACE32 missing font error.

> cd /etc/X11
> sudo gedit xorg.conf

Add the following line to your xorg.conf in the "Files" (witht he other FontPath directives)

FontPath       "/home/username/t32/fonts"

(Substitute your own path to the t32 install directory)

Now restart your PC and TRACE32 will find the fonts.

---

