---
title: "Brother MFC-J870DW"
date: 2014-02-06
forum: Hardware
---

### Post by jdier on 2014-02-06
I have the printer above and my Ubuntu is current. 

Whether I click the attached, either of the network versions or if I choose to add the IP in the URI section have the same problem.

I have been to the Brother site and downloaded and installed (using software center) both the driver and the wrapper.

While installing, I get to the driver selection section, I find Brother MFC-J870DW CUPS [en] (recommended)

When I get to test page it submits the job, the window reads:

Processing Processing - Connecting to printer Processing - The printer is not responding

When I try to access CUPS via [http://localhost:631/](http://localhost:631/) I am presented with problems related to permissions.

If anyone can help out, it would be much appreciated.

(Printer is working as advertised from Windows machines)

---

### Post by jdier on 2014-02-07
As a forever newbie, I am woefully inept at explaining how I fix things, but it looks like I have this working now.

Background is that I found the driver and cups wrapper here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html")

The .debs opened in Ubuntu Software Center and I clicked through the **Package "is of bad quality"**

Following all the typical Add Printer stuff, nothing was working.

In my final property settings that work I have:

_Device URI:_ **//Brother%20MFC-J870DW._printer._tcp.local**
_Make and Model:_ **Brother MFC-J870DW CUPS**

I am not printing wirelessly, but at least I am printing.

---

### Post by gifford on 2014-02-07
The easiest and most trouble free way of installing is to follow the instructions on the Brother site. On the page for downloading the drivers, it has install instructions under the box where the drivers are located. Following the instructions I have never had any problems installing several Brother printers both for network and USB.

---

