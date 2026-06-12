---
title: "Ubuntu and SonyEricsson W660i?"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by pinkunicorn on 2008-02-03
I wonder if a SonyEricsson W660i will work without problems with Ubuntu (copying music to it, copying photos from it)? Will both USB and Bluetooth work?

---

### Post by hyperair on 2008-02-03
Copying music and photos will require you to put your phone into file mode (via USB), but via Bluetooth, it should work. Other phone features can be handled by Wammu if I'm not mistaken.

---

### Post by hojthojt on 2008-03-04
Hi,
I have a SonyEricsson K610i and Ubuntu 7.10 on a tx1151ea laptop. I'm able to copy files to and from my phone using both the USB cable and with bluetooth.

For bluetooth however, I needed to do this first:

The first time  I tried to connect to my Sony Ericsson K610i with bluetooth, the tx1000 found it when browsing for BlueTooth devices, but when connecting to it I got the following error message:

"OBEX [mac address] is not a valid location"

Googled and found a tip to install the following:
```
sudo apt-get install gnome-vfs-obexftp
```

Now it works to connect and browse files on the phone.
Unfortunately I have not yet been able to use my mobile as a modem. Any hints are welcome.

---

### Post by hyapadi on 2008-07-17
How about texting ( sms ) via computer. Like what official SE software can do?

---

### Post by hyperair on 2008-07-21
> **hyapadi said:**
> How about texting ( sms ) via computer. Like what official SE software can do?

Wammu can handle that.

---

### Post by Kevbert on 2008-07-21
Your SonyEricsson phone should work fine with either 7.10 or 8.04 Ubuntu.  I'm using a K800i on both.

---

### Post by hyapadi on 2008-07-21
I just realized that can be done with linux! Wow!

What else can be done with SE handphone? sync with outlook ( evolution )?

---

### Post by Kevbert on 2008-07-23
You can import contacts from the phone into Evolution.  What you have to do is send the contacts to the PC via bluetooth (as a vcf business card file).  Once you have this you can import the contact into Evolution where they are saved under contacts.  I don't think it's possible to sync contacts without a plugin program (not known to me) as the only syncing by default in Evolution is for the Palm Pilot.
To send contacts to the phone save the contact as a vCard and then right-click the file and send to phone via Bluetooth.

---

### Post by hyapadi on 2008-07-23
If I'm using VmWare or VirtualBox to have windows inside Linux, could it access the USB cable data for sync with the PCSuite inside the windows?

---

### Post by Kevbert on 2008-07-24
I don't know, but it may be possible to sync Outlook with the phone.

---

