---
title: "Canon Pixma MG2120"
date: 2012-10-04
forum: Hardware
---

### Post by recycledhippy on 2012-10-04
I just purchased a Canon Pixma mg2120 printer and I cant get it to work. It will print with black ink only. Ive tried to find drivers but havent had any luck. My version of ubuntu is 12.04. any help would be great!!! thanks

---

### Post by GeForce 9500GT on 2012-10-04
Check this site for the correct Canon drivers: [https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers](https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers).
 
Canon is not fully supported by Linux out-of-the-box, but Canon does make Linux drivers. This driver you need to install to get your Canon hardware working.

---

### Post by BicyclerBoy on 2012-10-04
You can get the open source canon drivers (for some printers) from a ppa..

[https://launchpad.net/~michael-gruz/+archive/canon-trunk?field.series_filter=precise](https://launchpad.net/~michael-gruz/+archive/canon-trunk?field.series_filter=precise)

---

### Post by recycledhippy on 2012-10-04
Thanks for the responses. GeForce I tried your suggestions and nothing was able to help me. Bicyclerboy, ill have to try that out later when I get home. Its odd it prints black but no color. Thanks guys. Anyone else have any thoughts please let me hear them.

---

### Post by GeForce 9500GT on 2012-10-05
**@recycledhippy**
 
At the bottom you see the same ppa. Follow the insrtructions given on that webpage i gave you. It should work!

---

### Post by pdc on 2012-10-05
and if adding the ppa doesn't work for you;

you go to the Canon Asia website; 

and download the debian package that Canon provide for the MG2120

[COLOR="Red"]MG2100 series IJ Printer Driver Ver. 3.60 for Linux[/COLOR] ([COLOR="Green"]debian Packagearchive[/COLOR])

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100392602.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100392602.html)

**_Keep the printer turned off_**

it comes down as a .tar.gz file

[COLOR="DeepSkyBlue"]cnijfilter-mg2100series-3.60-1-deb.tar.gz[/COLOR]

.....open a terminal..........

the commands that you can copy and paste into the terminal are

> cd Downloads....hit enter key (after each pasted command)

> tar  -zxvf cnijfilter-mg2100series-3.60-1-deb.tar.gz

> cd cnijfilter-mg2100series-3.60-1-deb

> ./install.sh

.........the programme will interact with you; ask you to turn printer on;

I installed one of these a month ago; it went very smoothly

_________________________________________________________________

for running the scanner, you need

[COLOR="Red"]MG2100 series ScanGear MP Ver. 1.80 for Linux[/COLOR] ([COLOR="SeaGreen"]debian Packagearchive[/COLOR])

from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100392902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100392902.html)

it comes also as a .tar.gz file

[COLOR="DeepSkyBlue"]scangearmp-mg2100series-1.80-1-deb.tar.gz[/COLOR]

I would suggest having done the above you issue the following commands

> cd

> cd Downloads

> tar  -zxvf scangearmp-mg2100series-1.80-1-deb.tar.gz

> cd scangearmp-mg2100series-1.80-1-deb

> ./install.sh

............once installed issue the command

> scangearmp and the programme opens......

.....let us know how it all goes......

---

### Post by recycledhippy on 2012-10-05
ive tried thee ppa but when i do an update for it I get a 404 problem and it dosent work.

---

### Post by recycledhippy on 2012-10-05
PDC Thank you!!! that all seems to have worked! test page printed color an the scanning works also! Thank you so much everyone!

---

### Post by pdc on 2012-10-05
hi recycledhippy;

delighted to hear all is good

great that it is working for you: enjoy ! :p

______________________________________________________


instead of typing 

> scangearmp 

.......into a terminal each time, you can automate the process by creating a launcher.....that launches scangear

from this thread

[http://ubuntuforums.org/showthread.php?t=1582497&page=9&highlight=canon](http://ubuntuforums.org/showthread.php?t=1582497&page=9&highlight=canon)

see post # 85

and this thread

[http://linuxhelp.host.org/index.php?page=news&type=view&id=linux-help_2%2Fhow-to-create-desktop](http://linuxhelp.host.org/index.php?page=news&type=view&id=linux-help_2%2Fhow-to-create-desktop)

that tells you how to create a launcher in Ubuntu 12.04

---

### Post by sean neilan on 2013-03-10
recycledhippy, I used the commands for the canon mg2120 and they worked perfectly but with the scanner I don't know where my laptop put the practice page that I did. I use Ubuntu10.04 so if you can help me find it that would be great, also the community keeps on telling that I should upgrade to the newest version of Ubuntu like 12.04 or12.10 so I want to ask you should I? I'm completely happy with 10.04 I'm not that much of a computer geek I use it to surf the net and to write papers so is it necessary to upgrade if I'm happy and the fact that conical will still support it even though the community won't , am I correct with my logic? Oh and thank you so much for the help with my printer!!!

---

### Post by pdc on 2013-03-10
Hi Sean; I think it was me helping recycledhippy: .......if you are happy where you are, use the computer to get more fluent; ........as we say..........linux is for adults........... 

you say scangearmp worked well for you; 

........but ..........

> but with the scanner I don't know where my laptop put the practice page that I did.

I enclose a thumbnail of what happens when I go to run scangearmp on my computer

........it insists I tell it what folder I want it to be saved in.........so if you have forgotten that.............. if you use the SEARCH function in your list of programmes and search on what you might have called the file.............

........ would that be an Eire name by any chance? The reason I ask is many places have LUGs........Linux User Groups..............packed full of friendly, helpful........abeit slightly obsessional..........linux enthusiasts........if you go along to one of those, you would get help if........at some stage.....you wanted to add a new version of ubuntu......

see here

[http://www.linux.ie/articles/inthenews/essentialguidetoilug.php?style=printer](http://www.linux.ie/articles/inthenews/essentialguidetoilug.php?style=printer)

good luck

---

### Post by sean neilan on 2014-01-31
It did work for the printing but not the scanner? I thank you for the instructions.

---

### Post by sean neilan on 2014-01-31
Thanks for the info I have tried to find groups here in Orange County Cali but I get directed to the San Francisco area and not here in southern ca.

---

