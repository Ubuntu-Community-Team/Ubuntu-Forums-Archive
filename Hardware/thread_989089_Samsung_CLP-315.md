---
title: "Samsung CLP-315"
date: 2008-11-21
forum: Hardware
---

### Post by m0ntels on 2008-11-21
Anyone have any experience with this printer?  I was thinking of picking one up but I cant find much on people running it in Linux, only the older CLP-310.  I'm running Mint 5.0 with an Athalon XP 3000 and 1GB RAM.

---

### Post by jespdj on 2008-11-21
I saw this printer in a store a few days ago and wondered if it would work well with Linux.

I don't know, but looked it up on Samsung's website and the specs explicitly said that it works with Linux, so that's a good sign.

---

### Post by SujayV on 2009-03-25
> **m0ntels said:**
> Anyone have any experience with this printer?  I was thinking of picking one up but I cant find much on people running it in Linux, only the older CLP-310.  I'm running Mint 5.0 with an Athalon XP 3000 and 1GB RAM.

Hi There

I have just been given the clp-310 at no cost.  I will be attempting to install this on Ubunut Desktop, which is rather daunting for a newbie to linux.  Did you buy this printer ?  Were you able to make it work on Ubuntu ?  Do you have some tips on how to install the Samsung provided driver ?

Thanks and look forward to some help.

---

### Post by m0ntels on 2009-03-25
I did end up getting it on Black Friday.  I'm currently fighting with Samsung to get my $100 rebate. :(

So far it's been a nice printer.  I don't have any other printers to compare it to, but it prints well enough for me.  I set the quality low to save toner.

Installation is pretty straight forward...I think it's just a bash script that installs the drivers and you get the Samsung Smart Panel or something like that.  All it really does is say it's printing and has bar graphs showing how much toner is left.  It will work without the Sammy drivers, but it had been temperamental sometimes doing it that way.  The only big issue is I don't have it on unless I'm printing, and in Hardy and Intrepid I'd have to unplug and replug the USB cable to get it to see it was there.  Now I'm on Jaunty and it works great.  In fact I'm loving just about everything in Jaunty so far!

For the price you paid, you got a fine printer as far as I'm concerned.  Just try to plug and play it first and see if the printer applet sees it, which it should.

---

### Post by Pa Blum on 2009-09-10
I got a 315 recently and Jaunty installed it automatically and it came right up.  However, it's having color problems, with some being way, way too dark.  I think this is foomatic's fault, as it prints colors properly in its own testpage.

I thought I would try Samsung's CD Linux installation, but I can't get that to work because it INSISTS on being supplied an administrator-account named "Root", and I can't get Jaunty to let me create an administrator-account with that name.  It's a plot, I tells ya!

Also, it has the disconcerting habit of making my room lights flicker periodically unless it's in sleep mode.  Weird!

Conclusion: B&W is a breeze, color is a flop....

---

### Post by josvanr on 2009-10-06
The samsung clp-315w works out of the box (I only tried with usb cable though, 
as my wifi still doesn't work)
but it performs rather poorly in some respects

Printing black on white text works fine

Printing images (photos) is a different matter. I'm having the same trouble with the colors
as stated in previous posts.
They appear too dark and brown. Only way to get around it is to modify the image itself before 
printing it. Still also there is a lot of anti aliasing effects in the image, looking like it has been 
printed on a painting-canvas with raw structure. 

I really feel a bit cheated with this printer. I can't imagine that the images that roll out 
of it, as shown on the pictures on the samsung site, could have been actually printed on this machine. These
pictures are really misleading. They probably picked up an HP printer to print them on, and then 
stuck them in their own printer to shoot the ad picture. 

I'll probably just use the printer until the toner has run out, and buy a better one then... 



 

josvanr

---

### Post by josvanr on 2009-11-06
what helps is to edit the image to be printed in gimp, and:

- in dialog 'color levels' put the middle value of color levels to 2.5
- in dialog 'color balance' put value of 'blue' to 50

when I print the image like this it looks pretty ok. Does loose some 
dynamic range in the colors...

josvanr

---

### Post by Addiso on 2009-11-06
Anyone try to use the Samsung drivers for this?

I'm using Ubuntu 9.10.

---

### Post by josvanr on 2009-11-12
i'm now on ubuntu 9.10. The driver that comes with ubuntu (clp 310/315) doesn't work (printer prints a page with text 'pleas use proper driver').. Will be installing samsung's driver again..

---

### Post by upuaut on 2009-12-16
confirming the canvas effect and the too-dark colour.

doing as explained in
[http://www.xappsoftware.com/wordpres.../clp315karmic/]("http://www.xappsoftware.com/wordpress/2009/11/11/clp315karmic/")
makes the printer work, but does not solve the image quality problem.

Any ideas any1?
If i find a solution, i'll post it here.

---

### Post by batterybaby on 2009-12-16
it  does not work very well ,though.

---

### Post by RINKO on 2010-01-16
i used these directions
[http://foo2qpdl.rkkda.com/](http://foo2qpdl.rkkda.com/)
i can print perfectly from the internet and i have to update my spool or cups so that i can print from office but its worked so far for me.


UPDATE:
Make sure you do follow the directions to a T.  It is a well written step by step install.. i just forgot to make the cups for my printer
now im good.
Good luck

---

### Post by kleinebre on 2010-05-05
> **upuaut said:**
> confirming the canvas effect and the too-dark colour.

doing as explained in
[http://www.xappsoftware.com/wordpres.../clp315karmic/]("http://www.xappsoftware.com/wordpress/2009/11/11/clp315karmic/")
makes the printer work, but does not solve the image quality problem.

Any ideas any1?
If i find a solution, i'll post it here.

Yes. On my Hardy machine things printed fine after the Samsung driver installation whereas on Jaunty things still printed too dark even then. 

Using the Samsung drivers was tricky by the way; complaints that it can't find Qt. Solved by starting the program from the i386 folder in the Samsung drivers. Still the same trouble. Couldn't be bothered to do anything complex; what sorted out the colour in the end was using the CLP310 driver (after installing the Samsung ones). 

Hope this helps someone.

---

### Post by Rob Glenn on 2010-06-08
I was getting really horrible aliasing effects printing images with the foo2qpdl driver.  Switching to the SPL driver ("Samsung CLP-310 series (SPL-C)") produced quality results.

---

### Post by mozkill on 2011-01-08
I just bought a Samsung CLP-315w printer and it worked perfectly with Ubuntu 10.10 . 

Both the printer and my PC are both connected wirelessly to my network on a Netgear hub.

---

### Post by kleinebre on 2011-09-30
I have this printer and had the dark printing issue as well. Apparently it has something to do with the *kind* of driver being installed. Instead of insisting on the specific CLP-315 driver, what worked for me was to use the CLP310 *series* driver. Here are the steps I just followed to get this working on an ubuntu 11.04 install (although I pretty much followed the same steps on 10.4LTS and before):

- Go to the Samsung website and choose Support/Downloads. Search for your printer number (CLP-315). On tab Downloads/subtab driver, download thec ompressed archive on the line "unified driver for Linux". If you can't find it, try this direct link: [http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=UNI_UK&CttFileID=2031913&CDCttType=DR&ModelType=N&ModelName=CLP-315&VPath=DR/200911/20091106134900421/UnifiedLinuxDriver_1.00.tar.gz](http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=UNI_UK&CttFileID=2031913&CDCttType=DR&ModelType=N&ModelName=CLP-315&VPath=DR/200911/20091106134900421/UnifiedLinuxDriver_1.00.tar.gz)

Start a terminal and cd to the download directory, then
- mkdir samsungclp
- cd samsungclp
- tar xvfz ../UnifiedLinuxDriver_1.0.0.tar.gz
- cd cdroot/Linux
- sudo ./install.sh

Choose the options relevant for your printer (usb vs network etc).
When asked for the model, many of them are listed. Note that the CLP315 is not in the list, so we type this model number: 

CLP-310splc

(this may be case sensitive so mind upper/lower case).

The cups driver etc will now be set and installed, and a printer entry will be created automatically.

Finally we edit that printer entry.

System->Administration->Printing

In my case I've got a wireless printer and the device URI I've set is 
ipp://192.168.1.9
(192.168.1.9 is the IP address of my printer on the home network)
For "make and model" I choose "Samsung CLP-310 Series (SPL-C)"

Finally, I print a test page and notice that the colour balance is a LOT better than before!

Hope this helps someone!

Edit 1 - By the way, Rob Glenn- your previous post may have pointed me to that solution. Thanks!
Edit 2 - I ran the above commands from a remote terminal without access to X which caused the installer to run in text mode. No further complaints about Qt missing!

Best,
Marc

---

### Post by laercio on 2011-12-27
> **kleinebre said:**
> I have this printer and had the dark printing issue as well. Apparently it has something to do with the *kind* of driver being installed. Instead of insisting on the specific CLP-315 driver, what worked for me was to use the CLP310 *series* driver. Here are the steps I just followed to get this working on an ubuntu 11.04 install (although I pretty much followed the same steps on 10.4LTS and before):

- Go to the Samsung website and choose Support/Downloads. Search for your printer number (CLP-315). On tab Downloads/subtab driver, download thec ompressed archive on the line "unified driver for Linux". If you can't find it, try this direct link: [http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=UNI_UK&CttFileID=2031913&CDCttType=DR&ModelType=N&ModelName=CLP-315&VPath=DR/200911/20091106134900421/UnifiedLinuxDriver_1.00.tar.gz](http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=UNI_UK&CttFileID=2031913&CDCttType=DR&ModelType=N&ModelName=CLP-315&VPath=DR/200911/20091106134900421/UnifiedLinuxDriver_1.00.tar.gz)

Start a terminal and cd to the download directory, then
- mkdir samsungclp
- cd samsungclp
- tar xvfz ../UnifiedLinuxDriver_1.0.0.tar.gz
- cd cdroot/Linux
- sudo ./install.sh

Choose the options relevant for your printer (usb vs network etc).
When asked for the model, many of them are listed. Note that the CLP315 is not in the list, so we type this model number: 

CLP-310splc

(this may be case sensitive so mind upper/lower case).

The cups driver etc will now be set and installed, and a printer entry will be created automatically.

Finally we edit that printer entry.

System->Administration->Printing

In my case I've got a wireless printer and the device URI I've set is 
ipp://192.168.1.9
(192.168.1.9 is the IP address of my printer on the home network)
For "make and model" I choose "Samsung CLP-310 Series (SPL-C)"

Finally, I print a test page and notice that the colour balance is a LOT better than before!

Hope this helps someone!

Edit 1 - By the way, Rob Glenn- your previous post may have pointed me to that solution. Thanks!
Edit 2 - I ran the above commands from a remote terminal without access to X which caused the installer to run in text mode. No further complaints about Qt missing!

Best,
Marc

I have conection problem since last cups upgrade. Using ubuntu 11.10. Problem reported is related to SANE (can't be reached, I guess)wich is propoerly installed.

---

### Post by routed on 2011-12-27
I use a clp-315 on Ubuntu 10.04. I wish I could remember how I installed the drivers ( I think I got the one from Samsung). The printer works with no issue, so it is possible. I use the printer to print chemical drum labels and it works great. The only problem that I have had with it was a paper feed sensor that went out (cheap fix).

---

### Post by laercio on 2012-01-13
> **routed said:**
> I use a clp-315 on Ubuntu 10.04. I wish I could remember how I installed the drivers ( I think I got the one from Samsung). The printer works with no issue, so it is possible. I use the printer to print chemical drum labels and it works great. The only problem that I have had with it was a paper feed sensor that went out (cheap fix).

You certainly use the Samsung driver. And I agree with U, it used to work fine, till the cups upgrade in december. Something happened to SANE and I try to fix since then without success.

---

### Post by ThomasT2 on 2012-04-02
My Samsung CLP-315 also had a number of issues: It printed darker, it sometimes used a wrong font, it jammed after printing one job (turning it off and back on always solved that though) and additionally, printing over the network (CUPS) worked, but there seemed to be an offset (content moved to the right, so that there's white space on the left side and parts cut off on the right). OS is Ubuntu 11.10, everything up to date as of April 2012. The system always recognized the printer as CLP-310. Googling turned up nothing.

I found a solution, but it was a bit tricky to do so I signed up here to share it with others.

I downloaded the Samsung Linux Driver - the installer terminated during startup without an error message.  It turned out to need admin privileges, but never asks for them. Had to start it from terminal with sudo("sudo sh autorun"). Installation went fine, but the Samsung Linux Driver was unable to detect my printer, even though the system did recognize it.
I then manually added the new driver to the printer within the Ubuntu system. Go to System Settings > Printing > right-click printer > properties > make and model change > provide PPD > Select file: /opt/Samsung/mfp/share/ppd/CLP-310splc.ppd (path might be different if you didn't use the default installation path)

Save your changes, it should work now. You might have to restart the printer. This also solves the network printing problems.

---

### Post by kleinebre on 2013-03-03
> **laercio said:**
> I have conection problem since last cups upgrade. Using ubuntu 11.10. Problem reported is related to SANE (can't be reached, I guess)wich is propoerly installed.

UPDATE: Previously I found and posted a way to get the CLP-315w to print normally under Ubuntu 10.04.
My wife has upgraded to 12.04 or so, and, sure enough, found the printer to print too dark again. Man, was I happy to have posted this before, as I thought I'd helped myself by doing so. 
Tough luck though.

During installation, the old 2009 Samsung driver now complains about not being able to find the SANE library.
Looking into the installer code, it searches for a file called libsane.so.1 which under later versions of Ubuntu no longer seems to live under the same library path. Under 10.4 it's in /usr/lib whereas in 12.x it's under /usr/lib/i386-linux-gnu/ (probaby something changed due to differentiation between 32-bit/64-bit versions there; in any case, this is still under a 32-bit version of 12.04).

Creating a symbolic link for libsane from /usr/lib/i386-linux-gnu to /usr/lib :

sudo ln -s  /usr/lib/i386-linux/gnu/libsane.so.1 /usr/lib/libsane.so.1

Sure enough, this suppressed the error during install time (since this operation satisfies the check being done during install time) yet when sending a page to the printer, simply nothing happens. Checking out the cups log, 

cat /var/log/cups/error-log
or 
tail -n 20 /var/log/cups/error-log

still shows the same "filter error" of sorts, essentially mentioning that file /usr/lib/cups/filter/rastertosamsungsplc segfaulted (code 11).

I'll post if I find out anything else.
Black and white prints are still fine, and with the foomatic driver it's still possible to print colour (albeit fugly dark) and at least works, sort of.

Meanwhile if someone runs into a solution to this issue that properly solves this and makes prints look decent, I'll be glad to hear about it.

Suggestions?

---

### Post by grege on 2013-03-03
I have found that older Samsung drivers need the older version of libstdc++ - version 5.

It is still in the repositories and can be installed along side the newer version.

That is using Samsung's drivers

[http://www.samsung.com/us/support/owners/product/CLP-315/XAA](http://www.samsung.com/us/support/owners/product/CLP-315/XAA)

---

