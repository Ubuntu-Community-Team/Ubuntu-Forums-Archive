---
title: "Sane-genesys Visioneer 7100 scanner"
date: 2011-03-24
forum: Hardware
---

### Post by cinger on 2011-03-24
I am trying to see if ubuntu will work with a Visioneer 7100 scanner.  The SANE project lists the scanner driver backend for Visioneer 7100 as complete here [http://www.sane-project.org/sane-backends.html]("http://www.sane-project.org/sane-backends.html").  I am running ubuntu 10.04, kernel 2.6.32-25-generic, libusb1.0-0.  I have apt-get installed xsane frontend and downloaded sane-backend-1.0.22.  Following the backend README I did ./configure, make, make install, man sane.  I did sane-find-scanner and got: ```
found USB scanner (vendor=0x04a7, product=0x0229, chip=GL646?) at libusb:003:002

```  Which I believe to be the Visioneer scanner as 0x04a7 appears to be the Visioneer vendor number.  
I opened /etc/sane.d/genesys.conf and added ```
#Visioneer 7100
usb 0x04a7 0x0229
```  When I do scanimage -L I get ```
No scanners were identified. 
```
When I run xsane I get "no scanner found".

Any ideas on how to configure this scanner properly?

---

### Post by fjgaude on 2011-03-24
I got rid of my Visioneer scanner long ago, because I was told that there would never be a driver for it. So few in existence seems to be the issue.

---

### Post by desertdog on 2011-06-14
Cinger: see [https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)

Make sure you install the dependencies before you build from source. Also make sure you add the flags to the ./configure command.

---

