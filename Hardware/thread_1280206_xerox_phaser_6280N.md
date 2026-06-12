---
title: "xerox phaser 6280N"
date: 2009-10-01
forum: Hardware
---

### Post by DouglasAdams on 2009-10-01
hi,
i'm trying to install a xerox phaser 6280N printer but the nearest the installation process gets is a model 6250N (which may or may not be similar).
how do i get the model 6280N added to the list of drivers that the installation process "sees" please?

p.s.
noobie so any reply needs to be a kindergarten level please.

p.p.s.
i have tried to install this printer in 5 or 6 other distro's (inc head rat and mandrax) - ubuntu gets FAR closer to it working than any other distro!

---

### Post by BraedenNaylor on 2009-10-01
I went to xerox and onto drivers....

[http://www.support.xerox.com/go/results.asp?Xlang=en_GB&XCntry=GBR&prodID=6280&ripId=&Xtype=download](http://www.support.xerox.com/go/results.asp?Xlang=en_GB&XCntry=GBR&prodID=6280&ripId=&Xtype=download)


Direct link to the driver.
[http://www.support.xerox.com/go/getfile.asp?Xlang=en_GB&XCntry=GBR&objid=75240&EULA=0&prodID=6280&Family=Phaser&ripId=&langs=English&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_GB&XCntry=GBR&objid=75240&EULA=0&prodID=6280&Family=Phaser&ripId=&langs=English&plats=Linux&Xtype=download&uType=)

Hope that helps.

---

### Post by cariboo on 2009-10-01
The 6280N is not in the [OpenPrinting Database]("http:///www.openprinting.org/printer_list.cgi?make=Xerox"), if you do get it working you may want to add your experiences to the database.

---

### Post by DouglasAdams on 2009-10-02
> **BraedenNaylor said:**
> I went to xerox and onto drivers....

Direct link to the driver.
[http://www.support.xerox.com/go/getfile.asp?Xlang=en_GB&XCntry=GBR&objid=75240&EULA=0&prodID=6280&Family=Phaser&ripId=&langs=English&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_GB&XCntry=GBR&objid=75240&EULA=0&prodID=6280&Family=Phaser&ripId=&langs=English&plats=Linux&Xtype=download&uType=)



cheers, i did find that driver already ... and download it.
however,
during the add printer procedure i could not figure out how to direct it to the driver i had downloaded in ubuntu. i did mange this with other distro's but they then failed with a long and complex message that i simply didn't understand. from memory, it seemed to be some sort of script error.

---

### Post by DouglasAdams on 2009-10-02
> **cariboo907 said:**
> The 6280N is not in the [OpenPrinting Database]("http:///www.openprinting.org/printer_list.cgi?make=Xerox"), if you do get it working you may want to add your experiences to the database.

if i did it would be a miracle ...
not too sure i'm up to documenting miracles
:)

---

### Post by halitech on 2009-10-28
seems the download file is an rpm. Did you convert it with Alien before you tried to install it? Not sure it will work but you could try the PPD file for the 6180, not sure how much the same they are but they look the same.

---

### Post by DouglasAdams on 2010-09-08
it has just been pointed out to me, yeah, i missed the hint, that i really should have shared my experiences.
sorry but this all happened a while ago and i have slept since then.

to the best of my recollection:

at first i simply used the 6180 driver and i don't remember having any problems.

however, earlier this year i guess i must have clicked on the rpm file that was contained inside the file i had downloaded from the Xerox site: 6280_Linux.tar
i.e.
Xerox-Phaser-6280-1.0-1.noarch.rpm

then i must have just kept clicking, and clicking, and clicking.  eventually there are the gzipped ppd files for the three Phaser 6280 models: DN, DT & N

sorry i didn't post this before i tagged it as solved.


Linux user #519546  Id #424242  Ubuntu user #31963

---

### Post by KirbySmith on 2010-09-08
Thanks!!

---

### Post by DouglasAdams on 2010-09-09
> **KirbySmith said:**
> Thanks!!

not at all. my oversight.
it's just that it's hard to think of myself as a person who's "solved" owt on Linux m8.

---

### Post by virtualXTC on 2012-09-04
Using the openprinting postscript-Xerox 20090512 driver causes the printer to crash and request a restart when printing PDF files.

Because of this I'd reccomend trying the manufactuer's drivers.

---

### Post by overdrank on 2012-09-04
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

