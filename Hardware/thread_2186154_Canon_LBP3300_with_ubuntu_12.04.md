---
title: "Canon LBP3300 with ubuntu 12.04"
date: 2013-11-06
forum: Hardware
---

### Post by aliasger52mail on 2013-11-06
Respected 

I have a print problem with ubuntu 12.04 LTS with Canon LBP3300

the problem is while printing the pdf files and from firefox mozilla browser it taking long time while printing

after some print it printer gone for rest and after 15 to 20 minutes the remaining print are done 

i have observed that the ghost script is taking such a long time to convert the file to printer format 

i have upgrade the ghost script packages and cups packages and poppler packages as well but none of this has solved the issue and i think their might be a driver problem 

so please help me to get me out of this problem 

Regards,

---

### Post by aliasger52mail on 2013-11-06
the problem with the following pdf file to test the sample try to print the attached pdf file from page 61 to 84

---

### Post by aliasger52mail on 2013-11-06
the problem with the following pdf file to test the sample try to print the attached pdf file from page 61 to 84

---

### Post by zKhtdyX on 2014-03-06
which capt driver version are you using? x32 x64 system?

---

### Post by nikhilgaw072 on 2014-05-03
How to install LBP 3300 printer in Ubuntu 12.04 x64 system?

I had tried a lot, but its worth....
Pls anyone give me the steps to install it.

---

### Post by pdc on 2014-05-03
having 64bit just makes things a little more difficult..............................32bit is straightforward; ........have you had the 64bit install a long time?

for 64bit you need some extra bits installed first: so you need to be able to copy and paste commands; into a terminal; so you need to be able to open a terminal;

so the first series of commands are:

> [COLOR="#FF0000"]sudo apt-get install apt-get install libglade2[/COLOR]

> [COLOR="#FF0000"]sudo apt-get install libpopt0:i386[/COLOR]

> [COLOR="#FF0000"]sudo apt-get install ia32-libs[/COLOR]

_______________

then get the CAPT driver from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html) and it comes down as [COLOR="#008000"]Linux_CAPT_PrinterDriver_V260_uk_EN.tar.gz[/COLOR]

the commands are

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf Linux_CAPT_PrinterDriver_V260_uk_EN.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd Linux_CAPT_PrinterDriver_V260_uk_EN64-bit_Driver/Debian[/COLOR]/

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-common_2.60-1_amd64.deb[/COLOR]

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-capt_2.60-1_amd64.deb[/COLOR]

> [COLOR="#FF0000"]sudo /etc/init.d/cups restart[/COLOR]

> [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p LBP3300 -m CNCUPSLBP3300CAPTK.ppd -v ccp://localhost:59687 –E[/COLOR]

> [COLOR="#FF0000"]sudo service ccpd start [/COLOR]

_________________________________________________

now if we check the status of the cppd daemon ...........

> [COLOR="#FF0000"]sudo service ccpd status[/COLOR] 

you should see something like > [COLOR="#EE82EE"]Canon Printer Daemon for CUPS: ccpd[/COLOR]: 8956 8954 ....have you got two numbers? ......any two numbers??...........yours will be different...............

...............your printer should now work.....................any joy?

---

