---
title: "Connecting Nokia N70 using CA-53 USB data cable"
date: 2008-08-06
forum: Hardware
---

### Post by sharad.sharma on 2008-08-06
I am using Ubuntu 8.04 and trying to connect the Nokia 70 phone with the CA-53 USB data cable.The phone doesn't mount.How can I make it work?I need to transfer data between the computer and the phone.

---

### Post by sharad.sharma on 2008-08-07
Please help!

---

### Post by ben2talk on 2008-09-30
> **sharad.sharma said:**
> Please help!

I have followed several guides with my N70.
I can gain recognition of my phone using OBEX, but cannot browse it or gain anything else except for the information.

ben@linux601:~$ lsusb |grep Nokia
Bus 003 Device 003: ID 0421:043a Nokia Mobile Phones N70 USB Phone Parent

I also installed 'wammu' from synaptic, no luck.

I think this isn't an interesting topic, perhaps as phones change periodically, and will not find much support.

---

### Post by ben2talk on 2010-11-26
ROFL - same phone, same problem, and not much new help - but my other half's N73 connects okay for transferring files (with a Mass Storage mode)

---

### Post by desdecode on 2011-04-19
Hi,

I had the same problem but was I able to fix it very easily and upload/download files to/from my nokia n70, you need to use obexftp and obextool together.

First use obexftp to find the phone, then connect to it using the correct interface_number and pass this command to obextool.

I had two interfaces appear for my nokia n70 when I ran "obexftp -u" so I think that's probably why it didn't connect straight away.

Basically, connect the phone via the usb cable, run  "sudo obexftp -u" and it will show the interfaces it finds:

```
Found 2 USB OBEX interfaces

0 (Manufacturer: Nokia Product: Nokia N70 Serial: (null) Interface description: SYNCML-SYNC)
1 (Manufacturer: Nokia Product: Nokia N70 Serial: (null) Interface description: PC Suite Services)

```Then run "sudo obexftp -u INTERFACE_NUMBER -l" this'll try and connect using the interface and list the contents of the phone.

Lastly, once you've been able to connect and list the phones contents (the drives will show) you just pass that command straight to obextool: 

```
sudo obextool --obexcmd "obexftp -u 1"
```I've just done it this morning and downloaded some photos from my phone

I've posted how to do it on my blog to help people out: [http://desdecode.blogspot.com/2011/04/connecting-nokia-n70-to-ubuntu-10-via.html](http://desdecode.blogspot.com/2011/04/connecting-nokia-n70-to-ubuntu-10-via.html)

Hope this helps and you get it working,

desdecode

---

