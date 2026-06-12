---
title: "Need Help Installing HP Pole Display for POS"
date: 2009-09-17
forum: Hardware
---

### Post by sad1sm0 on 2009-09-17
I am building a linux based POS system using OpenBravo on Kubuntu 9.04.  I have an HP LD220 Poll Display that I need to get working with this system.  I am still relatively new to ubunutu as of yet, but I am comfortable editing source and making changes as needed provided that the changes actually fix the problem instead of breaking things further.
  I have done a bit of research, and apparently there was a patch for the kernel to assign ids to specifically this piece of hardware which connects via usb.  However, I am still not getting an id as far as I can tell.  I would assume it would be either /dev/usb/product_id or /dev/ttyUSBxx, neither of which is an option for me.  Do I have to enable this option in the kernel or something.  a quick lsusb does show the device as connected.  Let me know if you need anything else from me.  I would appreciate it.  The technical information about the patch can be found [here]("http://lists.zerezo.com/linux-kernel/msg19775534.html").  Hopefully this helps.  I dug into the kernel source and located it but I'm not really sure what I need to do to get it going.

---

### Post by dfnslink on 2011-05-18
Can you indicate how you solved this?  I am in a similar situation and noticed this post.  Thanks

> **sad1sm0 said:**
> I am building a linux based POS system using OpenBravo on Kubuntu 9.04.  I have an HP LD220 Poll Display that I need to get working with this system.  I am still relatively new to ubunutu as of yet, but I am comfortable editing source and making changes as needed provided that the changes actually fix the problem instead of breaking things further.
  I have done a bit of research, and apparently there was a patch for the kernel to assign ids to specifically this piece of hardware which connects via usb.  However, I am still not getting an id as far as I can tell.  I would assume it would be either /dev/usb/product_id or /dev/ttyUSBxx, neither of which is an option for me.  Do I have to enable this option in the kernel or something.  a quick lsusb does show the device as connected.  Let me know if you need anything else from me.  I would appreciate it.  The technical information about the patch can be found [here]("http://lists.zerezo.com/linux-kernel/msg19775534.html").  Hopefully this helps.  I dug into the kernel source and located it but I'm not really sure what I need to do to get it going.

---

