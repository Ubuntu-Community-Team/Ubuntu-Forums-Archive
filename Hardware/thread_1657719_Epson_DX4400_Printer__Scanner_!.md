---
title: "Epson DX4400 Printer / Scanner !"
date: 2011-01-01
forum: Hardware
---

### Post by Tom_T on 2011-01-01
Hi

My parents have an Epson DX4400 printer / scanner. I'm looking to install Ubuntu 10.10 on to their old PC.

I've tried the LiveCD and it's picked up all their hardware including the printer.

I didn't try printing, but that looks OK !!

I did try simplescan, but that errors with no device found.

I've read quite a few posts, but nothing definite.. Can anyone help me get this working so I can fully install Ubuntu for them !! 

Thanks

---

### Post by IcarusR on 2011-01-01
Download & install iscan which includes drivers from avasys here

[http://avasys.jp/eng/linux_driver/download/]("http://avasys.jp/eng/linux_driver/download/")

---

### Post by iceman30ad on 2011-01-01
install  x-sane and set up is no brainer 

i have a all in one from the same group and it works no problem though i do have to  re_pair ( reconnect/ or what ever else you want to call it takes 30 seconds to set back up) the conection  with the printer  every time i power cycle  either one while i have it connected wirelessly

---

### Post by IcarusR on 2011-01-02
iceman30ad
Epson DX4400 is not mentioned on the Sane supported devices [webpage]("http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-EPSON") so I suggested iscan.

OP says

> I did try simplescan, but that errors with no device found.


which would suggest no sane support as simplescan uses sane backends (drivers)

I still recommend iscan from avasys for this device, as they specifically list it as supported.

---

### Post by markosdel on 2011-10-27
hi!
I have the same printer.All I did was to connect the printer to my pc,switch it on and then follow the steps from the link below:
[http://www.eioba.com/a/1r8/printing-with-ubuntu](http://www.eioba.com/a/1r8/printing-with-ubuntu)

then go to a word office and you can print any page.

I haven't try scan yet.

---

