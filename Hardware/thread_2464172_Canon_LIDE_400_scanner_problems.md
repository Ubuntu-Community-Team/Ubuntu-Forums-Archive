---
title: "Canon LIDE 400 scanner problems"
date: 2021-06-25
forum: Hardware
---

### Post by ian49 on 2021-06-25
Has anyone any experience with getting the Canon LIDE 400 scanner working under Ubuntu 16.04?

Having installed the driver, I can get the Canon scangearmp2 application to both detect the scanner and scan and save a document. But the software is incredibly basic and doesn't allow any parameters to be specified such as dpi etc. When I run either Simple Scan or XSane or VueScan all of them fail to detect the scanner. Any help in getting these applications to detect the scanner would be greatly appreciated.

---

### Post by brian_p on 2021-06-26
> **ian49 said:**
> Has anyone any experience with getting the Canon LIDE 400 scanner working under Ubuntu 16.04?

Having installed the driver, I can get the Canon scangearmp2 application to both detect the scanner and scan and save a document. But the software is incredibly basic and doesn't allow any parameters to be specified such as dpi etc. When I run either Simple Scan or XSane or VueScan all of them fail to detect the scanner. Any help in getting these applications to detect the scanner would be greatly appreciated.

Neither simple-scan nor xsane will ever work with what Canon provides:

[https://wiki.debian.org/Scanner#canon](https://wiki.debian.org/Scanner#canon)

ipp-usb with sane-airscan is the way forward but, unfortunately, not when Ubuntu 16.04 is used.

[https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan)

---

### Post by rbmorse on 2021-06-26
If you don't mind spending $40 or so, Hamrick Software's VueScan should do the trick.  You can try before you buy to ensure it works.  VueScan, btw, is just brilliant.  I've been using it for years and it's never let me down. 

[http://hamrick.com](http://hamrick.com)

---

### Post by kurt18947 on 2021-06-26
Second VueScan. When we bought it we bought the Standard Edition, it was around 2015 I think. After some years the Standard Edition would no longer work. I didn't pursue why that was the case, the scanner we needed to support became supported 'out of the box'.

---

### Post by ian49 on 2021-06-27
Thanks for the responses. Looks like I should have researched a bit more carefully before buying!

I do have a laptop running Ubuntu MATE 20.04 so maybe I could try using that instead. I did try installing the scanner on a virtual machine running Windows 7 on the Ubuntu 16.04 host. Installation completed successfully, ran the Canon IJ scan utility, tried to scan a photo... got a message saying 'warming up scanner' or words to that effect and then BOOM! the blue screen of death.

I did try VueScan and it failed to detect the scanner. :(

---

### Post by ian49 on 2021-06-27
Update: having edited /etc/sane.d/canon_dr.conf to add the LIDE 400 details, Vuescan now appears to be working, so now it's a case of deciding whether to shell out for the software or return the scanner for one more Ubuntu friendly. Decisions, decisions.

---

### Post by brian_p on 2021-06-27
> **ian49 said:**
> Thanks for the responses. Looks like I should have researched a bit more carefully before buying!

I do have a laptop running Ubuntu MATE 20.04 so maybe I could try using that instead. I did try installing the scanner on a virtual machine running Windows 7 on the Ubuntu 16.04 host. Installation completed successfully, ran the Canon IJ scan utility, tried to scan a photo... got a message saying 'warming up scanner' or words to that effect and then BOOM! the blue screen of death.

I did try VueScan and it failed to detect the scanner. :(

Good information. Ubuntu 20.04 is a much more viable proposition.

You need ipp-usb and sane airscan:

[https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan) (main page).
[https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/](https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/) (Debian packages).

Feedback would be appreciated.

---

### Post by ian49 on 2021-06-30
> **brian_p said:**
> Good information. Ubuntu 20.04 is a much more viable proposition.

You need ipp-usb and sane airscan:

[https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan) (main page).
[https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/](https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/) (Debian packages).

Feedback would be appreciated.

Reporting back, as requested, that scanner is working fine with XSane, having installed ipp-usb and sane airscan on the laptop.

---

### Post by brian_p on 2021-06-30
> **ian49 said:**
> Reporting back, as requested, that scanner is working fine with XSane, having installed ipp-usb and sane airscan on the laptop.

Thank you, ian49, for taking the time to test and report.

---

