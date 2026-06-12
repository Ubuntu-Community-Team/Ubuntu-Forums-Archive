---
title: "Please help needed to use canon pixus mp480!!!"
date: 2009-05-22
forum: Hardware
---

### Post by hananias on 2009-05-22
No matter what I`ve tried, can`t get canon printer to work!  My computer sees it sort of.  When I plug it in, it searches for drivers..There isn`t any for this specific model.  So I tried some similar ones, but nothing happens. ](*,) WHen I print, I get the tool tip message that the job finished printing... but the printer is quiet, no actions!!  Please, This new release of Ubuntu 9.04 is amazing!!!  But if I can`t print my documents, that is more important, than wobbly windows and fish swimming inside a 3d desktop:frown:
Anybody got any advice how to print in Ubuntu!!!

---

### Post by hananias on 2009-05-22
Anybody????  Please

---

### Post by doug1212 on 2009-05-22
Hi,
Canon printer support is patchy at best, and there don't appear to be any open source drivers for your particular model.

There are commercial Turbo print drivers for that model or can it print from a memory stick?, not ideal I know.

Doug.

---

### Post by hananias on 2009-05-23
Thanks for the reply.  How do I find out more about the Turbo Print drivers???  thanks in advance

---

### Post by doug1212 on 2009-05-23
TurboPrint are commercial printer drivers and cost, I don't use them.

More info here:

[http://www.turboprint.info/]("http://www.turboprint.info/")

On the plus side according to "SANE supported devices" the scanner is support is described as good.

Doug.

---

### Post by jamisonaw on 2009-08-01
I have the same issue with Ubuntu 9.04 and Canon PIXMA MP480. Great OS, crappy printer but still no support for it.

---

### Post by Malta paul on 2009-08-01
I don't think your printer will work with linux, check out:
[http://openprinting.org/show_printer.cgi?recnum=Canon-Pixma_MP480](http://openprinting.org/show_printer.cgi?recnum=Canon-Pixma_MP480)

Why not either dual boot with windows and transfer your files across to that partition, or use a virtual partition and install windows there.
[http://www.virtualbox.org/](http://www.virtualbox.org/)    

sorry:(

---

### Post by jkeane on 2010-08-28
I know that this is reviving a bit of a dead thread, but I wanted to get this information out there for others.

It is possible to get the Canon Pixma MP480 working with Ubuntu (well I've tried both the scanner and the printer, there might be other minor features that don't work). (tested with 10-04 Lucid Lynx)


In order to install it you must download Canon's drivers for the MP490 (which seems to not be sold in the US, but is in Europe) 

product page: [http://www.canon-europe.com/For_Home/Product_Finder/Multifunctionals/Inkjet/PIXMA_MP490/]("http://www.canon-europe.com/For_Home/Product_Finder/Multifunctionals/Inkjet/PIXMA_MP490/") 

driver page: [http://software.canon-europe.com/products/0010754.asp](http://software.canon-europe.com/products/0010754.asp)

Download both Debian Linux Print Drivers (3.2), and ScanGear for Linux (1.4).

Open up both of these .tar files, and then open up the archives in them that look like *-mp490series-1.40-1-i386-deb.tar.gz. In each of these you will find a folder called packages that have two .deb files that you need to install to get this printer and scanner working.

There will be four files between the two files that you will need to install:
printer:
cnijfilter-common_3.20-1_i386.deb
cnijfilter-mp490series_3.20-1_i386.deb

scanner:
scangearmp-common_1.40-1_i386.deb
scangearmp-mp490series_1.40-1_i386.deb

Now you just need to use dpkg to install each of these four files. (For the scanner to work you will need to have gimp installed, you can do that with apt-get or synaptic)

It's slightly more complicated if you are running a 64-bit distribution of ubuntu. First you have to make sure you have the ia32bit libraries installed: ```
apt-get install ia32-libs
```

 and then you just force the architecture: ```
dpkg --force-architecture -i *.deb
```

---

### Post by pvfloripa on 2010-09-22
Great! jkeane's solution worked perfectly with Ubuntu 10.04 and printer MP480. 

Thanks!

---

### Post by ahorriblemess on 2010-10-25
I just plugged mine in and it worked. Scanning and printing works fine with 10.04 and 10.10

---

### Post by zuss on 2010-11-10
hello there... well i have got a problem... i cant understand what i should choose first for the printer... i mean which driver should i choose firstly in order to be visible to laptop and then install the packages?

thanks

---

