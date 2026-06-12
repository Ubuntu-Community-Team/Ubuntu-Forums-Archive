---
title: "HP 2540 deskjet: Unable to set up wireless printing"
date: 2014-01-18
forum: Hardware
---

### Post by clenny on 2014-01-18
I have an old 2.1 macbook running Ubuntu 13.10. I bought a HP 2540 deskjet all in one. I was able to set it up on my newer Macbook running Mavericks but haven't been able to set it up on the Linux box.
I downloaded the hplip package and opened the hplip-3.14.1.run shell script that was on the desktop.
It took a long time but seems to have run but as far as i can tell, nothing happened. I attempted to follow the install instructions found here:[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

However, right away i got this error message: Could not open hplip-3.14.1.run

Any suggestions?

---

### Post by clenny on 2014-01-19
I was able to get the printer installed following the instructions I found in another posting. However, now I keep getting a device communication error (5012). Any suggestions?

---

### Post by clenny on 2014-01-20
I've been trying to figure this thing out. Am I correct in thinking that this connection info (hp:/usb/deskjet_2540_series?serial=CN3992DM2J0604) indicates that my configuration is for a usb connection? I thought I was setting it up to print wirelessly. At least that's what I chose in the hp wizard that ran and at one point I was prompted to removed the usb cable. How can I reconfigure this to connect wirelessly?

---

### Post by clenny on 2014-01-20
Additionally, running the hp doctor just tells me that either the machine isn't powered on or fails to communicate. Turn on printer and re-run. So I turn it off and turn it back on and run the doctor, same result. I would really appreciate some advice here, please.

---

### Post by clenny on 2014-01-26
I finally got it to work. I plugged the USB cable back in and the printer rked. I went to settings and there was an option to set up wireless printing. I don't believe it was there before. Anyway, I ran the wizard but this time I waited until after I clicked finish before I pulled the usb cable. I then got a prompt to do a hp-setup and was given the printer IP address. I ran it from the terminal, which opened up another, different hp wizard and this time it worked. Test page printed successfully. So problem resolved.

---

