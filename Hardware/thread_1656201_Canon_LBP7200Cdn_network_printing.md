---
title: "Canon LBP7200Cdn network printing"
date: 2010-12-30
forum: Hardware
---

### Post by alan404 on 2010-12-30
I have set up this printer successfully on a laptop running Ubuntu 10.10 via USB. I used the instructions here
[URL="https://help.ubuntu.com/community/CanonCaptDrv190"]
https://help.ubuntu.com/community/CanonCaptDrv190[/URL]

However, my next task is to get this working on a desktop computer, via the network (the printer has an integrated network card). This hasn't been as successful. It seems to be installed correctly, but it isn't printing. I've tried everything on the page linked to above.
I went to System - Admin - printing and I had to change the location of the printer here as the install had assumed local. I clicked on Change and search network and the Canon was found. Now in this printing panel it appears as

socket://192.168.1.69:9100

When I try to print a test page here it says Idle - print file sent, waiting for printer to finish
I never does finish.
In the cups panel at [http://localhost:631](http://localhost:631) It reports
"Unable to write print data: broken pipe"

However if I start the Canon status monitor. It correctly reports the number of pages printed - and it says it is in sleep mode. So it is connected somehow, it just isn't sending data to it.

Where do I go next? Are there any logs I could look at? 

Thanks for any help however small.

Alan

---

### Post by EmpIzza on 2011-06-22
Hms, I have the exact same problem. Did you manage to solve it?

---

### Post by alan404 on 2011-06-22
Hello Empizza,

Yes I did - and like a lot of things in Linux, it was tricky to get going but once I did it has worked reliably without fail ever since. My problem was I was trying to alter the printer in System - Admin _Printing, rather than carefully going through all the command line commands in the Wiki. After I got it working I edited the Wiki page [HTML]https://help.ubuntu.com/community/CanonCaptDrv190[/HTML], but things seemed to have moved on a lot since then and now there is a ppa package. So I suggest you follow that page to the letter. My problem showed up by looking at this command.

```
sudo /etc/init.d/ccpd status
``` and I only had one number at the end instead of two. You need two numbers here, then it will work.


Also this is another useful page

[HTML]http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/[/HTML]If you are configuring a network printer, you may need to alter some of those commands in the Wiki - read the install instructions here
[HTML]
http://support-asia.canon-asia.com/contents/ASIA/EN/0900772407.html[/HTML] and compare with the Wiki page. As far as I remember - system - admin - printing send to ccp/Cups (not the network) and Cups is setup to resend it to the network - you don't actually see the network address in "printing" when it's working. My device URI says ccp://localhost:59687

Hope this helps, and modify the Wiki page for others when you get it going.
Alan

---

