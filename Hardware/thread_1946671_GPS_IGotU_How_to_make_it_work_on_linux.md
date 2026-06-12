---
title: "GPS IGotU How to make it work on linux ?"
date: 2012-03-25
forum: Hardware
---

### Post by diotcrozet on 2012-03-25
Hello,
 I have a GPS plotter** [ IgotU-GP-800PRO]("http://global.mobileaction.com/product/product_i-gotU_GT-800pro.jsp")**.

 I tried for several days to get it running on Linux with some setbacks:
 - I manage to create and read GPX files with [GPXEditor]("http://shamavideals.l-wa.org/GPXEditor1.1/") 
 - but at the moment,** I can not export or import GPX files from my GPS IgotU**. I tried**[ Igotu2GPX]("https://launchpad.net/igotu2gpx")** but apparently my GPS is not recognized.

 Here are some error messages that  I get when I tried :
[HTML]
igotu2gpx info Downloading configuration... Unable to download configuration from GPS tracker: Unable to find device '0df7:0900'[/HTML]I tried to change the ID in igtougui because it appears that the ID listed above is not the same i get :
[HTML]
lsusb
Bus 007 Device 018: ID 0df7:0b80 Mobile Action Technology, Inc. [/HTML]So even after that change I get this :
[HTML]# igotu2gpx info Downloading configuration... Unable to download configuration from GPS tracker: Unable to send data to device: Relais brisé (pipe)[/HTML]_My questions are :_

**1/ do you have an idea of what I could do to be able to use igotu2GPX with my GPS computer ?**

**2/ If someone already uses this IgotU GP-800Pro GPS with a linux OS, I would like to know which software to use to export and import GPX files** to and from this GPS...I'm trying GPSBabel at the moment but apparently it doesn't work either...

Thanks

---

### Post by diotcrozet on 2012-03-27
It appears that** Igotu2gpx** is not working with the IgotU GP-800Pro and GP-800 computers as it is specified in this [discussion]("https://answers.launchpad.net/igotu2gpx/+question/175208").

So I tried with** GPSBabel **but it doesn't work, apparently the IGotU GPS are not in the list of compatible format.

[B]Does someone have an idea to import and export GPX files from and to the IGotU GP-800 computer ?

[/B]If possible, II would like not to use my lost dusty windows parittion again [B]#-o.
[/B]

---

### Post by diotcrozet on 2012-04-19
No idea ?

---

