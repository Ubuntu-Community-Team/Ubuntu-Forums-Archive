---
title: "Print DriverCanon TS9020"
date: 2017-11-20
forum: Hardware
---

### Post by jerrylaz on 2017-11-20
I have 4 printers.  Three are installed and working.  I just purchased a Canon TS9020.  It is not in the Network database for Ubuntu 16.04 LTS (my main OS)  It is there in Ubuntu 17.10 running on my test computer.  For what ever it is worth the entire printer module in Ubuntu 17.10 is a mess along with other problems.  I will be scared to upgrade my 16.04 LTS to 18.04 LTS next April.

**My main issue is how to use my new Canon Pixma TS9020 in Ubuntu 16.04 LTS..**

Also my Brother MFC8890DW scanner has never worked. And no driver for Wacom Intuos Pro.  Sourceforge is too confusing for me.  Ubuntu needs the equivalent of an .exe file to install these things.

---

### Post by howefield on 2017-11-20
Thread moved to the "*Hardware*" forum.

---

### Post by pdc on 2017-11-20
Hi jerrylaz; 

with release 17.04, Ubuntu provided Airprint support; so your TS9020 is compatible; [https://support.apple.com/en-nz/HT201311](https://support.apple.com/en-nz/HT201311) so the theory with airprint-support is the user does not need drivers; it seems it is auto-configured, and appears as "driverless" so with 17.10 I wonder if it says something like "TS9020-driverless"

with 16.04, before airprint arrived; one needs a driver from Canon; [https://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_ts_series/pixma-ts9040.aspx?type=drivers&driverdetailid=tcm:14-1533040&os=Linux%20(64-bit)&language=](https://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_ts_series/pixma-ts9040.aspx?type=drivers&driverdetailid=tcm:14-1533040&os=Linux%20(64-bit)&language=)

if you click to download and **SAVE** ....... you will get [COLOR="#0000FF"]cnijfilter2-5.40-1-deb.tar.gz[/COLOR]

If you open a terminal and copy the commands below and paste them line by line into the terminal 

```
cd Downloads
```
```
tar -zxvf cnijfilter2-5.40-1-deb.tar.gz
```
```
cd cnijfilter2-5.40-1-deb
```
```
sudo ./install.sh
```

and that should run the install script; so that should get it working on 16.04

_______

I think you have very sensibly done a test install of 17.10 to see how it looks; you say > For what ever it is worth the entire printer module in Ubuntu 17.10 is a mess along with other problems.; can you spell that out a little to help us understand more some of the issues please?

---

### Post by jerrylaz on 2017-11-21
It seems that printers install automatically.  When you issue "remove printer" it reappears.  I think this is associated with cups.  Let me give you a specific example regarding my Canon IP8720 (same issue with Deskjet 2549).  I will compare the problem with Ubuntu 16.04 LTS with Ubuntu 17.10.  I am glad you are interested.  If you have questions I will answer you.

Here is just one thing I want to do.  I print photographs.  I edit them and then crop to a 3:2 aspect ratio.  That allows me to use any multiple of 3:2 with no further editing.  (example: 3:2 equates to 4x6, 6x9, 12x8, 18x12)  I print mostly with Gimp.  I set my image and print size.  Here comes the (not so fun)

Object I want to print a 4x6.  Printer default is Letter

**Using Ubuntu 16.04**

Under the photo paper size the drop down allows me to select 4x6 plus other selections like margins, borderless etc.
It all works just fine.


[B]
Using 17.10[/B]

Using the same drop down as above I see the default "Letter"  I select 4x6.  It does not change from Letter.  Some times I can select some oddball sizes and other times I can't.

There are other issues with Gimp but that is another subject.

I would like to be able to document other anomalies  like hitting the drop down to chage pixels to inches but it is hard to see dark gray text on a black background.  I wish I could docuent all this stuff and send it to someone at Ubuntu.  This was my job for 30 years working with all the software vendors.  I would like to ake a contributions but the process is too difficult.

Thanks for your help.

---

### Post by jerrylaz on 2017-11-22
This is a copy of what I have previously posted when I said the print module in 17.10 what I call a mess.  It indiscriminately does not allow you to make selections in paper size and other option.  It will not allow you to permanently remove a network printer.  It puts it back.  The bottom line is I do not have this issues with 16.04 using the same printers and printing the same photos with the same applications.  I will try your suggestions after I recover from Thanksgiving.

THIS IS WHAT I POSTED.  i NEED TO GET USED TO THE FORUM AGAIN SINCE I HAVE NOT USED IT FOR MANY YEARS.

It seems that printers install automatically.  When you issue "remove  printer" it reappears.  I think this is associated with cups.  Let me  give you a specific example regarding my Canon IP8720 (same issue with  Deskjet 2549).  I will compare the problem with Ubuntu 16.04 LTS with  Ubuntu 17.10.  I am glad you are interested.  If you have questions I  will answer you.

Here is just one thing I want to do.  I print photographs.  I edit them  and then crop to a 3:2 aspect ratio.  That allows me to use any multiple  of 3:2 with no further editing.  (example: 3:2 equates to 4x6, 6x9,  12x8, 18x12)  I print mostly with Gimp.  I set my image and print size.   Here comes the (not so fun)

Object I want to print a 4x6.  Printer default is Letter

**Using Ubuntu 16.04**

Under the photo paper size the drop down allows me to select 4x6 plus other selections like margins, borderless etc.
It all works just fine.


[B]
Using 17.10[/B]

Using the same drop down as above I see the default "Letter"  I select  4x6.  It does not change from Letter.  Some times I can select some  oddball sizes and other times I can't.

There are other issues with Gimp but that is another subject.

I would like to be able to document other anomalies  like hitting the  drop down to chage pixels to inches but it is hard to see dark gray text  on a black background.  I wish I could docuent all this stuff and send  it to someone at Ubuntu.  This was my job for 30 years working with all  the software vendors.  I would like to ake a contributions but the  process is too difficult.

Thanks for your help.

---

### Post by pdc on 2017-11-23
I feel the valuable information you are reporting should be reported to Ubuntu as a bug;

---

### Post by jerrylaz on 2017-11-24
I would be happy to make any contribution I can.  Could you tell me specifically how to do this?

Thanks in advance.

---

### Post by pdc on 2017-11-24
thanks Jerry; I don't have the info to hand: if you google on the topic of filing bug reports

---

