---
title: "does the canon pixma mp210 work in linux/kubuntu?"
date: 2008-07-08
forum: Hardware
---

### Post by binskipy2u on 2008-07-08
ive searched and didnt find any info..
its an all in one.. printer, scanner, copier

came with the computer.. it seems to be found by the printer section of system settings, but thats it.. no other functionality, and xsane says no devices found since it's a scanner too..
any info or suggestions for downloads to get it working well would be most appreciated.. its not so bad, i'm dualbooting with vista where of course it works.. but id rather not boot into vista just to print something(i dont actually print pictures, mostly text anyway)
thanks again

---

### Post by wilbbe01 on 2008-07-08
The following forum link seems to talk about the mp210 some, it may or may not be of interest to you.

[http://ubuntuforums.org/showthread.php?t=556980](http://ubuntuforums.org/showthread.php?t=556980)

You want to use all of its functionality I assume?  I know with my printer (different model, different company) the pain of getting the vendor supplied drivers to work is too much.  I'm using PCL 6 or something like it if I remember correctly and it does everything for me, but I guess you might have more of a problem with the multifunction.  The other printer in the house which I rarely use with my ubuntu box currently does not work, even with the generic drivers I have tried (it's multifunction).  Your luck probably depends on how it connects to your computer as well.  All of mine are networked which makes multifunction a nuisance, hence why my multifunction printer is unused by ubuntu and why my simple laser gets to do the work.  I don't see anything on the Canon website about linux drivers either, at least on that printers support page. Does any of that help anything or is it just a lot of worthless rambling?

---

### Post by ramjet_1953 on 2008-07-09
Here's the Open Printing Database listing for your printer:

[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP210](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP210)

It may also be worthwhile trying the demo version of TurboPrint to see if it works well with your printer:

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

Regards,
Roger :cool:

---

### Post by binskipy2u on 2008-07-09
i got the printer working per the instructions on the thread you directed me to.. 
cant get the scanner working.. but thats ok.. i dont scan much anyway, it was a free product.. i can do scanning in vista..

i found a how-to, but there was like 20 directions.. and i have a 64bit os/computer.. i had to use the force install command to install those 4 files.. 

so i'm guessing why thats the scanner doesnt work.. 
thanks for everything

---

### Post by bemma on 2008-08-24
I installed the files on xubuntu 8.04 
* cnijfilter-common_2.80-1_i386
* cnijfilter-mp210series_2.80-1_i386.deb
* scangearmp-common_1.10-1_i386.deb
* scangearmp-mp210series_1.10-1_i386.deb
from [http://www.canon.com.au/products/all...0_support.aspx](http://www.canon.com.au/products/all...0_support.aspx)

I can see the printer in the printer configuration dialog. The printers state is "idle".

When I try to print the test page I get the error: There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

Any ideas?

Thanks,
Stan

---

### Post by satyr83 on 2009-01-19
You should select your printer from the configuration. If you click 'Change' for your 'Make and Model', you can find the Cannon, after then you should select your installed driver there (in my case it was MP210 Ver.2.80)..

It worked for me.

---

