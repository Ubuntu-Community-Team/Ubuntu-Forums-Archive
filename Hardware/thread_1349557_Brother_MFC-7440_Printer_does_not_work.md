---
title: "Brother MFC-7440 Printer does not work"
date: 2009-12-08
forum: Hardware
---

### Post by h_ariakiaariakia on 2009-12-08
I've spent whole a day to find a way to install my brother mfc-7440 printer on ubuntu 9.1, unfortunately  there in no ppd file for the model.

I followed the steps on Brother web site:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html)
[B]sudo aa-complain cupsd
[/B][B]sudo mkdir /usr/share/cups/model

[/B][http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)[B]
sudo dpkg -i --force-all cupswrapperMFC7440N-2.0.2-1.i386.deb
[/B]
I received these error messages [B]

ERROR : Brother LPD filter is not installed.
chmod: cannot access `/usr/local/Brother/inf/brMFC7440Nrc': No such file or directory
chmod: cannot access `/usr/local/Brother/inf': No such file or directory
[/B]
Then I checked the CUPS
The CUPS shows that printer has been installed and its status is IDLE, but if I want to print off a page, the printer will not work while even  there is no error message.

I found a solution for a similar problem on the Brother web page ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#80](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#80)) but it did not help as well because  some lines which should be edited do not exist in the driver files or some lines which should be change are already changed, I mean I could not find the original line but I found the edited lines ! I think it is because the guide is an old one and they have already applied changes in new driver.I tried to use LPR driver as well, but even  it does not add theprinter to the list of printers, so it does not work as well !

---

