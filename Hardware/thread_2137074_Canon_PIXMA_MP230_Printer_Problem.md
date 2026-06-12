---
title: "Canon PIXMA MP230 Printer Problem"
date: 2013-04-19
forum: Hardware
---

### Post by sadekso2001 on 2013-04-19
I am using HP-Pavilion-g6-Notebook-PC and OS as [COLOR=#000000]Raring Ringtail. Trying to use [/COLOR]Canon PIXMA MP230 but I can't use it. I am a new user of Ubuntu. Looking for Step by step solution.

---

### Post by ajgreeny on 2013-04-19
Here you go:-
[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP230.aspx](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP230.aspx)

Read everything carefully and you should be OK, unless things have changed so much in RR that it does not work.

The drivers themselves are at:-
[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP230.aspx?DLtcmuri=tcm:14-994535&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP230.aspx?DLtcmuri=tcm:14-994535&page=1&type=download)
[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP230.aspx?DLtcmuri=tcm:14-994513&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP230.aspx?DLtcmuri=tcm:14-994513&page=1&type=download)

I used a Canon PIXMA MP250 for a while with no problems at all on 10.04, but have no experience on later versions of ubuntu.

---

### Post by pdc on 2013-04-20
so you can download it from the Canon Asia site

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100465901.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100465901.html)

it is the [COLOR="#0000FF"]MP230 series IJ Printer Driver Ver. 3.80 for Linux (debian Packagearchive)[/COLOR] which comes down as [COLOR="#008000"]cnijfilter-mp230series-3.80-1-deb.tar.gz[/COLOR]

If you copy and paste these commands into a terminal..hit the enter key after each paste..

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mp230series-3.80-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mp230series-3.80-1-deb[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

that should have the printer driver installed..............

______________________________________________________

Canon also provide [COLOR="#0000FF"]**ScanGearMP**[/COLOR] to run the scanner...........

get it from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100469501.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100469501.html)

it comes down as [COLOR="#008000"]scangearmp-mp230series-2.00-1-deb.tar.gz[/COLOR]

install using the same format as above..

run it by 

> [COLOR="#FF0000"]scangearmp[/COLOR]

......so you don't use simple scan or xscan.....................you then need a launcher to ..launch it..........each time

---

### Post by sadekso2001 on 2013-05-04
Hi all, Thanks for your help. It is working now.

---

### Post by csperry-2802 on 2014-01-28
Thanks also from me for these very clear instructions, my Canon Pixma MP235 printer is now working perfectly.

---

