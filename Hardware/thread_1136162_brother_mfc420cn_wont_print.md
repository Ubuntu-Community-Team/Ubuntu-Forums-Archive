---
title: "brother mfc420cn wont print"
date: 2009-04-24
forum: Hardware
---

### Post by wirechief on 2009-04-24
I have install the printer driver according to the instructions on brothers
web page.
sudo apt-get install csh
make sure have to poweroff the printer at this point)
 mkdir /var/spool/lpd/MFC420CN
 ln -s /etc/init.d/cupsys /etc/init.d/cups
 sudo dpkg -i --force-architecture mfc420cnlpr-1.0.2-1.i386.deb
sudo dpkg -i --force-architecture cupswrapperMFC420CN-1.0.2-3.i386.deb

I have tried adding the printer using localhost:631 and browseing and using
the .ppd file, it seems to accept everything however fails to print. I also
tried using the System printer add printer, it again seemed to work but fails to print. attaching log from debugger. not sure but i saw one message
on the printer that the black ink was low, not sure this is the problem ...
Linux wirechief-laptop 2.6.30-020630rc2-generic #020630rc2 SMP Wed Apr 15 13:20:18 UTC 2009 x86_64 GNU/Linux

---

