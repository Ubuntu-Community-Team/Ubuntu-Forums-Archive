---
title: "Dialup modem set up"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by doctorbrowder on 2007-07-24
Dear Ubuntu community,

I successfully loaded Ubuntu 7.04 onto my HP Pavillion ZE5270 laptop. I like the feel of it and would like to keep it as an OS. BUT, it doesn't do me much good if I can't get access to the internet. I have tried to get the dial up modem set up on this thing, but I have discovered that you just about have to be a computer hacker to do it. One has to identify the chipset first, using some program called "scanModem" but I can't find the program on the internet anywhere (all links turn up 404). 

Can anyone help me to get this dial up modem set up on my laptop? Otherwise it's back to XP!

---

### Post by kevinlyfellow on 2007-07-24
Whatsup Doc?  Welcome aboard!

Here is a direct link to the download [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

You can decompress it using file-roller (double click on the file).  Put it on your desktop (or somewhere else if your comfortable with commandline) and make sure that it is named scanModem (just like that, nothing more, nothing less).  Here comes the hard part

[Open up the terminal]("http://www.psychocats.net/ubuntu/terminal")
and put in the following
```
cd Desktop
chmod 700 scanModem
sudo ./scanModem

```

A folder will be created on your desktop and you can browse through it however you like.

Be sure to let us know what modem you have, and we will help you get it installed.

BTW, if you can't get it working, be sure to check out the next release of Ubuntu, there are plans to include some softmodem drivers in it.

---

### Post by doctorbrowder on 2007-07-24
Thanks for the help. Unfortunately I have seen this link to the scanModem.gz program before; the link doesn't work. How else can I get this program? Is it possible to look up the chipset based on the make and model of the modem itself?  Under SYSTEM --> PREFERENCES --> HARDWARE INFORMATION, it tells me that the modem is an M5457 AC'97 Modem Controller by ALi Corporation, bus type "PCI". Is this info useful?

Thanks!

---

### Post by kevinlyfellow on 2007-07-24
> **doctorbrowder said:**
> Thanks for the help. Unfortunately I have seen this link to the scanModem.gz program before; the link doesn't work. How else can I get this program? Is it possible to look up the chipset based on the make and model of the modem itself?  Under SYSTEM --> PREFERENCES --> HARDWARE INFORMATION, it tells me that the modem is an M5457 AC'97 Modem Controller by ALi Corporation, bus type "PCI". Is this info useful?

Thanks!

Useful?  It's so useful you don't need scanModem!  (Although it is weird that the link doesn't work for you).  

Ok, so from what I've gathered with a little research, is that it may or may not work (I was really hoping you'd say you had lucent ;-))  But, there are some things we can try out.

So, there are three drivers that may work for you modem... the smartlink drivers, linuxant drivers, and pctel drivers.  One website says that it does work with the linuxant drivers.  

Now, there are three ways of getting this driver, only one way is the right way (I think) and it costs money and isn't the very easiest.  Let's try the easiest way first.

Dell (as you may have heard) has started offering Ubuntu in the US.  They use conexant modems, so they now have a driver for download.  I don't know how specific it is to their cards, but we can give this a try

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)

There are instructions on the page on how to install the driver.  Let me know how you fair with this.

---

### Post by doctorbrowder on 2007-07-24
OK, thanks! I went to the DELL website and downloaded the driver. It appears to have installed correctly. I also think I have the network connection configured through SYSTEM --> ADMINISTRATION --> NETWORK.

Now for a really foolish question... how do I dial in??? I'm looking for a 'dial in' panel like Windows has. Am I looking for the wrong thing?

---

### Post by Bartender on 2007-07-24
Hi, doc -
That would be interesting if the Dell drivers work for other PC's as well.  Please give us updates.
The Network GUI in 7.04 is broken.  It was broken in the previous release also.  Try the steps that duncan and I discuss [here]("http://ubuntuforums.org/showthread.php?t=480717").

You can set up either wvdial or pppconfig (or both, apparently) to operate as your dialer.  gnome-ppp is a graphical front-end for wvdial.  In other words, what you see on your screen is gnome-ppp but what's actually happening in the background is gnome-ppp is telling wvdial to connect.

There are 3 distinct hurdles to dial-up
#1 Modem
#2 Linux dial-up software (or understanding how to configure it)
#3 Your ISP

Your modem must work with Linux, you must learn how to set up at least one of the available Linux dialers, and your ISP must cooperate.  Any link, or part of the link, that doesn't work right will stop you.  Sometimes it's a really simple thing that hangs you up.  Like your ISP wants your entire username "linuxuser@isp.com" instead of just "linuxuser". 
Do you use MSN, AOL, Juno, PeoplePC, or one of the other ISP's that use proprietary software?  If so, your first step will be to move to another ISP, such as Fry's.com, ISP.com, Copper.net, BasicISP, etc. etc.

---

### Post by shawnmcdonald on 2007-07-24
Hi Doc,

You should have a look at the community HOWTO on configuring your dialer:

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

You're not alone in your confusion over modem setup and configuration under Ubuntu - it seems like a black art at times.  Once the hardware is working, I find wvdial to be most useful and then I use gnome-ppp as my regular dialer.

Hope this helps, (don't give up)
Shawn



> **doctorbrowder said:**
> OK, thanks! I went to the DELL website and downloaded the driver. It appears to have installed correctly. I also think I have the network connection configured through SYSTEM --> ADMINISTRATION --> NETWORK.

Now for a really foolish question... how do I dial in??? I'm looking for a 'dial in' panel like Windows has. Am I looking for the wrong thing?

---

### Post by Bartender on 2007-07-24
The "Set Up Dialer" link isn't inaccurate.  It's very complete.  Problem is, it has the same fatal flaw that's endemic to so many dial-up tutorials.  For instance, this line:

*"gnome-ppp is a graphical frontend to wvdial and can be installed by $ sudo apt-get install gnome-ppp." *

I'm sorry, but that's just lame.  It's not inaccurate, but it certainly is misleading to the newb.  Picture yourself as a new user, struggling to make sense of any advice tossed at you.  Your modem doesn't work in Ubuntu so you can't get online with it.  You've printed out the "Set Up Dialer" directions from an online Windows PC.  Now you're back at your Ubuntu desktop, trying your darndest to type stuff into this weird terminal  that you fervently hope will get you online.  Problem is, the advice you're following ASSUMES YOU HAVE AN INTERNET CONNECTION.

Sorry for the capital letters, but that just pisses me off

---

### Post by doctorbrowder on 2007-07-24
IT WORKS!!!!!!!!!!!! The driver I got from the Dell website mentioned above did the trick. Works like a charm. I am, in fact, at this moment, writing this response on my HP/Ubuntu laptop while connected to my dial-up ISP. I am now connected! A million thanks to all of you.

Now I need to try to figure out how to configure the ethernet card...

---

### Post by kevinlyfellow on 2007-07-24
> **doctorbrowder said:**
> IT WORKS!!!!!!!!!!!! The driver I got from the Dell website mentioned above did the trick. Works like a charm. I am, in fact, at this moment, writing this response on my HP/Ubuntu laptop while connected to my dial-up ISP. I am now connected! A million thanks to all of you.

Now I need to try to figure out how to configure the ethernet card...

Hooray!!!  That was the easiest winmodem setup I've ever heard of!  I can't wait to try out dell's driver on my father's winmodem.

---

### Post by Bartender on 2007-07-24
So did Dell do a big favor for dial-up users?

How common are these Conexant chipset modems?  It would be super if the Dell drivers worked for a decent collection of Conexant-based winmodems!

---

### Post by kevinlyfellow on 2007-07-24
> **Bartender said:**
> So did Dell do a big favor for dial-up users?

How common are these Conexant chipset modems?  It would be super if the Dell drivers worked for a decent collection of Conexant-based winmodems!

Almost all of the super cheap modems available are conexant.  The linux drivers are available for the 'low' price of 20 bucks (usually more than one pays for their actual modem).  I assume Dell made a deal with Conexant to let them distribute this modem driver for free.  Even if it only works with some conexant chipsets, it still seems like a great place to start.

---

### Post by crouger92 on 2007-07-31
I have the SiS AC'97.  Does that driver work for me as well? Can you help me otherwise?

---

### Post by crouger92 on 2007-07-31
i just tried that dell driver and either i'm not doing it right or it doesn't work for me.

---

### Post by kevinlyfellow on 2007-07-31
> **crouger92 said:**
> I have the SiS AC'97.  Does that driver work for me as well? Can you help me otherwise?

Only if it will work with a connexant chipset.  Have you run scanModem?

---

### Post by crouger92 on 2007-08-01
yes. Here is the contents of ModemData.txt:



 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 7.04  kernel 2.6.20-16-386 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-16-386 (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Thu Jun 7 20:16:13 UTC 2007
 scanModem update of:  2007_July_26


ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:02.6	1039:7013	1025:0083	Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller 

 Modem interrupt assignment and sharing: 
 17:        485   IO-APIC-fasteoi   SiS SI7012

 --- Bootup diagnostics for card in PCI slot 00:02.6 ----
[   19.190152] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 17
[   19.190160] ACPI: PCI interrupt for device 0000:00:02.6 disabled

 The PCI slot 00:02.6 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

CodecFiles not found

---

### Post by kevinlyfellow on 2007-08-01
I think you need the sl-modem drivers.  

Try this howto: [http://knowledge76.com/index.php/Laptop_Modem_%28sl-modem%29_on_Ubuntu_Breezy](http://knowledge76.com/index.php/Laptop_Modem_%28sl-modem%29_on_Ubuntu_Breezy)

---

### Post by crouger92 on 2007-08-02
Those drivers didn't work. I think I did everything right. It says there's  ' NO CARRIER!' and then tries to connect again.

---

### Post by kevinlyfellow on 2007-08-02
What does it say when you put in the command ```
slmodemd
```?

Just so you know what's going on in my head, I'm wondering if it's because of a certain bug in the drivers.  I tried installing it myself and came across it.  I'm looking at these bug reports 
[https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/103705](https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/103705)
[https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/92777](https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/92777)

---

### Post by crouger92 on 2007-08-03
This is what happens when I cd to the directory and run the slmodemd program:


error: mdm setup: cannot stat `/dev/slamr0': No such file or directory
error: cannot setup device `/dev/slamr0'

---

### Post by kevinlyfellow on 2007-08-03
This may be a bit of a stretch for some people, but it seems like your modem installation won't be particularly easy (certainly not as easy as the op).  You will need to compile some drivers.  While it may be frustrating, use this opportunity to learn a little bit about computing that you may never come across otherwise.  I spent countless hour attempting to get a lucent modem to work on red hat, I don't feel that I wasted a moment of that time, even though it would be another year and ubuntu to get the dang thing to work.

Now that the pep talk is done, let's get to work.

First you will need to install the necessary tools to install the driver.  Unfortunately, you will need an internet connection.  Local libraries often have wifi, or you can use any linux or unix machine to grab the needed files via a script generated by synaptic.  If you need help figuring out how to get all the needed files easily, just let me know, I've know a few ways to get those files without lurking around packages.ubuntu.com in windows and downloading each file individually.  Fortunately, most of the needed files should be on the installation cd (unless you have updated your kernel).  Follow this howto on installing the needed tools, including gcc-3.4 [https://help.ubuntu.com/community/DialupModemHowto/FromSource](https://help.ubuntu.com/community/DialupModemHowto/FromSource)

Then read through this up-to-date howto [https://help.ubuntu.com/community/DialupModemHowto/Smartlink](https://help.ubuntu.com/community/DialupModemHowto/Smartlink) and then attempt it.  I think it would be good to read through first just so you have an idea on whats going on.  BE SURE TO NOTE THE SPECIAL INSTRUCTIONS.  They may be necessary (these instructions are a result of the bug that you may be afflicted with).  

I have not tried these instructions myself (especially since I have no idea if my laptop modem works with the sl-modem and I don't have any way of testing if it works).  If you run into any problems, I will give you the best advice I can, but I am admittedly ignorant of the process beyond what the howto, google, and you tell me.  If I cannot answer your questions, feel free to start another post specifying your modem and problems, since I bet there is someone on these forums that has a modem just like yours.  

And a final note, I am fairly sure your modem works.  In looking for clues, I did run across a person using Gentoo who had your modem working flawlessly.  But Gentoo is very different then Ubuntu, so we need to go through a different process (to say the least).  Also, Gutsy Gibbon (the next release) will have improved modem support.  If you cannot get your modem working or just don't have enough need or desire to get it working, definitely give Gutsy a shot at it.

Best of luck

---

### Post by crouger92 on 2007-08-04
I installed all the packages and then tried to build them, but for some reason it didn't work. Here is the error log:


 dh_testdir                                                                 &#8593; 
 &#9474; dh_testroot                                                                &#9646; 
 &#9474; rm -f build-arch-stamp build-indep-stamp configure-stamp                   &#9618; 
 &#9474; # Add here commands to clean up after the build process.                   &#9618; 
 &#9474; /usr/bin/make clean SUPPORT_ALSA=1                                         &#9618; 
 &#9474; make[1]: Entering directory `/usr/src/modules/sl-modem'                    &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/sl-modem'                     &#9618; 
 &#9474; cd modem; /usr/bin/make clean SUPPORT_ALSA=1                               &#9618; 
 &#9474; make[1]: Entering directory `/usr/src/modules/sl-modem/modem'
make[1]: Entering directory `/usr/src/modules/sl-modem/modem'              &#8593; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/sl-modem/modem'               &#9618; 
 &#9474; dh_clean                                                                   &#9646; 
 &#9474; /usr/bin/make -C drivers clean                                             &#9618; 
 &#9474; make[1]: Entering directory `/usr/src/modules/sl-modem/drivers'            &#9618; 
 &#9474; rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o               &#9618; 
 &#9474; amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~                                &#9618; 
 &#9474; rm -f -r .tmp_versions                                                     &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/sl-modem/drivers'             &#9618; 
 &#9474; /usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules     &#9618; 
 &#9474; make[1]: Entering directory `/usr/src/modules/sl-modem'                    &#9618; 
 &#9474; dh_testdir                                                                 &#9618; 
 &#9474; dh_testroot                                                                &#9618; 
 &#9474; rm -f build-arch-stamp build-indep-stamp configure-stamp                   &#9618; 
 &#9474; # Add here commands to clean up after the build process. 
make[2]: Entering directory `/usr/src/modules/sl-modem/modem'              &#8593; 
 &#9474; make[2]: *** No rule to make target `clean'.  Stop.                        &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/sl-modem/modem'               &#9618; 
 &#9474; make[1]: [clean] Error 2 (ignored)                                         &#9618; 
 &#9474; dh_clean                                                                   &#9618; 
 &#9474; /usr/bin/make -C drivers clean                                             &#9618; 
 &#9474; make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'            &#9646; 
 &#9474; rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o               &#9618; 
 &#9474; amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~                                &#9618; 
 &#9474; rm -f -r .tmp_versions                                                     &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'             &#9618; 
 &#9474; for templ in                                                               &#9618; 
 &#9474; /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst         &#9618; 
 &#9474; /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.backup  &#9618; 
 &#9474; /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.module
 &#9474; s.in; do \                                                                 &#8593; 
 &#9474;     cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.20-16-386/g'` ; \       &#9618; 
 &#9474;   done                                                                     &#9618; 
 &#9474; for templ in `ls debian/*.modules.in` ; do \                               &#9618; 
 &#9474;     test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in}         &#9618; 
 &#9474; ${templ%.modules.in}.backup 2>/dev/null || true; \                         &#9618; 
 &#9474;     sed -e 's/##KVERS##/2.6.20-16-386/g ;s/#KVERS#/2.6.20-16-386/g ;       &#9618; 
 &#9474; s/_KVERS_/2.6.20-16-386/g ; s/##KDREV##/2.6.20-16.29/g ;                   &#9618; 
 &#9474; s/#KDREV#/2.6.20-16.29/g ; s/_KDREV_/2.6.20-16.29/g  ' < $templ >          &#9618; 
 &#9474; ${templ%.modules.in}; \                                                    &#9646; 
 &#9474;   done                                                                     &#9618; 
 &#9474; dh_clean -k                                                                &#9618; 
 &#9474; dh_installdirs lib/modules/2.6.20-16-386/misc usr/lib/sl-modem             &#9618; 
 &#9474; if ! test -e drivers/Makefile ; then echo "Please update the package,      &#9618; 
 &#9474; extract the tarball!"; exit 1 ; fi   
/usr/bin/make -C drivers KERNEL_DIR=/lib/modules/2.6.20-16-386/build       &#8593; 
 &#9474; KVERS=2.6.20-16-386                                                        &#9618; 
 &#9474; make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'            &#9618; 
 &#9474; gcc-4.1 -I/lib/modules/2.6.20-16-386/build/include -o kernel-ver           &#9618; 
 &#9474; kernel-ver.c                                                               &#9618; 
 &#9474; kernel-ver.c: In function ‘main’:                                          &#9618; 
 &#9474; kernel-ver.c:11: error: ‘UTS_RELEASE’ undeclared (first use in this        &#9618; 
 &#9474; function)                                                                  &#9618; 
 &#9474; kernel-ver.c:11: error: (Each undeclared identifier is reported only once  &#9618; 
 &#9474; kernel-ver.c:11: error: for each function it appears in.)                  &#9618; 
 &#9474; make[2]: *** [kernel-ver] Error 1                                          &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'             &#9618; 
 &#9474; make[1]: *** [binary-modules] Error 2                                      &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/sl-modem'                     &#9646; 
 &#9474; make: *** [kdist_build] Error 2

---

### Post by kevinlyfellow on 2007-08-04
That has some very interesting characters in it.  Anyways, it seems like something just isn't installed.  How about you try this (be warned, blind leading the blind right now)

```
sudo apt-get build-dep sl-modem-daemon
```

---

### Post by crouger92 on 2007-08-05
Still not working. Tries twice in less than a second and then quits. Ahhhh................! I wonder what  
the problem is. The last line of the special commands for feisty doesn't work, though.

---

### Post by kevinlyfellow on 2007-08-05
> **crouger92 said:**
> Still not working. Tries twice in less than a second and then quits. Ahhhh................! I wonder what  
the problem is. The last line of the special commands for feisty doesn't work, though.

You're right, the last commanding is trying to touch a config file in a directory that doesn't exist.  I'm looking into this problem now, and I'll let you know when I get it figured out.  You can try to create the missing directory, but I have no idea how this will work
```
sudo mkdir /usr/src/linux-headers-`uname -r`/linux
```

---

### Post by ubuntuforums on 2007-08-06
Thank you so much kevinlyfellow!  I used the dell driver and was able to get my AOpen FM56-USB Pro working, for the hell of it I also tested my old AOpen FM56-SVV, it works as well.  I just ran the package, then I went System>Administrator>Network, and I put in my dialup info, and changed it to modem port /dev/ttySHSF0 (for the USB Pro modem).  That was the easiest thing I have ever had to do in Linux.  Thanks again.

I'm currently making this posted in Ubuntu, connected to dialup on my FM56-USB Pro.  One question though, how can I see what speed I am connecting at, because it does seem a bit slower than normal.  On XP I connect 40Kbps or higher, this feels like low 30Kbps, lol.   How can I check?

---

### Post by kevinlyfellow on 2007-08-06
> **ubuntuforums said:**
> That was the easiest thing I have ever had to do in Linux.  Thanks again.

Your welcome.  I never would have expected that someone would say that installing a winmodem on linux was easy... I thought the winmodem problem would go away by the death of dialup, not because Dell decided to preinstall linux!

I'm not sure if you can get the 'connection speed'.  I'm in doubt that that number really means anything from my past experience anyway.  I think on windows it is just the initial connection speed and doesn't probe the speed at any later time.  I remember gnome-ppp gave me enough information for me to be happy (plus a very handy way to connect).

I tried various things to get a faster connection.  I remember fiddling around with something like this site suggests [http://www.lockergnome.com/nexus/linux/2002/01/23/speeding-up-your-modem/](http://www.lockergnome.com/nexus/linux/2002/01/23/speeding-up-your-modem/) .

---

### Post by ubuntuforums on 2007-08-06
I'm still amazed how easy that was, after messing around for almost a week already trying to install other winmodem drivers.  I've never liked Dell or any other "namebrand" pc company until now.  I've always bought barebones...  But major props to Dell for the driver. 

Are you sure that it's just an initial speed in windows?  I know that when I was using my FM56-SVV in windows it always connected at 31.6Kbps, and with my FM56-USB Pro it always connects between 37.2 and 46.8 (something like that), I never heard of that being just the initial speed, I've assumed that would be the connected speed.  I guess you could be right, I'm off to do some googling on that.

Also, thanks for the article, useful commands.  Although you should be able to tweak a lot more than that, I know I can in windoze.  I'll be googling that as well.  :D

---

### Post by kevinlyfellow on 2007-08-07
> **ubuntuforums said:**
> Are you sure that it's just an initial speed in windows? 

lol, nope!  I just remember that it never really seemed representative of the speed that I had experience,d and when trying to figure out why slower connection speed often felt faster I had heard that from someone.  I don't know if its true or not, by the time I started to understand computers better, I started using linux and had started to attend college (so therefore a very very nice connection to the net).

Edit: I forgot to add that although I don't really care to get a dell comp, I was excited to here their linux offering because I knew more and better drivers were on the way!  My computer is a System76, and as long as they are still the same company when I need my next laptop (i'd just build a desktop) I'll be buying from them.  Don't really want a dellbuntu machine, but happy that they exist!

---

### Post by timboe on 2007-08-07
> **Bartender said:**
> So did Dell do a big favor for dial-up users?

How common are these Conexant chipset modems?  It would be super if the Dell drivers worked for a decent collection of Conexant-based winmodems!


Dell did me a big favor ! I did get the conexant working on my Compaq Pesario laptop with the drivers from linuxant, but at 14.4k speed it was a joke & I refuse to pay $25 for the 56k version.:guitar:

---

### Post by crouger92 on 2007-08-08
that didn't work either. It seems to be getting farther along though.

---

### Post by kevinlyfellow on 2007-08-08
> **crouger92 said:**
> that didn't work either. It seems to be getting farther along though.

Well, thats good I guess.

Have I suggested yet to try this
```
sudo mkdir /usr/src/linux-headers-`uname -r`/include/linux
sudo touch /usr/src/linux-headers-`uname -r`/include/linux/config.h
```?

---

### Post by crouger92 on 2007-08-09
still didn't work. it gets to 28% on the second try if that's helpful.

---

### Post by kevinlyfellow on 2007-08-09
> **crouger92 said:**
> still didn't work. it gets to 28% on the second try if that's helpful.

I haven't heard back from the guy on the bug reports and I'm fresh out of ideas.  You may be better off to start a new thread on the problem.  Be sure to put your modem make and model in the title so people who have the same modem will take notice.

---

### Post by Bachstelze on 2007-08-09
Please do a scanModem scan and post the ModemData.txt. The information we have about your modem definitely is not enough.

[http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

```
gunzip scanModem.gz
chmod +x scanModem
sudo ./scanModem
```

EDIT : Woops, I didn't see there was already a ModemData posted. Sadly, it doesn't have enough information for us to find out which driver your modem needs, which makes me think it might just be unsupported. Do you have a /proc/asound directory ? If so, please post the contents of /proc/asound/card0

---

### Post by crouger92 on 2007-08-09
which files do you want? There are quite a few.

Dir /proc/asound/card0:

Directory: codec97#0 
File: id 		
File: intel8x0 		
File: oss_mixer 	
Directory: pcm0c 	
Directory: pcm0p 	
Directory: pcm1c

---

### Post by surfer69 on 2007-10-11
**[COLOR="Red"][SIZE="4"]BRILLIANT,[/SIZE][/COLOR]** after a coupla days messing around with modem settings, the Dell one did it for me!

[** [COLOR="Blue"]ALi M5457 AC'97 modemdriver[/COLOR]**](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)

On my Sony PCG-FR295MP laptop! Hardly a Dell machine.
Got this from scanModem:
____________________________________________________________________________________
[I]Several modems are supported by drivers with ALSA, the Advanced Linux Sound Architecture software.
Copying ALSA diagnostics to Modem/ALSAroot.tgz
ALSAversion = 1.0.13

Modem or candidate host audio card have firmware information and diagnostics:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:03.0	10b9:5457	104d:8158	Modem: ALi Corporation M5457 AC'97 Modem Controller
____________________________________________________________________________________[/I]
[COLOR="red"]I just followed the instructions on the Dell page![/COLOR]

---

