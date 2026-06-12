---
title: "CUPS problems"
date: 2010-02-18
forum: Hardware
---

### Post by rainy-day on 2010-02-18
Hi, I had cups working with cups-pdf (I don't have any other printers that'd work in linux). However, when I was trying to set up my ljet1100, which turned out not to work through the usb adapter, I messed something up and now cups doesn't work at all.

The interesting thing is that even if I uninstall all cups-related packages as well as CUPS itself, there is no /etc/cups/cupsd.conf. When I run dpkg-reconfigure cups, answer all questions, it still does not create the conf file. The only things in /etc/cups are: raw.convs, raw.types, ppd and ssl.

When I use gnome printer configuration tool, it says not connected and if I try to connect, it says, 'httpConnectionEncrypt failed'.

If I run /etc/init.d/cupsd start , it says child returned with status 1.

If I look at /var/log/messages and syslog, the only thing related to cupsd are a few lines like this:

Feb 18 01:22:53 ak-desktop kernel: [10966.817079] type=1505 audit(1266474173.481:37): operation="profile_replace" pid=6788 name=/usr/sbin/cupsd


Please help! Any advice/comments appreciated. I've already spent many hours on this and this is pretty frustrating..

---

