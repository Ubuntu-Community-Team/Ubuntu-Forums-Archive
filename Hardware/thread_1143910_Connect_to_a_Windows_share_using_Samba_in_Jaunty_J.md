---
title: "Connect to a Windows share using Samba in Jaunty Jackalope"
date: 2009-04-30
forum: Hardware
---

### Post by Jammy4041 on 2009-04-30
Hi All,

I would like to connect to a printer that is connected to a PC running Win***s.

I have found out a way to do it in what I do believe to be 7.04 Feisty Fawn, but the gnome-cups-manager is now not a part of ubuntu.

It's located here:

[http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-computers.html](http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-computers.html)

The system-config-printer tool does things differently and so, I am very confused. :confused:

Before, I had to make sure that my printer was shared, which it is, and where it says "printer", type the name of its share name. Then I had to type its IP address in where it says "host".

If I cannot do this using the system-config-printer tool, is there any way I can do this using the localhost:631 CUPS manager using firefox?

Thankyou in advance for all your help.

---

### Post by dandnsmith on 2009-04-30
I was trying this earlier today, using UNR on a USB stick with a netbook.

The config stuff is accessed via Administration|Printing, and follows roughly the path shown in that site you quoted.

However, that doesn't tell the whole story - the bit dealing with the sharing model at the W* end doesn't take into account the various methods of sharing security used by W* versions. You may need to set up SAMBA to make the linux machine appear part of the W* workgroup - I haven't got it all worked out yet - and also there is any firewall effect to be considered (especially if this is the first time you've tried to share files or the printer).

---

