---
title: "INIC-162x SATA Drivers
INIC-162x SATA (1620/1622/1623) Install on Ubuntu Help!!!!"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by ukraine1988 on 2008-04-10
Hello everyone,

I am new to these forums, but I have been using Ubuntu for a while. So now I have a big dilemma. Since i have been using Ubuntu on my laptop for a few weeks now I have decided to upgrade my server too. So my setup is as follows: IBM eServer xSeries 220 with dual P3 @ 1.1GHz +2GB RAM. I have 160 GB IDE HDD that holds my Ubuntu install. I did not want to use the on board SCSI adapter so I bought and installed a Initio SATA controller card with 2 300 GB Seagate HDDs.  The SATA controller model is as follows: INIC-162x SATA (1620/1622/1623), I believe my is 1620. So I have installed the server Dapper and then decided to go with the xubuntu-desktop on top due to my Linux inexperience. I have found the drivers here: [http://www.initio.com/support/index-download.htm](http://www.initio.com/support/index-download.htm)
However I do not know what to do with the files or any clue as to how to approach this. I am trying to understand but I am having a hard time. Please help me. 

Thank You very much ahead of time for your help.

---

### Post by bobhenz on 2008-04-12
There is a readme.txt inside of the zip that has these instructions that should get you started.

> 
Download  linux-2.6.15.tar.gz (you did this)
copy it to /usr/src/ (in ubuntu this means "sudo cp linux-2.6.15.tar.gz /usr/src/")

use root to do the following command (means preface the following command with "sudo ")
tar zxvf linux-2.6.15.tar.gz


Now I think you can...
cd /usr/src/linux-2.6.15

Then look for the readme.txt file and continue with t their instructions.

---

### Post by ukraine1988 on 2008-04-16
Oh Ok, now I see it. Thanks for pointing that out. I will post back after I try it.

---

### Post by ukraine1988 on 2008-04-18
Well I tried my best to follow the instructions, but I get errors and it wont compile. I dono what I did but I have to reinstall the OS now. I locks up and is acting very weird. I will keep trying tho and see what I can get done.

---

