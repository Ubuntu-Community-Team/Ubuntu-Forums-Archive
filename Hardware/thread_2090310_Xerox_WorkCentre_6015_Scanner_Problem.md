---
title: "Xerox WorkCentre 6015 Scanner Problem"
date: 2012-12-01
forum: Hardware
---

### Post by GerryGG on 2012-12-01
I'm trying to get a Xerox WorkCentre 6015NI Printer connected to my lan to work with my Ubuntu 12.04 (32 bit) system. I installed the deb driver package that Xerox offers, and it installed OK... sort of. I can print with the 6015 from Ubuntu now. However, I can't scan. Both Xsane and Simple Scan say "no devices available". So, if anyone has gotten the 6015 to scan, I would love to hear from you. Thanks.

---

### Post by PhilGil on 2012-12-02
> **GerryGG said:**
> I'm trying to get a Xerox WorkCentre 6015NI Printer connected to my lan to work with my Ubuntu 12.04 (32 bit) system. I installed the deb driver package that Xerox offers, and it installed OK... sort of. I can print with the 6015 from Ubuntu now. However, I can't scan. Both Xsane and Simple Scan say "no devices available". So, if anyone has gotten the 6015 to scan, I would love to hear from you. Thanks.

A possible work-around...

I've never had good luck getting SANE to see a scanner on a LAN. We have a WorkCentre multifunction at the office and I use the controls on the scanner to scan to a Samba share I've set up on my local machine. It looks like your model also has scan to network share functionality.

---

### Post by GerryGG on 2012-12-02
Hi Phil. Thanks for your reply. It does show scan to network on the panel. But I can't get that to work either. I'm getting "Connect error 031-555" on the panel. I've set up the Samba share on my Ubuntu 12.04 box, with all permissions set, but it's not working. So, not sure if I just haven't set up the share properly (or properly listed the share in the printer Computer/Server Address Book) or whether it is simply a bug in the Xerox deb driver. From the printer panel I can scan to a USB memory stick, inserted into the printer directly. So I do have that as a clumsy workaround (i.e., scan to USB stick; remove stick; insert stick in Ubuntu computer; access scan). But it would be nice if I could scan directly to the computer. I haven't tried connecting the printer directly to the computer yet - via USB.

---

### Post by PhilGil on 2012-12-02
> **GerryGG said:**
> Hi Phil. Thanks for your reply. It does show scan to network on the panel. But I can't get that to work either. I'm getting "Connect error 031-555" on the panel. I've set up the Samba share on my Ubuntu 12.04 box, with all permissions set, but it's not working. So, not sure if I just haven't set up the share properly (or properly listed the share in the printer Computer/Server Address Book) or whether it is simply a bug in the Xerox deb driver. From the printer panel I can scan to a USB memory stick, inserted into the printer directly. So I do have that as a clumsy workaround (i.e., scan to USB stick; remove stick; insert stick in Ubuntu computer; access scan). But it would be nice if I could scan directly to the computer. I haven't tried connecting the printer directly to the computer yet - via USB.

The Xerox drivers will have no effect on whether the scan to network drive is functional.

The first thing to do is troubleshoot the Samba share. Can other computers on your network see it and write to the shared folder?

If the share is working correctly, then you probably don't have it set up right on the Printer/Scanner. I remember it being somewhat complicated to initially set up on my office Xerox. I had to set up a scan to network template then enter the share information. FWIW, here is the page from the management console showing how my share is set up.  

[IMG]https://dl.dropbox.com/u/30771937/ShareForScannedDocuments.jpg[/IMG]

---

### Post by GerryGG on 2012-12-03
Hi Phil. Thanks for your follow-up. I had suspected that it could have something to do with how samba is set-up. However, I've just discovered another unrelated problem with this printer (or possibly cups). This has been reported numerous times, and a bug is already filed... but I am also unable to print colors. I can copy colors OK but I can't print them accurately. Because of the color issue and the scanning issue, I have decided to return this printer, as it is still within the return period. Thanks again Phil for your help. Hopefully it will guide others who have the same problem, but are not able to return their printer.

---

### Post by PhilGil on 2012-12-03
Sorry it didn't work out for you. I guess incompatible peripherals are something Linux users have to put up with. It's especially frustrating when Linux drivers are available but things still don't work as they should.

---

### Post by jarome on 2013-08-01
> **PhilGil said:**
> Sorry it didn't work out for you. I guess incompatible peripherals are something Linux users have to put up with. It's especially frustrating when Linux drivers are available but things still don't work as they should.
The firmware in the printer apparently does not work with newer SMB servers. It does work using an ftp server.

---

