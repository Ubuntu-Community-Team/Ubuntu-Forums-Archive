---
title: "HPLIP Bug? Cannot scan with HP 3330 MFP."
date: 2011-02-01
forum: Hardware
---

### Post by Silhorn on 2011-02-01
Hello, 
(Complete beginner)

Over the past couple of days I have been trying to get scanning working with my HP 3330 MFP from USB connection.

I've tryed uninstaling hplip from ubuntu 10.10 and installing with the latest hplip 3.11.1.

What happends is when I go into XSane or simple scanner it gives me a I/O error after about 1 minute.

I've also tried using another Distro, Mandriva which is not as technical and I just point and click and it downloads and configures the latest everything for me.

It does the same thing with Mandriva.

hp-check gives no errors and scanimage-L gives no errors.

The scanner is recognized in mandrivas scanner window.

I've done a bit of searching and found this bug report:
[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/652963](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/652963)

Where it says to change the mfp io mode to 1 and the scan type to 7 but the only thing it does is make the I/O error come up quicker.

Does anyone know what I can do now?

---

