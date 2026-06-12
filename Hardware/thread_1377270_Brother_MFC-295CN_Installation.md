---
title: "Brother MFC-295CN Installation"
date: 2010-01-10
forum: Hardware
---

### Post by uzzo2 on 2010-01-10
Hey Guys, I posted this over in the general help section and haven't much success. So I thought I would try posting it over here to see if someone might know what was going on with this installation.
[http://ubuntuforums.org/showthread.php?t=1376055](http://ubuntuforums.org/showthread.php?t=1376055)

---

### Post by labinnsw on 2010-01-11
Not sure if this will work, but I am sure it won't hurt. Try re-installing the printer using the instructions attached and the appropriate drivers for your printer

[ATTACH]143272[/ATTACH]

---

### Post by SheamusPatt on 2010-07-30
Works for me. I had to go to the Brother site, though, and download the drivers from there. It seems that they aren't yet part of the brother packages in Ubuntu.

Here's basically what I did. First, download the two packages from Brother, at [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc295cnlpr-1.1.2-1.i386.deb&#9001;=English_lpr ]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc295cnlpr-1.1.2-1.i386.deb&lang=English_lpr")and [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc295cncupswrapper-1.1.2-2.i386.deb&#9001;=English_gpl]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc295cncupswrapper-1.1.2-2.i386.deb&lang=English_gpl") .

Now, install the packages via
[FONT=Lucida Console]sudo dpkg --force-architecture -i mfc295cncupswrapper-1.1.2-2.i386.deb mfc295cnlpr1.1.2-1.i386.deb [/FONT]

(I needed --force-architecture to install on AMD64 - if you're on an i386 install, you shouldn't need this).

After that, if you're connecting via USB, you should be good to go. If you're using the network option, though, go into CUPS administration ([http://localhost:631]("http://localhost:631/")) and go through the Add Printer dialog. That should detect your network connected MFC-295CN as long as it's configured and connected.

The scanner portion is also easy to set up. Just follow the instructions here [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html). After installing their package, you simply need to run one command to configure the scanner, and then XSane could see it. I was quite impressed that I could scan over the network so easily.

---

### Post by dwaindibbley on 2010-08-29
SheamusPatt You are the Maestro! Installing the printer worked for me with one minor change. It seems you have a typo in the second line, it should be
sudo dpkg --force-architecture -i mfc295cncupswrapper-1.1.2-2.i386.deb mfc295cnlpr[COLOR="Red"]-[/COLOR]1.1.2-1.i386.deb
Notice the missing hyphen

---

### Post by badman35 on 2010-09-28
I followed these instructs and i still can not get my 295cn to print. Can someone give me a hand with this..

---

### Post by uzzo2 on 2010-09-28
> **badman35 said:**
> I followed these instructs and i still can not get my 295cn to print. Can someone give me a hand with this..
If you've tried going to Brothers website and downloading the drivers there and it didn't work. Try turning off the power to the printer and unplugging the usb cable. Then plug it back in and power the printer up and see if it will detect it.

---

### Post by badman35 on 2010-10-20
> **uzzo2 said:**
> If you've tried going to Brothers website and downloading the drivers there and it didn't work. Try turning off the power to the printer and unplugging the usb cable. Then plug it back in and power the printer up and see if it will detect it.

Well i'm using it on a network.. I know that the network settings r right because win xp pc's on the network us the print fax and scan functions over the network..

---

### Post by uzzo2 on 2010-10-20
> **badman35 said:**
> Well i'm using it on a network.. I know that the network settings r right because win xp pc's on the network us the print fax and scan functions over the network..
Okay, it's printing from your xp machine via a router I'm assuming. How do you have it connected to your linux machine? I have pretty much the same setup, mine prints from my linux machine via USB and with the xp box via  wired router.

---

### Post by badman35 on 2010-10-27
well i want to use the network for my printing not the usb cable.. i also would like to be able to scan to/from it on the network...

---

### Post by badman35 on 2010-10-27
i got it to work on my network and here is what i did to get it to get it to work.

you will need to open terminal for all of the following code..
1. i did was ```
sudo -s
```
2. i already had all of the deb files downloaded to my downloads folder and made another folder named "brother-mfc-295cn" and i put them into that folder.
3. i did a ```
sudo aa-complain cupsd
```
4. then i did ```
sudo mkdir /usr/share/cups/model
```
5. then ```
sudo mkdir /var/spool/lpd
```
This part you have to "cd" to where the drivers are at before u do the rest this code.
6.then ```
sudo dpkg -i --force-all mfc295cnlpr-1.1.2-1.i386.deb
```
7. then```
sudo dpkg -i --force-all mfc295cncupswrapper-1.1.2-2.i386.deb
```
8. then ```
dpkg -l | grep Brother
```
after all that all i had to do was change the the device UDI: to "lpd://192.168.2.10/BRN001BA925C051"

and poof my printer works......!!!!!!!

now on to the scanner

here is what i did....
1. i installed the driver with gdebi in the GUI on my desktop...
2. ```
brsaneconfig3 -a name=brother model=MFC-295CN ip=192.168.2.10
```
3. ```
brsaneconfig3 -q | grep brother
```



And poof got the scanner working and it works great....!!!



Now to get the PCFAX to work.

```
# NOTE:
This FAQ is verified using Ubuntu 10.04 Beta2.
Operation may differ in the formal release of Ubuntu 10.04.


   1. Install openjdk-6-jre from Synaptic Package Manager.

   2. Create /usr/share/cups/model, if it does not exist.

      Command: sudo mkdir /usr/share/cups/model


   3. Install the drivers.

      Command: sudo dpkg -i -force-all brmfcfaxlpd-1.0.0-1.i386.deb
      Command: sudo dpkg -i -force-all brmfcfaxcups-1.0.0-1.i386.deb


   4. Change the access permission of /usr/lib/cups/filter/brfaxfilter

      Command: sudo chmod 755 /usr/lib/cups/filter/brfaxfilter



```

 And YES it works. Now that my brother MFC-295cn now works on Ubuntu Lucid....

---

### Post by mwray on 2011-03-01
How do I get the FAX part to work on my NETWORK attached brother.

Have scanning and Printing working, have the brfax driver installed, pointing to the same udf as the brother printer. No complaints from cups on the complain thingy. How does one actually get a fax to the fascimile and get it to dial/send the fax? I have not found any documentation on this. (I keep getting the same info posted here for printing/scanning.) 

:confused:

---

### Post by uzzo2 on 2011-03-01
> **mwray said:**
> How do I get the FAX part to work on my NETWORK attached brother.

Have scanning and Printing working, have the brfax driver installed, pointing to the same udf as the brother printer. No complaints from cups on the complain thingy. How does one actually get a fax to the fascimile and get it to dial/send the fax? I have not found any documentation on this. (I keep getting the same info posted here for printing/scanning.) 

:confused:
I had this problem with mine, but when I fax I do it straight from the machine. I called brother and they ran me through a series of tests including unplugging my DSL modem and then plugging the wire from the machine into the jack. That was the problem, I installed a filter on the line to the fax machine and haven't had any trouble since then, hope this helps.

---

### Post by mwray on 2011-03-01
> **uzzo2 said:**
> I had this problem with mine, but when I fax I do it straight from the machine. I called brother and they ran me through a series of tests including unplugging my DSL modem and then plugging the wire from the machine into the jack. That was the problem, I installed a filter on the line to the fax machine and haven't had any trouble since then, hope this helps.

Nope, not what I am looking for. As I said before I need a step by step guide on how to make use of BRFax when printing to a network attached MFC295CN. I have successfully faxed from Windows and OSX multipage documents. How to accomplish this in ubuntu? (Or any flavour of linux). I just sent a 17 page fax last night from OSX. so it's definitely not related to "line filters" especially since I don't have DSL. 

Just don't know how to make use of the brfax driver as printing to the "BRFAX" does absolutely nothing. Cups complain doesn't return anything, so I know filters are setup correctly, that and I verified by my own eyes the settings on permissions on those files as well. (Sometimes cups-complain misses stuff)

On Windows I just print to the Bother-Fax printer.
On Mac OSX, I print to the regular printer, and under options select Fascimile in 2 places. What do I need to do to make use of the brfax on Linux?
](*,)

---

### Post by uzzo2 on 2011-03-02
> **mwray said:**
> Nope, not what I am looking for. As I said before I need a step by step guide on how to make use of BRFax when printing to a network attached MFC295CN. I have successfully faxed from Windows and OSX multipage documents. How to accomplish this in ubuntu? (Or any flavour of linux). I just sent a 17 page fax last night from OSX. so it's definitely not related to "line filters" especially since I don't have DSL. 

Just don't know how to make use of the brfax driver as printing to the "BRFAX" does absolutely nothing. Cups complain doesn't return anything, so I know filters are setup correctly, that and I verified by my own eyes the settings on permissions on those files as well. (Sometimes cups-complain misses stuff)

On Windows I just print to the Bother-Fax printer.
On Mac OSX, I print to the regular printer, and under options select Fascimile in 2 places. What do I need to do to make use of the brfax on Linux?
](*,)

I can't help you then, I don't have any problems with mine. I would suggest you contact Brother directly. They used to have a dedicated Linux tech support staff. You had to contact them via email. I visited the website and don't see the option for contacting the Linux support folks anymore. I would just start here and maybe someone can get you to the right person.

[http://www.brother-usa.com/Support/Default.aspx](http://www.brother-usa.com/Support/Default.aspx)

---

### Post by mwray on 2011-03-02
Thanks..found the FAQ on it at brother's website. Now however, I want to create a passthrough printer so we can "print" to fax. Started a new thread on this else where. 

There's a program called brpcfax that can be used to send a fax. There are several documents on google on how to add it as a "document" handler for things like konqueror...which would be fine if I used KDE..so now I['m trying to find a way to plug it into CUPS.

---

### Post by mazingaz01 on 2011-06-21
I have installed 11.04 32bit and after following the installation method indicated this thread.  I am unable to open Localhost/631.  and my printer prints blank when i select grey instead of color.

How can i uninstall CUPS and driver all together and start fresh installation of CUPwrapper and the driver?

---

### Post by sonicladybug on 2012-03-06
I have a Brother MFC-295cn copier/printer/scanner/fax.


 I have downloaded the drivers for the printer and the scanner.


 I am able to print, BUT NOT scan. XSane does NOT recognize the scanner.


I'm showing the following information in the terminal:


dpkg  -l  |  grep  Brother
[sudo] password for (information intentionally removed)
ii  brscan-skey                           0.2.1-3                                    Brother Linux scanner S-KEY tool
ii  brscan3                               0.2.11-4                                   Brother Scanner Driver
ii  mfc295cncupswrapper                   1.1.3-1                                    Brother CUPS Inkjet Printer Definitions
ii  mfc295cnlpr                           1.1.3-1                                    Brother lpr Inkjet Printer Definitions




 I do NOT know how to print from root.


 It is a LAN NETWORK printer attached to a TP-Link TL-R860 router attached to a broadband cable router. NO firewall.


 I need my scanner. Can anyone help?


 I use Ubuntu 11.04 AND I am like a  newborn babe when trying to understand how the operating system works.  Very frustrating to say the least.

---

### Post by uzzo2 on 2012-03-06
> **sonicladybug said:**
> I have a Brother MFC-295cn copier/printer/scanner/fax.


 I have downloaded the drivers for the printer and the scanner.


 I am able to print, BUT NOT scan. XSane does NOT recognize the scanner.


I'm showing the following information in the terminal:


dpkg  -l  |  grep  Brother
[sudo] password for (information intentionally removed)
ii  brscan-skey                           0.2.1-3                                    Brother Linux scanner S-KEY tool
ii  brscan3                               0.2.11-4                                   Brother Scanner Driver
ii  mfc295cncupswrapper                   1.1.3-1                                    Brother CUPS Inkjet Printer Definitions
ii  mfc295cnlpr                           1.1.3-1                                    Brother lpr Inkjet Printer Definitions




 I do NOT know how to print from root.


 It is a LAN NETWORK printer attached to a TP-Link TL-R860 router attached to a broadband cable router. NO firewall.


 I need my scanner. Can anyone help?


 I use Ubuntu 11.04 AND I am like a  newborn babe when trying to understand how the operating system works.  Very frustrating to say the least.

open up a terminal and type ```
sudo gedit
```
then follow these instructions:

Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 

That should get you going, hope it helps.

---

### Post by G4-Reborn on 2013-03-03
I'm using Ubuntu 12, I followed the instructions on the Brother website, but to no avail. I  can see the status of my printer in my web browser. I can see a list of  jobs that have been sent to it. But nothing prints, although the print  queue will list print jobs as complete. Any suggestions about how I can  correct this?

---

### Post by uzzo2 on 2013-03-03
> **G4-Reborn said:**
> I'm using Ubuntu 12, I followed the instructions on the Brother website, but to no avail. I  can see the status of my printer in my web browser. I can see a list of  jobs that have been sent to it. But nothing prints, although the print  queue will list print jobs as complete. Any suggestions about how I can  correct this?

I wish I could help you, but I had to downgrade to 10.04 to get everything working properly. The very same bug that I reported with 11.10 is still unresolved as far as I know. I've actually swapped printers a good while back since the print head went out in my Brother. I went to an epson and it seems to do a great job, even with Linux.

---

### Post by G4-Reborn on 2013-03-11
I got it working. I went back and re-did the preliminary steps that Brother prescribes.

---

