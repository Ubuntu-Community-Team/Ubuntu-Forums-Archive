---
title: "HP 710C problems with margins"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by hyperboloid on 2005-05-23
I've just migrated from RedHat 9.0 to Ubuntu 5.04. Great install, and eveything works except for printing. I have an HP 710C which worked perfectly under RedHat. I configured it with the Ubuntu Printer tool, installed the recommended driver (pnm2ppa), and I can print just fine. 

However, the margins are all wacky and I cannot get many things to print properly centered on the page. I did select the proper paper type (US Letter) but that did not solve the problem. Printing HTML works ok, but lpr doesn't, a2ps doesn't, and printing postscript (dvips) doesn't. Printing from gv does not work properly. (Everything prints, but the margins are wrong.) 

As I said, printing from all of these apps worked perfectly in RedHat, with the very same printer.

Any ideas or suggestions?

EDIT:  This is resolved!  :)  After poking around in /etc I noticed a file [COLOR=Olive]/etc/papersize[/COLOR] which was set to "A4", and after I changed it to "letter" the problem with margins went away. 

Comment: I DID reset the paper size in the Gnome Printer tool, to "letter', but apparantly that did NOT work. It did not reset the value in the file [COLOR=Olive]/etc/papersize[/COLOR]. Is this a bug with the Printer tool? Anyone else experience this? 

It does seem that Ubuntu needs to improve the printer configuration. Selecting the proper papersize should be a question on the install, for instance.

---

### Post by BrianT on 2005-05-24
First, thanks for the way to change the default papersize.  I could not get it to print on letter size paper, no matter what option I chose in any program!  It would seem that when the regional settings on install were selected as US, the default paper size would be set to letter...is this easy to do?

I have an HP 1200 LaserJet and have been trying to get it to work with Ubuntu.  I have had it configured under Suse and Fedora, but I cannot get it to print properly now--at least now from the 'Print test page'.  I did get it to print a document in OO.org that I converted from a Word File (Excellent   :) ).  I have checked several documents from OO.org and they all print fine.  I was even able to print from Firefox without issue.

But the print test page still does not print properly.  Any ideas why?  Does anyone know if the print test image is defined for A4? or is it customizable for various paper sizes?

Thanks in advance.

Brian

---

### Post by hyperboloid on 2005-06-02
> But the print test page still does not print properly. Any ideas why? Does anyone know if the print test image is defined for A4? or is it customizable for various paper sizes?
Some test pages are indeed predefined for A4.

---

