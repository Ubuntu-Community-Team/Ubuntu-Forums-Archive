---
title: "xsane: &quot;no device&quot; - brother dcp-340cw driver?"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by Sofie on 2007-10-05
I installed the drivers from:
[http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html)

I installed the brscan2 driver for deb and then the scan tool.

When I start xsane it cant find any device?

I think I might have done something wrong and need to do it all again? How can I delete what I have done?

Or why does xsane not find the scanner?

---

### Post by linuxwizard on 2007-10-05
Have you installed Sane ? You need that also.

---

### Post by Sofie on 2007-10-06
I think so, yes. But I think the problem may be, that my wireless netcard: 
WN2302A-F4 13 ch. mPCI WLAN IEEE802.11 b/g (Atheros) is not working. 
I need to find a driver?

But then again, I am connectet to my router via wire, so it should be able to find brother in that way...

How do I install Xsane? If that is what Im missing?

---

### Post by linuxwizard on 2007-10-06
You can install through Synaptic.


[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

### Post by Sofie on 2007-10-06
Thanks.

But...

I do not know what synaptic is?

I tried the link, and removed the line with "net" in the file /etc/sane.d/dll.conf

But still no evices.

The scanner should work with ubuntu. Theres another post about it. I just dont understand what to do...

---

### Post by Sofie on 2007-10-06
Oh

The help says to enable the line
"net"

in the file
/etc/sane.d/dll.conf

How do I enable a line?

---

### Post by linuxwizard on 2007-10-06
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Just a suggestions before you start changing things get sane installed first than see how things go.

---

### Post by Sofie on 2007-10-07
Thanks!
Sane is installed. Someone told me to reinstall OS, but... I made so many changes now in all the files, so that seems almost impossible...

I "feel" the driver for brother MFC-210 is not working with DCP-340cw, but that is brothers suggestion, since there is no driver for dcp-340cw.

I just wonder how other people got it to work?

Perhaps its a combination of my notebook, my router (Linksys) and my brother...

---

