---
title: "Secure boot violation"
date: 2013-02-17
forum: Hardware
---

### Post by husetikanada on 2013-02-17
My new computer is an Acer xc600. The first thing i did was to delete the Windows 8 operating system, format the hd and installed ubuntu 12.10. No big problems so far.

But now the computer is totaly locked. When I start I get a red frame with the text "Secure boot violation. Invalid signature detected. Check secure boot policy in set up." There is also a OK-buttom I can't click.

I don't know how to reach setup. F12, F11 and so on doesn't work.

Can't start from usb or cd either, because it's not seems possible to make a choise when start. I also tried pmagic with the same result.

I am stucked. Any help here?

---

### Post by TheFu on 2013-02-17
Does this explain/help?
[http://askubuntu.com/questions/206950/12-10-uefi-secure-boot-install](http://askubuntu.com/questions/206950/12-10-uefi-secure-boot-install)

---

### Post by oldfred on 2013-02-17
A user in another thread was able to flash UEFI/BIOS and get back in. 

But many new system have a fast boot that only gets into UEFI from Windows. You have to turn fast boot off first from Windows.

Ubuntu/Grub added a new entry that should get into UEFI menu. But no idea how to get to it if you cannot change boot to flash drive.

---

### Post by husetikanada on 2013-02-17
Now I managed to reach the setup by the DEL key (silly me, it was TO simple).

But it doesn't help much. When I set the start to usb or cd/dvd, the machine still try to start the hard disk. There are no alternatives to change the prior hard disk from uefi to anything else.

When I try to start I get the message: Error: No boot disk has been detected or the disk has failed.

---

### Post by oldfred on 2013-02-17
You should also have a one time boot key.


       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

