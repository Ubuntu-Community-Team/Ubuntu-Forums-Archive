---
title: "[SOLVED] Wiped out my /etc/modprobe.d/blackslist..."
date: 2008-08-14
forum: General Help
---

### Post by toyota_f1 on 2008-08-14
In a frantic attempt to get my ridiculous Broadcom4306 to work more than 5 feet from a wireless AP I was running through a series of possible fixes..

in one I was changing my blacklist but missed the -a when using tee (which I had admittedly never used before).  Apparently in missing that it simply wrote the one line I wanted to add and wiped out everything else.  I don't believe a backup was made anywhere either...

I was able to undo the rest of the damage I had done but now I'm left with an empty /etc/modprobe.d/blacklist file which is giving me errors anytime I try to modprobe -r anything.

Anything I can do to recover or at least replace what would have been in my basic blacklist file?

---

### Post by pytheas22 on 2008-08-14
First of all, are you sure you don't have a backup at /etc/modprobe.d/blacklist~ ?

If not, the default blacklist looks like:
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
```

Also, you may want to try using bcm43xx with your 4306 card...it works well for me (the weak signal issue is the fault of b43, the driver that Ubuntu uses by default, which doesn't work very well for most people).  ndiswrapper would also work, though.

---

### Post by Zack McCool on 2008-08-14
Here's what I have...   It hasn't been modified since my original install, so it should be pretty much OK.  Just cut and paste it into a new file, created by root, of the same name...

```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# disable ipv6
# blacklist ipv6

```

Or, simply download the attachment, save it to the proper location (without the .txt), and chown it to root.

---

### Post by toyota_f1 on 2008-08-14
Thanks for the copies - yes, I absolutely wiped mine out - I didn't trust a script so was picking through it and messed up which caused it to be overwritten by a single line.

Every time I think I'm getting comfortable with a distro is when I realize I still don't know nearly enough.  :)

Ok, so I am using B43 right now - the default option from the restricted drivers.  What should I do to switch over to the bcm43xx?  Because if that will help with the poor signal strength and being stuck at 1 mb/s I'm all over it.

Thanks a ton!

---

### Post by pytheas22 on 2008-08-14
To install bcm43xx, first open up your blacklist and remove or comment the line that says, "blacklist bcm43xx."  Then add these lines to the blacklist:
```

blacklist b43
blacklist b43legacy
blacklist ssb
```

and save the file.

Then you need to install the bcm43xx firmware:
```

sudo apt-get install bcm43xx-fwcutter
```

You should be prompted to automatically download the firmware; say yes.  Then reboot and your wireless should be working better.

---

### Post by toyota_f1 on 2008-08-14
Well, it's better and it's not.  But I'll have to live with it until something better comes along I'm afraid...

I still can't connect to anything that has less than about 60% strength, although I'm now connecting up to 24 mb/s rather than 1 mb/s.

So thank you a bunch!

---

