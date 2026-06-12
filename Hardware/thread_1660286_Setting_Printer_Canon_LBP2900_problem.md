---
title: "Setting Printer Canon LBP2900 problem"
date: 2011-01-05
forum: Hardware
---

### Post by green007 on 2011-01-05
Really sorry if the problem has been raised before but Im really novice and just understand simple english (not technical explaination). Before this i set this printer under Ubuntu 10.04 and its function very well. 
1. I download the driver CAPT_Printer Driver for Linux V200 from Canon.
2. I extract the file with this command from terminal:
> tar xvf CAPT_Printer_Driver_for_Linux_V200_uk_EN.tar.gz

3. Inside the package -> driver -> Debian got two files.cndrvcups-capt_2.00-2_i386.deb  cndrvcups-common_2.00-2_i386.deb


 
 4- When I tried to install with this command:

> sudo dpkg -i cndrvcups-common_2.00-2_i386.deb

I got this error message in terminal:
>     	 	 	 	p { margin-bottom: 0.08in; }  [COLOR=Red]sudo dpkg -i cndrvcups-common_2.00-2_i386.deb [/COLOR]
 [COLOR=Red](Reading database ... 145269 files and directories currently installed.) [/COLOR]
 [COLOR=Red]Preparing to replace cndrvcups-common 2.00-2 (using cndrvcups-common_2.00-2_i386.deb) ... [/COLOR]
 [COLOR=Red]Unpacking replacement cndrvcups-common ... [/COLOR]
 [COLOR=Red]dpkg: dependency problems prevent configuration of cndrvcups-common: [/COLOR]
 [COLOR=Red] cndrvcups-common depends on cupsys; however: [/COLOR]
 [COLOR=Red]  Package cupsys is not installed. [/COLOR]
 [COLOR=Red]dpkg: error processing cndrvcups-common (--install): [/COLOR]
 [COLOR=Red] dependency problems - leaving unconfigured [/COLOR]
 [COLOR=Red]Errors were encountered while processing: [/COLOR]
 [COLOR=Red] cndrvcups-common [/COLOR]
  

Anybody please help me in simple english and step by step.

---

### Post by green007 on 2011-01-05
According to another forum, the error because "...all of a sudden they decided to realign their printing system naming  conventions with the rest of the Linux community which broke the  original canon printer driver". So they suggest me to create / reproduce .deb from RPM files. So this is what I do:

1. download alien
> sudo apt-get install alien
2. Open RPM Driver

> 
sudo alien cndrvcups-common-2.00-2.i386.rpm
sudo alien cndrvcups-capt-2.00-2.i386.rpm


3. Run the .deb from rpm folder
> 
sudo dpkg -i cndrvcups-common_2.00-3_i386.deb
sudo dpkg -i cndrvcups-capt_2.00-3_i386.deb 


4. restart CUPS :

> sudo /etc/init.d/cups restart

5. Next
> /usr/sbin/lpadmin -p LBP2900 -m CNCUPS[COLOR=Red]LBP2900[/COLOR]CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
*[COLOR=Red]Your Printer Model[/COLOR]
6. Next
> /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0

7. Start ccpd :
> sudo /etc/init.d/ccpd start

8. Now Set ccpd to start when you startup your computer:
> sudo update-rc.d ccpd defaults 20 

9. Next
>  /etc/init.d/ccpd start

10. Check printer status
> captstatusui -P LBP2900

All the process running smooth but my till now the printer doesn't respond.

---

### Post by green007 on 2011-01-06
still problem after a few hours configure. when type:
> captstatusui -P LBP2900

I got this:
[[IMG]http://img717.imageshack.us/img717/5729/lbp1.png[/IMG]](http://img717.imageshack.us/i/lbp1.png/)

I try check the error --> "Check the [DevicePath]("https://help.ubuntu.com/community/DevicePath") of /etc/ccpd.conf" with this :
> lsmod | grep usblp
I receive output --> usblp
[[IMG]http://img508.imageshack.us/img508/6748/pr1r.png[/IMG]](http://img508.imageshack.us/i/pr1r.png/)

Now I dont know what to do! Anybody please help me.:confused:

---

### Post by green007 on 2011-01-23
Canon release V220, so all problem settle. Printer running smooth. Thanks:D

---

### Post by saintraphael on 2011-06-06
hi,i saw you have discovered  the right solution to set up yr printer LBP2900
i have the same one and research the simplest way to set it up
the automatic way doesn t work and it s too tricky for me to download files and drivers and extract them and create new directories ...
couls you send me yr solution with few explanations
tks for that nice day .sainraphael

---

