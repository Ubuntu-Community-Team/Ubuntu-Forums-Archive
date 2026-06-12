---
title: "Canon LBP Printer"
date: 2010-08-10
forum: Hardware
---

### Post by grinaldi on 2010-08-10
Please help

I have Elonex Webbook running Ubuntu 10.04 and a Canon LBP 3000 Printer I successfully got my printer to print yesterday using the steps on Sun Screen Blog: [http://sunscreen.blog.com/2010/03/31/how-to-install-the-canon-lb2900-on-ubuntu-910/](http://sunscreen.blog.com/2010/03/31/how-to-install-the-canon-lb2900-on-ubuntu-910/).

However, when I switched on my computer and printer this morning the printer did not print. Also Statusmonitor showed no message. Further when I checked the "Document Printer Status (my jobs)" window this showed the print job appearing and disappearing as though it had been printed. The "Printing - localhost" shows the LBP 3000 printer as installed, as the default printer.

Thanks

grinaldi

---

### Post by grinaldi on 2010-08-13
I have managed to solve the problem. I discovered by deleting the printer in System>Administration>Printing then reinstalling it that it was named Canon-LPB300. I also noticed Statusmonitor was checking LBP300. When I changed every thing over to Canon-LPB300. All worked well.

Thus:
Statusmonitor LBP3000
became:
Statusmonitor Canon-LBP3000
&
sudo /usr/sbin/lpadmin -p LBP3000 -m CNCUPSLBP3000CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
became:
sudo /usr/sbin/lpadmin -p Canon-LBP3000 -m CNCUPSLBP3000CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
&
sudo /usr/sbin/ccpdadmin -p LBP3000 -o /dev/usb/lp0
became:
sudo /usr/sbin/ccpdadmin -p Canon-LBP3000 -o /dev/usb/lp0
etc.

If this is helpful to anyone, then de nada (your welcome).

grinaldi

---

