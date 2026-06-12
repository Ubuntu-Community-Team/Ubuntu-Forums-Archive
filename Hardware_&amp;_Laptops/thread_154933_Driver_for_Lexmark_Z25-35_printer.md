---
title: "Driver for Lexmark Z25-35 printer"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by Alan Wagner on 2006-04-04
Ubuntu correctly recognises my printer as a Z25-35 printer, but it does not have a suitable driver.  The driver I got from the Lexmark website (CJLZ35LE-CUPS-2.0-1.TAR.GZ) is not accepted by Ubuntu.  Can anyone point me to one that I CAN use?

---

### Post by Sef on 2006-04-04
From LinuxPrinting:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z23]("http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z23")

I hope this works.

> LEXMARK Z23 
Tom G.
t g l i n b o x @ h o t m a i l . c o m

Works great on Ubuntu and Xandros. This is how I was able to make it work.

Similar instructions for other printers at [http://ubuntuforums.org/archive/index.php/t-83456.html](http://ubuntuforums.org/archive/index.php/t-83456.html)


Modified HOWTO from [http://ubuntuforums.org/showthread.php?t-83456.html](http://ubuntuforums.org/showthread.php?t-83456.html).


Dependencies:
sudo apt-get install alien # rpm to deb converter
sudo apt-get install libstdc++5 # (need v5 for compatibility)

1. Download the driver from lexmark's site Z35 (CJLZ35LE-CUPS-2.0-1.TAR.GZ)

2. Run though the following commands

# A extract the driver.
    tar -xvzf CJLZ35LE-CUPS-2.0-1.TAR.GZ  

# B the sh script is broken for newer systems.
     tail -n +143 lexmarkz35-2.0-1.gz.sh > install.tar.gz 

# C extract the contents produced by tail
     tar -xvzf install.tar.gz 

# D & E convert unusable rpm packages to tgz
     sudo alien -t z35cups-2.0-1.i386.rpm 
     sudo alien -t z35llpddk-2.0-1.i386.rpm 

# F & G extract the tgz's to / putting the files in their right place
     sudo tar xvzf z35llpddk-2.0.tgz -C / 
     sudo tar xvzf z35cups-1.0.tgz -C / 

# H refresh ubuntu to see the new libraries
    sudo ldconfig 

# I change directories
    cd /usr/share/cups/model

# J unzip the ppd, which should _not_ be gzipped
    sudo gunzip Lexmark-Z35-lxz35cj-cups.ppd.gz 

# K The driver is now installed. Restart the cups daemon.
    sudo /etc/rc2.d/S19cupsys restart 

3. Now we run:
# A  (optional)
    /usr/lib/cups/backend/z35
   #You should be something like:
   #direct z35:/dev/usb/lp0 "Lexmark Lexmark Z35 Series" "Lexmark Printer"

4. Set up your printer using the new z35 driver. 
   In UBUNTU/GNOME  --   System->Administration->Printing)


---

### Post by Alan Wagner on 2006-04-04
Thanks Sef!  I will try this (with much intrepidation - I am an absolute beginner!).  
One question: re: "Dependencies:
sudo apt-get install alien # rpm to deb converter
sudo apt-get install libstdc++5 # (need v5 for compatibility)"

Does this mean I need to install other software?

---

