---
title: "DYMO label writer How-To"
date: 2008-07-16
forum: Hardware
---

### Post by bpalone on 2008-07-16
This is a How-To for getting and installing the CUPS drivers for the DYMO label writers.

This was written for and by my experience in and with Ubuntu 8.04.  It should be of help with other releases and distros.

According to their information (at this writing) their drivers support the following models:

LabelWriter 400
LabelWriter 400 Turbo
LabelWriter DUO
LabelWriter Twin Turbo
LabelWriter 300
LabelWriter 330
LabelWriter 330 Turbo
LabelMANAGER 450
LabelPOINT 350

The first thing to do is go to this site:

[https://global.dymo.com/enUS/RNW/RNW.html?pg=std_adp.php&p_faqid=101](https://global.dymo.com/enUS/RNW/RNW.html?pg=std_adp.php&p_faqid=101)

Then scroll down to the Linux section and download the DYMO SDK and CUPS drivers for Linux.

I am going to describe how to do most of this from the GUI, there will be a little bit of command line stuff done.  If someone wants to pitch in and redo this including how to do it from the command line, please do. (I am still getting to know Linux and don't feel that I'm qualified to lead someone down the command line path.  Yet anyway.)

The next thing to do is go to where you downloaded tarball from DYMO and double click it to unpack it.  When that is done, go into the newly created directory called &#8220;dymo-cups-drivers-1.0.1&#8221; and open a text file called &#8220;INSTALL&#8221;.  This is their instructions, and is what I am about to embellish upon.

Next you need to go to the Synaptic Package Manager and install some headers and libraries.  They are as follows:

libcupsimage2-dev
g++

Once these packages are installed, we need to Open a terminal window to do the command line stuff.

Now that you have your terminal window open, change directory (cd) into     _dymo-cups-drivers-1.0.1_   wherever that may be located.  Which depends on what you did when you extracted the files.  Once there you are ready to start to make this  all come together,

In the terminal enter the following:   _sudo ./configure_  (then hit enter)

When that finishes enter this:   _sudo make_

Now to do what we came here for, enter this:    _sudo make install_

CUPS should now have everything it needs to print to the DYMO printer.


These are fairly new drivers and SDK so I don't think there is anything out there made for just these label printers. I could be wrong, I have been in the past.  What I have done is gone into OO-Writer and created some templates with the page size set to the label size.  Seems to work just fine.  

I hope this helps someone out and they find it before they have done a lot searching.  I know it would of saved me a fair amount of time.

---

### Post by Keith_Beef on 2008-10-06
Thanks a lot for that, bpalone.

I had got the sticky label half of my Dymo LaberWriter Duo to work, but was not satisfied with the right margins, and in any case the tape half of the printer was not working at all.

This driver from Dymo works better, installed perfectly well with your instructions, but still I can't find out how to print tapes...

I added two Local Printers, one of them using the LabelWriter DUO Label driver, the other using the LabelWriter DUO Tape driver. Both of them set themselves to using the following address:
```
usb://DYMO/LabelWriter%20DUO%20Label?serial=06102216133691
```

So I looked in the Device Manager (System, Preferences, Hardware Information) and looked at connected USB devices.

I saw a device listed as LabelWriter Duo Tape 128 on ```
printer.physical_device /org/freedesktop/Hal/devices/usb_device_922_1d_06102216133691_if1
```

Now, the label printing part of the printer has the following:
```
printer.physical_device /org/freedesktop/Hal/devices/usb_device_922_1d_06102216133691_if0
```

The URL given in the printer configuration dialog (see above) has the 06102216133691 number, but not the if0 or if1... so I can't see how to make the difference between the two halves of the printer...

Can anybody enlighten me as to how to get the tape printing side working?


K.

---

### Post by dslax27 on 2009-02-22
It's been a few months since the above was posted and Dynmo updated their site with a new driver (v1.0.3). 

I receive an error when installing the driver on the Dynmo site using the above directions (intended for v.1.0.1). 

My terminal outputs the following when I get the install error

```

doug@doug-laptop:~/Desktop/dymo-cups-drivers-1.0.3$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/doug/Desktop/dymo-cups-drivers-1.0.3/missing: Unknown `--run' option
Try `/home/doug/Desktop/dymo-cups-drivers-1.0.3/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for cups-config... /usr/bin/cups-config
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for cupsMarkOptions in -lcups... yes
checking for cupsRasterReadHeader in -lcupsimage... no
**configure: error: Can't find cupsimage library**


```

**Two questions:**
[LIST=1]
[*]Does [this bug log]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/322210") mean that there is no solution for the above problem yet?
[*]Is there a way to get access to v1.0.1 that does work?
[/LIST]

---

### Post by sigmason on 2009-02-22
This tutorial works fine on Ubuntu 8.10 with the Dymo provided 1.0.3 drivers.

The only caution I have is to send ONLY postscript to this printer from the system.  You *CAN* print to the cups queue from Windows computers via IPP using the standard Windows driver (it works fine), but if you print from gedit or even use the "Print Test Page" functionality in (system-config-printer) you'll spit out label after label of badly printed junk that looks like it should be correct, but isn't if you look closely and even if you print 1 test page you'll get dozens and dozens of labels.

I used a page I created with OpenOffice that is formatted to fit the printer and then exported from OpenOffice as a PDF.  If you try to print that very same file from OpenOffice it will not switch to landscape.  However, if you open the PDF you exported from OpenOffice with Document Viewer you can print it fine from there.  This works because now it's in PDF and therefore it's postscript.

So just be careful, if you're not near this thing and you print a test page the default way (like say a network print server), I can picture a floor full of wasted labels.

My printers to test with: Dymo LabelWriter 310, Dymo LabelWriter 320, Dymo LabelWriter 330, Dymo LableWriter 330 Turbo.  All exhibit this behavior.

---

### Post by Tictoon on 2009-03-21
With LabelWriter 400, it gives me 2 labels for the test page.

---

### Post by iBurger on 2009-04-06
Anyone been successful to use gLabels with a Dymo label writer?

---

### Post by sebiXVI on 2009-04-12
Hi,

my LabelWriter worked out-of-the-box until Intrepid. With Jaunty, I can install the printer as well (CUPS gives Dymo/Costar as option) and I get printings from it.

However, I cannot set the pagesize correctly. I use "large address" labels, attempting to print always spans the output over several labels (3 or 4). Seems it internally sets the pagesize to A4?

Any hints on this?

Thx,
Sebastian

---

### Post by DeadMetal on 2009-04-28
> **sebiXVI said:**
> Hi,

my LabelWriter worked out-of-the-box until Intrepid. With Jaunty, I can install the printer as well (CUPS gives Dymo/Costar as option) and I get printings from it.

However, I cannot set the pagesize correctly. I use "large address" labels, attempting to print always spans the output over several labels (3 or 4). Seems it internally sets the pagesize to A4?

Any hints on this?

Thx,
Sebastian

I have the exact same problem. Does anyone have a solution regarding this?

---

### Post by sebiXVI on 2009-04-28
Hi,

yes, there is a solution. This topic is been discussed as bug #35722 [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/357732]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/357732"). In this thread there is a different pstopdf file that corrects the problem for me.

However, meanwhile an updated cups package (1.3.9-17ubuntu2) has been released that already contains the fix. So please try upgrading, if that doesn't work, follow the instructions given in the above thread.

Regards,
Sebastian

---

### Post by Keith_Beef on 2009-04-28
This might automatically be fixed by upgrading to Jaunty Jackalope, then...

Thanks for the information.

---

### Post by DeadMetal on 2009-04-29
Thanks, updating (after enabling the jaunty-proposed channel) has indeed solved the problem for me, now the printer works fine again, great!

---

### Post by mbirth on 2009-05-03
Did anyone fix the problem with the endless labels printing?

I used the default Dymo PPD from Jaunty but found no way to switch to error diffusion (half-toning looks sooooo bad!). So I compiled this driver and now I have beautiful error diffusion but printing one label makes the printer print forever... even when printing from Adobe Reader. (I have a LabelWriter 320.)

I wanted to use this for printing stamps via [www.internetmarke.de](www.internetmarke.de) (there you can put some custom pictures on a stamp and print it yourself).

Cheers,
  -mARKUS

P.S.: The "DYMO_SDK_for_Linux.rtf" says: > The following products can work only when shared over the network from a Windows machine. This is due to limitations in the USB support in these printers &#8211; Linux USB support only recognizes fully compliant USB devices. 
-LabelWriter 310
-LabelWriter 315
-LabelWriter 320
-LabelMANAGER 400
-LabelMANAGER PC but Linux DOES recognize the device.

---

### Post by Keith_Beef on 2009-05-05
> **mbirth said:**
> Did anyone fix the problem with the endless labels printing?

I used the default Dymo PPD from Jaunty but found no way to switch to error diffusion (half-toning looks sooooo bad!). So I compiled this driver and now I have beautiful error diffusion but printing one label makes the printer print forever... even when printing from Adobe Reader. (I have a LabelWriter 320.)

I wanted to use this for printing stamps via [www.internetmarke.de](www.internetmarke.de) (there you can put some custom pictures on a stamp and print it yourself).

Cheers,
  -mARKUS

P.S.: The "DYMO_SDK_for_Linux.rtf" says:  

> The following products can work only when shared over the network from a Windows machine. This is due to limitations in the USB support in these printers – Linux USB support only recognizes fully compliant USB devices.
-LabelWriter 310
-LabelWriter 315
-LabelWriter 320
-LabelMANAGER 400
-LabelMANAGER PC 

but Linux DOES recognize the device.
In other words, whoever wrote the document you quoted is admitting that the device is not fully compliant! The document could have stated:
> The following products can work only when shared over the network from a Windows machine. We could have done the USB implementation correctly, but that would have taken too much time and work. So instead, we cut corners in the USB hardware in the printers and fixed it in the software, but only for Windows. 

I did a quick test a couple of nights ago... I set up new queues, using the HAL layer rather than direct USB.

Test pages printed, but not at the correct scale, so each test gave me the left-hand edge of the test image spread over several labels and over a length of tape.

This is promising, though... I hope to get the scaling problem fixed by defining the correct page size for the two queues.

Keith.

---

### Post by kat_ams on 2009-06-10
> **dslax27 said:**
> It's been a few months since the above was posted and Dynmo updated their site with a new driver (v1.0.3). 

I receive an error when installing the driver on the Dynmo site using the above directions (intended for v.1.0.1). 

My terminal outputs the following when I get the install error

```

doug@doug-laptop:~/Desktop/dymo-cups-drivers-1.0.3$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/doug/Desktop/dymo-cups-drivers-1.0.3/missing: Unknown `--run' option
Try `/home/doug/Desktop/dymo-cups-drivers-1.0.3/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for cups-config... /usr/bin/cups-config
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for cupsMarkOptions in -lcups... yes
checking for cupsRasterReadHeader in -lcupsimage... no
**configure: error: Can't find cupsimage library**


```

**Two questions:**
[LIST=1]
[*]Does [this bug log]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/322210") mean that there is no solution for the above problem yet?
[*]Is there a way to get access to v1.0.1 that does work?
[/LIST]


You need to install two packages in order to install the DYMO drivers:
```
sudo aptitude install libcups2-dev libcupsimage2-dev
```

Once you have these two packages the ```
sudo ./configure
``` will run flawlessly.

---

### Post by andersja on 2009-06-18
Is this tutorial still valid for Jaunty?

---

### Post by mirabilos on 2009-07-31
libcairo2-dev is also required to compile.

---

### Post by mikehenson on 2009-08-12
Thank you for your time and effort in bringing this to the public. This helped me!

MSH

---

### Post by gordong11 on 2009-11-19
Thanks. Karmic works perfect here's how.

I went to dymo.com and downloaded the linux drivers and followed your installation instructions.

Cups automatically recognized my Dymo 330 Turbo, when I added a printer.

Labels:

1. Open Software Center
2. Install **glabels** program
3. Open glabels
4. Goto File then click New (Cntl+ N)
5. Choose "search all templates" tab (Must do this)
[B]6. For "Brand" choose "Dymo"
7. For "Page size" choose "Any"
[/B]
This will bring up about a dozen different size Dymo labels. Then just design your label. I don't think you can use a Twin label printer, at least expect both labels to print.

I'm getting PERFECT LABELS (except driver is not recognizing images for me).

I added a small text box at the top, then added a horizontal line separating the top and bottom of the label. Then  added a large text box for the shipping address. I also added another very small text box inside top left of the large box, for "To:". It looks great!!! for linux anyway. and it prints perfect, even in large bold type. :p:p

Thanks again for the driver install info!!

---

### Post by userFrodo on 2009-11-23
Hello,

I'm running Ubuntu 9.1 with a Dymo 400.

Installed cups & basically did what's on Dymo's pages and here on the forum.

At this point, the test labels are fine (99012 - large address). However, I would like to print labels generated online, using a webbrowser like Firefox. This used to work under WinXP, but I can't get it running under Ubuntu 9.1.

It looks like there's something wrong with margins. Also, I've had the problem of endless printing and wasting labels.

Hopefully anybody else has some more information.

Best Regards,

---

### Post by iBurger on 2010-01-01
Really helpful topic. I have somehow managed to print lables now from my Dymo 400. I find it hard to get the perfect template, but I still wanted to share this one for the 99017 labels. (realy tiny ones). This is a pretty workable template, but you will lose a tiny bit on the right.

Save the following code as "dymo_99017.template" in your ~/.glabels directory.

```
<?xml version="1.0"?>
<Glabels-templates xmlns="http://snaught.com/glabels/2.2/">
  <Template brand="Dymo" part="99017" size="Other" width="20mm" height="50mm" description="Test">
    <Label-rectangle id="0" width="11mm" height="50mm" round="2mm" x_waste="0mm" y_waste="5mm">
      <Markup-margin size="0mm"/>
      <Layout nx="1" ny="1" x0="0mm" y0="-5mm" dx="9mm" dy="-10mm"/>
    </Label-rectangle>
  </Template>
</Glabels-templates>

```

---

### Post by MikeSierra on 2010-02-14
A little help is highly appreciated here.

I have now managed to install the Dymo Laberwriter 400 with the instructions found from here and with driver package found from Dymo website. CUBS is installed too. My Ubuntu version is 9.10.

The printer is now detected but problem is, when print the test page i get error message that says, cant find template "rastertodymo". The error points to /usr/lib/cups/filter/ but in this folder there is "raster2dymolw". It looks like that it is the correct file but with different name?

Now to the (more) stupid question, is it so simple that i just rename the the file?? And what command should i use? I am still quite a newbie... Or should i edit something to point to right file name?

And what about the Dymo software? I installed it with Wine but install stops to error message that said something about deficensy at the program or wine (?)
Can you basically install and use Dymo software in Linux with wine? Or perhaps older version? 
Tried the gLabel but it is not exactly what i want.

Sorry again for the dumb q but i cannot find this from other posts...
I am still on the proccess of re-calibrate my brains from M$ world =)

---

### Post by Texasdad on 2010-02-17
I cannot make it work--after I downloaded the Drivers from the Dymo site.

Perhaps a step wise clear instructions page for newbies would be helpful--on the lines of :

1. Download driver.
2. this is what it looks like:
3. Extract files:
4. go to Terminal , this is what it looks like: etc etc.

Have been on Ubuntu only for a few days--and I must say that the help in Microsoft is a lot easier and more "graphics" rich. Help here is more of a "techy kind" !

---

### Post by MikeSierra on 2010-02-19
I am one happy puppy!

Basically i needed to reinstall cups and printer driver and start again from first of this thread.
After i did exactly as described, in my great suprise, Dymo spit out a label. Well actualy one and 1/8, but that was fixed...

But basically i started with this file:
[http://download.dymo.com/Download%20Drivers/Linux/Download/dymo-cups-drivers-1.2.0.tar.gz](http://download.dymo.com/Download%20Drivers/Linux/Download/dymo-cups-drivers-1.2.0.tar.gz)

unpacked it and then followed these instructions.

Life with Ubuntu is really mutch of Googling and try/error/try but afterall very rewarding when something actually works =)

---

### Post by michaelayland on 2010-04-02
As someone who has struggled for several hours to get my DYMO 400 turbo to talk to glabels may I thank all contributors to this thread for their help.. only by reading and rereading all the messages and plodding one line at a time through terminal did it eventual print.. Thank you all.

---

### Post by thomas_anderson on 2010-04-19
> **userFrodo said:**
> Hello,

I'm running Ubuntu 9.1 with a Dymo 400.

Installed cups & basically did what's on Dymo's pages and here on the forum.

At this point, the test labels are fine (99012 - large address). However, I would like to print labels generated online, using a webbrowser like Firefox. This used to work under WinXP, but I can't get it running under Ubuntu 9.1.

It looks like there's something wrong with margins. Also, I've had the problem of endless printing and wasting labels.

Hopefully anybody else has some more information.

Best Regards,

Yes I am having the same problem except that I am trying to print on a File Folder label 30327.  I have a generated PDF document online that we used in windows and it worked with our dymo lw400 but we had to make sure the text was in the field of print view.  

The template is created in a (letter) formatted page with the text at top left margin.  Cant seem to get it to land in field of print view.  Any help would be appriciated. 

BTW:  I had a hard time just installing printer on 9.1 and this forum help me out 100% so far so I hope to keep the tally going.. Thanks guys for all your help thus far.

---

### Post by mike555 on 2010-04-25
I got my Dymo 450 working by downloading the driver from their site , putting it in my home folder , unarchiving it so it says " dymo-cups-drivers-1.2,0 "  then open terminal and type " cd dymo-cups-drivers-1.2.0 " without quotes, enter, then type " sudo ./configure " , enter , then type " sudo make " ,enter , then type " sudo make install " , enter .......... now install "Glabels and try it , it should work although the margins might be a little off .......

---

### Post by craig100 on 2010-05-16
> **mike555 said:**
> I got my Dymo 450 working by downloading the driver from their site .......

Could you tell us where you found the driver please? i.e a URL would be nice. I can't get a decent driver for my LW400 for Lucid. Worked on Karmic:(

Cheers.

---

### Post by rogerb1583 on 2010-05-23
I would also want to know how or if the LW 400 can work with Lucid Lynx. :)

---

### Post by phubert28 on 2010-06-05
I tried Mike555's instructions (with sudo), but got the error message:

configure: error: Can't find cups library

---

### Post by donlinux on 2010-06-30
I'm using Mint Isadora which is same as Lucid.
Had my 400 turbo working fine in "karmic"

Downloaded the sdk file from dymo.  unpacked into my home directory,  ran sudo ./configure   got this error message:

configure: WARNING: `missing' script is too old or missing


then when I run make I get this error message:

Making all in src
make[1]: Entering directory `/home/donlinux/dymo-cups-drivers-1.2.0/src'
make  all-recursive
make[2]: Entering directory `/home/donlinux/dymo-cups-drivers-1.2.0/src'
Making all in lw
make[3]: Entering directory `/home/donlinux/dymo-cups-drivers-1.2.0/src/lw'
Making all in tests
make[4]: Entering directory `/home/donlinux/dymo-cups-drivers-1.2.0/src/lw/tests'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/donlinux/dymo-cups-drivers-1.2.0/src/lw/tests'
make[4]: Entering directory `/home/donlinux/dymo-cups-drivers-1.2.0/src/lw'
source='raster2dymolw.cpp' object='raster2dymolw.o' libtool=no \
	DEPDIR=.deps depmode=none /bin/bash ../../depcomp \
	g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -c -o raster2dymolw.o raster2dymolw.cpp
../../depcomp: line 504: exec: g++: not found
make[4]: *** [raster2dymolw.o] Error 127
make[4]: Leaving directory `/home/donlinux/dymo-cups-drivers-1.2.0/src/lw'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/donlinux/dymo-cups-drivers-1.2.0/src/lw'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/donlinux/dymo-cups-drivers-1.2.0/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/donlinux/dymo-cups-drivers-1.2.0/src'
make: *** [all-recursive] Error 1


Anyone smarter than me is welcomed with open arms to help.

I purchased my labelwriter 400 turbo because Open Office doesn't print on envelopes as easily as MS Office does and I don't use any windoze software anymore.

Thanks in advance

---

### Post by phubert28 on 2010-06-30
I purchased Codeweavers Crossover Office and found it to be SO lame (so limited in program support (including the Dymo software), I ordered an OEM WinXP SP3 and installed it in the ORACLE Pro version of VirtualBox for USB support.

THAT didn't recognize my Dymo printer on the USB port, but there were some hints on how to get it to work... I just haven't followed it up.

If Crossover Office doesn't work, I wouldn't expect WINE to.

I'm REALLY puzzled (and disappointed) over WINE/Crossover. I THOUGHT the method was to emulate the API's. One would THINK the API for older software (such as Dymo's) would be STATIC and ONCE they had it working it would ALWAYS work.

Long time since I was a programmer and it wasn't on UNIX or PC's, but AS a former Assembly language machine level (EXCP IO) programmer, as well as a designer of systems in several environments I HAVE to wonder what the heck those people are doing. To me the end product of WINE, if it only supports fairly current MICROSOFT software is USELESS.

One member of the varlinux.org site has said that IN-HOUSE software at his site that worked under earlier versions of Crossover were broken by later versions. He, too, is unimpressed with their effort.

They WERE good about one thing: I got a full refund.

IF you can get your USB devices working in a VM, I'd recommend that path... the OEM version of XP (get your copy soon!) won't cost any more than Crossover!

IF anyone gets Dymo printers working under WinXP in a VirtualBox VM, I'd love to hear it!!!

---

### Post by donlinux on 2010-07-01
Followed the most excellent tutorial by BPAlone.
Couldn't get it to work.

Then I realized something.  I had missed installing g++

Once I did that, I redid ./configure   make and make install and then added printer and everything worked great !!!!

I use an open office template for printing labels and it works fine.
Basically just a document that's 1" high and 3 1/2" wide.

Thanks to everyone for all their help!

---

### Post by phubert28 on 2010-07-01
Yes, that lets you print labels. But we still don't have the Dymo address book or online address CORRECTION software (zip + 4). And I used both of those. So, I still need to get Windows XP in a VM to see my printer!

---

### Post by spiced on 2010-08-07
using lucid the above methods didn't work for me either ( ./configure aborted with "error: Can't find cups library")

however thsi worked fine:
i found this site [http://www.miek.nl/blog/archives/2009/10/31/dymo_400_label_writer_in_ubuntu_jauntykarmic/index.html](http://www.miek.nl/blog/archives/2009/10/31/dymo_400_label_writer_in_ubuntu_jauntykarmic/index.html) with a .ppd file working like a charm with my labelwriter 400.
just plug in the printer and after a while (no drivers found) select the dymo.ppd file. (zipped file attached)

edit:
this also works very fine with gLabels. even printing graphics works - yay <3<3<3

---

### Post by phubert28 on 2010-08-07
Well, my Dymo is working with Ubuntu and glabels (and OO Write, of course), but that STILL leaves me without the DYMO software.

So my problem now is getting Windows XP running under Oracle's VirtualBox to see the printer ... I've gotten to the point where I think I just need a separate box to run WinXP!!

---

### Post by bpalone on 2010-08-28
I haven't tried XP in virtual machine with the Dymo software.  But, 2000 works just fine in VirtualBox with the Dymo software, even the Dymo Postage.

I didn't pay that much attention of which version of Ubuntu you're using.  But, I do recall that with 8.04 there was some tweaking to get the USB to work.  Once it was up and working, I haven't had any issues with it.

You did activate it in the USB filter list in VB, didn't you?

---

### Post by phubert28 on 2010-08-28
Although Windows could SEE my Dymo printer, the Dymo software could not.

It turned out that my solution was the following:

Connecting to Linux printers from VBox Windows!!

 Re: Sharing printers with Windows XP in VirtualBox
You need to know the IP address of your Ubuntu machine. for instance, 192.168.0.2 You also need to know what your printer is called on your Ubuntu machine. Windows XP would then install the printer via XP Printer and Faxes setting. the printer would be installed as : [http://192.168.0.2:631/printers/Canon-6300](http://192.168.0.2:631/printers/Canon-6300) for instance.

From the terminal find your IP. Type : ifconfig. Note the IP address.
Use your browser with : [http://localhost:631](http://localhost:631) to run CUPS, go to Printers and note the printer queue name.

From XP go to Start, Printers and Faxes, add new printer.
Fill in details with port http://<your IP>:631/printers/<your printer>

***

Additional notes:

O.K. I think I've GOT it: 

I had to set CUPS to allow printing from the Internet... don't know I LIKE that one, but...

For the HP printer, I needed the driver disk
For the Dymo, USB-attached, nothing more was needed

---

### Post by phubert28 on 2010-08-28
Likewise, though Windows 'sees' my Logitech Illuminated Keyboard, Logitech's SetPoint software does NOT... and for that, and my Logitech MX Revolution mouse, I'm STILL out of luck when it comes to configuring functions only available THROUGH SetPoint.

If only all the vendors would port their software TO Linux, I wouldn't need to TOUCH Windows again!

---

### Post by bpalone on 2010-08-28
I wonder if the difference is software versions?  I am not where I can check the Dymo software versions, but I have had my Dymo printers for 3 yrs.  I also don't use the latest and greatest VB version either, it is 2.2 or some where there abouts (if it ain't broke don't fix it).  When I get back to my desktop I'll see if I can get the Dymo versions and post them.

Almost afraid to say this one here, but could also be a change in Ubuntu, I'm still using 8.04.  I think we should compare software versions, just in case that may be the issue.  Could save someone some hassle.

---

### Post by phubert28 on 2010-08-28
I am using the latest version of the Dymo software and I'm on 64 bit Ubuntu 10.4 with the latest version of Oracle's VirtualBox. Under that I'm running WinXP SP3 with the latest patches.

Still, I would hardly expect a Virtual Machine to 'see' USB devices the way the OS on a physical machine would. After all, isn't a Virtual Machine OS SUPPOSED to be generic?

Again, I blame the hardware suppliers for not fully supporting Linux.

Clearly they don't realize that such a level of support would RESULT IN higher demand for their products BY Linux users. ...or perhaps they DO and remain in fear of Microsoft.

---

### Post by bpalone on 2010-08-29
O.K., here are my version numbers:

VirtualBox ----- 2.2.4

Dymo Label  ----- 7.6.0.9

Ubuntu ------ 8.04

I run 32 bit, and have no issues with software seeing and using the USB ports through VirtualBox.

Seeing that you are using 64 bit Ubuntu and I'm assuming a 32 bit XP, I am wondering if that may be why.  Could be some addressing issues.  But, the above are the 32 bit versions that I use and work fine with Win 2K.

Don't know if this will help anybody or not.

---

### Post by bpalone on 2010-08-29
Just a side note here.

I do still use my Dymo printer with OOo, so I haven't abandoned using it in Linux.  I may check out GLabel, seeing some of the comments here.  Good to see that one has helped out some people.  Which is good, as many have helped me out along the way too.

---

### Post by donlinux on 2010-08-30
OK... 
Strangely enough.  My Dymo LW 400 Turbo stopped working!
Showed up in the print manager, showed as idle.
Tried to print and got this error message:  usr/lib/cups/backend/usbfailed

I deleted the dymo cups drivers folder.  followed the installation instructions to install again from bpalone's first post.  Worked fine until I shutdown and restarted.  Then again, I see the printer,shows it as idle and when I try to print a test page, I get the same error and no print.
This is maddening!!
I'm using Mint9, which I believe is Ubuntu 8.10

Many thanks for any help from someone smarter than I!

---

### Post by phubert28 on 2010-08-30
Have you tried the solution below? I got that from another thread - I'm saving solutions like that in notes using Tomboy. Unfortunately, THIS time I didn't save the attribution - usually I am careful to give the provider credit!

---

### Post by donlinux on 2010-08-31
Which solution do you refer to?
I've tried all suggestions from the ubuntu forums for Dymo thus far.
Thanks,

---

### Post by phubert28 on 2010-08-31
THIS one (in this thread, a few items down)

 				 				**Re: DYMO label writer How-To** 			
 			 			 		   		 		 		Although Windows could SEE my Dymo printer, the Dymo software could not.

It turned out that my solution was the following:

Connecting to Linux printers from VBox Windows!!

 Re: Sharing printers with Windows XP in VirtualBox
You need to know the IP address of your Ubuntu machine. for instance,  192.168.0.2 You also need to know what your printer is called on your  Ubuntu machine. Windows XP would then install the printer via XP Printer  and Faxes setting. the printer would be installed as : [http://192.168.0.2:631/printers/Canon-6300](http://192.168.0.2:631/printers/Canon-6300) for instance.

From the terminal find your IP. Type : ifconfig. Note the IP address.
Use your browser with : [http://localhost:631]("http://localhost:631/") to run CUPS, go to Printers and note the printer queue name.

From XP go to Start, Printers and Faxes, add new printer.
Fill in details with port http://<your IP>:631/printers/<your printer>

***

Additional notes:

O.K. I think I've GOT it: 

I had to set CUPS to allow printing from the Internet... don't know I LIKE that one, but...

For the HP printer, I needed the driver disk
For the Dymo, USB-attached, nothing more was needed

---

### Post by donlinux on 2010-09-01
That post didn't relate to me as I can't get it to print in linux.  I don't use windoze anymore.

I keep getting usr/cups/backend/usb failed message.

Thanks,

---

### Post by donlinux on 2010-09-02
While looking at etc/cups/ppd, I noticed that I had a ppd for DymoLabelwriter-400-turbo but then when I looked at hidden files I saw a dw400t.ppd which I had never seen.  I deleted it and it appears, (he said cautiously), that my labelwriter now works.

I will update after a few re-starts etc...

Thanks for all the input and help.

Update:  didn't work.  Restarted and no-go.  
I've discovered a workaround that does work though.
I need to do a "sudo modprobe usblp" and then the printer is discovered and works.
Problem is:  I need to do it each time I start my computer.

---

### Post by narcisgarcia on 2010-09-28
I don't find GNU/Linux section in the mentioned webpage:
[https://global.dymo.com/enUS/RNW/RNW.html?pg=std_adp.php&p_faqid=101](https://global.dymo.com/enUS/RNW/RNW.html?pg=std_adp.php&p_faqid=101)

The guide may be updated byt the link [http://download.dymo.com/Download%20Drivers/Linux/Download/dymo-cups-drivers-1.2.0.tar.gz](http://download.dymo.com/Download%20Drivers/Linux/Download/dymo-cups-drivers-1.2.0.tar.gz)

---

### Post by jelcoward on 2010-09-30
Thanks for the great thread. I have read it a few times over the last months as I keep coming back to sorting out my labelwriter 400 turbo running on Ubuntu 10.04 and then giving up again (until my staff nag me enough so that I pay attention again!).

So, all is good (well, not all, you probably guessed that already!), installed, all seen, even prints labels (which is a hand feature in a label printer :)

...but.....left hand margin....ugh....label is a landscape 28mmx89mm (1 1/8" x 3 1/2").  Printing starts just off the left hand side of the label.  The rest of the label looks fine.

I have to print labels from pdf (just because of an application we use that generates them).  Choosing 'shrink to fit' and 'size to fit' etc is all to no avail.

It must be a ppd file thing, I am guessing.  
(oh, and I tried in CUPS setting the default to a custom paper size, but it does not 'hold' (save, or whatever the correct term should be for 'staying set').

I have taken a peek at the ppd file for the printer and am trying to understand it - with a view to tweaking it.

I have a feeling that this is the line that sets the 'margins' for the label
*ImageableArea w79h252/30252 Address: "4.32 4.32 76.08 235.44"

...the important bit being between the ""s  

But that is as far as I have got - I don't understand what each figure refers to - they are in 'points' (I get that bit) but I don't know what measurement each figure refers to, whether they have to add up to the dimensions of the label etc (the label dimension is 79x252 points).

My current questions, I think, are:

Can I tweak the ppd file (and if I can is it then live or do I need to do something else to get it read)?

If I can tweak the ppd file, then what settings should I try?

Is there another way of doing this?  (the labels have to be printed from a pdf reader because that is how they are generated - so I can't change that part of the process).

Thanks for any advice :)

PS I run my whole office on Ubuntu - server, scanning large volumes and all usual office type applications - and why? Well, because it it better and easier. (apart from this one label printing issue that I am determined to get fixed......but I am no tech!)

---

### Post by jelcoward on 2010-09-30
> **jelcoward said:**
> 

My current questions, I think, are:

Can I tweak the ppd file (and if I can is it then live or do I need to do something else to get it read)?

If I can tweak the ppd file, then what settings should I try?

Is there another way of doing this?  (the labels have to be printed from a pdf reader because that is how they are generated - so I can't change that part of the process).



I think I have in part answered the second question - here is the information re the ppd file and it defining print area
[http://download.oracle.com/docs/cd/E12839_01/bi.1111/b32121/pbr_uxprt004.htm#CIHJHIIH](http://download.oracle.com/docs/cd/E12839_01/bi.1111/b32121/pbr_uxprt004.htm#CIHJHIIH)

I will try it tomorrow :)

---

### Post by narcisgarcia on 2010-09-30
A little experience thay may help you to think about scaling:

I configured a "Dymo LabelWriter 400" without touching any else CUPS preference, then created a Draw document with OpenOffice and drawn a rectangle that fits in the default margins for an A4 sized sheet.

When printed this, the rectangle lines fit in the label area, but only less long than the label. This could be corrected by enlarging the sheet dimension in the application document: 29.7 x 21 cm -> 40 x 21 cm (not exact)

---

### Post by azekee on 2010-10-20
> **bpalone said:**
> This is a How-To for getting and installing the CUPS drivers for the DYMO label writers.

This was written for and by my experience in and with Ubuntu 8.04.  It should be of help with other releases and distros.

According to their information (at this writing) their drivers support the following models:

LabelWriter 400
LabelWriter 400 Turbo
LabelWriter DUO
LabelWriter Twin Turbo
LabelWriter 300
LabelWriter 330
LabelWriter 330 Turbo
LabelMANAGER 450
LabelPOINT 350

The first thing to do is go to this site:

[https://global.dymo.com/enUS/RNW/RNW.html?pg=std_adp.php&p_faqid=101](https://global.dymo.com/enUS/RNW/RNW.html?pg=std_adp.php&p_faqid=101)

Then scroll down to the Linux section and download the DYMO SDK and CUPS drivers for Linux.

I am going to describe how to do most of this from the GUI, there will be a little bit of command line stuff done.  If someone wants to pitch in and redo this including how to do it from the command line, please do. (I am still getting to know Linux and don't feel that I'm qualified to lead someone down the command line path.  Yet anyway.)

The next thing to do is go to where you downloaded tarball from DYMO and double click it to unpack it.  When that is done, go into the newly created directory called “dymo-cups-drivers-1.0.1” and open a text file called “INSTALL”.  This is their instructions, and is what I am about to embellish upon.

Next you need to go to the Synaptic Package Manager and install some headers and libraries.  They are as follows:

libcupsimage2-dev
g++

Once these packages are installed, we need to Open a terminal window to do the command line stuff.

Now that you have your terminal window open, change directory (cd) into     _dymo-cups-drivers-1.0.1_   wherever that may be located.  Which depends on what you did when you extracted the files.  Once there you are ready to start to make this  all come together,

In the terminal enter the following:   _sudo ./configure_  (then hit enter)

When that finishes enter this:   _sudo make_

Now to do what we came here for, enter this:    _sudo make install_

CUPS should now have everything it needs to print to the DYMO printer.


These are fairly new drivers and SDK so I don't think there is anything out there made for just these label printers. I could be wrong, I have been in the past.  What I have done is gone into OO-Writer and created some templates with the page size set to the label size.  Seems to work just fine.  

I hope this helps someone out and they find it before they have done a lot searching.  I know it would of saved me a fair amount of time.

In Ubuntu software center get (gLabels)   it will be your front sofware for printing any Dymo Label.  Only after you have installed cups and drivers first.

---

### Post by Babbage on 2010-11-07
Thanks for the tutorial, it worked perfectly for me. I had to install the packages *libcupsimage2-dev* and *g++* using Synaptic, that was very easy.

Just to say there's an extra step that I did that might help others. After I installed the drivers. I selected the label size like this:

[LIST=1]
[*]Open Printers, and double click the Dymo-LabelWriter icon.
[*]Click "Printer Options" on the left
[*]Under "Media Size" select the label size you're using from the drop down list.
[*]Choose the label number that matches the Art. No. marked on the reserve of your label strip, or box, for example, if the Art. No. says 99012, choose 99012 Large Address from the list.
[*]Click Apply. (Optional - go to Settings and print a test label. I used an old label for this.)
[*]Close the Dymo-LabelWriter properties dialog and Printers page.
[/LIST]

I then installed GLabels using Add/Remove Apps. There's also a slight issue there as well. In the Template Designer, I had to select Mailing/Shipping products from the Category drop down list, brand Dymo and page size Other, before the Dymo templates showed. Then I selected the same label number for my template, 99012, (yours might be different) and checked the Rotate box at the end.

Everything printed fine for me.

Thanks for the help. :)

---

### Post by iGeorgie on 2010-11-17
I just bought a Dymo Labelwriter 450.
I have a Mac and the installation went great. Put I had to install with the CD-Rom.

So, up to my Ubuntu PC (10.10). Plugged it in and immediately Ubuntu told me it was searching for drivers. Then a pop-up the pick one from the list and done.
I installed Glabel and selected Dymo-->Other-->"your label size".
Tada... My first label from Ubuntu in 2 minutes.

Hmmm... and I thought my Mac was impressive.

---

### Post by ben72 on 2010-12-16
I can confirm that this works in Ubuntu 10.04 with Dymo 400. I just..

1. Installed the "LabelWriter/ LabelManager SDK for Linux" from [http://sites.dymo.com/DeveloperProgram/Pages/LW_SDK_Linux.aspx](http://sites.dymo.com/DeveloperProgram/Pages/LW_SDK_Linux.aspx)

2. Installed the Label Writer in Ubuntu
And then I was able to print on Multi purpose labels (dymo 11354) adjusting the page size to the label size with 0,1cm borders in OpenOffice. And it prints really nice!

I couldn't find the correct label size in Glabels.

---

### Post by PlasticArmyMan on 2012-02-01
I'll verify that this works with 10.04 and the Twin Turbo.

i'm just wondering if we can print postage from paypal using this...

---

### Post by johansmits on 2012-02-20
> **iBurger said:**
> Really helpful topic. I have somehow managed to print lables now from my Dymo 400. I find it hard to get the perfect template, but I still wanted to share this one for the 99017 labels. (realy tiny ones). This is a pretty workable template, but you will lose a tiny bit on the right.

Save the following code as "dymo_99017.template" in your ~/.glabels directory.

```
<?xml version="1.0"?>
<Glabels-templates xmlns="http://snaught.com/glabels/2.2/">
  <Template brand="Dymo" part="99017" size="Other" width="20mm" height="50mm" description="Test">
    <Label-rectangle id="0" width="11mm" height="50mm" round="2mm" x_waste="0mm" y_waste="5mm">
      <Markup-margin size="0mm"/>
      <Layout nx="1" ny="1" x0="0mm" y0="-5mm" dx="9mm" dy="-10mm"/>
    </Label-rectangle>
  </Template>
</Glabels-templates>

```

Did you solve the tiny bit on the right size?
I have spend almost 40 labels and it is still not correct. And as in the [http://glabels.sourceforge.net/doc/templates-2.0/](http://glabels.sourceforge.net/doc/templates-2.0/) is told, the parameters do not add up as it should.

So if anyone can help me out

---

### Post by Keith_Beef on 2012-02-29
So it looks like we've got label printing working, but I'm still disappointed that I can't print tapes from my Dymo LaberWriter Duo.

---

### Post by Amedee on 2012-11-28
Hello to my fellow penguins!

I've been working as a software QA engineer for Newell Rubbermaid at the DYMO site in Belgium since March 2012, but I'm a Ubuntu user^Wmember since at least 2005 (see my [Launchpad profile]("https://launchpad.net/~amedee")). So you can sort of say that Linux infiltrated DYMO. ;-)

This topic appears in the top results when googling for DYMO+Linux.
I'm not going to give tech support here (there are other and better channels for that) and there are of course things that I can't comment on (Newell Rubbermaid's social media policy, Non-Disclosure Agreement, yada yada yada) but if there is any other way that I can help, gimme a shout and I'll see what I can do.

Meanwhile: rock on!
:guitar:

---

### Post by -ijk- on 2012-11-29
How about making the driver install automatic? (openprinting database)
It seems a bit weird that the drivers included with Ubuntu are different to the download on Dymos site.

---

### Post by Amedee on 2012-11-30
> **-ijk- said:**
> How about making the driver install automatic? (openprinting database)
It seems a bit weird that the drivers included with Ubuntu are different to the download on Dymos site.

Great idea, and as the drivers for the Mac version are already CUPS drivers, this should *in theory* be relatively easy to do.

HOWEVER. I don't know how, I don't know who to contact, I don't know what to provide.

Googling for "openprinting database" shows that there are already a few DYMO printers in the database, listed under Dymo-CoStar: [http://www.openprinting.org/printers/manufacturer/Dymo-CoStar](http://www.openprinting.org/printers/manufacturer/Dymo-CoStar)
That's a great start, but these are mostly older printers. Some (most?) of them are EOL.
I clicked around on the OpenPrinting website, but it wasn't really obvious how I can contribute.

Just to get this straight: I do this as a volunteer, I just happen to work at a printer manufacturer so I have access to all printer models. And I really should do this outside the office hours... nope... you know the 20% rule of Google? Something like that. ;-)

---

### Post by Naveedch on 2012-12-11
Guys I skimmed through the instructions in here, they are too complicated/confusing but follow this link:
[http://wiki.birth-online.de/know-how/hardware/dymo-labelwriter-320-under-ubuntu]("http://wiki.birth-online.de/know-how/hardware/dymo-labelwriter-320-under-ubuntu") These instructions are much easier to follow. Good luck!

---

### Post by bsantos on 2013-01-04
There is a new package that doesn't need any modifications with the latest gcc:

[http://www.dymo-label-printers.co.uk/dymo-cups-drivers-1.4.0.tar.gz](http://www.dymo-label-printers.co.uk/dymo-cups-drivers-1.4.0.tar.gz)

from here: [http://www.dymo-label-printers.co.uk/dymo_sdk_linux.html](http://www.dymo-label-printers.co.uk/dymo_sdk_linux.html)

I'm having issues with the top of the labels being cut off, is this normal?  I tried to change the PPD margins but it didn't work. Could it be an issue with the raster filter?

I'm using a LabelWriter 450.

---

### Post by Babbage on 2013-01-07
> I'm having issues with the top of the labels being cut off, is this normal? I tried to change the PPD margins but it didn't work. Could it be an issue with the raster filter?

I'm using a LabelWriter 450. 

Are you using GLabels? Have you selected the correct label type/size in the GLabels templates?
Here's how I got it working: [http://ubuntuforums.org/showpost.php?p=10085575&postcount=54](http://ubuntuforums.org/showpost.php?p=10085575&postcount=54)

---

### Post by bsantos on 2013-01-07
> **Babbage said:**
> Are you using GLabels? Have you selected the correct label type/size in the GLabels templates?
Here's how I got it working: [http://ubuntuforums.org/showpost.php?p=10085575&postcount=54](http://ubuntuforums.org/showpost.php?p=10085575&postcount=54)

There wasn't a template for this label, I was able to reduce the issue somehow by adding a negative label positioning in the template by hand (not ideal, maybe glabels could permit this). 
I also noticed that the first label pair isn't well positioned, but the other ones come out almost perfect (the top of the label has a ~2mm margin that I'm unable to remove, even when selecting the appropriate media size in cups).
See how the first pair is offset to the right in the picture, while the second one is centred. Also, the QR code is a bit (1 line?) cut out on the left side, so I can't use the whole label if I wanted to, but maybe that's normal. Is this an issue with the printer firmware and the way it feeds the first label pair in a print job, or is it with the driver/filter that converts the PS to raster for printing and sends the tape moving commands to the printer?

[IMG]http://i.imgur.com/fCzH9.jpg[/IMG]

---

### Post by Babbage on 2013-01-14
You can design your own template using the GLabels Template Designer, you can also manually design your own custom template:

> [3.6.&#8195;To Create a Custom Template]("http://library.gnome.org/users/glabels/2.2/glabels-usage.html.en#glabels-create-template")

To create a new custom template, choose File &#9656; Template Designer ... to display the Template Designer dialog. This dialog will assist you in creating a custom template for most types of label or card stationery that you may encounter.

If you prefer, you can create your templates manually. For this option see [Section 6 &#8213; Manually Creating New Templates]("http://library.gnome.org/users/glabels/2.2/glabels-manual-create-template.html.en") 

---

### Post by Berenscott on 2013-01-21
Hi, how exactly do you get the dymo printer  working from an XML output from a web browser? We have a template on our windows boxes and from within Internet explorer the server feeds an XML reply which prints the label. This process seems to only work in IE, how can I get this to function under ubuntu using an open source browser?

---

