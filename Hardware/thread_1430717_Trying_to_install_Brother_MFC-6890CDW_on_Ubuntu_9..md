---
title: "Trying to install Brother MFC-6890CDW on Ubuntu 9.10"
date: 2010-03-15
forum: Hardware
---

### Post by oilitright on 2010-03-15
Ubuntu detects the printer but does not have a driver.  When I go to the Brother site 
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-6890CDW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-6890CDW)
and try to install the deb drivers shown below I get an error about incorrect architecture i386

I am fairly new to Ubuntu and haven't quite figured this out.  My cpu is an I7 proccessor is that the architecture it is talking about?

It will be a bummer if I have to go back to windose to print

**MFC-6890CDW**  DownloadFormatVersionSizeRelease Date  [LPR driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc6890cdwlpr-1.1.2-4.i386.rpm&lang=English_lpr") rpm 1.1.2-4 2539 KB 2009.May.25   [cupswrapper driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc6890cdwcupswrapper-1.1.2-4.i386.rpm&lang=English_gpl") rpm 1.1.2-4 16 KB 2009.May.25   [LPR driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc6890cdwlpr-1.1.2-4.i386.deb&lang=English_lpr") deb 1.1.2-4 2538 KB 2009.May.25   [cupswrapper driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc6890cdwcupswrapper-1.1.2-4.i386.deb&lang=English_gpl") deb 1.1.2-4 15 KB 2009.May.25   Install Instruction : [lpr driver]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html") | [cupswrapper driver]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html") | 

 [Page Top]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#top")

---

### Post by bastiegast on 2010-11-07
Wow, no one asnwered this?

I found this thread when looking for a solution myself. In the end I found out on my own how to do it and it's super easy. Just install the packages from the brother site using ```
dpkg -i --force-architecture mfc6890cdw*
``` For me the installation hung on starting the cups service but the driver was installed anyway.

After that you can just use ubuntu's printer add method and it will find the driver automatically.

---

