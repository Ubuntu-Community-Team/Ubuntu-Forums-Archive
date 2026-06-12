---
title: "trying to install m printer with ubuntuforums guide but doesnt success"
date: 2008-06-29
forum: Hardware
---

### Post by dinbrca on 2008-06-29
the guide:
[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

I have downloaded the driver from lexmark website and i have made a little terminal execute file for the guide:
```

sudo apt-get install alien # convert and install rpm packages
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
tar -xvzf install.tar.gz # extract the contents produced by tail
alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
/etc/rc2.d/S19cupsys restart # the driver is now installed. Restart the cups daemom
# Check whether the printer backend works
##The output should be similar to: direct z600:/dev/usb/lp0 "Lexmark Lexmark Z600 Series" "Lexmark Printer"
cd /usr/lib/cups/backend
./z600

```
but when the file gets to the command:
/etc/rc2.d/S19cupsys restart
it says:
bash: /etc/rc2.d/S19cupsys: No such file or directory
what should i do?

---

