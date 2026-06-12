---
title: "HP Photosmart 5515 will not print out full page"
date: 2015-07-20
forum: Hardware
---

### Post by Budoc on 2015-07-20
Hello,

I've been attempting to show my friend that Linux is now easier than ever to use and works "out of the box"! Unfortunately, I decided to help them try to get their HP Photosmart 5515 and I may have given the impression that Linux is anything but easy!

The central problem that I am experiencing is that when the printer prints an A4 page, it doesn't appear to be printing the lower fifth of the page. At first, I thought that this was a Libreoffice Writer quirk but I get this problem with a pdf in evince too.

I first tried to print a document with the default packages in my version of Ubuntu (14.04) and after I couldn't get the entire page printed, I installed HPLIP 3.15.7 with the instructions on this page: [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

The Printer was installed by running hp-setup and the Wireless/802.11 option that requires a temporary USB connection. The printer is recognised as Photosmart-5510d-series but still the full page is not printed out. I have checked that the printer setup in Libreoffice is A4 and the page appears as expected in the print preview. The problem only occurs once a page is physically printed. 

Has anybody managed to get Ubuntu working with this printer before? From the HPLIP website, I'd expect the printer to be reasonably compatible. 

Thanks in advance.

---

### Post by mansonfan78 on 2015-07-20
Does it do the same thing when connected to usb?  If you haven't already try a direct usb connection and disable it's wifi connection.  This will at least help to narrow down the problem.

---

### Post by PaulW2U on 2015-07-20
*Thread moved to **Hardware**.*

---

### Post by Budoc on 2015-07-21
> **mansonfan78 said:**
> Does it do the same thing when connected to usb?  If you haven't already try a direct usb connection and disable it's wifi connection.  This will at least help to narrow down the problem.

Yes, the problem occurs with a direct usb connection as well.

---

