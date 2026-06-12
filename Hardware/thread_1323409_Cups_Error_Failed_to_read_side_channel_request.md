---
title: "Cups Error: Failed to read side channel request"
date: 2009-11-11
forum: Hardware
---

### Post by slambrick on 2009-11-11
Cant print!
I have setup my Canon mp620 according to several posts as a network printer but when I try to print I get  "Processing - Failed to read side channel request"
The printer is unable to print even a test page.
I initially tried to get it to work by USB but this appears to have a similar result except that the print jobs appear to be sent with no result at all.

Any help would be appreciated.

---

### Post by ropieur on 2009-11-29
I encounter the same issue.
Hereafter the procedure I followed to install the printer.


[LIST=1]
[*]USB Install
[LIST]
[*]Add at the end of /etc/apt/sources.list:
[LIST]
[*]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main universe
[/LIST]
 
[*]sudo apt-get install libcupsys2
[*]sudo apt-get install ia32-lib
[*]sudo dpkg -i --force-architecture ./cnijfilter-common_3.00-1_i386.deb
[*] sudo dpkg -i --force-architecture ./cnijfilter-mp610series_2.80-1_i386.deb
[*]Extract ppdMP620-630en-1.5.tar.gz
[LIST]
[*] sudo cp canonmp620-630en.ppd /usr/share/ppd/
[*]sudo cp canonmp620-630en.ppd /usr/share/ppd/cups-included
[*]sudo mv /usr/lib/bjlib/cifmp610.conf{,.orig}
[*]sudo cp cifmp610.conf /usr/lib/bjlib/
[/LIST]
 
[*]sudo /etc/init.d/cups restart
[/LIST]
 
[*]Network install
[LIST]
[*]sudo apt-get install libcups2-dev
[*]download cups-bjnp ([http://sourceforge.net/projects/cups-bjnp/](http://sourceforge.net/projects/cups-bjnp/))
[*]Install cups-bnjp
[LIST]
[*] tar xvzf cups-bjnp-0.5.4.tar.gz
[*]cd cups-bjnp-0.5.4
[*]./configure --prefix=/usr
[*]make
[*]sudo -s
[*]make install
[/LIST]
 
[*]sudo /etc/init.d/cups restart
[*] firefox [http://localhost:631](http://localhost:631)
[LIST]
[*]In Adminstration, add printer
[*]MP620 appears in "Discovered Network Printers"
[*]... continue and follow instructions in the installation wizard
[*] In Printers, select the printer
[*]In Maintenance drop down list, select "Accept Jobs"
[*]In Maintenance drop down list, select "Resume Printer"
[/LIST]
 
[/LIST]
 
[/LIST]

---

### Post by Knockpaw on 2009-12-15
I fixed this by running 'ldconfig -v' as root after installing, then 'service cups restart'.

It may not be the solution to your problem; I'm using 32-bit Ubuntu, and I did have to install the Canon drivers using 'dpkg -x' instead of through the package management system - which would tend to leave out steps like ldconfig - but my symptoms were the same and that's what I did to resolve it. At the very least, it suggests that your problem may be a failure to correctly load a shared library.

---

### Post by dithsche on 2009-12-28
Hello,

I encountered same problems using an MP620, wireless with karmic 64Bit. But strangely I first succeded in installation and printing/scanning with my device.
Since somewhen in december it's not working anymore, and I get the same error message.
Even more strange: the printout of the test page is working. Printing from browser or office fails.

So my guess would be, that there was an update.
In another network I had the same problems with another mp620 printer.

Running 'ldconfig -v' as Knockpaw suggensted failed, but he already mentioned this could happen on 64 bit systems.

@ slambrick, ropieur - did you try to print a test page by cups? or even better did you find a solution?

thanks for any help

---

### Post by y@w on 2009-12-28
I ran into the same thing.. 9.10 x86 on a PIXMA MP620B.

I followed the steps above and ended up with the same error

I ended up finding this: [http://mp610.blogspot.com/2009/01/new-mp620-and-mp630-printers-ppds.html](http://mp610.blogspot.com/2009/01/new-mp620-and-mp630-printers-ppds.html)

I installed the PPD file linked in the article, but.. 

That didn't work, so I went and put the driver back to MP610 in the CUPS config and now it prints.. Magically? :)

The page that printed looks terrible, so I'm aligning the print heads to see if that helps.

So, to answer your question dithsche, not a clue on what I did that fixed it, but it seems like these steps get you in the right direction.

---

### Post by y@w on 2009-12-29
Yeah.. disregard that reply. It works sometimes when sending a test page. The page is stretched out and ugly when it comes out. Then, when I try to print from an application it throws that same message. I will be playing with it more tonight when I get home from work and will report back.

Turns out my new Christmas present is more like a headache :(

---

### Post by BigBananaMan on 2010-01-25
I've been trying since Christmas with the same results.  I've installed cups-bjnp-0.5.4 and the MP620-630 ppd file.  With the ppd file and through the method ropieur outlined I just ended up with "failed to read side channel request"
When I first tried with just cups-bjnp and the MP610 gutenprint 5.2.4 drivers I got the following.  y@w, I'm assuming this is what you got too.
> **y@w said:**
> The page is stretched out and ugly when it comes out. Then, when I try to print from an application it throws that same message. 
[IMG]http://img200.imageshack.us/img200/2005/img5784uk.jpg[/IMG][IMG]http://img200.imageshack.us/img200/1051/img5785f.jpg[/IMG]

I'm going to contact canon tech support to see if they happen to have any input but when I asked them how to get connected wirelessly I was told it is impossible without their crummy proprietary software.  About 20 minutes later an nmap scan revealed that there was an HTTP interface which just allowed me to enter the information.  Great job knowing your own printers Canon =D>
I guess if anything, being bothered and wasting money on Linux users might at least let them know we're out there.

---

### Post by ubuking on 2010-04-30
Anyone already succeeded to get MP620 up-and-running using 64-Bit Ubuntu? I have both printing and scanning working flawlessly on 3 computers running 32-Bit Ubuntu, but have not managed to get the job done on 64-Bit. 
I also have a Brother laserprinter, worked out-of-the-box on 64-Bit :(

---

### Post by ubuking on 2010-05-01
I have succeeded in installing my MP620 over WLAN and get it up-and-running without problems.
Please refer to [this post]("http://ubuntuforums.org/showpost.php?p=9208604&postcount=4") to see what I did.

---

### Post by dirtyhabanero on 2010-08-26
No luck yet. I'm another victim of the MP620 and have tried using the above mentioned method but to no success. There may be an installation error on my behalf but to my knowledge, the new cups 0.5.4 and the i386 drivers were installed correctly using --force-architecture; I too am on amd64. 

I think I'm ready for round two so I've reverted back to factory settings. There was something [here]("https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/246310") about changing the way the computer locates the printer (not sure if that's what changing lpd does) but I had no success.

---

### Post by BigBananaMan on 2010-12-17
I'm copy/pasting this to a couple places so please excuse any redundancies.

After getting fed up wasting time re-learning and screwing up setting up multiple computers, I was going to write an install script so I never have to spend an entire day re-learning the whole process again. Kevin Carter beat me to it and did a better job than I would have anyway. These are good for new users or just somebody that has to install to multiple systems or occasional reinstall. You can find the scripts [HERE]("http://bkintegration.com/2010/08/install-canon-mp620-on-ubuntu-linux-10-04/")

To make life even easier the proper .ppd file is [HERE]("http://sourceforge.net/project/showfiles.php?group_id=210977")

If you just bought the printer and are wondering how to get it to connect wirelessly (which Canon says is impossible and then suggested I buy Windows just to set up the kickbacks err printer. hmm...) You can connect it first to your router with a patch cable and check the IP through the printer interface. Then punch [http://printer](http://printer) ip here into your browser and set it up to use your wifi.

---

