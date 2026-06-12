---
title: "Canon Imageclass D420 Only Prints Test Pages"
date: 2015-04-12
forum: Hardware
---

### Post by webusr1 on 2015-04-12
All,
I had this same Canon Imageclass D420 printing great under Ubuntu 10.04 Server, but migrated to Lubuntu 14.04 64Bit. However, after connecting this printer on the new Lubuntu 14.04 64bit/OS the printer does not work. I download the printer drivers from Canon website (Linux_UFRII_PrinterDriver_V290_us_EN), and installed with no problems.

Installed the following 64bit drivers:
- cndrvcups-common_2.90-1_amd64.deb
- cndrvcups-ufr2-us_2.90-1_amd64.deb

I added the Canon -D400-450-(IFR11-LT) to the config printer software, and I am able to successfully print a Test Page;however, I'm unable to print and documents, pdf files, or website content from the Firefox broswer. Only Test Page prints work. I've tried several different settings in the Printer Options of the printer properties.

Tried uninstalling and resintalling, canon drivers, cups, and resetting cups (sudo /etc/init.d/cups restart).

Also, tried installing with CUPS on browser as follows: [https://wiki.debian.org/PrinterDriver/Canon/UFR-II](https://wiki.debian.org/PrinterDriver/Canon/UFR-II)

Any help would be greatly appreciated.

Best Regards!

---

### Post by pdc on 2015-04-12
Inside the UFR package you downloaded; is a readme file; various distros need extra files installed; if one chooses to go the 64bit way; 

for ubuntu, Canon say

```
sudo apt-get install libxml2:i386 libjpeg62:i386 libstdc++6:i386
```

__________________

it worked here [http://ubuntuforums.org/showthread.php?t=2265278&highlight=Canon+UFR+64bit+libxml2%3Ai386](http://ubuntuforums.org/showthread.php?t=2265278&highlight=Canon+UFR+64bit+libxml2%3Ai386)

---

### Post by webusr1 on 2015-04-12
Thanks for the quick reply, but no joy... It looks like a few of these files already installed (See below).... I installed libjpeg62.

$ sudo apt-get install libxml2:i386 libjpeg62:i386 libstdc++6:i386
[sudo] password for etcmon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstdc++6:i386 is already the newest version.
libstdc++6:i386 set to manually installed.
libxml2:i386 is already the newest version.

Installation of libjpeg62
Reading state information... Done
libjpeg62:i386 is already the newest version.
libstdc++6:i386 is already the newest version.
libxml2:i386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by webusr1 on 2015-04-12
Looks it's working NOW!!! YEA!!!

I don't understand why it took several minutes to start working. It seems that "libjpeg62:i386" installation made it work. 

Thanks so much!!! I've labored over this problem for about 8 hours, and it sure is nice to  have it fixed.

Best Regards!

---

### Post by pdc on 2015-04-12
glad to hear it is working

perhaps I should have recommended a restart of cups after the extra libraries were installed ```
sudo service cups restart
```       

(the old-fashioned "reboot" also should work .........)

---

