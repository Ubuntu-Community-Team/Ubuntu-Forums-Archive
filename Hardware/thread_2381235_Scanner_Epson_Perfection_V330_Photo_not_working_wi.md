---
title: "Scanner Epson Perfection V330 Photo not working with Ubuntu 17.10"
date: 2017-12-28
forum: Hardware
---

### Post by Val42 on 2017-12-28
I had been on Ubuntu 16.04 LTS because my graphics card was apparently only supported under LTS versions.  I upgraded my computer (and graphics card) during the summer.  Last Saturday (23 December) I finally upgraded from the LTS 16.04 to 17.10.  I can no longer access my V330 scanner.  I have tried [https://ubuntuforums.org/showthread.php?t=2352664&highlight=v330](https://ubuntuforums.org/showthread.php?t=2352664&highlight=v330) and several other threads where people got their V330 working with Ubuntu.  However, after trying all of these things I still get, "Could not send command to scanner.  Check the scanner's status."

I have verified that the scanner is powered on.  The USB cable also works because it is the one that I used with this scanner before the upgrade, and I used it earlier today with another scanner (that is lower resolution) using XSane.  sane-find-scanner also finds it with the result of "found USB scanner (vendor=0x04b8 [EPSON], product=0x0142 [EPSON Perfection V33/V330]) at libusb:003:004".

I'm out of ideas.  Does anyone have any other suggestions?

Thanks!

---

### Post by rbmorse on 2017-12-28
17.10 broke some dependencies for the Epson proprietary driver and support files required for your scanner, and I was not successful in getting mine to work by copying the files over from an older repository.  

I have been told, but have not tried this myself, that one can download the Epson image-scan package, the extras package and the model specific driver package from Epson's Linux support site, extract the executables and install them using dpkg with the "force" parameter and the files will install and the scanner will be recognized by 17.10.  As I said I haven't tried this myself and can't vouch for it, but I don't see any reason it wouldn't work.  I also don't know if forcing the installation of those packages would break something else. Possible something critical to 17.10.   

In the end, and in recognition of the reality that at some point my time really is money, I replaced my Perfection 4490 Photo with a $79.00 Cannon CanoScan LiDE 220 that is plug 'n play with Ubuntu 17.10 so long as one remembers to install the libsane-extras package.  The Canon is much faster than the Epson, as well, but lacks the attachments for copying slides and photo prints.  Works a treat with VueScan as the front-end package.

---

### Post by kurt18947 on 2017-12-29
Not strictly relevant but 17.10 doesn't like Brother MFC-6490CW or Samsung MFD scanners either. I assume there's something changed in Sane or other package common to many scanners. Vuescan does work in both cases.

---

### Post by him610 on 2017-12-30
>  upgraded from the LTS 16.04 to 17.10
> Does anyone have any other suggestions?
If scanner doesn't work using 17.10,
if you need scanner to be operational,
suggest you revert back to Long Term Support (LTS) 16.04

---

