---
title: "persistent usb drive install?"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by heiNey on 2009-09-21
hey guys,

i just installed 9.04 onto a usb drive using unetbootin.  i read that in order to make any changes persistent, i need to download a casper-rw file and extract it into the root of the usb drive.  then i need to edit the syslinux.cfg file to add the word 'persistent' on the line that starts with append and before the two dashes.  

the problem is that its not persistent.  everything disappears when i reboot.  is there anything else that i needed to do?  it is a 2GB usb stick

this is what my file looks like:

```

default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash persistent --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit

label ubnentry1
menu label oem=OEM install (for manufacturers)
kernel /ubnkern
append initrd=/ubninit oem=oem-config/enable=true

```

---

### Post by Plumtreed on 2009-09-21
You can do this with  System>Administration>USB Startup Disk Creator

Or have I missed something.

---

### Post by heiNey on 2009-09-21
i dont think that makes it persistent, does it?

---

### Post by heiNey on 2009-09-21
ill give it a shot anyway

---

### Post by Plumtreed on 2009-09-21
If you follow the few steps it should develop a persistent USB drive. I have not tried it on anything other than an Ubuntu based OS. It worked, for me, on Ubuntu, Crunchbang, Spri and Masonux. 

However, when I tried it on Mint it has not retained it's persistency but that may be more the fault of a bad cd burn. It does set Mint up on a USB drive and it works as a live CD but it does not retain any changes.

---

### Post by heiNey on 2009-09-25
hmm...i tried it and it seemed to work...but when i plugged it into a different computer, it just died on me.  how weird.  maybe the usb stick is dead.  i give up.  thanks anyway

---

### Post by Plumtreed on 2009-09-28
> **heiNey said:**
> hmm...i tried it and it seemed to work...but when i plugged it into a different computer, it just died on me.  how weird.  maybe the usb stick is dead.  i give up.  thanks anyway

I suspect the 'other' computer may have required a BIOS adjustment or perhaps it is just not able to boot from a USB.

---

