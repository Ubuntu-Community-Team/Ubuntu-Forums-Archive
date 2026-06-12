---
title: "iriver clix + amarok"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by rienfleche on 2008-03-31
I recently purchased an iriver clix and I wanted to use it with my linux machine.  I have looked through a lot of threads about various mtp players on this site, and I can't for the life of me get anything to work.  I have attempted, and (I believe falied) to install libmtp correctly.  No matter what I do, I can't seem to get the device to show up in amarok.  Any help would be greatly appreciated, bearing in mind that I know nothing about anything.

Thanks

---

### Post by archlich on 2008-04-02
Settings>Configure Amarok>Plugin>MTP Media Device>Close Out>Devices (tab on the left)>Connect (button at the top)

Or add new device, and select mtp, and an appropriate name.  Let me know if you have any trouble.

---

### Post by rienfleche on 2008-04-03
does not work.  I believe that I need to install the libmtp libraries first, which I do not know how to do.

---

### Post by archlich on 2008-04-03
I was able to get it working using a vanilla 7.10 installation.

Make sure it's connected, and that you see the device when you do a $lsusb on the command line.

---

