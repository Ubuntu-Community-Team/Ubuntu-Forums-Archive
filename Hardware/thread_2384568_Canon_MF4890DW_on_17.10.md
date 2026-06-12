---
title: "Canon MF4890DW on 17.10"
date: 2018-02-08
forum: Hardware
---

### Post by Bachstudies on 2018-02-08
Hi,

Is anyone successfully printing to a Canon MF4800 series in 17.10? I have installed the official drivers (v.3.4) from the Canon site and double-checked that the i386 dependencies are met. The only thing that raises a red flag is when running the install.sh it gives the following messages in red:

#----------------------------------------------------#
# Install Package Check
#----------------------------------------------------#
 Replace: libbeecrypt7:i386 -> libgcrypt20:i386

and

#----------------------------------------------------#
# Install Package Check
#----------------------------------------------------#
 Replace: libbeecrypt-dev:i386 -> libgcrypt20-dev:i386

However, later in the install process it *does* state that libgcrypt20:i386 is present and the installation completes. I can see the printer and it automatically finds the MF4800 series drivers but any printing hangs on "processing".

Thanks for any help!

---

### Post by User-007 on 2018-02-08
Same problem with another i-Sensys model. I got it working by installing older (3.10) version. There was some dependency problem (i dont recall what was that), but downloaded and installed the missing package from internet manually (from older ubuntu version repos) and after that everything was fine.

---

### Post by pdc on 2018-02-09
thanks very much for this, user007. Just to clarify, your signin says you are using 14.04 ...... so you used an older version of the Canon driver with 14.04; is that correct?

so the MF4890DW uses the 3.4 UFR [http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html) that comes down as linux-UFRII-drv-v340-uken.tar.gz

that was a 9th Nov release; so probably supporting 17.04 

you say you used an older version ....... was that the 3.1 version you used please?

a lot of the newer Canon MF devices are airprint-compatible; and from 17.04 Ubuntu, there has been airprint support; but the MF-4890 is sadly not compatible; it is often worth waiting updating if one is using drivers from the manufacturer

---

### Post by User-007 on 2018-02-10
Sorry, my signin info is outdated. 17.10 was the Ubuntu version I used. As I said, only UFRII 3.1 seemed to work. 

Which makes this little weird is the truth that I managed to get the UFRII 3.4 version working on Mint 18.3 (based on Ubuntu 16.04.03).

---

### Post by pdc on 2018-02-10
thanks; 

....... I don't think it is weird that 3.4 works well with 16.04; (Mint 18) .......... in the readme that Canon provide, for the 3.4 version; they warrant that it is good up to 16.10/17.04;

they do provide very good and very detailed advice; there is just lots of detail; the problem for us all; (me very much included!!) ..... is to patiently work our way through it ...... eg they talk of the bi-directional printing connections and those that use that need 

```
sudo /usr/sbin/lpadmin -p [printer name to be registered] -P [PPD file path] -v cnusb:/dev/usb/lp0 -E
``` ..........but one sort of hopes their install script would be able to cope with that; as the install script issues the registration command ........

---

