---
title: "Missing print filter"
date: 2017-08-07
forum: Hardware
---

### Post by Cariboo1938 on 2017-08-07
I run ubuntu 16.04 LTS and have a HP-Photosmart D7100priner connected. For some time now I cannot print anymore.
The error message is: "There is a  missing print filter for printer 'Photosmart-D7100-series'" 
The printer works well with 
Linux Mint 'Sarah', Knoppix 7.xx and Windows 10.
Where can I get the ,missing filter?

---

### Post by gsahli on 2017-08-08
Read this:
[http://hplipopensource.com/node/306](http://hplipopensource.com/node/306)

---

### Post by Cariboo1938 on 2017-08-08
I followed the instructions in the link but, although installation was successful it didn't work.
Error when configuring the printer:
error: No PPD found for model photosmart_d7100 using old algorithm.
error: No appropriate print PPD file found for model photosmart_d7100_series

---

### Post by gsahli on 2017-08-09
I wonder why the printer name shows Photosmart D_7100_2.
I looked here and don't see your model listed as supported. Maybe try selecting d7150 series instead?
[http://hplipopensource.com/hplip-web/supported_devices/photosmart.html](http://hplipopensource.com/hplip-web/supported_devices/photosmart.html)

---

### Post by Cariboo1938 on 2017-08-09
I wondered myself when I saw the error message: " ....for model photosmart_d7100_series" , because my printer is a model D7160.
When I want to add this (D7160) printer the system recognized it the second time also as D7100 series.
A Recovery boot from an earlier kernel didn't help.
I ran 16.04 LTS from Live DVD and all was OK. 
So, it might be that some of the frequent updates did alter something.
I'm going to do a new install from DVD..
.

---

### Post by Cariboo1938 on 2017-08-09
More info:

it looks like 'hp-setup' does not recognize my HP D7160 series printer.
I tried ubuntu "Printers", which want to connect to CUPS server: localhost
but got the meswsage: failed to connect to server

---

### Post by gsahli on 2017-08-09
I don't have an HP, so that's all I can do for you.

---

### Post by gsahli on 2017-08-10
Regarding the cups localhost web page:
[http://hplipopensource.com/node/231](http://hplipopensource.com/node/231)

And, you may just need to add your user to the lpadmin group.

---

### Post by Cariboo1938 on 2017-08-11
No success with this either...I'm not educated enough to find out what is corrupted... 
Thanks for your help...
Going to do a new system install from DVD!

CASE CLOSED

---

