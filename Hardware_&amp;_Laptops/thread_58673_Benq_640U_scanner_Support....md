---
title: "Benq 640U scanner Support..."
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by omiazad on 2005-08-21
Dear Experts,
I own a Benq 640U scanner. I found this Scanner works by Sane. But when I open [color=RoyalBlue]Applications->Graphics->Xsane Image scanning program[/color], it gives me a error message: [color=Red]Failed to open device 'snapscan:libusb:001:004':Invalid Argument.[/color]

Can anyone please suggest me how can i use my Scanner?

---

### Post by daller on 2005-12-30
Have you tried in Breezy?

---

### Post by gmc2000 on 2006-01-17
i did, same result..

---

### Post by gmc2000 on 2006-01-17
Ah yes, the driver needs firmware.

Here is how to get this scanner to work under ubuntu.

- Find the file u96v121.bin on the scanner's driver disk or on a windows machine that has the driver installed (I found it in c:\windows\usbbin).

- Copy the bin file to some appropriate location, I put it in /etc/sane.d

- Edit /etc/sane.d/snapscan.conf (be root, eg 'sudo vi /etc/sane.d/snapscan.conf)

- Set the correct path to the firmware by changing the firmware line (eg. 'firmware /etc/sane.d/u96v121.bin)

- (Re)start xsane, and presto! One working scanner..

---

