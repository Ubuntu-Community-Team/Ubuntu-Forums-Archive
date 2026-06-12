---
title: "Canon MP600 - Anyone get it working in Ubuntu"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by BajanAlan on 2007-05-28
Hi Ubuntu users
Has anyone got the MP600 to work yet?
Regards Alan

---

### Post by easy_target on 2007-06-01
Hi,

I've tried downloading the drivers from canon australia ([http://canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx](http://canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx)) and used alien to convert them, to no avail since I don't have the technical knowledge necessary to make it work. 
I can print, though, using the drivers that come with Ubuntu for the Canon Multipass MP500 with decent results. I had to tweak the brightness and saturation a little bit to get appropriate colors. Let me know if you find something else that works!

Cheers!

---

### Post by hummingbird59 on 2007-06-01
The MP500 driver works as previous poster noted and is the easiest route by far.  Also, the IP4200 driver works well too.  See [http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600).  You may have to download and install some rpm files and use alien to convert them to deb.  AS far I know, the scanner is not supported by xsane although there are drivers out there in the early stages, ie you will have to compile them yourself.  Google Canon Pixma MP 600 and you will find a wealth of info.  Good luck.  

P.S.  If you can print good photos without buying Turboprint ( not worth it IMHO) and/or scan without building your own driver, please post a how-to.  Thanks and hope this is helpful!

BTW Easy-Target:  The drivers from the au website are giving others fits too.  There is a bug report filed on launchpad [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/114708](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/114708).

---

### Post by easy_target on 2007-06-01
All right, I think I got that to work:

Download the files "cnijfilter-common-2.70-1.i386.rpm" and "cnijfilter-mp600-2.70-1.i386.rpm" from [here]("http://canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx") 

Produce deb packages with alien
```
sudo alien cnijfilter-common-2.70-1.i386.rpm
sudo alien cnijfilter-mp600-2.70-1.i386.rpm --scripts
```

Install required packages
```
sudo apt-get install libxml1
sudo apt-get install libglib1.2
sudo apt-get install libtiff4
```

Use dpkg for installing the resulting packages

Create some symbolic links
```
sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```

Restart CUPS
```
sudo /etc/init.d/cupsys restart
```

Setting up the printer:

Go to System -> Administration -> Printing

1. Double-click "New Printer"
2. Select option "Canon MP600 (USB Printer #1 with status readback for Canon IJ)" , click forward
3. If the driver option "MP600 Ver.2.70" is not available in the list, select "Install driver" at the bottom and locate it at "/usr/share/cups/model/canonmp600.ppd"

Follow the remainder of the process to completion and print a test page to make sure that it is working.  Printer works perfectly for me now, let me know if something doesn't work as expected.

Cheers!

---

### Post by hummingbird59 on 2007-06-01
Beauitful!  I'll try it this weekend - I may have only done half of what you describe.  Can't really remember bc I've tried so many things!  Anyway, thanks for the step-by-step!  Here's hoping:D

---

### Post by hummingbird59 on 2007-06-05
Hello!  I just thought I would post a follow-up!

After trying to follow Easy-Target's much appreciated guide, I am sad to say it did not work for me.:(  I am 85% sure that I did not do everything just right because I got some error messages along the way.  Anyway, the printer shows up, the MP600 driver 2.70 shows up... etc... but the printer fails to print.  I have attached some screenshots if anyone is interested and/or can shed some light on what I have missed.  Ayway, the MP 500 driver works well enough such that it is not the end of the world if I cannot get this driver to work.  I was really trying to see if it could print quality photos as none of the other drivers I have tried can.  Anyway, I have some questions too if anyone can answer?

1.  Easy_Target gave me some packages and symbolic links to install and create:

 Install required packages
```
sudo apt-get install libxml1
sudo apt-get install libglib1.2
sudo apt-get install libtiff4
```

Use dpkg for installing the resulting packages

Create some symbolic links
```
sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```

 How do you know how to do this?  Where does this info come from?  Forgive me if I should know this !

2.  There is a scanner driver on the autralian website - has anyone gotten it to work?  If so, how?

3.  Are photos of good quality using this driver bc that it really all I was interested in!

Thank you again Easy_Target!:)  I am sure I have much to learn! I will continue trying with this driver......

---

### Post by easy_target on 2007-06-06
Hmmm.. maybe I have forgotten some of the symlinks... 
Try doing this:

```
cd /usr/lib 
sudo ln -s libpng12.so.0 libpng.so.2
sudo ln -s libtiff.so.4 libtiff.so.3
sudo ln -s libxml2.so.2 libxml.so.1
```


There are also instructions for the scanner somewhere. I will see if I can find them and post them here.

---

### Post by hummingbird59 on 2007-06-07
Hello!  I did this - still no dice even though it says "file exists" (I assume that is good, eh?):

melanie@atlasinstall:~$ cd /usr/lib
melanie@atlasinstall:/usr/lib$ sudo ln -s libpng12.so.0 libpng.so.2
ln: creating symbolic link `libpng.so.2' to `libpng12.so.0': File exists
melanie@atlasinstall:/usr/lib$ sudo ln -s libtiff.so.4 libtiff.so.3
ln: creating symbolic link `libtiff.so.3' to `libtiff.so.4': File exists
melanie@atlasinstall:/usr/lib$ sudo ln -s libxml2.so.2 libxml.so.1
ln: creating symbolic link `libxml.so.1' to `libxml2.so.2': File exists
melanie@atlasinstall:/usr/lib$ 

Thank you very much for your efforts!

---

### Post by tzahov on 2007-06-07
I found this and and got it working with the new mp600 drivers, very usefull:

[http://66.249.91.104/translate_c?hl=en&u=http://blog.livedoor.jp/shobondama/archives/54385500.html&prev=/search%3Fq%3Dmp600%2Bkubuntu%2Balien%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:eek:fficial%26hs%3DEe7%26sa%3DG](http://66.249.91.104/translate_c?hl=en&u=http://blog.livedoor.jp/shobondama/archives/54385500.html&prev=/search%3Fq%3Dmp600%2Bkubuntu%2Balien%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:eek:fficial%26hs%3DEe7%26sa%3DG)

It is in japanese, but translated. Here is the copy -paste of the text:


With Ubuntu Canon MP600 printer driver re-installation
sudo apt-get install alien libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common
sudo alien - c cnijfilter-common-2.70-1.i386.rpm cnijfilter-mp600-2.70-1.i386.rpm
sudo dpkg - i cnijfilter-*.deb
sudo ln - s /usr/lib/libpng12.so.0.15.0 /usr/lib/libpng.so.3
sudo ln - s /usr/lib/libtiff.so.4.2.1 /usr/lib/libtiff.so.3
sudo ln - s /usr/lib/libxml.so.1.8.17 /usr/lib/libxml.so.1
sudo ldconfig
sudo /etc/init.d/cupsys restart

In case of me it was not necessary to stretch symbolic link. (It was stretched already)
With “the system -> system management -> adding USB_Printer_1_with_status_readback_for_Canon_IJ or MP600-Ver.2.70 the printer” of the Gnome panel.
In case of which selecting the driver MP600-Ver.2.70.
Addition of the printer ends with this.
cngpij - P USB_Printer_1_with_status_readback_for_Canon_IJ
Or
cngpij - P MP600-Ver.2.70
So the Canon genuine printer utility starts. (As for illegal character cancellation this: [http://66.249.91.104/translate_c?hl=en&u=http://blog.livedoor.jp/shobondama/archives/54111114.html&prev=/search%3Fq%3Dmp600%2Bkubuntu%2Balien%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:eek:fficial%26hs%3DEe7%26sa%3DG](http://66.249.91.104/translate_c?hl=en&u=http://blog.livedoor.jp/shobondama/archives/54111114.html&prev=/search%3Fq%3Dmp600%2Bkubuntu%2Balien%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:eek:fficial%26hs%3DEe7%26sa%3DG)

Either command is used, it added the printer of either name depending upon.
In case of me, because USB_Printer_1_with_status_readback_for_Canon_IJ was added,

/etc/cups/ppd/USB_Printer_1_with_status_readback_for_Canon_IJ.ppd

Has been completed.
Opening this file, it expands the setting range such as printing quality and resolution.

sudo gedit /etc/cups/ppd/USB_Printer_1_with_status_readback_for_Canon_IJ.ppd

*OpenUI *Resolution/Output Resolution: 3 lines below are added to the section which starts with PickOne.
*Resolution 1200/1200 dpi: “<>>setpagedevice”
*Resolution 2400/2400 dpi: “<>>setpagedevice”
*Resolution 4800/4800 dpi: “<>>setpagedevice”
The following section is added anew under the truth of this section. (Total 7 lines)
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: “2”
*CNQuality 3/Normal: “3”
*CNQuality 4/Standard: “4”
*CNQuality 5/Economy: “5”
*CloseUI: *CNQuality

And

sudo /etc/init.d/cupsys restart

Now “the system -> system management -> the printer” of the Gnome panel menu empty it reaches the point where it can do various setting.
The place where it refers:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

---

### Post by hummingbird59 on 2007-06-07
Hello tzahov!  Thanks for the post!  I am trying to figure out where to put this:



[QUOTE=tzahov;2802722]The following section is added anew under the truth of this section. (Total 7 lines)
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: “2”
*CNQuality 3/Normal: “3”
*CNQuality 4/Standard: “4”
*CNQuality 5/Economy: “5”
*CloseUI: *CNQuality

Sorry for my ignorance:)

Just for laughs - this is the first time I've had more than twenty windows open.  Under WINDOZ, my computer would have crashed long ago.....:lolflag:

Also, my ppd file I am adding this too is read only - how do I change it?  Thanks!


[COLOR="Red"]UPDATE:  I changed my ppd filed, saved it etc...  Printer gets stuck on "printing" but  does not print.  I think I am just unlucky or wrong or tired or all of the above..... Will try later.  Thank you for your help![/COLOR]](*,)

---

### Post by tzahov on 2007-06-08
Hm, what do you try to print? Try to print a test page.

---

### Post by hummingbird59 on 2007-06-08
Hello again! 

I always try to print a test page first and then an open office doc.  Neither works.  It literally gets stuck on "printing", ie my printer icon pops up in the tray as if printing is happening but it will stay that way forever without printing anything???

[COLOR="RoyalBlue"]EDIT:  I want to thank you Easy Target and tzahov for your help.  My MP 600 prints doc beautifully with the 500 driver so I am going to stick with that for now.  As for photos, I know this a bit tricky.  Fortunately, I have an HP Photosmart that works very well and I can print photos via sd card if I need to.  As for the scanner, I have used it maybe three times in six months.  So, I am happy that my printer just works.  It didn't in Dapper, but did in Edgy and Feisty which is the only reason I was able to come to Linux.  I'm thinking Gutsy will offer even more hdwre support.  I  am truly amazed and thrilled to have gotten this far.  So, thanks to everyone who made my switch possible - Seriously - thank you!  I was so tired of XP (it took an hour to load on my six year old computer and I could only have a few windows open at a given time or my computer would get really loud.  With Ubuntu, it loads in seconds and is as quiet as a mouse.  I LOVE it even though I do have some small probs like this printer thing.)  Bottom line:  **Thank you** for your kind help - I'll keep using Ubuntu and see if Gutsy helps with my Canon.  If it doesn't I might just trade the Canon in for an HP  [/COLOR]:D

---

### Post by samlown on 2007-06-09
Hi, I too have been fighting a bit with my MP600, with similar symptoms to those above.

No matter how many times I tried to send a job to the printer, CUPS would just pretend to have sent and the printer would say nothing. However, after playing with the connection panel in the Ubuntu/gnome printer properties setup, I selected the "Use another printer by specifying a port" and selected the simple "Canon MP600 USB #1 (Canon MP600)" option, the printer started accepting my print jobs.

Hope this helps, its not very technical I'm affraid!

Cheers, sam

---

### Post by samlown on 2007-06-09
.... nope sorry, that was a lie, turned out I had another driver selected ... However, here's how I *really* managed to get it working:

First, I enabled debug mode in CUPS: (I use vi, you can use any editor provided you use sudo in-front)

```

sudo vi /etc/cups/cupsd.conf

```

Change the LogLevel at the top of the file from ```
warning
``` to ```
debug
```.

restart CUPS:

```

sudo /etc/init.d/cupsys restart

```
 
Now use tail to see what the CUPS error log is spitting out:

```

sudo tail -f /var/log/cups/error_log

```

You'll see a lot of info, which you can safely ignore.

In the printer properties window, click to send a test page, and shortly after press CTRL+C in the terminal window to stop the tail command reading from the CUPS error log. Look for something like the following:

```

D [09/Jun/2007:20:56:09 +0200] [Job 13] pstocanonij: /usr/bin/gs -r600 -g4958x7016 -q -dNOPROMPT -dSAFER -sDEVICE=ppmraw -sOutputFile=- -| /usr/local/bin/cifmp600 --imageres 600 --papersize a4 --media plain --paperload switch --bbox 9,14,585,834 
D [09/Jun/2007:20:56:09 +0200] [Job 13] Printer using device file "/dev/usblp0"...
D [09/Jun/2007:20:56:09 +0200] Discarding unused printer-state-changed event...
D [09/Jun/2007:20:56:09 +0200] [Job 13] backendRunLoop(print_fd=0, device_fd=4, use_bc=0)
D [09/Jun/2007:20:56:09 +0200] [Job 13] /usr/local/bin/cifmp600: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

```

Here we can see that the filter command can't find the libpng.so.3 file. You may get something different, the general idea though is to find out what is missing for the cifmp600 command to function correctly. In this case, it looks like I need to install libpng3.

```

sudo apt-get install libpng3

```

Run the tail command again and press the print test button. In my case it started working perfectly!

After you're working again, don't forget to set the cups.conf log level to its previous setting, otherwise you're log files will start getting very large very quickly!

Hope this helps!
Cheers, sam

---

### Post by hummingbird59 on 2007-06-09
Alright - here is a sampling of what I get:

D [09/Jun/2007:14:21:49 -0500] Get-Printer-Attributes ipp://localhost/printers/LaserJet-6L
D [09/Jun/2007:14:21:49 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:49 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:21:49 -0500] cupsdAuthorize: No authentication data provided.
[B]D [09/Jun/2007:14:21:49 -0500] Get-Printer-Attributes ipp://localhost/printers/MP600-Ver.2.70
D [09/Jun/2007:14:21:49 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:49 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:21:49 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:49 -0500] Get-Printer-Attributes ipp://localhost/printers/MULTIPASS-MP500
D [09/Jun/2007:14:21:49 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:50 -0500] cupsdAcceptClient: 10 from localhost (Domain)
D [09/Jun/2007:14:21:50 -0500] cupsdCloseClient: 8
D [09/Jun/2007:14:21:50 -0500] cupsdReadClient: 10 POST /printers/MP600-Ver.2.70 HTTP/1.1
D [09/Jun/2007:14:21:50 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:50 -0500] Print-Job ipp://localhost/printers/MP600-Ver.2.70
D [09/Jun/2007:14:21:50 -0500] print_job: auto-typing file...
D [09/Jun/2007:14:21:50 -0500] print_job: request file type is application/postscript.
D [09/Jun/2007:14:21:50 -0500] add_job: requesting-user-name="melanie"
D [09/Jun/2007:14:21:50 -0500] Adding default job-sheets values "none,none"...
I [09/Jun/2007:14:21:50 -0500] Adding start banner page "none" to job 113.
D [09/Jun/2007:14:21:50 -0500] Discarding unused job-created event...
I [09/Jun/2007:14:21:50 -0500] Adding end banner page "none" to job 113.
I [09/Jun/2007:14:21:50 -0500] Job 113 queued on "MP600-Ver.2.70" by "melanie".
D [09/Jun/2007:14:21:50 -0500] Job 113 hold_until = 0
D [09/Jun/2007:14:21:50 -0500] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:54 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [09/Jun/2007:14:21:54 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:54 -0500] CUPS-Get-Printers
D [09/Jun/2007:14:21:54 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:54 -0500] cupsdReadClient: 6 POST / HTTP/1.1
[/B]D [09/Jun/2007:14:21:54 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:54 -0500] Get-Printer-Attributes ipp://localhost/printers/LaserJet-6L
D [09/Jun/2007:14:21:54 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:54 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [09/Jun/2007:14:21:54 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:54 -0500] Get-Printer-Attributes ipp://localhost/printers/MP600-Ver.2.70
D [09/Jun/2007:14:21:54 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:54 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [09/Jun/2007:14:21:54 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:54 -0500] Get-Printer-Attributes ipp://localhost/printers/MULTIPASS-MP500
D [09/Jun/2007:14:21:54 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:54 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:21:54 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:54 -0500] CUPS-Get-Printers
D [09/Jun/2007:14:21:54 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:54 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:21:54 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:54 -0500] Get-Printer-Attributes ipp://localhost/printers/LaserJet-6L
D [09/Jun/2007:14:21:54 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:54 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:21:54 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:54 -0500] Get-Printer-Attributes ipp://localhost/printers/MP600-Ver.2.70
D [09/Jun/2007:14:21:54 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:54 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:21:54 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:54 -0500] Get-Printer-Attributes ipp://localhost/printers/MULTIPASS-MP500
D [09/Jun/2007:14:21:54 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:59 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [09/Jun/2007:14:21:59 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:59 -0500] CUPS-Get-Printers
D [09/Jun/2007:14:21:59 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:59 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [09/Jun/2007:14:21:59 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:59 -0500] Get-Printer-Attributes ipp://localhost/printers/LaserJet-6L
D [09/Jun/2007:14:21:59 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:59 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [09/Jun/2007:14:21:59 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:59 -0500] Get-Printer-Attributes ipp://localhost/printers/MP600-Ver.2.70
D [09/Jun/2007:14:21:59 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:59 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [09/Jun/2007:14:21:59 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:59 -0500] Get-Printer-Attributes ipp://localhost/printers/MULTIPASS-MP500
D [09/Jun/2007:14:21:59 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:59 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:21:59 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:59 -0500] CUPS-Get-Printers
D [09/Jun/2007:14:21:59 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:59 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:21:59 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:59 -0500] Get-Printer-Attributes ipp://localhost/printers/LaserJet-6L
D [09/Jun/2007:14:21:59 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:59 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:21:59 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:59 -0500] Get-Printer-Attributes ipp://localhost/printers/MP600-Ver.2.70
D [09/Jun/2007:14:21:59 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:21:59 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:21:59 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:21:59 -0500] Get-Printer-Attributes ipp://localhost/printers/MULTIPASS-MP500
D [09/Jun/2007:14:21:59 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:22:04 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [09/Jun/2007:14:22:04 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:22:04 -0500] CUPS-Get-Printers
D [09/Jun/2007:14:22:04 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [09/Jun/2007:14:22:04 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [09/Jun/2007:14:22:04 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:22:04 -0500] Get-Printer-Attributes ipp://localhost/printers/LaserJet-6L
D [09/Jun/2007:14:22:04 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [09/Jun/2007:14:22:04 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [09/Jun/2007:14:22:04 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:22:04 -0500] Get-Printer-Attributes ipp://localhost/printers/MP600-Ver.2.70
D [09/Jun/2007:14:22:04 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [09/Jun/2007:14:22:04 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [09/Jun/2007:14:22:04 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:22:04 -0500] Get-Printer-Attributes ipp://localhost/printers/MULTIPASS-MP500
D [09/Jun/2007:14:22:04 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [09/Jun/2007:14:22:04 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:22:04 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:22:04 -0500] CUPS-Get-Printers
D [09/Jun/2007:14:22:04 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:22:04 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:22:04 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:22:04 -0500] Get-Printer-Attributes ipp://localhost/printers/LaserJet-6L
D [09/Jun/2007:14:22:04 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:22:04 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:22:04 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:22:04 -0500] Get-Printer-Attributes ipp://localhost/printers/MP600-Ver.2.70
D [09/Jun/2007:14:22:04 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [09/Jun/2007:14:22:04 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [09/Jun/2007:14:22:04 -0500] cupsdAuthorize: No authentication data provided.
D [09/Jun/2007:14:22:04 -0500] Get-Printer-Attributes ipp://localhost/printers/MULTIPASS-MP500
D [09/Jun/2007:14:22:04 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)

The BOLD is what I think is relevant but I am not sure?  It looks to me like I am still missing something???

Thanks again!

P.S. Sorry Bajaalan for hijacking this thread:)

---

### Post by samlown on 2007-06-10
Oh, thats strange, it doesn't look like the job you sent even gets to the filter program. Double check the printer entry to ensure that it is not on-hold/stopped.

Also, have a look at the CUPS web interface: [http://localhost:631](http://localhost:631) that can often provide a little bit more information on its state. You can also try removing the printer entry and re-installing to see if that helps. (Sounds a bit desperate, but its the easiest way to reset configuration values to their defaults.)

Looking at my logs, you should get something similar to following from where your log entry stops:

```

I [09/Jun/2007:20:58:59 +0200] Job 14 queued on "CanonMP600" by "sam".
D [09/Jun/2007:20:58:59 +0200] Job 14 hold_until = 0
D [09/Jun/2007:20:58:59 +0200] Discarding unused printer-state-changed event...
D [09/Jun/2007:20:58:59 +0200] job-sheets=none,none
D [09/Jun/2007:20:58:59 +0200] banner_page = 0
D [09/Jun/2007:20:58:59 +0200] [Job 14] argv[0]="CanonMP600"
D [09/Jun/2007:20:58:59 +0200] [Job 14] argv[1]="14"
D [09/Jun/2007:20:58:59 +0200] [Job 14] argv[2]="sam"
D [09/Jun/2007:20:58:59 +0200] [Job 14] argv[3]="Test Page"
D [09/Jun/2007:20:58:59 +0200] [Job 14] argv[4]="1"
etc. etc. etc.

```

Good luck! sam

---

### Post by hummingbird59 on 2007-06-10
Thank you Sam!  I have done all of these things many times over.  I am even considering a complete reinstall of Feisty but not just yet.  Anyway, thank you for your help!  It is much appreciated.  If I have any success, I will post.  Thanks to all!

---

### Post by zero-9376 on 2007-06-13
The scanner drivers worked for me on edgy, yet to try on feisty as my MP510 is being repaired at the moment. Im am pretty sure I put instructions on how to get it to work in another post

---

### Post by hummingbird59 on 2007-06-14
Thanks for the post Zero-9376!  When I try to install the scanner deb files, dpkg puts them in usr/lib (see screenshot).  Shouldn't they be going into usr/bin?  I suspect the same problem with my printer deb files.  Does anyone know why or what I am doing wrong?  Thanks in advance!

[COLOR="Blue"]EDIT:  I shoud also mention that when I ask dpkg (dpkg  -L) to check my installation, it tells me files are not installed but see the screenshot and sure enough there they are??? [/COLOR]

---

### Post by hummingbird59 on 2007-06-16
Hello all!  I FINALLY got my scanner to work!!!!!!!!!!!  I followed Easy Target's instructions from [http://ubuntuforums.org/showthread.php?t=371573&highlight=can%27t+set+up+my+canon](http://ubuntuforums.org/showthread.php?t=371573&highlight=can%27t+set+up+my+canon) (post #5 specifically, changed my udev file as stated by mgmiller in post #7) and I am off and running.  THANK YOU easy target and mgmiller!  Now, for those printer drivers.......

---

### Post by simple simon on 2007-07-12
> **samlown said:**
> Oh, thats strange, it doesn't look like the job you sent even gets to the filter program. Double check the printer entry to ensure that it is not on-hold/stopped.

Also, have a look at the CUPS web interface: [http://localhost:631](http://localhost:631) that can often provide a little bit more information on its state. You can also try removing the printer entry and re-installing to see if that helps. (Sounds a bit desperate, but its the easiest way to reset configuration values to their defaults.)

Looking at my logs, you should get something similar to following from where your log entry stops:

```

I [09/Jun/2007:20:58:59 +0200] Job 14 queued on "CanonMP600" by "sam".
D [09/Jun/2007:20:58:59 +0200] Job 14 hold_until = 0
D [09/Jun/2007:20:58:59 +0200] Discarding unused printer-state-changed event...
D [09/Jun/2007:20:58:59 +0200] job-sheets=none,none
D [09/Jun/2007:20:58:59 +0200] banner_page = 0
D [09/Jun/2007:20:58:59 +0200] [Job 14] argv[0]="CanonMP600"
D [09/Jun/2007:20:58:59 +0200] [Job 14] argv[1]="14"
D [09/Jun/2007:20:58:59 +0200] [Job 14] argv[2]="sam"
D [09/Jun/2007:20:58:59 +0200] [Job 14] argv[3]="Test Page"
D [09/Jun/2007:20:58:59 +0200] [Job 14] argv[4]="1"
etc. etc. etc.

```

Good luck! sam

samlown

Would you be so kind to as to post a larger chunk of your cups error_log.  I have a similar problem as hummingbird59 and my error_log has none of the above in it.  I am hoping that if I see a log for a working printer I might be able to work out what is going wrong.

Many thanks,

Simon.

---

### Post by frychiko on 2007-07-23
I just selected the MP500 drivers and in the driver box below just (something) simple, there were only two options.

Printing is working fine. I haven't tested scanning yet.

---

### Post by Kristen86 on 2007-07-24
Hi everyone,

I am pretty new to ubuntu, as I recently got a new computer with ubuntu already installed after using windows for years (and yes, I complained about how much I hated it all those years too, but was too lazy to get my finger out and install ubuntu).

Anyway, my only problem so far is my printer, I have the MP600 and found that the MP500 driver didn't work well for me. When I printed PDF's, they would print out half the size (and nothing I changed would help) and I found I lost alot of the printer functionality (which is what I bought it for!). So I have been booting into windows just to print, which pi$$es me off!

Did anyone have much luck with anything but the MP500 driver? Or can anyone tell me why the MP500 driver is doing what it's doing?

Thanks ;)

---

### Post by Wyrm_1972 on 2007-07-25
I, too, found the MP500 just not quite right. Currently gave up and am using...

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

The free version allows you to print at draft quality but for higher quality you have to pay (30 euro). I'm happy at draft quality for now, and it was very easy to install and use.

---

### Post by Wyrm_1972 on 2007-07-26
> **tzahov said:**
> I found this and and got it working with the new mp600 drivers, very usefull:

With Ubuntu Canon MP600 printer driver re-installation
sudo apt-get install alien libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common
sudo alien -c cnijfilter-common-2.70-1.i386.rpm cnijfilter-mp600-2.70-1.i386.rpm
sudo dpkg -i cnijfilter-*.deb
sudo ln -s /usr/lib/libpng12.so.0.15.0 /usr/lib/libpng.so.3
sudo ln -s /usr/lib/libtiff.so.4.2.1 /usr/lib/libtiff.so.3
sudo ln -s /usr/lib/libxml.so.1.8.17 /usr/lib/libxml.so.1
sudo ldconfig
sudo /etc/init.d/cupsys restart


> **easy_target said:**
> 

3. If the driver option "MP600 Ver.2.70" is not available in the list, select "Install driver" at the bottom and locate it at "/usr/share/cups/model/canonmp600.ppd"

Cheers!

Has done the trick for me!

Cheers guys!

EDIT: Adding this however, though it allows you to select more options, doesn't appear to make any differences...

Editing: etc/cups/ppd/MP600-Ver.2.70.ppd

> **tzahov said:**
> I found this and and got it working with the new mp600 drivers, very usefull:

*OpenUI *Resolution/Output Resolution: 3 lines below are added to the section which starts with PickOne.
*Resolution 1200/1200 dpi: &#8220;<>>setpagedevice&#8221;
*Resolution 2400/2400 dpi: &#8220;<>>setpagedevice&#8221;
*Resolution 4800/4800 dpi: &#8220;<>>setpagedevice&#8221;
The following section is added anew under the truth of this section. (Total 7 lines)
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: &#8220;2&#8221;
*CNQuality 3/Normal: &#8220;3&#8221;
*CNQuality 4/Standard: &#8220;4&#8221;
*CNQuality 5/Economy: &#8220;5&#8221;
*CloseUI: *CNQuality

And

sudo /etc/init.d/cupsys restart



---

### Post by easy_target on 2007-08-09
In order to get the advanced options, after setting up the printer with the cups uitility or the gnome printer configuration tool, you should:

```
sudo gedit /etc/cups/ppd/"name of the file for your MP600 printer"
```


look for and replace the lines:

```
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution
```

with:

```
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*Resolution 4800/4800 dpi: "<</HWResolution[4800 4800]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality
```

then:

```
sudo /etc/init.d/cupsys restart
```

I hope it helps.

---

### Post by Wyrm_1972 on 2007-08-11
> **easy_target said:**
> 

I hope it helps.

It certainly has. Cheers.

---

### Post by clinto on 2007-08-18
Yeah, I've followed what tzahov said and got it working with the mp500 driver. Thanks so much guys. I really appreciate it. Now, I just have to get the scanner working.

---

### Post by Bruce S on 2007-08-21
You can get a linux driver from  Turboprint --  [www.turboprint.de/enlish.html](www.turboprint.de/enlish.html)   if you are prepared to pay Euo 30 / us$39  for it.

---

### Post by wobwill on 2007-09-11
Hi,

I have a really basic question. 

I have downloaded the relevant files from the Canon website. They are currently sitting in my home directory. I have installed alien. When I type in the command to start making deb packages I am told that the file does not exist. Please could someone tell me what I am doing wrong?

Will

---

### Post by doojsdad on 2007-09-23
I know this is an old thread, but I just wanted to express my gratitude to the people who can answer these questions for us.  I've been trying to install canon's mp600 drivers.  I had some issues with symbolic links but I finally managed to get it working after finding this thread. Thanks again!

---

### Post by clinto on 2007-09-24
I'd used the mp500 driver which allows me to print from text editors and firefox. However, when I try to print from other things like image viewers or PDFs in Evince Document Viewer, it does nothing.

If anyone comes across a better driver, please let us know.


> **wobwill said:**
> Hi,

I have a really basic question. 

I have downloaded the relevant files from the Canon website. They are currently sitting in my home directory. I have installed alien. When I type in the command to start making deb packages I am told that the file does not exist. Please could someone tell me what I am doing wrong?

Will
When you ask such questions, you should copy whatever you're doing and paste it in code tags. For instance:

```
bott@bott-desk:~$ ** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

```

If you try to state your problem so that someone can answer without asking you a bunch of questions or having to write paragraphs, you'll get more help quicker.

So, if you're still having the problem, do whatever you been doing and copy the output from your terminal shell and throw it in some code tags. Are you positive the files you're trying to convert are in your home folder and not in a directory *within* your home folder?

---

### Post by SAR2007 on 2007-10-27
Hi,

I would just like to add that I am using the MP610 with the MP600 driver as described above. It mostly works fine, but 4800 dpi does not work neither do the high quality option  (some colors are skewed).

SAR

---

### Post by mjcritchie on 2007-11-16
Just to add my thanks to everyone that has contributed to this thread.

I *finally* managed to install my MP600 along with the advanced options following the advice on this thread and it all seems to work perfectly now.

Great job guys.

MIKE

---

### Post by jbernardo on 2007-11-16
I shouldn't have bought a MP610 hoping it would work the same way... In kubuntu x86_64, even - as the packages provided by Canon are 32bits only, my only option to print was to buy Turboprint, and forget the scanner for now.

---

### Post by nicolos on 2007-11-17
Hi, 

Did you try to install the ia32-libs and then the debian translated rpm packages from Canon ?

```
$ sudo apt-get install ia32-libs
```

Then, dpkg with --force-architecture option:

```
sudo dpkg -i --force-architecture x86_32_package-xyz.deb
```

Here, after translating the Canon .rpm packages to .deb:

```
$ sudo dpkg -i --force-architecture cnijfilter-common-2.70-1.i386.deb
$ sudo dpkg -i --force-architecture cnijfilter-mp600-2.70-2.i386.deb
```

---

### Post by jbernardo on 2007-11-17
Sorry, I just gave up after failing to convert the RPMs using alien - dpkg-gencontrol fails because "architecture amd64 does not appear in package's list (i386)" . Maybe if I get a 32bits env to convert the RPMs I have more luck.

---

### Post by nicolos on 2007-11-18
Did you try booting on a Feisty or Gutsy 32 bit CD, then install alien in the live session, and place the 2 rpms to convert on a USB key so that you can do just the alien conversion in the live session ? Then reboot normally in 64 bits and install the 2 .deb with dpkg --force-architecture

Nicolas

---

### Post by jbernardo on 2007-11-18
> **nicolos said:**
> Did you try booting on a Feisty or Gutsy 32 bit CD, then install alien in the live session, and place the 2 rpms to convert on a USB key so that you can do just the alien conversion in the live session ? Then reboot normally in 64 bits and install the 2 .deb with dpkg --force-architecture

I am doing that right now, with a virtual machine. Will see if it works. Anyway, I've bought the turboprint drivers and they work very well, now all I need is to get the scanner to work and to wait for a open source version of the drivers.
Thanks for all the help!

---

### Post by nicolos on 2007-11-25
Hi,

Just to inform you that I've updated the pixma Sane library to include a Sane scanner driver for Canon MP610. I'm going to contact the libsane-pixma maintainer to see for an official release. 
As a clone of the 'Doze scanner driver, it currently does the same: scan up to 600 dpi. Don't know under 'Doze, how to scan at more (4800 dpi ?). If anyone can tell, i' could give a try to upgrade also this linux driver.

Also, I've set up a modified version of the PPD files supplied in the Canon MP600/MP610 printer driver, that provides many more printing options in the standard Gnome printing dialogs (like the Canon UI). 

The files are available on a small blog, regrouping several utilities and tools for both printers MP600 and MP610.

Address : [[COLOR="DarkOrange"]http://mp610.blogspot.com[/COLOR]]("http://mp610.blogspot.com")

Feel free to feedback, especially on the new MP610 scanner driver, if anyone could give it a try ...

Nicolas

---

### Post by jbernardo on 2007-11-26
Nicolos,
I just replied on your blog, but will sum it here:

First - Thanks a lot!

- Scanning over 600dpi in windows can only be made in the scangear app, in advanced settings. Output image size is limited to 21000x30000 pixels. So the advertised 9600dpi are only for half a photo...

- I have /dev/sg0 owned by root.root and with 660 permissions. Need to find out why before I can scan with my regular user (which is already a member of the ***scanner*** group).

Once again, thanks!

---

### Post by nicolos on 2007-11-26
Well, we're just talking of open source spirit ... :)

I had this beautiful brand new printer sitting on its table, and I was unable to have it scan.
So I started looking by myself, for a solution against that, based on other's previous work. 
As I had the skill to do it, I simply ... did it.
And as I brought only my small stone to the whole pyramid, I naturally make it available to anyone; If this other's pyramid did not exist before, I probably never could reach this result today, and my scanner would surely be still silent.

Ok, I'll give a try to the scangear program (don't remember if it is on the Canon CD or on their site), and let you know ... Hope this 4800 dpi would not be a simple marketing delirium ... !

For the permissions, check also the udev rules. The file /etc/udev/rules.d/45-libsane.rules might need to be edited to add the MP610.
FYI, I have my MP610 connected to a Mandriva box (server) and I use another box as Ubuntu desktop. I access the scanner with saned running on the Mandriva box. When I log onto the Mandriva box under a normal account, this account can access the scanner only if he is member of group "usb". I did not try yet direct connection of the MP to the Ubuntu box, but it seems to be a point to check also.
FYI, Canon is setting in its driver, permissions to 666 in the udev rules, for the MP600 device ...

---

### Post by jbernardo on 2007-11-27
> **nicolos said:**
> 
Ok, I'll give a try to the scangear program (don't remember if it is on the Canon CD or on their site), and let you know ... Hope this 4800 dpi would not be a simple marketing delirium ... !




The scangear program is on the cd, it is installed when you install the cannon tools.
I'm just thinking that the restrictions on size and dpi might be memory limitations on the scanner.

As for the udev rules, thanks for the pointer, I'll check it.

---

### Post by jbernardo on 2007-12-01
Still no luck with the permissions - ```
crw-rw---- 1 root root 21, 0 2007-11-30 12:53 /dev/sg0
```.
Even though I have added the following lines in /etc/udev/rules.d/45-libsane.rules:
```
# Canon PIXMA MP610
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="1725", MODE="664", GROUP="scanner"
```

There must be something obvious that I am missing. I also have to change permissions in /dev/usb/lp0 to 666 on every boot, or it won't print - even though it is ```
crw-rw---- 1 root lp 180, 0 2007-11-30 12:53 /dev/usb/lp0
``` at boot, it won't work.

---

### Post by lerrup on 2008-02-13
If anyone with printing problems gets this far, I followed the instructions without luck UNTIL I tried another instance of my printer (this one's location began with hal) and then it worked.

I would suggest the different USB instances are worth trying.

L


:mrgreen:

---

### Post by BajanAlan on 2008-02-28
Finally gave up. Went out and bought a HP C5280.
Pluged it in and within seconds it was readyto go
Regards Alan

---

### Post by MisterSanders on 2008-03-14
For what it's worth (maybe for others doing a search in the same boat), after hours of Googling and fiddling I've discovered that the the MP500 drivers (Canon PIXMA MP500 - CUPS+Gutenprint v5.0.1, & Canon PIXMA MP500 - CUPS+Gutenprint v5.0.1 simplified) work very well.
Idea to try taken from [http://www.j2fi.net/2007/10/28/ubuntu-and-the-canon-prixa-mp600-all-in-one/]("http://www.j2fi.net/2007/10/28/ubuntu-and-the-canon-prixa-mp600-all-in-one/")

The only problem, seemingly, is that despite enabling a whack of printing options it only presents the option to print at 600dpi. I thought that could be fixed with the change/addition to the .ppd as given from [http://waterseven.universebox.com/?p=29]("http://waterseven.universebox.com/?p=29"), but it looks like it already has those lines. Perhaps I was looking at the wrong file (/usr/share/ppd/pstocanonbj/canonmp500.ppd)?

---

### Post by bayouoldguy on 2008-03-17
Ditto on the Canon Pixma MP500-CUPS+Gutenprint v5.0.1 Simplified driver found in Ubuntu 7.10. Have not tried scanner yet. I did find an updated Gutenprint 5.0.2 on Sourceforge.net. This may have added features for the MP500 if someone is "brave to try" !. I will keep posted, I am learning the Ubuntu/Linux system, & am not completely comfortable with installs !. ( kind of looking for more printer controls...)   "G"

---

### Post by jbernardo on 2008-03-18
For the scanner, check [here]("http://mp610.blogspot.com/"), Nicolos has done a great work. For the printing part - I am using the 32bit closed drivers from [here]("http://cweb.canon.jp/drv-upd/bj/other.html#linux"), with Nicolo's PPDs. Beats the HP I had before, in print quality and speed...

---

### Post by pieter van brakel on 2008-05-20
I still can't get the printer working in ubuntu 8. It says,

cup is missing filter

Does any one know what that means? I searched and tried  many google pages, but none of them seems to work. 

the printer is a conon pixma mp600

The sane scan works although it crashes a lot.

Pieter

---

### Post by nicolos on 2008-05-20
> **pieter van brakel said:**
> I still can't get the printer working in ubuntu 8. It says,

cup is missing filter

Does any one know what that means? I searched and tried  many google pages, but none of them seems to work. 

the printer is a conon pixma mp600


Do you have a 64 bits system?
In such case, a small tweak has to be brought in order for the Canon driver to find its pstocanonij lib, which is installed in the 32 bits directory instead of the 64 bits one. [Click here to see this comment]("http://mp610.blogspot.com/2008/01/borderless-linux-printing-on-pixma-now.html?showComment=1211287980000#c7491122727719049557")

> **pieter van brakel said:**
> 
The sane scan works although it crashes a lot.

Pieter

This is because pixma backend in SANE 1.0.19, supplied with Hardy, has a bug which makes scanning full pages buggy. 
A fix has been brought to all releases of pixma backend since then, you can get those, or better, install SANE CVS version which works great for most PIXMA scanners (including MP600).

See my signature below to get those, have instructions to install them, and learn how to compile and install the SANE CVS version.

Note: next SANE release (1.1.0) is scheduled to be released in August 2008. Hope Ubuntu devs will propose a backport for SANE backends, so that latest pixma backend would be available in Hardy.

Nicolas

---

### Post by pieter van brakel on 2008-05-21
Thanks for your reaction,

No ie got a 32bits system. 

But I think it has something to o with my usb settings. Because if I used my printer and disconnect it, later on it won't mount anything, even my usbdrive or usbstick.

I installed everything what has something to do with usb in synap, but once Ie disconnect the printer, and put something another thing in the usb port, it doesn work any more.

sorry for my bad english

Pieter

---

### Post by nicolos on 2008-05-21
Then it looks more like a USB issue, if the USB device is no more recognized.

Did you try a 

$ lsusb

to check how the USB devices get listed ?

---

### Post by tzevy on 2008-05-21
Please help me!I`ve poste a link to a printscreen.It`s an error when I install canon.  [http://photobucket.com/video/Bubbly/pbhomepage/video2/d6a067fc.flv?ref=homepagequadv2](http://www.freacaouale.com/ref.php?nume=tzevy)

---

### Post by nicolos on 2008-05-21
> **tzevy said:**
> Please help me!I`ve poste a link to a printscreen.It`s an error when I install canon.  [http://photobucket.com/video/Bubbly/pbhomepage/video2/d6a067fc.flv?ref=homepagequadv2](http://www.freacaouale.com/ref.php?nume=tzevy)

I'm afraid I could not get your printscreen :-k

There are 2 web addresses in your link, one points to a photobucket page with a video :biggrin: , the other to a page to freacaouale but only a blank default.asp page gets downloaded ... :???:

Could you double check the link ? :confused:

---

### Post by pieter van brakel on 2008-05-22
or it crashes or it everything is zero.

0000x000

or something

(I change to fedora for I while wich installed my printer right away, but got problems with my video drivers so i switcht back

---

