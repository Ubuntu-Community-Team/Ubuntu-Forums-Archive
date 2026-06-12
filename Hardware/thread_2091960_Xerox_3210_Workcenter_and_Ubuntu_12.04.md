---
title: "Xerox 3210 Workcenter and Ubuntu 12.04"
date: 2012-12-06
forum: Hardware
---

### Post by gkjohn on 2012-12-06
Hi. I have two assembled desktops both running 12.04 LTS and I have been trying to setup a [Xerox 3210 Workcenter]("http://www.office.xerox.com/multifunction-printer/multifunction-under-30ppm/workcentre-3210-3220/enus.html") as a network printer that they can both access. 

Yes, it has terrible Ubuntu support and we should have checked before we bought it. 

The Ubuntu printer auto-detect routine found the printer as a network printer but it did not work out of the box. I followed the method [described here]("http://jozefklacko.blogspot.in/2011/11/how-to-install-xerox-workcentre-3210-on.html") and got it to work on Machine 1 using the default dnssd option presented.

However, on Machine 2, this identical method does not work and the Print Queue shows all print jobs sent to this printer as stopped because the "Printer is Out of Paper". Of course, the printer is not out of paper. I can ping the printer just fine and can even have it do a self test from the Printer menu. But cannot print even an Ubuntu test page. 

Any ideas on what I could try, please? I have tried setting it up as IPP and HTTP with no success either. 

cupsd.conf and printer.conf attached

---

### Post by magnus07 on 2013-02-16
I'm considering to buy the Xerox 3210.

I see nobody answered you.

Did you solve the problems?

Do you have 64bit or 32bit Ubuntu versions?

It's a pity that a printer with linux official support is so backlevel.

Thanks

---

### Post by gkjohn on 2013-02-16
I was unable to solve this problem in any meaningful way. Gave up and exchanged this printer for a HP printer that works well with HPLIP.

---

### Post by omarchianni on 2013-06-13
I have installed the xerox work centre 3210 as network printer on ubuntu 12.04.2 with the following prcedure sucessfully on my lenovo b590 labtop and an old msi mainboard ms71-42:
a) updated firmware of the workcentre from here: [http://www.support.xerox.com/support/workcentre-3210-3220/file-download/enus.html?operatingSystem=linux&fileLanguage=en_GB&contentId=101848&from=downloads&viewArchived=false](http://www.support.xerox.com/support/workcentre-3210-3220/file-download/enus.html?operatingSystem=linux&fileLanguage=en_GB&contentId=101848&from=downloads&viewArchived=false)
(with workcentre connected temporarily via USB)
b) then downloaded printer drivers from here: [http://www.support.xerox.com/support/workcentre-3210-3220/file-download/enus.html?operatingSystem=linux&fileLanguage=en_GB&contentId=101643&from=downloads&viewArchived=false](http://www.support.xerox.com/support/workcentre-3210-3220/file-download/enus.html?operatingSystem=linux&fileLanguage=en_GB&contentId=101643&from=downloads&viewArchived=false)
c) setup all the network settings according to xerox manual on the printer itself
d) extracted the file "wc3210.tar"
e) searched with nautilus (= the basic file browser) for "wc3210.ppd" and copied to my desktop
f) searched with nautilus for rastertosamsungspl and copied as welll to desktop
e) code in terminal: # cd Desktop
#sudo cp rastertosamsungspl /usr/lib/cups/filter
g) open systemsettings in ubuntu 12.04.2 and choose printing
add new printer- network printer - (it will find the workcentre with its IPafter about ten seconds, be patient!) - click that; then "forward" (searching for drivers wait till "choose driver appears), click "provide ppd file" and navigate to your desktop where you'll find the previously saved wc3210.ppd
h) click apply and print test page - you're done!

---

