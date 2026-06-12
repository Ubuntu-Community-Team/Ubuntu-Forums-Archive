---
title: "Canon Pixma MP210 Linux Drivers"
date: 2011-03-07
forum: Hardware
---

### Post by Dipper on 2011-03-07
A while back there was a [thread explaining how to set up the Canon MP210 printer](http://ubuntuforums.org/showthread.php?t=556980).  The links to the download sites in Australia and Asia are now dead.  Here is a link to my own archive of the necessary files:

[http://www.sattech.us/forums/index.php?topic=13858.msg78567](http://www.sattech.us/forums/index.php?topic=13858.msg78567)

---

### Post by Kolitar on 2011-03-07
There is also a great site that explains how to set up a canon pixma 250. [http://ubuntica.com/pixma-mp250-on-ubuntu.html](http://ubuntica.com/pixma-mp250-on-ubuntu.html)

Maybe it'll also be useful for the MP210. I have an MP250 printer/scanner, I installed the printer drivers with the method on the page and it works perfectly! I haven't tried out the scanner part yet, though.

---

### Post by bartman2589 on 2011-07-12
> **Dipper said:**
> A while back there was a [thread explaining how to set up the Canon MP210 printer]("http://ubuntuforums.org/showthread.php?t=556980").  The links to the download sites in Australia and Asia are now dead.  Here is a link to my own archive of the necessary files:

[http://www.sattech.us/forums/index.php?topic=13858.msg78567](http://www.sattech.us/forums/index.php?topic=13858.msg78567)


Thank you for supplying these, I had just picked up a used MP210 this morning for $10 and was kind of disappointed when I got home and found out that the US Canon site had absolutely no mention of linux support, and then when I found the drivers on the Australian site I was further disappointed because of the annoying problem with the libcupsys2 dependency.  I was delighted to find that the drivers you had on your site have this problem fixed!  Thank you!  Now if only there was a fix for the fact that the Canon drivers limit the scan resolution to 1200dpi in Linux (I read on the Canon US site that the scanning portion of this printer is actually capable of 4800dpi resolution).

---

### Post by Anglagard on 2011-08-25
Hello,

An update to this thread since it was on the top of my google search...
I'm using Ubuntu 64bit 11.04 didn't try to install the official Canon drivers because I didn't see a compiled 64bit version.

I got MP210 to work by selecting MP180 driver on "new printer detected" wizard that pops up after connecting the printer the first time. (tip from fatfool user at [http://ubuntuforums.org/showpost.php?p=5363765&postcount=37](http://ubuntuforums.org/showpost.php?p=5363765&postcount=37))

The scanner works out of the box with xsane and simple scan.
simple scan has options for 2400 dpi but I'm not sure if its accurate. I just did a quick test scan and it looks ok.

---

### Post by Refon_oSu on 2011-09-15
> **Dipper said:**
> A while back there was a [thread explaining how to set up the Canon MP210 printer]("http://ubuntuforums.org/showthread.php?t=556980").  The links to the download sites in Australia and Asia are now dead.  Here is a link to my own archive of the necessary files:
[URL="http://www.sattech.us/forums/index.php?topic=13858.msg78567"]
[/URL][http://www.sattech.us/forums/index.p...13858.msg78567]("http://www.sattech.us/forums/index.php?topic=13858.msg78567")

Hmm... I looked through the thread but found nothing for 10.04 LTS. 
I have that infamous libcupsys2 installation error. I thought that I could find something on Sattech, but it requires registration and I can't register, forum shows that I'm banned!
> Sorry Guest, you are banned from using this forum!
This ban is not set to expire.
How could I make that thing work?

---

### Post by demonipuch on 2011-09-15
Hello Refon_oSu

Try this :

```
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-common cnijfilter-mp210series
```

---

### Post by gearond on 2011-12-26
Thank you, Thank you,Thank you. The repository for the drivers worked great and I was printing in less than 60 seconds. (got 12mbit uverse). Truly appreciate putting the link up for us all.:)

---

### Post by tnicewicz on 2012-02-06
This worked for me as well, THANK YOU!

---

