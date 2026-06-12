---
title: "How to Lexmark E260dn ubuntu hardy ... and on"
date: 2010-09-01
forum: Hardware
---

### Post by Claus7 on 2010-09-01
Hello,

I was trying to install that printer in ubuntu hardy, not finding a how to.

The installation went more easier than I thought. I just type here some comments for easy reference.

Go to:
[http://support.lexmark.com/index?page=content&actp=DD_LIST&productCode=LEXMARK_E260&id=DR1714&os=UBUNTU_8_04_LTS&oslocale=en_US&segment=DOWNLOAD&userlocale=EN&locale=en](http://support.lexmark.com/index?page=content&actp=DD_LIST&productCode=LEXMARK_E260&id=DR1714&os=UBUNTU_8_04_LTS&oslocale=en_US&segment=DOWNLOAD&userlocale=EN&locale=en)

and download the driver files.

For installation, navigate to the folder where you have them downloaded and type:

```
gunzip PPD-Files-LMACG.tar.Z
tar -xvf PPD-Files-LMACG.tar
cd ppd_files
sudo ./install_ppd.sh
```

Then go to: System->Administration->Printing
choose New Printer
and as Model you will find the options of lexmark and e260dn (among others that were not there before).
Also fill in the:
lpd://*ip_address_of_printer*

and you are ok.

Hope this helped,
Regards!

---

### Post by Claus7 on 2010-12-21
Hello,

this printer enables the duplex technology to be used, meaning that someone can print an odd and the following even numbered page on one sheet of paper with just one click.

For this printer to make this option to work, one has to do the following:
Go to System->Administration->Printing and choose the tab Printer Options.

There you will see the Finishing option and underneath the option Duplex. Choose the Duplex - Long Edge and click apply.
(about differences on long and short edge check:
[http://answers.yahoo.com/question/index?qid=20090428074533AAoa1st](http://answers.yahoo.com/question/index?qid=20090428074533AAoa1st))

Now for the changes to take effect for hardy open a terminal and type:
```
sudo /etc/init.d/cupsys restart
```

and just print.

In other flavors of ubuntu you might have to type a similar command like the one above. Just press tab after typing cup(here tab) to see the options you are getting. And you are ok!

Regards!

---

