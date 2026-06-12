---
title: "[SOLVED] Canon Pixma ip3500"
date: 2008-07-22
forum: Hardware
---

### Post by Unotforme on 2008-07-22
Anyone here have one, and able to get it working? I've found out that Canon has very poor Linux support [I]after[I] I installed HH 8.04. HH recognizes the ip3500, but when I go to print, the printer error light comes on. If anyone has been able to get this printer working, I'd like to hear about it...

---

### Post by Unotforme on 2008-07-24
I found two .deb files for the Canon ip3500 at this site:

**[http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&query=ip3500&binning-state=model%3d%3dPIXMA%20iP3500%0amenu%3d%3dDownload%0aos%3d%3dLinux&](http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&query=ip3500&binning-state=model%3d%3dPIXMA%20iP3500%0amenu%3d%3dDownload%0aos%3d%3dLinux&)**

You will need both files and you should install '**IJ Printer Driver Ver. 2.80 for Linux(debian Common package)**' first then the '**IJ Printer Driver Ver. 2.80 for Linux(debian Package for the iP3500 series)**' second.

Then setup your printer under system>admin>printing.

I haven't thoroughly tested it yet, however I did get good colour prints out of GIMP and Open Office Spreadsheet.

---

### Post by Newby HH user on 2008-08-15
It still doesn't work in linux 64 though....Is there some way to install 32 bit drivers in 64 bit Kubuntu Hardy?

---

### Post by dorite on 2008-08-29
Well, here's my experience.  I had my iP3500 working well on 7.10 but decided to upgrade to 8.04.  Many things broke, and I ended up having to do a clean reinstall.  Then I discovered that my backups were no good, so I'm having to reconstruct everything.

Both [[COLOR="Blue"]Canon-Europe[/COLOR] ]("http://software.canon-europe.com/software/0028475.asp?model=") and [ [COLOR="Blue"]Canon-Australia[/COLOR] ]("http://www.canon.com.au/products/printers/colour_bj_printers/ip3500_support.aspx") have the same driver packages.  You'll find .deb and .rpm packages for the "common" and the "iP3500-specific" driver portions.  In addition, there is a guide and a FAQ each in a zipped tarball.

I suggest you download the .deb's and the guide, then read the guide.  It has clear instructions for installing on Ubuntu 7.04.  Unfortunately, the part about specifying the driver as "cnij_usb:/dev/usblp0" doesn't work, nor does specifying it as "cnij_usb:/dev/usb/lp0.  I ended up with the device uri set to "usb://Canon/iP3500%20series".  This works: I don't know why.

Anyway, there are several good, working, utilities provided in the Canon packages -- all explained in great detail in the Guide.

Good luck.

---

### Post by aceqbaceq on 2009-06-04
> **Unotforme said:**
> Anyone here have one, and able to get it working? I've found out that Canon has very poor Linux support [I]after[I] I installed HH 8.04. HH recognizes the ip3500, but when I go to print, the printer error light comes on. If anyone has been able to get this printer working, I'd like to hear about it...

my expereience with installation into debian  ip 3500 and ip 3600.

first of all you can use driver of canon 4600 for canon 3600 , and you can use driver of canon mp520 for canon 3500.

because debian squeeze doesn't have drivers for canon 3500 and 3600. but debian has drivers for canon mp 520 and canon 4600 by default. and you can use 4200 instead of 4600.

the type of driver for 4600 and mp520 is cups+gutenrpint.
also you can try to find appropriate driver by installing additional set of drivers (type foomatic)

# apt-get install foomatic-filters-ppds
(don't forget restart cups service)

but there is no drivers for our printers.

but. there is a problem. if picture that you want to print is smaller than A4. so in this case printer will scroll paper very slow during all A4 length. it doesn't matter how small the real picture is. it's really annoying. 

if you don't like it. you can download original drivers from canon site.

for 3500 : [http://software.canon-europe.com/products/0010483.asp](http://software.canon-europe.com/products/0010483.asp)
you will two variants for linux. if you have debian (as i have) so choose lower variant. 

for 3600: [http://software.canon-europe.com/products/0010648.asp](http://software.canon-europe.com/products/0010648.asp)

so download, untar. and 

for 3600

# dpkg -i cnijfilter-common_3.00-1_i386.deb
# dpkg -i cnijfilter-ip3600series_3.00-1_i386.deb

for 3500

# dpkg -i cnijfilter-common_2.80-1_i386.deb
# dpkg -i cnijfilter-ip3500series_2.80-1_i386.deb


unfortunately the printer monitor 
$ printuiip3600

doesn't work. so we can start it. but really it doesn't work. so for instance we can't print in a silent mode. it's bad. because if you print very much the mechanism that scroll paper will wear out (destroy) faster. and at last in speed mode printer will not be able to scroll paper . but it will be able do it in silent mode in the same time. so in linux we can't change mode. it's sucks.


if you want to select the paper tray so this is the correspondence between real tray position and in the http cups control panel


vertical tray on the back of printer - rear tray 
horizontal tray in front of printer - cassetee or continious 


the next moment.

suppose we need (as i need) to print from 3500 and 3600 printers simultaneously. so we have to have two drivers (i mean two original drivers) simultaneously at the computer. the solution.

# dpkg -i cnijfilter-common_3.00-1_i386.deb
# dpkg -i cnijfilter-ip3600series_3.00-1_i386.deb
# dpkg -i cnijfilter-ip3500series_2.80-1_i386.deb

it works perfectly.

so the next stupid problem. when printer prints - we have a huge pressure on processor. if we use "top" we will see that the reason is "gs".
so when we print we have a problem of using another applications. it's very stupid. so i suggest to set very low prioritet for process gs. in that case we can do all we need without any unpleasant "slow downs" and the printing process will take place in a foreground mode. it's obvious :).

by manuyally:

# $ renice 19 -p `ps aux | grep -i /usr/bin/gs | awk '{ print $2 }'`

i don't want to renice process gs by manually and i print very often. so i suggest the next method.

/etc/crontab

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user command
17 * * * * root cd / && run-parts --report /etc/cron.hourly
25 6 * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6 * * 7 root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6 1 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
*/1 * * * * root /etc/cron.minutes/pechat-renice.sh
#


/etc/cron.minutes/pechat-renice.sh

#!/bin/bash

for i in `ps aux | grep -i /usr/bin/gs | grep -v grep| awk '{ print $2 }'`
do
renice 19 -p $i
done

---

