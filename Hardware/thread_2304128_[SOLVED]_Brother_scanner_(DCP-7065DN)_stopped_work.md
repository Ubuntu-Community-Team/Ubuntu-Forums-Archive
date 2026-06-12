---
title: "[SOLVED] Brother scanner (DCP-7065DN) stopped working after 15.10"
date: 2015-11-24
forum: Hardware
---

### Post by arlenn2 on 2015-11-24
Hello,

After upgrading to 15.10, my Brother scanner has stopped working.  Using previous posts' suggestions, I have removed and re registered the scanner, but no improvement.  No scanner is detected by simple scan, or Xsane.  

Anybody seen this?  Anybody have a work-around?

Thanks

---

### Post by gifford on 2015-11-24
Is the scanner/printer USB or networked?

---

### Post by arlenn2 on 2015-11-25
Yes, Network.  Sorry

---

### Post by rajasekar3 on 2015-11-25
dsafafa

---

### Post by gifford on 2015-11-25
From the terminal run this command:brsaneconfig4 -q
This will let you know if the scanner is assigned an IP address on your network and what the address is. Sometimes the address changes and while the printer will pick it up, the scanner requires it to be re registered. Make sure you have the correct IP of your printer, see what your router has it listed as. 
See this previous thread in the forum:[http://ubuntuforums.org/showthread.php?t=2222027&p=13013698#post13013698](http://ubuntuforums.org/showthread.php?t=2222027&p=13013698#post13013698)

What I do when this happens is go to usr/local/brother/sane and open file brsanenetdevice4.cfg and make the changes to the IP there.

---

### Post by arlenn2 on 2015-11-25
Actually, I have. 

I have removed the scanner brsane... -r <common name>, and recreated it -a .... 
I will check that file to see if the changes are actually getting written correctly.  I will also try purging and reinstalling the driver.

I have printer configured on a static IP, to keep it from inadvertently hopping IPs.

It was working just fine up to the point of my upgrade, and now doesn't recognise the presence of a scanner.  It still prints just fine, mind you.

Was a change made to firewalls or other security aspects in 15.10?

---

### Post by arlenn2 on 2015-11-25
Yup, a purge and reinstall of brsane4 got it.

Thanks for the help

---

