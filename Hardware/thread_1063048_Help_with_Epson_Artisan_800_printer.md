---
title: "Help with Epson Artisan 800 printer"
date: 2009-02-07
forum: Hardware
---

### Post by doughnutz on 2009-02-07
I'm new to the Linux and Ubuntu environments. I have found a lot of information here that has helped me get things going. However, I am still having issues getting my Epson Artisan 800 printer working.

The printer is setup as a wired network printer plugged directly into my router. I have tried downloading and installing the following drivers from [http://linuxprinting.org]("http://linuxprinting.org"):

[http://openprinting.org/download/printdriver/debian/dists/lsb3.1/main/binary-i386/gutenprint_5.0.1-1lsb3.1_i386.deb]("http://openprinting.org/download/printdriver/debian/dists/lsb3.1/main/binary-i386/gutenprint_5.0.1-1lsb3.1_i386.deb")

[http://openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-i386/openprinting-gutenprint_5.2.2-1lsb3.2_i386.deb]("http://openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-i386/openprinting-gutenprint_5.2.2-1lsb3.2_i386.deb")

But I have not had any luck. I have also downloaded the gutenprint 5.2.3, but I have not been able to figure out how to compile and install it successfully. If anybody could explain, in simple instructions, on how to compile and install the gutenprint 5.2.3, I will give that a try next.

Also, if you have any other suggestions please let me know.

---

### Post by cariboo on 2009-02-07
Can you ping the printer? 

The Gutenprint driver is installed by default, so you don't need to install it.

---

### Post by doughnutz on 2009-02-07
Yes I can ping the printer. When I add the printer it even shows up as a networked printer. I just cannot get the drivers to show up. I have tried a couple of other Epson drivers, but they do not seem to work correctly with this printer. Either they print blank pages or just keep form feeding paper.

---

### Post by unused_bagels on 2009-02-09
you go to system>administration>printing>new or something like that, that's how I added my artisan 800.
I want to know how I can get the kind of functionality it offers windoze users, it's driving me up the wall!  I can't get anything to make it scan, not iScan, or XSane

---

### Post by jupitershane on 2009-02-09
yes..system>administration>printing>add new should work
[http://www.google.com/cse?cx=015370965154551446593%3Ac-6heqrjwqg&ie=UTF-8&q=install+Epson+Artisan+800+printer+&sa=Search]("http://www.google.com/cse?cx=015370965154551446593%3Ac-6heqrjwqg&ie=UTF-8&q=install+Epson+Artisan+800+printer+&sa=Search")

---

### Post by unused_bagels on 2009-02-09
yeah shane, but my big problem is getting it to scan.

---

### Post by doughnutz on 2009-02-10
I gave up and went back to Windows. I have to have a functioning printer/scanner for business.

---

### Post by unused_bagels on 2009-02-10
I hate to say it, but donutz has a point.  I'm really getting tired of all my hardware not "just work"ing like everybody says it does.

---

### Post by scott_selberg on 2009-02-15
I have printing working with Intrepid Ibex (Ubuntu 8.10).  I suspect by my solution that it will work out of the box in the next release.

My solution was to download the following packages from the Januty release:
[cups-driver-gutenprint_5.2.3-0ubuntu1_i386.deb]("https://launchpad.net/ubuntu/jaunty/i386/cups-driver-gutenprint/5.2.3-0ubuntu1")
[libgutenprint2_5.2.3-0ubuntu1_i386.deb]("https://launchpad.net/ubuntu/jaunty/i386/libgutenprint2/5.2.3-0ubuntu1")

I then installed them manually:

```

sudo dpkg --install libgutenprint2_5.2.3-0ubuntu1_i386.deb
sudo dpkg --install cups-driver-gutenprint_5.2.3-0ubuntu1_i386.deb

``` 

I could then add a printer with the Artisan 800 driver without problems!

---

### Post by unused_bagels on 2009-02-15
thanks! I'll try it tonight.

---

### Post by unused_bagels on 2009-02-16
ack! I installed the new packages (had to search for exact same packages in amd64) and now it won't find my printer.  How can I set it up to be a scanner, as well? ;-;

---

### Post by blegs38552 on 2010-05-03
> **unused_bagels said:**
> ack! I installed the new packages (had to search for exact same packages in amd64) and now it won't find my printer.  How can I set it up to be a scanner, as well? ;-;
I have an Artisan 810 installed and have the same problem on 10.4. Prints fine (natively, only had to add the printer), but will not scan. 

This is one reason why I maintain a dual boot setup with Windows 7. Ubuntu is great for some things (web browsing, email), but it is not ready for prime time mission critical applications yet. I still do my financial record keeping (Quicken), tax preparation, synching with my Zune HD media player, photo editing and printing (Photoshop Elements for RAW capability)...etc. in Windows. To that, I can now add scanning. Strange, I was able to scan with my previous HP All-In-One in 9.04, which just goes along with my "not ready for prime time" statement.

---

