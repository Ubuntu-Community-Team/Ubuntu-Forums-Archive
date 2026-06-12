---
title: "[SOLVED] Tap to click"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by Stryker777 on 2008-03-13
Hello,
My touchpad settings seem to have been lost after the last update I got but it was just a python update.  I am running on Gutsy.  I set all of my settings again and everything seems to be working except I can not disable tap to click.   Checked or unchecked tapping still works and I really need it turned off.  Anyone have any ideas?
Thanks

---

### Post by OffAxis on 2008-03-13
within your xorg.conf file there should be  a section for "synaptics" (which is probably the driver you're using)

```
sudo nano /etc/X11/xorg.conf
```

Look for the line MaxTapTime option and set it to zero.


```
Option        "MaxTapTime"       "0"      #0 should disable, 100 should enable
```

If the option isn't there just add it in.

restart x and it should be disabled.

---

### Post by Stryker777 on 2008-03-13
Perfect!  Thanks.  It was working yesterday and today gone lol.  Glad someone pays attention and remembers the options.  
Thanks again.

---

### Post by OffAxis on 2008-03-13
you're welcome.

For future reference, there's a community docs page here:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Of particular interest (once you have the **Option "SHMConfig" "on"** line in there) is

```
synclient -l
```

which will list available options to enable or disable with the synclient tool.

---

