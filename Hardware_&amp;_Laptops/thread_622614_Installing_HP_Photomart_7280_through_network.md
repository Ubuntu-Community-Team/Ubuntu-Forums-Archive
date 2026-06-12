---
title: "Installing HP Photomart 7280 through network"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by pauld100 on 2007-11-24
I recently purchased this printer and I have it installed on my Windows machine, but is there any way of installing it on gutsy through the network?

thanks
Paul

---

### Post by jmcvey on 2007-11-25
If it's the C7280 model, then HP's linux driver ([http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)) will support it and via a network connection. Ubuntu includes a version of HP's driver program in the repo's but you might need a later version depending on printer model. If that's the case, HP's site has Ubuntu specific versions you can download and install. Setting it up for network printing/access is pretty straight-forward. I had to do the same thing (download a later version) to have Ubuntu print to a HP Photosmart D7460 that I have.

Jer

---

### Post by Metaljaz on 2007-12-29
I got this same pinter for xmas and after reading the post and link left by jmcvey I was able to get my printer up and running. The printer is hooked to a vista box via ethernet cable but i am now able to sit in my den with my wireless ubuntu laptop and print to the printer in the office. Very easy to do following the directions posted by HP.

---

### Post by chernigov on 2008-03-17
Good to see someone else has the D7460 up and running wirelessly, as that is what I am trying to do as well.

The problem I am having is with install, and was wondering if anyone else had this issue. I am following the hplip install instructions carefully on their sourceforge site, but encountered this error after choosing the proper Ubuntu build (I have 7.10, and it detected 8.04; I tried both but encountered the same error):

DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes build-essential build-essential libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp-dev python-reportlab libsane-dev python-imaging libsane xsane'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ?

Choosing yes does not fix the problem as you can imagine. Anyone else have this issue/error?

---

