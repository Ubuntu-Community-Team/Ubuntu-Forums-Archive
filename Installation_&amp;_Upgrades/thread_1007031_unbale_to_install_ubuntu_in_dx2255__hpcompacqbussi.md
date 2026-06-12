---
title: "unbale to install ubuntu in dx2255  hpcompacqbussinesspc"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by ramvik on 2008-12-10
Hi my pleasure to join with ubuntu
well, I have a desktop pc model HP compaq bussiness pc dx2255
the below is url to connect and see more about 

[http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=in&prodTypeId=12454&prodSeriesId=3328436&lang=en&cc=in](http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=in&prodTypeId=12454&prodSeriesId=3328436&lang=en&cc=in)

I am not able to install most latest ubuntu in this particular model,The following eroors i am getting while installing

Loading Please wait...
 
 
Busy Box v1.10.2
(ununtu 1:1:10.2.-1 ubuntu6)
built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
[72.7522013] ata:1 srst faild (error no:-16)
This id (id 10ec:8139 vev 10) is not an 8139 c+ comaptiable chip
(149.012847] 8139 cp
0000:04:06:0: Try the "8139 too" driver  in stead.

please letme know how do work out this

ramvik

---

### Post by DieB on 2008-12-10
at the boot menu press F6 (i guess it was F6 but it should be named "more options" u should after that see the end of a long commandline add here the following

> all_geneirc_ide

 and hit enter.

this was a solution i found here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223187](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223187)
at the bottom of post

---

### Post by ramvik on 2008-12-11
Hi buddy

I am working on it thanks for the reply
thanks a lot
ramvik.

---

### Post by ramvik on 2008-12-11
Hi buddy 

Here is what i got after working out

all_generic_ide

Well This time i am getting struck at splash screen.

The splash screen become blurr and installatio stop there.

So I tryed options like
linux all_generic_ide noapic nolapic

still no result

Please help me out how to solve the above 

Thanks once again
ramvik.

---

