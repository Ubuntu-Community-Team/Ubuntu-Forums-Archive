---
title: "[SOLVED] Bootable XP iso on USB, through Ubuntu?"
date: 2008-08-02
forum: General Help
---

### Post by Eastisle on 2008-08-02
Hi,

I've been trying to get a touch screen properly working on my EEE pc w/ Ubuntu. 

I'm starting to think there might be something wrong with the controller or the screen itself. The screen came with a driver for Windows and I need to test it out. 

The problem is I don't have a cd burner to burn an XP iso on. I do have an usb flash drive. Is it possible to make a bootable iso on the flash drive in Ubuntu?

I've done bootable live CDs on USB before using syslinux. I've tried to do it for the XP iso, but failed miserably. Any advice? Thanks.

---

### Post by ModelM on 2008-08-02
I don't know anything about it, but these folks seem to know what they are talking about...

[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)

---

### Post by Eastisle on 2008-08-02
> **ModelM said:**
> I don't know anything about it, but these folks seem to know what they are talking about...

[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)

Thanks for the help. One of the prerequisites is to have a computer running Windows, which I have none. Nevertheless, I'll be trying this out over the weekend on my friend's computer. Thanks again.

In the meantime, any other ways I can attempt through Ubuntu?

---

### Post by ModelM on 2008-08-02
If you have the xp iso disk image in your computer, you can mount it like you would any other filesystem with the command:

mount -t iso9660 -o loop xp_cd.iso /mnt

You can then move to the /mnt directory & the entire contents of the XP disk will be there. You can copy whatever files you need to build your USB booting XP whatchathinger...

---

### Post by Eastisle on 2008-08-02
Thanks a lot!

---

