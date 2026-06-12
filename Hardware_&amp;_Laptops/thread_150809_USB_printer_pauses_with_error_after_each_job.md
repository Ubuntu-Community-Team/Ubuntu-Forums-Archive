---
title: "USB printer pauses with error after each job"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by gkiller on 2006-03-26
I have a Panasonic KX-P7105 USB printer. Although this printer is not supported by cups directly, the "ljet4" driver works well enough because my printer understands PCL.

I am able to print both locally and from a remote Windows box, but there is one problem:

The first job is printed normally. But after I send the second job, the printer status goes to "Paused" and does not print. If I click on Properties of the printer in the print manager (System > Administration > Printing) the status field shows the following:
```
Paused: Unable to open USB device "usb://Panasonic/KX-P7105": No such device
```
The Job window shows my job with the state "pending: printer-stopped".

I can then right-click on the printer in the manager and select "Resume", and my printer starts printing again. But now every time I want to print (remotely or locally) I have to hit "Resume". Even after I restart cups with
```
sudo /etc/init.d/cupsys restart
```
I have to hit "Resume".

Can anybody help me? Because now I basically cannot use my printer, especially from remote, because I have to run to my Ubuntu box everytime and hit "Resume".

If you think some cups or other logs would help, I can paste them here, but basically what I saw in the log files is the same "Unable to open USB device" error.

I once sent two jobs really quickly one after another remotely from my Windows box and it printed both of them normally. But then I sent another and the printer "paused" again.

Thanks in advance for your help.

---

### Post by gkiller on 2006-04-01
I just tried the Dapper Flight 6 Live CD, and it seems fixed there.

---

