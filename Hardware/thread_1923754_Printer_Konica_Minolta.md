---
title: "Printer Konica Minolta"
date: 2012-02-11
forum: Hardware
---

### Post by Nicolab on 2012-02-11
Hi I have a printer Knoica Minolta Pagepro 1490 MF and I can't find the drivers. I am using UBUNTU can I have some help please.

Thanks a lot 

Nico

---

### Post by wolfen69 on 2012-02-11
[Linux Driver]("http://www.konicaminolta.eu/business-solutions/products/laser-printers/all-in-one/pagepro-1490mf/downloads/download-details.html?packageId=43368&productName=PagePro%201490MF")

---

### Post by Nicolab on 2012-02-12
Thanks  for the advice now I have the drivers folder on my desk top and Now ? Sorry but I am not really an expert can you help me.

thanks

---

### Post by kurt18947 on 2012-02-12
The above link appears to be the scanner driver.  This looks like the printer or all-in-one driver:

[http://www.konicaminolta.eu/business-solutions/products/laser-printers/all-in-one/pagepro-1490mf/downloads/download-details.html?packageId=43367&productName=PagePro%201490MF](http://www.konicaminolta.eu/business-solutions/products/laser-printers/all-in-one/pagepro-1490mf/downloads/download-details.html?packageId=43367&productName=PagePro%201490MF)

This may include all functions.  You can download and extract the .zip file.  There are folders for different Linux releases, Ubuntu is included.  The instructions appear to be based on Ubuntu 7.10 :frown: but they may still be valid.  I'm not an expert but a user with some experience (and some bruises:))

---

### Post by Nicolab on 2012-02-12
> **kurt18947 said:**
> The above link appears to be the scanner driver.  This looks like the printer or all-in-one driver:

[http://www.konicaminolta.eu/business-solutions/products/laser-printers/all-in-one/pagepro-1490mf/downloads/download-details.html?packageId=43367&productName=PagePro%201490MF](http://www.konicaminolta.eu/business-solutions/products/laser-printers/all-in-one/pagepro-1490mf/downloads/download-details.html?packageId=43367&productName=PagePro%201490MF)

This may include all functions.  You can download and extract the .zip file.  There are folders for different Linux releases, Ubuntu is included.  The instructions appear to be based on Ubuntu 7.10 :frown: but they may still be valid.  I'm not an expert but a user with some experience (and some bruises:))
Thanks I will let you know but do not give up if I will ask the next step
thanks

---

### Post by Nicolab on 2012-02-12
> **Nicolab said:**
> Thanks I will let you know but do not give up if I will ask the next step
thanks
Back to square one I download the files, connected the printer and switch it on then open a window called new printer there are three option:
1select printer from database (my printer is not on the list)
2 Provide PPD file (here I tried to open the file which I download but there are no PPD files
3 Search for a file to download (no way)

What next :confused:

thanks any way

---

### Post by kurt18947 on 2012-02-12
The printer will not be found until the driver package is installed successfully.  You have downloaded the .zip file pp14x0MFGDIlinux*.zip?  If so, you now need to extract it, just like any other zip file.  This will yield a folder with the same name as the zip file -  pp14 something.  If you open that folder, you will find several folders, one of which is ubuntu.  There are also two files, qtcups_install.doc & readme.txt.  Readme.txt doesn't seem helpful.  I'm not certain whether you need to install qtcups or not, it looks like you might have to.  Another issue is the age of this package; things have changed, mostly for the better since gusty gibbon. 

There is a readme inside the ubuntu folder.  The README_Ubuntu.htm has more detailed directions on how to install.  I don't have this printer and am not familiar enough with Linux & Ubuntu to give reliable instructions on something I have not done before.  You're sort of on your own unless someone more experienced will join in.  I'll help where I can but don't want to give wrong advice.

---

### Post by Nicolab on 2012-02-13
> **kurt18947 said:**
> The printer will not be found until the driver package is installed successfully.  You have downloaded the .zip file pp14x0MFGDIlinux*.zip?  If so, you now need to extract it, just like any other zip file.  This will yield a folder with the same name as the zip file -  pp14 something.  If you open that folder, you will find several folders, one of which is ubuntu.  There are also two files, qtcups_install.doc & readme.txt.  Readme.txt doesn't seem helpful.  I'm not certain whether you need to install qtcups or not, it looks like you might have to.  Another issue is the age of this package; things have changed, mostly for the better since gusty gibbon. 

There is a readme inside the ubuntu folder.  The README_Ubuntu.htm has more detailed directions on how to install.  I don't have this printer and am not familiar enough with Linux & Ubuntu to give reliable instructions on something I have not done before.  You're sort of on your own unless someone more experienced will join in.  I'll help where I can but don't want to give wrong advice.
Thanks for the advice but I was stopped at the very beginning.
In the Ubuntu read me it say to open HTTP :/local host: :631
and so I did but appear a warning saying do not continue unless you know what you are doing. Since I don not know what I am doing I gave up.
Hopping that somebody will guide me step by step.

Thanks a lot any way

---

### Post by kurt18947 on 2012-02-13
I wish I could be of more help.  What you might consider at some point is to create another Ubuntu install on another partition or another hard drive.  10 Gb. is enough space and I haven't created a swap partition unless the machine had < 1 gb.RAM.  Use that install for your experimental adventures.  If you mess it up irretrievably,  delete the partition recreate it, reformat and reinstall.  Creating an image might prove even quicker.  The advantage of restoring an image over reinstalling is the image will contain any additional software or config setting modifications present when the image was created.   I use boot manager software that will create partitions that cannot see one another and each install's GRUB goes in the partition, not the MBR.  Then I can create, resize and delete OSs and partitions without affecting any others and installing Windows won't overwrite Linux boot loaders.  

It's said we learn more from our failures than from our successes.  I"ve learned a LOT!! :lolflag: but I have a good time with it.

---

### Post by Nicolab on 2012-02-14
> **kurt18947 said:**
> I wish I could be of more help.  What you might consider at some point is to create another Ubuntu install on another partition or another hard drive.  10 Gb. is enough space and I haven't created a swap partition unless the machine had < 1 gb.RAM.  Use that install for your experimental adventures.  If you mess it up irretrievably,  delete the partition recreate it, reformat and reinstall.  Creating an image might prove even quicker.  The advantage of restoring an image over reinstalling is the image will contain any additional software or config setting modifications present when the image was created.   I use boot manager software that will create partitions that cannot see one another and each install's GRUB goes in the partition, not the MBR.  Then I can create, resize and delete OSs and partitions without affecting any others and installing Windows won't overwrite Linux boot loaders.  

It's said we learn more from our failures than from our successes.  I"ve learned a LOT!! :lolflag: but I have a good time with it.
Thanks I will think about it:-?

---

