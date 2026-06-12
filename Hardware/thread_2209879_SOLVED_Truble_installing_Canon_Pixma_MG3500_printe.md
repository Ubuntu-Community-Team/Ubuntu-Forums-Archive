---
title: "SOLVED Truble installing Canon Pixma MG3500 printer driver"
date: 2014-03-07
forum: Hardware
---

### Post by Bryce_Hutchison on 2014-03-07
Hi all; :p

I'm running Ubunu Dream Studio 32bit.

I have tryed to install 'cnijfilter-mg3500series-4.00-1-deb'  whitch I downloaded from best-drivers-blogspot site but it won't find my printer.

Any help would be very much appreciated.       ](*,)

---

### Post by pdc on 2014-03-08
so if one was starting from the beginning, I would suggest going to the Canon Asia site

[http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal)

and finding the MG3500 page

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100550402.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100550402.html)

and what you would download would be [COLOR="#008000"]cnijfilter-mg3500series-4.00-1-deb.tar.gz[/COLOR]

the commands to install it .......

if the Downloads directory is where you download things to ...

........ would be..........

> [COLOR="#FF0000"]cd Downloads[/COLOR]

then

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mg3500series-4.00-1-deb.tar.g[/COLOR]z

then 

> [COLOR="#FF0000"]cd cnijfilter-mg3500series-4.00-1-deb[/COLOR]

then 

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

and that should install it for you;

____________________

what does 

> [COLOR="#FF0000"]dpkg -l | grep cnijfilter[/COLOR]

give if you copy and paste it into a terminal? .......for my Canon I get "ii  cnijfilter-common 3.60-1 IJ Printer Driver for Linux. ii cnijfilter-mg3100series 3.60-1 IJ Printer Driver for Linux."

.....if you don't get any results, it suggests nothing was installed and you can run the commands I suggested; if you do get results, can I suggest you use synaptic to find the cnijfilter-mg3500series and cnij-common and remove and use the commands I suggest?

---

### Post by Bryce_Hutchison on 2014-03-08
:)  Thanks for your time and support .  

Thanks to you I got it working perfectly.  \\:D/

Terific help; thanks again .  :p

---

### Post by pdc on 2014-03-08
great; enjoy

..............Canon provide [COLOR="#0000FF"]ScanGearMP[/COLOR] which is a programme to run the scanner side of the device

you can get it from here 

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100552102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100552102.html)

and it comes down as [COLOR="#008000"]scangearmp-mg3500series-2.20-1-deb.tar.gz 
[/COLOR]
you install as for the printer driver; .....let me know if you want the commands detailed

to run it, you type

> [COLOR="#FF0000"]scangearmp[/COLOR] into a terminal; if you google on ubuntu launcher, you can see ways to set up a launcher for repeated use

---

