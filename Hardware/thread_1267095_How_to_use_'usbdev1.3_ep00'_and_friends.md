---
title: "How to use 'usbdev1.3_ep00' and friends"
date: 2009-09-15
forum: Hardware
---

### Post by Silvernail on 2009-09-15
When I boot, I have in '/dev':
> usbdev1.1_ep00
usbdev1.1_ep81
usbdev1.2_ep00
usbdev1.2_ep02
usbdev1.2_ep81
usbdev2.1_ep00
usbdev2.1_ep81
usbdev3.1_ep00
usbdev3.1_ep81
usbdev4.1_ep00
usbdev4.1_ep81
usbdev5.1_ep00
usbdev5.1_ep81

When I plug in my USB TV capture cable  [View Here]("http://www.brilliantstore.com/computer_monitor_accessories_dekcell_cpa_1280.html"), I have:
> sbdev1.1_ep00
usbdev1.1_ep81
usbdev1.2_ep00
usbdev1.2_ep02
usbdev1.2_ep81
usbdev1.3_ep00
usbdev1.3_ep81
usbdev1.3_ep82
usbdev1.3_ep84
usbdev2.1_ep00
usbdev2.1_ep81
usbdev3.1_ep00
usbdev3.1_ep81
usbdev4.1_ep00
usbdev4.1_ep81
usbdev5.1_ep00
usbdev5.1_ep81

I have some new ones (usbdev1.3_ep82 etc). They are discussed here

[Link]("http://www.linuxquestions.org/questions/linux-newbie-8/usb-devices-in-linux-734529/?highlight=usbdev1.3_ep00")

Can I assume that this is the same as a 'sdb1' for mounting purposes? How to use them.

---

