---
title: "Network Scanning HP Photosmart 3200"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by xerman on 2006-01-04
Hello there,

I just installed new HP Photosmart 3210 multifunction with the Ethernet option and Dual Side printing.
Installing the printer was as smooth as eating a piece of cake and now network printing is easy, so easy....

But when trying to scan a picture through Xsane i get a "no devices found" dialog which is quite annoying.
If anyone has come out with an answer to ethernet scanning with this product, I'll appreciate that info a lot.

By the way, for the record: to get printing done the easyway:
 1- power on your ubuntu machine, get to gnome and
 2- follow the printed guide provided with the printer up to where it tells to plug it .
 3- plug the ethernet cable in the ethernet switch/router/whatever and to the  multifunction
 4- wait the 4 min the Photosmart takes to callibrate
 5- in the Photosmart 3200 screen get to Network after pressin the "Configuration" button on the pannel.
 6- Set manual network configuration that matches your soho network
   example:
    network with 4 ubuntus 169.245.254.0-1-2-3
    network mask: 255.255.255.0
    network gateway: 169.245.254.100
  choose for example, 169.245.254.101 for the printer.
 7- Administration -> Printers -> New Printer select LAN printer "HP JetDirect" and put 169.245.254.101 as "host" leaving "port" as is (default 9100).

Now, someone add the lines for scanning ;)

And some kind of help to get this things arranged:
1- Multifunction has TwoSidedPrinting Module installed. 2Side printing is allowed everywhere on the system but certain apps, like Evince never print doublesided even if selected.
2- There is no way to scan through Xsane (checked sane and sane-net giving printer IP in the lan with no results)
3- No acces to memory card slots. Introducing a memory card just makes the printer read the card and show its contents on the printer screen. No mounting memory card on desktop and no way to access them in Ubuntu.
4- "hp-toolbox" does not work. It asks for a printer that is not detected as it was not set through CUPS webmanager nor "System->Administration->Printers" though multifunction was set this second way. This "hp-toolbox" is a way to acces all the functionalities of the machine, at least is what it shows before quiting.
5- updating driver from hp version 0.95 (ubuntu's) to 0.97 (hp's) doesn't solve these issues.
6- there is no way to select quality printing from any app, nor paper type. It has to be done through "System->Administration->Printers->Photosmart3210).
7- Gimp has not listed this model, selecting the closest "photosmart 1100" allows printing, but selecting "glossy photo paper" causes print process to stop printing in the middle of the task and feed out the paper.
8- Maximum resolution provided by gimp is 600x600dpi while printer has 4800.
9- Printout mode limits printing resolution to 1200dpi, better than Gimp, but 4 times less than hardware availability.

take care

---

### Post by deerfieldtech on 2006-01-05
I lost network scanning to an OfficeJet 7110 sometime last week I believe. I used hpoj, and never tried HPLIP. For some reason hpoj lost the ability to communicate with my officejet, and this happened on two breezy machines. So today I tried to get scanning to work using hplip, and I get the same results as you. I can scan using the following command from a terminal (which I found on this page [http://hpinkjet.sourceforge.net/hplip_readme.html);](http://hpinkjet.sourceforge.net/hplip_readme.html);)

xsane <"hpaio" device uri> 

Look for the scanning troubleshooting section on the page I mentioned, it's there.

So, at this point my scanner is useless. Not sure what happened...

---

### Post by xerman on 2006-01-31
Finally I found the way to solve this issue, thanks to the link provided by **deerfieldtech**.

it was as easy as get "Applications Menu editor" and change XSANE init command from
 - ```
xsane
```
to
 - ```
xsane "hpaio:/net/PrinterName?ip=1.1.1.1"
``` (Multifunction IP Address)

This text between quotes must be exactly the one provided by
 - ```
$ hp-makeuri <ip-address>
```

Though scanimage -L doesn't see the device, it works. I fooled around config files for sane: ```
dll.conf
```, ```
saned.conf
```, ```
net.conf 
``` and the only thing neede is uncomment the line in ```
dll.conf
``` having ```
hpaio
```, maybe comment all the others backends not being used, include the Multifunction IP in ```
net.conf
``` and in ```
saned.conf
```

Obviously it takes some time to preview through the net, but the stuff works as it should. 

Thanks a lot **deerfieldtech**, as I was almost to give up with this one. I don't understand how I couldn't get to the bottom of the page of that link. Seems this time the thing is, as many others RTFM, and read carefully and slowly.

Take care

---

