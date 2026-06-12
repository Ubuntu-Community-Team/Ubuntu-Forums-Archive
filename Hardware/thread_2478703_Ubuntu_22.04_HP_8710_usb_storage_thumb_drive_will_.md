---
title: "Ubuntu 22.04 HP 8710 usb storage thumb drive will not mount"
date: 2022-09-02
forum: Hardware
---

### Post by wahchek on 2022-09-02
After upgrading to 22.04 the usb drive in HP 8710 printer will not mount.
reinstalling 20.04 it works just fine.
20.04 automatically set up the printer and everything works.
In 22.04 there isn't any useful information in dmesg, lsblk, lsusb, fdisk -l, 
The printer sets up automatically and everything works. except ubuntu does not recognize the printer's thumb drive.

---

### Post by TheFu on 2022-09-04
Hp released new  software for 22.04 sometime in June.  Try that.

---

### Post by wahchek on 2022-09-06
Using the latest HPlip release , the printer works fine, but still does not mount the printer's usb drive. I re-installed 20.04 and all printer functions work  including the mounting of the printer's usb drive. 
My computer is a System76 Gazelle with 64 gig/RAM, 3 terabyte SSD storage.
Manufacturer has not found a solution and has suggested that the issue is in the Linux Kernel but with no errors in the logs they can't troubleshoot.
I have been using Linux since 1993 and this one has me stumped.

---

### Post by wahchek on 2022-09-06
I finally found a roundabout solution to the printer usb drive       not mounting on 22.04.
     I had to remove "ipp-usb". ( "ipp-usb" prevents "hplip" from       proper printer and scanner communication)
     Then Install, "hplip" 
    
     Then install a scanner package "simple scan"
     The above still does not let the printer USB drive mount, but it       allows the scanner software to scan to a folder in "home".
     The scanner package negates the need for the printer's usb drive.
     I also found a solution for the SNAP version of Firefox not       properly playing news videos on CNN.
     This version of Firefox, (apt-repository       ppa:ubuntu-mozilla-security/ppa) is faster than the SNAP version       and enables proper video streaming especially on CNN.

---

