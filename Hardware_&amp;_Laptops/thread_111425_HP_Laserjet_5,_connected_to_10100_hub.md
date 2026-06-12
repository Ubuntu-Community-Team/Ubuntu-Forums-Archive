---
title: "HP Laserjet 5, connected to 10/100 hub?"
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by handy on 2006-01-02
I have the Laserjet 5, printer on my wifes computer in another room, the printer has a nic built in.
  
If I connect the Laserjet with cat5 to my "hp procurve switch 2124", can anyone tell me the procedure to set up Ubuntu to be able to use it on the LAN?

If there is a Wiki, Sticky or another post that I could be pointed to? That would be great.  

If there is not, & someone can take the time to explain the steps?  THAT would certainly be even greaterer!:p 

Thanks in advance, I have an inkling that ink & toner can be hard to waste in Ubuntu, time will tell as usual... :rolleyes: 

handy

---

### Post by handy on 2006-01-02
I just found this info', I must admit that it is a little confusing, too much information at this time of the morning I think!

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_5](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_5)

If someone has a LJ-5 functioning on Ubuntu, it would be nice to hear about it?

I guess I'll just have to cable it up later today, (after a sleep ;) ) & see what happens, more specific questions then I expect.  :confused: 

Cheers,

handy

---

### Post by handy on 2006-01-03
Printing is not a popular topic I'm finding.  :rolleyes:

---

### Post by tim15856 on 2006-01-03
I believe this is what you need to do (I'm at work and can't step through exactly). Select Administartion/printer. Select 'add printer'. You need to know the IP address of the printer and it has to be in the same subnet that your computer is on. Select 'network printer'. For port, try HP jetdirect. The host should be the IP address, port should be the default 9100. If that doesn't work, try the Unix (LPD) port, host will be the IP address, you'll need to know what the queue name is. My brother laser printer uses the LPD port. Two printers on another print server use the HP Jetdirect port. If you can't set the IP address to what you need it to be or otherwise need to configure the printer, you might try the Jetadmin software on a Windows system just to get it configured. [http://h10010.www1.hp.com/wwpc/pscmisc/vac/us/en/en/network_software/wja_overview.html](http://h10010.www1.hp.com/wwpc/pscmisc/vac/us/en/en/network_software/wja_overview.html)

---

### Post by handy on 2006-01-04
Thanks for your reply Tim, 

I was starting to think that no one wanted to know about this one.

I will put more cable between the 2 rooms NOW, time to knock this one over. ;) 

I think I have control of both the IP address & the subnet mask through the onboard printer control panel.

Thanks again.

handy

---

### Post by handy on 2006-01-04
Well I've layed, terminated & conected a cable between the HP LJ 5, & the network switch.  That was the easy part...  ;) 

I've downloaded the driver **HPIJS-2.1.4**  Following the very thorough step by step instructions on the hp site.  Going all too smoothly until I got the following:

=====================
handy@BirdFish:~/downloads/hpijs-2.1.4$ ./configure --prefix=/usr checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for a BSD-compatible install... /usr/bin/install -c
checking for jpeg_set_defaults in -ljpeg... no
configure: error: "cannot find libjpeg support"
handy@BirdFish:~/downloads/hpijs-2.1.4$ make make: *** No targets specified and no makefile fou nd.  Stop.
handy@BirdFish:~/downloads/hpijs-2.1.4$
======================

This being the offending part:

[B]checking for jpeg_set_defaults in -ljpeg... no
configure: error: "cannot find libjpeg support"[/B]

There is no **libjpeg** in synaptic,  there is libjpeg62  ??

I thought I'd try my luck with **make**  no go.

Any Ideas anyone?

Thanks in advance.

handy

---

### Post by tim15856 on 2006-01-04
Well, if you followed what I said before and selected the proper port to use, the next step is to select the printer driver which is built into Ubuntu. Just select HP as the manufacturer at step 2 and Laserjet 5 as the model.

---

### Post by dragonfyre13 on 2006-01-04
Grab Libjpeg62-dev. It doesn't work with just libjpeg62, but it compiles fine if you have the dev files.

---

### Post by handy on 2006-01-04
[QUOTE=tim15856]Well, if you followed what I said before and selected the proper port to use, the next step is to select the printer driver which is built into Ubuntu. Just select HP as the manufacturer at step 2 and Laserjet 5 as the model.[/QUOTE]

Ahh! Tim, I won't go into all the details, (as is natural to me  :rolleyes: )

When I got to the **JetDirect** part of your most helpful instructions, the default port was set to 9100, great!  

**Install driver?**   Here was MY problem - I missed the fact that the driver listing was a drop-down menu,   :confused: duh!:confused:

So, after seeing your note this morning, I looked a teeny bit harder, after which it took about 1 minute before I was looking at the Ubuntu test page!!  :KS 

I valuable lesson in more ways than one.

I'm a happy boy,

Thanks Tim,

handy

---

### Post by handy on 2006-01-04
By the way, thanks also for the link to HP's Jetadmin download,  (I didn't like the registration bit though).

Using the Jetadmin software I was able to upgrade the firmware on the printer, & setup the LJ-5 on my wifes xp pro' box.

Since then, I've got her Powerbook printing on the LAN & she now also has access to broadband via the notebook too.  (I put 2 cables  through last night).

So, next time I'm forced to boot into xp myself, I'll setup the LJ-5 & that's it!

I print very little, but it's easy to see the advantage with Ubuntu, sometimes it's nice to have printed the required detailed instructions for this or that procedure.

It's all good, thanks again.

handy

---

### Post by tim15856 on 2006-01-05
Being a newbie Linux user myself, I'm glad when I can help someone else. Glad to see you got everything working :KS

---

### Post by handy on 2006-01-05
It's good for the soul to see a system like the Ubuntu forums, running so well, on pure good will!

How else **could** it run?

handy

---

### Post by handy on 2006-01-05
I've incorporated your help only slightly modified into my hardware compatibility post, I'm sure you don't mind.

It's here if you care to look:

[http://ubuntuforums.org/showthread.php?t=88639&page=2](http://ubuntuforums.org/showthread.php?t=88639&page=2)

Cheers,

handy

---

