---
title: "CANON iR1022F, Ubuntu 14.04 recognized but won't print"
date: 2014-09-20
forum: Hardware
---

### Post by tjelka on 2014-09-20
Hello!

This is my first post. I'm searching for this specific problem on this forum, did't find answer so I made new post.

My problem is Canon iR1022F. Bought used. I tested it in Win XP and fully works with drivers for Windows. 

I'm install and tested in Ubuntu [http://software.canon-europe.com/products/0010348.asp](http://software.canon-europe.com/products/0010348.asp) all Linux drivers from this site.

 The last I tried to install Canon Printer Driver Common Modules Ver.2.90. from that site. Recognized but not working. When choose Forward, on selected printer finded in New Printer dialog, after Apply and Print test page nothing happens. Printer is turned on and everithing looks fine but won't print.

I need help. What screenshots and log files to attach how someone could help. Thank you!

---

### Post by pdc on 2014-09-20
welcome to the Ubuntu forums;

so this device uses the ubiquituous Canon UFR driver; 

that has two components: the common package ([COLOR="#0000CD"]cndrvcups-common_2.90-1_amd64.deb[/COLOR]) and a second package ([COLOR="#0000CD"]cndrvcups-ufr2-uk_2.90-1_amd64.deb[/COLOR])     (if using 64bit ubuntu)

________________________________________

Canon supply both Debian and RPM packages; in both 32bit and 64bit variants;

Canon say: install the common package first and then the second package;

_______________________________________

after that, one needs to  **[COLOR="#B22222"]Register the printer (PPD) with the print spooler[/COLOR]** and one needs to know which ppd to tell the print spooler to use: reading the readme that Canon supply with the UFR, you need [COLOR="#EE82EE"]CNCUPSIR1023ZK.ppd[/COLOR]

so the format is > [COLOR="#0000CD"]sudo /usr/sbin/lpadmin -p [Printer Name] -m [PPD file] -v usb:[device file location] -[/COLOR]E

so the command looks something like > sudo /usr/sbin/lpadmin -p iR1022F -m CNCUPSIR1023ZK.ppd -v cnusb:lp0 -E

.......if you have only one printer; the iR1022F and it is connected by usb cable .......................

___________________________
___________________________

1) so if we check what you have installed with the command > [COLOR="#FF0000"]dpkg -l | grep cndrvcups[/COLOR] that you should copy and paste into a terminal; and paste back here;

2) is your system 32bit?

3) check how your system sees your printer (if USB) with > [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR]

____________________________

this 2.9 version of the UFR driver was issued 3rd July 2014; and they say it works on 32bit and 64bit ubuntu 13.10; it would be great if it did work

Canon do say you need to install extra packages if you have a 64bit system; they are [COLOR="#0000FF"]libxml2:i386[/COLOR] and [COLOR="#0000FF"]libjpeg62:i386[/COLOR] and [COLOR="#0000FF"]libstdc++6:i386[/COLOR] and the command would be > [COLOR="#FF0000"]sudo apt-get install libxml2:i386 libjpeg62:i386 libstdc++6:i38[/COLOR]6

________________________

If I was getting the UFR, I would get it from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html?r=s&q=](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html?r=s&q=) and it comes down as [COLOR="#008000"]Linux_UFRII_PrinterDriver_V290_uk_EN.tar.gz[/COLOR] 

Sounds like you have downloaded an identical copy from the Europe website?

back to you for comments ............

---

### Post by tjelka on 2014-09-21
I have only one, this iR1022F printer conected via USB. My system is Ubuntu 14.04 64 bit.


1. I searched in Ubuntu software center for canon driver and uninstall 4 drivers that vwas there, also 2.9 i mentioned before, so this is clean
2. downloaded drivers from link you provided: [http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html?r=s&q=](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html?r=s&q=)
3. Installed first cndrvcups-common_2.90-1_amd64  and after that installed second package cndrvcups-ufr2-uk_2.90-1_amd64
4. run command in terminal sudo /usr/sbin/lpadmin -p iR1022F -m CNCUPSIR1023ZK.ppd -v cnusb:lp0 -E, no errors
5. installed packages for 64 bit system with command: sudo apt-get install libxml2:i386 libjpeg62:i386 libstdc++6:i386  with no errors
6. opened Printers dialog and there is iR1022F printer, and I set as default
7. Try print one text document and printer in Printers dialog set message in Printer State: Processing - Printer not connected; will retry in 30 seconds...
8. restarted pc in xp boot, try print and print ok, wake up from sleep mode and print document sucesfully. 
9. Restarted in Ubuntu 14.04 64 bit, this system, wake up printer manualy (soft on/off button) and still same message: Processing - Printer not connected; will retry in 30 seconds...




For your questuion about results of command: dpkg -l | grep cndrvcups
ii  cndrvcups-common      2.90-1      amd64        Canon Printer Driver Common Modules Ver.2.90
ii  cndrvcups-ufr2-uk        2.90-1      amd64        Canon UFR2 Printer Driver for Linux


For your question about results of command: /usr/sbin/lpinfo -v
direct cnusb:/dev/usb/lp1
direct cnusb:/dev/usb/lp2
network ipp14
serial serial:/dev/ttyS0?baud=115200
direct parallel:/dev/lp0
network socket
network lpd
direct hp
network smb
direct usb://Canon/iR1018/1022/1023%20(FAX)?serial=1975O1PH0057&interface=1
direct usb://Canon/iR1018/1022/1023%20(UFRII%20LT)?serial=1975O1PH0057&interface=2
network ipp
network http
network https
network ipps
direct hpfax

Thank you for your response, I appreciate and I am available for further action

---

### Post by pdc on 2014-09-21
so when I said lp0 in the example I gave, that would be if the system saw your printer as lp0, whereas looking at the results, it probably sees it as lp2 .......................looks like FAX gets lp1 and PRINTER gets lp2

so in their readme, Canon say

> Depending on the distribution you are using, when you register the USB printer   with the print spooler specifying /dev/usb/lp* as [Device URI], printing may fail with an error "Printer not Connected" displayed. To solve this problem, specify the printer specific name as [Device URI] that is displayed by using the following command.
    Example: When you use MF4600 Series
    1) Display the [Device URI]
      # /usr/sbin/lpinfo -v
      direct usb://Canon/MF4600%20Series%20(FAX)
      direct usb://Canon/MF4600%20Series%20(PCL5e)
      direct usb://Canon/MF4600%20Series%20(PCL6)
      direct usb://Canon/MF4600%20Series%20(UFRII%20LT)
    2) Register the printer
       [COLOR="#DDA0DD"]sudo lpadmin -p MF4600_USB -m CNCUPSMF4600ZK.ppd -v usb://Canon/MF4600%20Series%20(UFRII%20LT) -E[/COLOR]

so you get direct usb://Canon/iR1018/1022/1023%20(UFRII%20LT

so best remove the registration with the printer spooler with > [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -x iR1022F[/COLOR]

and try a new registration, using the ID for the printer we got from your enquiry (/usr/sbin/lpinfo -v)

 > [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p iR1022F -m CNCUPSIR1023ZK.ppd -v cnusb://Canon/iR1018/1022/1023%20(UFRII%20LT) -E[/COLOR]

---

### Post by tjelka on 2014-09-21
Ok, i get it now readme file is there so I can read it of an answer. Thank you for your understanding :)

Sucessfully remove the registration:

> [COLOR=#FF0000]*sudo /usr/sbin/lpadmin -x *[/COLOR][COLOR=#417394]*iR1022F*[/COLOR]

and tried another so I run command and something strange happend:

> sudo /usr/sbin/lpadmin -p iR1022F -m CNCUPSIR1023ZK.ppd -v usb://Canon/iR1018/1022/1023%20(UFRII%20LT) -E
bash: syntax error near unexpected token `('

Maybe some encoding issue, some advice please. Thanks!

---

### Post by tjelka on 2014-09-21
I escaped brackets  with \ and sucessfully executed command, so command looks at final:

> sudo /usr/sbin/lpadmin -p iR1022F -m CNCUPSIR1023ZK.ppd -v usb://Canon/iR1018/1022/1023%20\(UFRII%20LT\) -E

Printed test page successfully!!!

Driver works fine on Duplex (two sided printing). Wow happy!

Device has Fax too. I executed also:

> sudo /usr/sbin/lpadmin -p iR1022F -m CNCUPSIR1023ZK.ppd -v usb://Canon/iR1018/1022/1023%20\(FAX\) -E

but nothing happend. Some advice  please.

Thank you!

---

### Post by pdc on 2014-09-21
that's great; and thank you very much: you have solved the issue of the brackets; 

............ the registration you tried for the fax is the lpadmin (linux printing admin) and I can't see registering with the printer spooler will get it going .......... that would need to be a google search

As it is your thread, you can proudly edit the THREAD TOOLS at the top of the menu and add SOLVED!! (even if the fax isn't tweaked yet.........surely for the printer we can say solved

__________________________________

I suspect you need something like this [http://www.aboutdebian.com/fax.htm](http://www.aboutdebian.com/fax.htm) and you need to configure it once the phone line is in place (I used wvdial to configure ZTE modems before network manager integrated them)

---

