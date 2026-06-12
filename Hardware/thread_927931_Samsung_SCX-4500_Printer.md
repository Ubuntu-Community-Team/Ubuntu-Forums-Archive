---
title: "Samsung SCX-4500 Printer"
date: 2008-09-23
forum: Hardware
---

### Post by soxs on 2008-09-23
I am going to get a new printer within the next one or two weeks.. so I saw one which stated to have linux driver support: Samsung SCX-4500 ( a very shiny one :-P ). As I had some bad experience with hardware (especially printers/scanners) that state explicit Linux compatibility, I would like to get some help wether to buy it or not. [http://www.alternate.de/html/product/Laserdrucker_Multifunktion/Samsung/SCX-4500/245753/?tn=HARDWARE&l1=Drucker&l2=Laserdrucker&l3=Multifunktion](http://www.alternate.de/html/product/Laserdrucker_Multifunktion/Samsung/SCX-4500/245753/?tn=HARDWARE&l1=Drucker&l2=Laserdrucker&l3=Multifunktion) (caution! german page! )

I am using hardy, so anything older than hardy won't help me. Thx for any rising voices and comments.

---

### Post by soxs on 2008-09-29
Bump!

---

### Post by cyberkost on 2008-12-27
Hey Soxs, have you gotten your question answered?  I'm not sure how you've concluded that Samsung states Linux compatibility for SCX-4500.  I know Samsung does state Linux compatibility for some of its printer products (e.g., [http://www.newegg.com/Product/Product.aspx?Item=N82E16828112076](http://www.newegg.com/Product/Product.aspx?Item=N82E16828112076)), but this one has no mentioning of Linux compatibility ([http://www.newegg.com/Product/Product.aspx?Item=N82E16828112089](http://www.newegg.com/Product/Product.aspx?Item=N82E16828112089)) .. neither is this MFC/printer mentioned here: [http://www.openprinting.org/printer_list.cgi?make=Anyone](http://www.openprinting.org/printer_list.cgi?make=Anyone).  I kinda want to get it for the functionality (need scanner and copier functionality too, don't need fax) and the price .. but not knowing whether or not it's Linux compatible stops me.

---

### Post by soxs on 2008-12-28
Same for me, I now don't own a printer... and I don't have enough money to get a shiny like that...

---

### Post by sethtriggs on 2009-01-30
This page 
[Samsung SCX-4500]("http://www.samsung.com/us/consumer/detail/support.do?group=printersmultifunction&type=printersmultifunction&subtype=monochromelasermultifunctionprintersfaxes&model_nm=SCX-4500&language=&cate_type=all&dType=D&mType=DR&vType=&prd_ia_cd=06010300&disp_nm=SCX-4500&model_cd=SCX-4500/XAA&menu=download") seems to indicate there's a Linux driver and application.

-Seth

---

### Post by soxs on 2009-01-30
Thx! Do you know if anybody had success using these?

---

### Post by sethtriggs on 2009-01-30
> **soxs said:**
> Thx! Do you know if anybody had success using these?

Nope, but I was interested in it as I was looking for an all-in-one that works fully with Linux for a change.

-Seth

---

### Post by jtreg on 2009-02-09
I got a problem unzipping these files. I get error while extracting files.

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by soxs on 2009-02-10
Same, here... someone (other than me ;-) should contact the support)

---

### Post by willburt on 2009-02-26
Hey,

Thought I'd post a reply here in case anyone else is having problems with the set up of the SC 4500W on Ubuntu.

After a lot of messing about I got it working.

The download on [http://www.samsung.com/us/consumer/detail/support.do?group=printersmultifunction&type=printersmultifunction&subtype=monochromelasermultifunctionprintersfaxes&model_nm=SCX-4500&language=&cate_type=all&dType=D&mType=DR&vType=&prd_ia_cd=06010300&disp_nm=SCX-4500&model_cd=SCX-4500/XAA&menu=download]("http://www.samsung.com/us/consumer/detail/support.do?group=printersmultifunction&type=printersmultifunction&subtype=monochromelasermultifunctionprintersfaxes&model_nm=SCX-4500&language=&cate_type=all&dType=D&mType=DR&vType=&prd_ia_cd=06010300&disp_nm=SCX-4500&model_cd=SCX-4500/XAA&menu=download") has been fixed now.

I tried installing from the supplied install.sh file but the Samsung GUI couldnt detect the printer on the network.

I finally got the printer working by adding a new printer in System->Administration->Printers and specifying the PDD from the Samsung download that's located at /cdroot/Linux/noarch/at_opt/share/ppd/scx4500w.ppd in the archive.

Hope this helps anyone who's having trouble.

Cheers.

---

### Post by soxs on 2009-02-26
If there was a thank you button, I would hit it right now...

---

### Post by Son of William on 2009-03-21
I would like to add to this thread:

I also own a SCX-4500 and attached it via USB cable to my Ubuntu box.  

The drivers at the [Samsung download site]("http://www.samsung.com/us/consumer/detail/support.do?group=printersmultifunction&type=printersmultifunction&subtype=monochromelasermultifunctionprintersfaxes&model_nm=SCX-4500&language=&cate_type=all&dType=D&mType=DR&vType=&prd_ia_cd=06010300&disp_nm=SCX-4500&model_cd=SCX-4500/XAA&menu=download") seem to work OK.

Just like Jtreg, however, I had trouble getting the smartpanel application to uncompress with the built in archive manager in Ubuntu.  I kept getting the "Child retunred status 2" error (whatever that is).

My solution was to download the file to my desktop and then manually uncompress and run the script as follows:

cd Desktop
tar -zxvf smartpanel-2.00.33.tar.gz
sudo ./cdroot/Linux/smartpanel/install.sh


That seemed to do the trick and everything seems to be working fine now.

---

### Post by curig on 2009-04-20
I have just got one of these and installed it with the drivers from the Samsung download site, as per the instructions there for the driver and Son of William's method for smartpanel. It's working fine.

---

### Post by n.lindberg on 2009-05-18
Hello there!

Thinking about buing a SCX4500 Printer for my home network.

Is it working well? Printing wireless, copying and scanning.

Everything will be wireless.

In openprinting.org the printer gets grade "working" and not "pefect". Just wondering of your experiences.

best regards

Niclas Lindberg

---

### Post by freek_zero on 2009-07-28
n.lindberg, this is not a wireless printer. USB only.

---

