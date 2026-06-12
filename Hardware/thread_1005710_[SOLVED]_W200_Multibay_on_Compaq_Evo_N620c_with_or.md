---
title: "[SOLVED] W200 Multibay on Compaq Evo N620c with orinoco_usb under 8.10"
date: 2008-12-08
forum: Hardware
---

### Post by wittgeinstein on 2008-12-08
Hello dear ubuntuforumusers!

After upgrading to Intrepid Ibex my W200 Multibay (WLAN Adapter) on my [Compaq Evo N620c]("http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=316682&submit.y=0&submit.x=0&lang=en&cc=us") doesn't work under Intrepid Ibex, altough I have worked out [WifiDocsDeviceCompaqW200]("https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200").

That means that I had probably used [orinoco_usb]("http://www.nongnu.org/orinoco/") driver for my w200 and [deactivated network-manager]("https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager") in 8.04 and it was working, but I can't disable the network-manager in Intrepid Ibex. So my assumption is that orinoco_usb and network-manager can't work together.

I've posted some terminal outputs on paste-service of ubuntuusers:
[http://paste.ubuntuusers.de/393181/]("http://paste.ubuntuusers.de/393181/")

So have anybody an idea how to get my w200 working under 8.10? Or how to disable the network-manager under 8.10? If so, please let me know.

Thanks and Regards,
Wittgeinstein

---

### Post by wittgeinstein on 2008-12-25
I've solved this problem by myself now. There was a problem in the driver, but now it still works.

regards,
wittgeinstein

---

