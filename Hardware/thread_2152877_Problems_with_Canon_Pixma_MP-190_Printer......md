---
title: "Problems with Canon Pixma MP-190 Printer....."
date: 2013-06-09
forum: Hardware
---

### Post by wbee on 2013-06-09
Hello,

When I was using 10.04,long-term-support,32 bit,this printer worked beautifully,flawlessly.

After Christmas,with a new computer build,I installed 12.04,long-term-support,64 bit,installed the printer driver from CUPS,printed a test page,and all seemed well.

Printing one copy of one page presents no problems. Turn on the printer,setup the print page,hit print,and turn off the printer.

But to print more than one page,or to print multiple copies of the same page presents problems.

When I hit print,it prints one copy of the first page and then stops printing. When you check the data referenced from the icon on the top panel,it says the printing is in progress;all the data in the involved readout seem correct.

With the situation given above,the printer will not turn off. When I cancel the job,the printer will still not turn off.

My updates are up to date,as of last night.

What is the shell command to remove and reinstall the driver?

If that does not work,should I report it to be a bug?

-------------

Thank you.

---

### Post by aikishugyo on 2013-06-10
When you say you are using the driver from CUPS, do you mean the gutenprint driver for CUPS?
If so, what version?
And what version of CUPS?
Maybe an exception needs to be added to the USB backend in CUPS....

---

### Post by wbee on 2013-06-10
aikishugyo,

Thank you. 

Canon PIXMA MP190 - CUPS+Gutenprint v5.2.8-pre1 is what is installed.

Under "Job Options", subcategory, "copies" it is set to "1". Is that as it should be? What would happen if I changed it to "0" or "14" ?

------

Thank you.

---

### Post by aikishugyo on 2013-06-10
Hi,
Copies is the number of copies of the job, not the page selection (that is a completely different option).
I recommend you use 5.2.9, since 5.2.8pre-1 was an old testing release.
I don't know if the problem is with the gutenprint driver or with CUPS (or both), but upgrading to 5.2.9 will make sure the specs for gutenprint are as I expect them to be.

---

### Post by wbee on 2013-06-11
aikishugyo,

Thank you for your prompt reply.

I rechecked the data at system settings/printing--and it says that 5.2.8pre-1 is what is installed.

However,when I checked the Synaptic Package Manager,it says that 1.5.3 is what is installed.

I  took out the old driver,reinstalled it,and it shows it is the 5.2.8pre-1.

Should I attempt to remove 1.5.3 and install 1.5.2,and if so,how?

------------

Thank you.

---

### Post by wbee on 2013-06-13
Bump.

---

### Post by aikishugyo on 2013-06-13
5.2.8pre-1 is the gutenprint package. You should get 5.2.9. This package has the drivers for the printer.

1.5.2 or 1.5.3 are the CUPS printer system package versions (printing system for your OS). CUPS and gutenprint are fundamentally separate: you need a printing system to send something to the printer. The printing system makes use of a particular end-driver to convert the data which it sends to the printer.

I don't know what bugs might exist in CUPS 1.5.2 or 1.5.3 on Ubuntu. But I know that you should be using the stable 5.2.9 gutenprint driver package, rather than the testing pre-release which has plenty of bugs.

---

### Post by wbee on 2013-06-14
aikishugyo ,

Thank you very much.

-------------

For anybody else reading this,here is the link to download the stable 5.2.9 gutenprint driver:

[http://sourceforge.net/projects/gimp-print/files/gutenprint-5.2/5.2.9/](http://sourceforge.net/projects/gimp-print/files/gutenprint-5.2/5.2.9/)

---

