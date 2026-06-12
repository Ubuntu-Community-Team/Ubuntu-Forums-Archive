---
title: "Mythbuntu: doesn't boot pre-install"
date: 2008-10-16
forum: General Help
---

### Post by laga on 2008-10-16
Hello,

as requested on IRC, here's my bug report:

I tried wubi-8.10-rev512 with the latest Mythbuntu daily i386 live disk. When I rebooted my VM to complete the install, I was dropped into a grub prompt. Hitting ESC brought me back to this menu: [http://laga.ath.cx/wubi-mythbuntu.png](http://laga.ath.cx/wubi-mythbuntu.png)
Selecting any of the options there drops me back into a grub shell ("halt" and "reboot" however work fine).

Here are some menu.lst files I found on my hard disk: [http://pastebin.ca/1228627](http://pastebin.ca/1228627) and  [http://pastebin.ca/1228631](http://pastebin.ca/1228631)

I'm running Windows XP in a VirtualBox VM. Windows is installed on one virtual hard disk (c:) and Ubuntu is supposed to be installed to another virtual hard disk (e:).

Let me know if you need anything else.

Regards,

Michael

---

### Post by ago on 2008-10-16
Hi Michael, 

please check that 

A) /ubuntu/disks/boot/grub/menu.lst is indeed available
B) that grub4dos can actually reach it

To do the latter, press "C" in grub and navigate to the file using tab completion

root (hdX,y)/ubuntu/disks[TAB]

---

### Post by laga on 2008-10-17
Hi Ago,

E:\ubuntu\disks\boot\grub does not exist. Of course, /ubuntu/disks/boot/grub/menu.lst  is not available in grub4dos.

---

### Post by ago on 2008-10-18
Laga in fact that is created after linux-side installation, on the first reboot the relevant menu.lst is /ubuntu/install/boot/grub/menu.lst which is used if /ubuntu/disks/boot/grub is not available (which is not on first reboot). Should have mentioned it earlier.

---

### Post by laga on 2008-10-23
Yeah, those files are available. However, it only boots when I remove the "find --set-root" options and replace them with "root (hd1,0)". It looks like grub doesn't look on the second hard disk by default?

---

### Post by ago on 2008-10-23
> **laga said:**
> Yeah, those files are available. However, it only boots when I remove the "find --set-root" options and replace them with "root (hd1,0)". It looks like grub doesn't look on the second hard disk by default?

find --set-root /file/to/search/for

Will look for the specified file and set root to that partition.

So if the file is in (hd1,3)/file/to/search/for that is equivalent to the command: root (hd1,3)

---

