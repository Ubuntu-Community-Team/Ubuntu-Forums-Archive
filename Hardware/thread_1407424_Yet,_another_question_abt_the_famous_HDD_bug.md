---
title: "Yet, another question abt the famous HDD bug"
date: 2010-02-15
forum: Hardware
---

### Post by Askalton on 2010-02-15
First of all i'd like to appologize if my question doesnt belong tot his forum, as it is related with Kubuntu and not Ubuntu :) But since they are almost the same, i thought this could be the right place.

Im running Kubuntu 9.10 (the regular version and not the netbook remix) on my EEE 1002HA without any problems, but id like to know how i can monitor and sort out (if it exists) the load cycles problem of my HDD. Ive tried many ways i found on the net but tbh i couldnt get them to work :/ maybe im a bit too noob on (K)Ubuntu!

Also, if someone could tell me how to do it on Ubuntu as well id be thankful :) (as i usually change between Ubuntu and Kubuntu every few months =p)

Ty in advance :)

---

### Post by benargo on 2010-02-15
Well, my first suggestion would be to take any feathers out of it... God knows how many you have in there! :D

*[SIZE="1"](Please ignore this comment, it is a personal joke between myself and Askalton)[/SIZE]*

Personally, this might be an issue with your particular hard disk model. Is there any chance you could include the complete hard disk details and I will scout around a little bit for you. :)

~Ben (aka Fluffy)

---

### Post by Askalton on 2010-02-15
for the matter, the HDD is this one:

[http://www.seagate.com/ww/v/index.jsp?vgnextoid=af8d58a3fd20a110VgnVCM100000f5ee0a0aRCRD&locale=en-US](http://www.seagate.com/ww/v/index.jsp?vgnextoid=af8d58a3fd20a110VgnVCM100000f5ee0a0aRCRD&locale=en-US)

thanks for the reply =p

---

### Post by benargo on 2010-02-15
Here, did a bit of scouting around and from what you told me on MSN as well as what you said here I've devised this solution.

There is a similar issue which exists for Macintosh computers, where the hard disk spins too fast and causes it to degrade. For Mac OS X there is a solution which I use called SMCFanControl, which monitors the fans and the speed at which the fans, hard drives and optical drives spin at. Following on from that idea I ran into this piece of software available for Linux and Windows...

> **hdparm** is a command line utility for the [Linux]("http://en.wikipedia.org/wiki/Linux") and [Windows]("http://en.wikipedia.org/wiki/Microsoft_Windows") operating systems to set and view [SATA]("http://en.wikipedia.org/wiki/Serial_ATA")  and [IDE]("http://en.wikipedia.org/wiki/Integrated_Drive_Electronics") [hard disk]("http://en.wikipedia.org/wiki/Hard_disk") hardware parameters. It can set  parameters such as drive caches, sleep mode, power management, acoustic  management, and [DMA]("http://en.wikipedia.org/wiki/Direct_memory_access") settings.

*(Quoted from [http://en.wikipedia.org/wiki/Hdparm](http://en.wikipedia.org/wiki/Hdparm))*

The original article which led me to this piece of software was from a website designed for Debian, but this also applies to Ubuntu and its variations. The particular article includes relatively clear instructions on how to execute the program. Being Linux, you will have to run it through the terminal.

You can find the article here: [http://www.debianadmin.com/tune-your-hard-disk-for-high-performance-using-hdparm.html](http://www.debianadmin.com/tune-your-hard-disk-for-high-performance-using-hdparm.html)

If you wish to try out HDparm you can download it from Sourceforge: [http://sourceforge.net/projects/hdparm/](http://sourceforge.net/projects/hdparm/)

I hope this helps. :)

~Ben

---

