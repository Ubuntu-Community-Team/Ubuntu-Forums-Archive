---
title: "Recent Epson all-in-one AMD64"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by cotcot on 2007-10-15
After long search and trials I found out how to get my Epson photo stylus RX640 working.
Problem is that this all-in-one is not yet supported with gutenprint from the ubuntu repos and that there are no epson drivers for 64 bit (pips or pipslite and iscan). 
You can try to install that all in a 32 bit chroot, but I could find a way that I do not need this. 

My printer is not supported by gutenprint-5.0 that is in the ubuntu repositories, although it is supported by gutenprint-5.1.6. Quite some other epsons are newly supported by version 5.1.6. Unfortunately [[COLOR="Red"]this[/COLOR]]("http://gutenprint.sourceforge.net/p_Supported_Printers.php3") list is not up to date; mine is not in the list although it is supported by 5.1.6. So install gutenprint to check it or find a more updated source for information.

I suppose that this method will also work on some other newer epsons (also from the DX all-in-one series and the CX printer series).


So here is how I did it :

**Printer-section**

Install gutenprint version 5.1.6
Download gutenprint from [[COLOR="Red"]here[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=1537"). Extract.(right click on the file and select "extract here")
```
sudo apt-get -i build-essential libcupsimage2-dev doxygen docbook-utils
cd gutenprint-5.1.6
./configure
make clean
make
sudo make install
```

The printer can now be configured using [[COLOR="Red"]http://localhost:631[/COLOR]]("http://localhost:631")


**Scanner-section**

```
sudo apt-get -i sane sane-utils libsane-extras
```

The file /etc/sane.d/dll.d/dll.conf must be modified by deleting &#8220;epson&#8221; and adding &#8220;epkowa&#8221;. Otherwise sane will be confused because of seeing 2 drivers at once.
```
sudo gedit /etc/sane.d/dll.conf 
```

Check the driver situation with :
```
scanimage -L
```
The output from this command should look like :
> cotcot@cotcot-desktop:~$ scanimage -L
device `epkowa:libusb:002:004' is a Epson Stylus Photo RX640/RX650 flatbed scanner


Then sane is to be restarted.
```
saned restart
```

The scanner works.


So good luck.

---

### Post by sausagepotato on 2007-12-03
thanks so much for this! This worked for my Epson CX5000 =)

---

### Post by art.by.bec.com on 2007-12-06
Hi Thanks for the tip
I got my print working with it
but had trouble with the scan directions
i am very new to linnux
and wasnt sure what i was doing
any further help would be most appreciated

i am not sure if this is a silly question
but once you confgure
what program do you use to work the scanner from the computer if the epson disc wont recognise or work on ubuntu??
thanks
bec

---

### Post by helpdeskdan on 2007-12-17
Thanks for the Printer section, Cotcot!  Unfortunately, this printer is such a worthless ink sucking piece of junk that it stopped printed after printing just (the equivalent of a) couple pages of text saying it was empty.  I think I'm going throw mine out the window to see what kind of noise it makes. 

A forewarning to other users - DO NOT BUY THIS PRINTER! If you bought it, DON'T TRY TO GET IT TO WORK IN LINUX! It's not worth the time, go, RUN back to where you bought and return it now!!

---

### Post by cotcot on 2008-01-09
> **art.by.bec.com said:**
> Hi Thanks for the tip
I got my print working with it
but had trouble with the scan directions
i am very new to linnux
and wasnt sure what i was doing
any further help would be most appreciated

i am not sure if this is a silly question
but once you confgure
what program do you use to work the scanner from the computer if the epson disc wont recognise or work on ubuntu??
thanks
bec
You do not need the epson disk. Just start 'xsane'.

---

### Post by cotcot on 2008-03-01
> **helpdeskdan said:**
> Thanks for the Printer section, Cotcot!  Unfortunately, this printer is such a worthless ink sucking piece of junk that it stopped printed after printing just (the equivalent of a) couple pages of text saying it was empty.  I think I'm going throw mine out the window to see what kind of noise it makes. 

A forewarning to other users - DO NOT BUY THIS PRINTER! If you bought it, DON'T TRY TO GET IT TO WORK IN LINUX! It's not worth the time, go, RUN back to where you bought and return it now!!
This can be solved by modifying the printer parameter in cups. I  have adapted following printer option in cups :
Brightness : 1.5
Density : 0.2
Cyan Balance : 0.7
Yellow balance : 0.7

---

### Post by ringoShells on 2008-05-26
this worked for my epson rx650 for a couple pages...but now the printer doensn't seem to be recieving the data.

also Kpdf doesn't seem to recognise the printer, so i have to convert to .ps first then try to print it...which fails.

---

