---
title: "USB Modem"
date: 2013-08-29
forum: Hardware
---

### Post by jipbuntu on 2013-08-29
Hi 
I have a USB Modem in India
My modem is not recognized by Ubuntu 13.04 (Ubuntu Studio) and I have stried several guides online including 
[http://www.greplinux.net/2012/07/eve...now-about.html]("http://www.greplinux.net/2012/07/everything-you-need-to-know-about.html")

My device appears in the lsusb output but when I use the command
$ cat /etc/usb_modeswitch.d/**[vendor code]**\:**[product code]** | grep MessageContent

I get a reply that there is no such file or directory. I opened my usb_modeswitch.d directory and it is empty.

My device works fine in windows but not in linux ( ive tried several distros)

Thanks in advance 				****

---

