---
title: "NVIDIA X Server Settings"
date: 2011-07-29
forum: Hardware
---

### Post by Blitzskee on 2011-07-29
Whilst trying to figure out why I don't have any 3D acceleration I opened NVIDIA X Server settings.  On opening I was presented with this message:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

So I ran

sudo nvidia-xconfig

and it gave me this:

> Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


What  is wrong here?? Why am I getting this error??

Thanks in advance.

---

### Post by mikewhatever on 2011-07-29
The first part of the message pretty much says it all:

the error: VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.

the reason: Device section "Default Device" must have a Driver line.

...and the following two lines say that nvidia-xconfig created a new configuration file. Does it work now?

---

### Post by Blitzskee on 2011-07-29
Nope now unable to startx =(

---

### Post by realzippy on 2011-07-29
So delete or rename the xorg.conf you have created..

Which driver?
How did you attempt to install it ?
Which (graphics) hardware?

```
sudo nvidia-bug-report.sh
```

creates a nice file in your home directory,which might give a clue...

---

### Post by realzippy on 2011-08-14
Did you give up?
So I would like to un-subscribe from this thread.

---

