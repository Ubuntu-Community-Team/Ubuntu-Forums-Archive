---
title: "Cannot mount volume."
date: 2009-12-18
forum: Hardware
---

### Post by asel_ on 2009-12-18
Hi, when I insert any usb flash disk it is not mounted automatically unless I make a folder and then mount the usb flash. I don't know why ?

see this picture.

[IMG]http://uploads.freeweb7.com/up/download_.php?id=68&key=2046424541[/IMG]

So, I want it to mount automatically.[HTML][/HTML]

---

### Post by asel_ on 2009-12-19
Any help ?

---

### Post by moddie666 on 2009-12-19
Hi.

Google this:

"invalid mount option when attempting to mount the volume"

greetings
/moddie

---

### Post by daemon3 on 2009-12-19
When mounting a device, the mount information is stored in /etc/fstab or /etc/mtab (fstab is more user-readable :) ).  see which device is trying to be mounted with [FONT="Courier New"]dmesg | grep usb[/FONT].  Read up on fstab documentation with [FONT="Courier New"]man fstab[/FONT].  I know man pages are confusing, but it take a lot longer to tell you what's going on in the file. :)
Hope this helps.  If you need any more help, don't  be afraid to ask.

---

