---
title: "Trouble with MFC-210c Printer on i386"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by rbarth on 2005-04-12
I am new at using Linux, but Ubuntu 5.0.4 has configured everything just fine with the exception of my Brothers MFC-210c Printer. Using the "Add Printer" which was able to identify my printer correctly, but did not offer the correct driver, and the mfc210c is not offered as a choice. Instead it selected the mfc-6550mc, which I tried but when you open "jobs" as well as "print test page" everthing appears to be working, but nothing happens. 

 This is a usb printer connected directly to the computer. When I tried the "lsusb -v" the Brothers printer was reconized and located on usb #4.

 Went to the Brothers site and downloaded there Linux files for Debian.
     > mfc210clpr-1.0.0-1.i386.deb
     > cupswrappermfc210c_1.0.0-1_i386.deb

  By using the "dpkg -i --force-overwrite mfc210clpr-1.0.0-1.i386.deb" I was able to install the LPR driver.

  When I tried to install "dpkg -i --force-overwrite cupswrappermfc210c_1.0.0-1.i386.deb" I recieved the message "Error: csh is required."

  I do not know what this message is trying to tell me, but I'm guessing that it has to do with the "c++ compiler." I would do an "apt-get install build-essential", but this also didn't help.

  The Brothers web site stated that for Debian users that the files "libstdc++2.10-glibc2.2" would be required and I was able to apt-get install with out any problems. The second file needed was "libqt3c102" which one cannot apt-get. A little research on the Ubuntu site stated that I should use the "libqt3c102-mt" file instead, this also cannot be gotten through apt-get. I tried some other variations that I had Goggled as a replacement for this file but had no luck. 

  Apparently both files are needed, and have to be linked. When I run the "brprintconfij2 -P mfc210c" command it tells me that it cannot find the linked file.

  If anyone can tell what the new version of "libqt3c102" is I would appreciate it. I'm also open to any suggestions that may be used as a work arround. 

  This is the first Linux disto that my wife has been willing to use, which says alot, but if I cannot get this printer to work I'm going to be forced to go back to Windows inorder for her to work at home.

Any help at all will be greatly appreciated.

Bob

---

### Post by pshanksta on 2005-06-03
Sorry I cant offer any help, I just wanted to say im in the exact same position as you wth this printer. I dont wanna go back to windows either!

Someone Help us.... please!

---

### Post by David Haas on 2005-06-03
The information at this site <http://www.linuxprinting.org/vendors.html> isn't encouraging for your efforts to get the printer function of your Brother multifunction injet working in Ubuntu. Fortunately, printer prices continue to decline. I wish I could be more helpful. Perhaps another forum member will be able to give good advice.
Good luck,
David

---

### Post by pshanksta on 2005-06-05
Ok I have a solution, My mfc-210c now prints perfectly.

First you need to install KDE using Synaptic.
Once thats installed goto the control center and go peripherials/printers.
If you printer isn't there add it, if it is click on it then hit the properties tab.

change the 'print system currently used:' to General Unix LPD print system.

Thats it.

Worked fine for me.

Good luck!

---

### Post by lignito on 2005-12-12
I had the same problem that you've had, and I resolved the problem by just downloding the "csh" program ,and it should be working right away my friend.I did for me.Did you manner to get the printer working? How did you do it?:)

---

### Post by BobSongs on 2005-12-16
Check out [the tutorial]("http://www.ubuntuforums.org/showthread.php?t=105703") on installing the Brother MFC210C in Ubuntu. The instructions are based on the Breezy Badger, but should install on just about any version of Ubuntu. :D 

For future reference for those browsing this thread.

Bob

---

