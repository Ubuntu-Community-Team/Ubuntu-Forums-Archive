---
title: "Brother MFC 5490CN Printer installation"
date: 2012-05-06
forum: Hardware
---

### Post by SuperFreak on 2012-05-06
I am trying to install the drivers for my Brother MFC 5490CN printer using the directions at the Brother web site [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html") but when I try the commands     Command (for dpkg)  :  dpkg  -i  --force-all  (lpr-drivername) or "--force-architecture" I get an error message (see screenshots please). I had this working with Ubuntu 10.10 64 bit and I remember it was a real hassle but eventually it worked fine. Any help would be greatly appreciated as it is one of the last things I need working for my new computer with 12.04 64 bit.
It appears to be a problem with the VAR directory. Oh and I have already downloaded and installed ia32-libs

---

### Post by SuperFreak on 2012-05-06
Problem solved. It was just a matter of creating the lpd folder in the VAR/Spool directory

---

