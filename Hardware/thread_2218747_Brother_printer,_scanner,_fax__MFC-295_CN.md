---
title: "Brother printer, scanner, fax  MFC-295 CN"
date: 2014-04-21
forum: Hardware
---

### Post by gary21 on 2014-04-21
I was having a trouble with my printer,  butt, I got it working.  But now I need to get my scanner and fax to work,  its an all in one.  I tried Xsane and Simple Scan but both say that there is no scanner detected.   I need to scan to documents and the like.   Any ideas??   I'm new to ubuntu,  I'm using 14.10, any help would be appreciated.
thanks

---

### Post by pdc on 2014-04-22
Brother have an install script; and I understand it installs all the drivers you need;

as you have the printer going;

perhaps best to install individual bits: one by one?

go here [http://support.brother.com/g/b/downloadlist.aspx?c=au&lang=en&prod=mfc295cn_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=au&lang=en&prod=mfc295cn_all&os=128) and you need to know if you have 32bit or 64bit Ubuntu: 

For the Fax driver, you install the [COLOR="#0000FF"]LPR[/COLOR] first; and the [COLOR="#0000FF"]CUPS[/COLOR] after; if you downloaded them to your Downloads directory, if you then open that directory and right-click on the LPR first; and select "install with gdebi installer" or whatever is offered... and then do the same with CUPS:

come back for more detailed instructions as you need them:

eg see here [http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on](http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on) as this is an index for all the instructions;

for the scanner, read this [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) and they ask you to download a file called [COLOR="#008000"]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR] and when it is to be downloaded, the dialogue box will offer "open with gdebi installer" or similar; accept that as it installs it ..............

---

