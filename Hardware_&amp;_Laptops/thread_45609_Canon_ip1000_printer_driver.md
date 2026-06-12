---
title: "Canon ip1000 printer driver"
date: 2005-06-30
forum: Hardware &amp; Laptops
---

### Post by aum11 on 2005-06-30
Has anyone been able to get canon ip1000 up and running without having to buy the turboprint driver?
I appreciate all help. Thanks. :)

---

### Post by aum11 on 2005-07-12
I was able to successfully use the turboprint driver  for the Canon ip1000.
By setting the resolution to "draft"(300 dpi), it prints using the free edition in both grayscale and colour.
Very handy. :)

---

### Post by mururoa-fr on 2005-07-12
Bad choice ( canon ) of printer under linux.
Canon and many other printer manufacturers wont publish ANY printer driver for linux by choice.
It's not that they cant do it with very few work since they publish for MAC OS-X, it's that they wont do it because they hate linux or want to please Microsoft; make your choice.
If you are using linux and want to buy a printer go at first there --> [http://www.linuxprinting.org/](http://www.linuxprinting.org/). Usefull if you already have a printer and want to find a driver too.
I own a canon i865 but it's my last canon printer since I hate having to export as pdf and find a windows computer to print my document while I have a printer directly attached to my computer :(

---

### Post by Boyzcha on 2005-07-18
This driver for ip1000

[COLOR=DarkOrange]The HOWTO:[/COLOR]
[COLOR=DarkRed]1. Install required packages
Install alien with synaptic
Install libxml1 with synaptic (required later on to run canon's bjcups application)[/COLOR]

**2. Download Driver**
open terminal
cd to your preferred download directory
For ip1000:

$ wget [http://www.mafia.or.id/bjfilter/bjfilter-common-2.50-2.i386.rpm](http://www.mafia.or.id/bjfilter/bjfilter-common-2.50-2.i386.rpm)
$ wget [http://www.mafia.or.id/bjfilter/bjfilter-pixmaip1000-2.50-2.i386.rpm](http://www.mafia.or.id/bjfilter/bjfilter-pixmaip1000-2.50-2.i386.rpm)
$ wget [http://www.mafia.or.id/bjfilter/bjfilter-pixmaip1000-lprng-2.50-2.i386.rpm](http://www.mafia.or.id/bjfilter/bjfilter-pixmaip1000-lprng-2.50-2.i386.rpm)

**3. Convert .rpm to .deb**
$ sudo alien bjfilter-common-2.50-2.i386.rpm
$ sudo alien bjfilter-pixmaip1000-2.50-2.i386.rpm
$ sudo alien bjfilter-pixmaip1000-lprng-2.50-2.i386.rpm

**4. Install**
$ sudo dpkg -i <names of the 3 generated deb files>

**5.Edit .ppd file**
To allow printing quality options to be accessed through cups' printer properties you must edit as root the printer's ppd file.(This applies only to the ip1000)
$ sudo gedit /usr/share/cups/model/canonpixmaip1000.ppd
Add these lines:
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

You can also replace these lines:
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution
with:
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*CloseUI: *Resolution

Save the file

**6. Fix libs**

$sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2
$sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
$sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1

**7. Restart Cups**
$ sudo killall cupsd
$ sudo cupsd

**8. Setup Printer**
-System>Administration>Printing>New Printer
-Choose Local or network printer and specify port or url, respectively
-Forward
Manufacturer>canon
Model> PIXMA IP1000
Driver>Standard
-Apply
(if you can't find your printer choose:install driver>choose the ppd file you edited, reboot and try again to setup printer)

**9. Test**
Right Click on printer> properties>print test page

10. Setup on GIMP
-open an image to print
-file>print>Choose your printer name>setup printer:
Printer Model>PostScript level 2
command>lpr -P <your printer name> (PIXMA IP1000)
PPD File>browse at /usr/share/cups/model/ (mine is /usr/share/cups/model/canonpixusip4100.ppd)
-OK
-Save Settings
-Print

Linux For All :-P I just try to help

---

### Post by cuboconojos on 2005-12-04
Boyzcha, thanks so much for the help. I followed your instructions and everything worked great!!
Give this guy some cups of Ubuntu!!!

Thanks again! I wish someday I could help someone like you did with me.

As you said... Linux for all!!!;)

---

### Post by aum11 on 2005-12-09
Thanks so much Boyzcha.  Awesome.

This is a great howto.

The old Ip1000 is now working perfectly.

---

### Post by krait on 2006-01-08
hi boyzcha,

i followed ur howto and am now able to print wit my ip1000. jus one problem tho, wen i used open office excel to print, even tho i set the properties to print in grayscale, it printed wit color. Is there any solution to this?

thanks in advance

cheers

---

### Post by bonjun on 2006-02-11
thanks to this howto, Boyzcha
my pixma ip1000 works great...

what about determining ink level, where and how can i get that... thanks

---

### Post by jingo811 on 2006-02-11
Does the well explained tutorial above work for all general Canon printers or is it exclusive only for ip1000?

I have Canon BJC 3000, in Windows XP I've installed it by using the Netgear Gateway/Router port and using the UNIX print drivers that's included in XP CD.
I haven't come to troubleshoot my printer yet still having other hardware trouble in Ubuntu so I might have to bookmark this Thread for later troubleshooting.

---

### Post by louis_nichols on 2006-04-12
Has anyone worked out how to use the GUI's that the packages offer? The monitor and the printer config?

I mean, they can be started from the command line, but bjcupsmon would be quite useful if it were started on print. And perhaps use bjcups to setup the printing properties...

---

### Post by www.rzr.online.fr on 2006-05-06
[QUOTE=jingo811]Does the well explained tutorial above work for all general Canon printers or is it exclusive only for ip1000?

I have Canon BJC 3000, in Windows XP I've installed it by using the Netgear Gateway/Router port and using the UNIX print drivers that's included in XP CD.

[/QUOTE]

Is your canon bjc 3000 a USB or paralel printer ?

---

### Post by wayanwolvie on 2006-05-17
Hi, I have followed the steps above. But my printer (IP1000, ofcourse) can't print. On the printer's properties I got this message 

Status :  Ready: /usr/lib/cups/filter/pstocanonbj failed

Can you help me solve this problem??

---

### Post by senorJ on 2006-06-02
Hello

I'm looking to enable my canon ip 1000 for printing too.
I tried the steps outlined by Boyzcha but fell down at step 2
This is the error from the terminal window:

Connecting to www.mafia.or.id|207.150.190.69|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:04:48 ERROR 404: Not Found.

Couldn't get any further :(
Any ideas?

Cheers
Jay

---

### Post by hamenarin on 2006-06-25
Hello,


I've used this drivers for ip1000 in Breezy, but I can't use them in Dapper.

I followed the steps and the printer was added, but when I try to print a file, the  job appears with state job-stopped in the printer job manager.

The /var/log/cups/error_log file have the following error:

     (/usr/lib/cups/filter/pstocanonbj) crashed on signal 11!

Does anybody installed the drivers in Dapper?

Thanks.

---

### Post by t[h]inker on 2006-06-25
Same problem with this "pstocanonbj" stuff for me (Canon i550 PIXMA driver).
On the other hand, printing from any application which *[COLOR="Red"]don't[/COLOR]* uses Gnome printing dialog (gtklp, Firefox, OOo) works great...

PS: Please, don't suggest me KDE instead - I just want to print from Gnome. There must be a solution, I hope.

---

### Post by abhijit222223 on 2006-07-05
[QUOTE=Boyzcha]This driver for ip1000

[COLOR=DarkOrange]The HOWTO:[/COLOR]
[COLOR=DarkRed]1. Install required packages
Install alien with synaptic
Install libxml1 with synaptic (required later on to run canon's bjcups application)[/COLOR]

**2. Download Driver**
open terminal
cd to your preferred download directory
For ip1000:

$ wget [http://www.mafia.or.id/bjfilter/bjfilter-common-2.50-2.i386.rpm](http://www.mafia.or.id/bjfilter/bjfilter-common-2.50-2.i386.rpm)
$ wget [http://www.mafia.or.id/bjfilter/bjfilter-pixmaip1000-2.50-2.i386.rpm](http://www.mafia.or.id/bjfilter/bjfilter-pixmaip1000-2.50-2.i386.rpm)
$ wget [http://www.mafia.or.id/bjfilter/bjfilter-pixmaip1000-lprng-2.50-2.i386.rpm](http://www.mafia.or.id/bjfilter/bjfilter-pixmaip1000-lprng-2.50-2.i386.rpm)

**3. Convert .rpm to .deb**
$ sudo alien bjfilter-common-2.50-2.i386.rpm
$ sudo alien bjfilter-pixmaip1000-2.50-2.i386.rpm
$ sudo alien bjfilter-pixmaip1000-lprng-2.50-2.i386.rpm

**4. Install**
$ sudo dpkg -i <names of the 3 generated deb files>

**5.Edit .ppd file**
To allow printing quality options to be accessed through cups' printer properties you must edit as root the printer's ppd file.(This applies only to the ip1000)
$ sudo gedit /usr/share/cups/model/canonpixmaip1000.ppd
Add these lines:
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

You can also replace these lines:
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution
with:
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*CloseUI: *Resolution

Save the file

**6. Fix libs**

$sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2
$sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
$sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1

**7. Restart Cups**
$ sudo killall cupsd
$ sudo cupsd

**8. Setup Printer**
-System>Administration>Printing>New Printer
-Choose Local or network printer and specify port or url, respectively
-Forward
Manufacturer>canon
Model> PIXMA IP1000
Driver>Standard
-Apply
(if you can't find your printer choose:install driver>choose the ppd file you edited, reboot and try again to setup printer)

**9. Test**
Right Click on printer> properties>print test page

10. Setup on GIMP
-open an image to print
-file>print>Choose your printer name>setup printer:
Printer Model>PostScript level 2
command>lpr -P <your printer name> (PIXMA IP1000)
PPD File>browse at /usr/share/cups/model/ (mine is /usr/share/cups/model/canonpixusip4100.ppd)
-OK
-Save Settings
-Print

Linux For All :-P I just try to help[/QUOTE]
i have to install alien first.i am using oem 6.06.

---

### Post by papuaoshi on 2006-09-02
> **senorJ said:**
> Hello

I'm looking to enable my canon ip 1000 for printing too.
I tried the steps outlined by Boyzcha but fell down at step 2
This is the error from the terminal window:

Connecting to www.mafia.or.id|207.150.190.69|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:04:48 ERROR 404: Not Found.

Couldn't get any further :(
Any ideas?

Cheers
Jay

1) Open this link:

[http://software.canon-europe.com/software/canon_print_filter_for_linuxs22414.asp]("http://software.canon-europe.com/software/canon_print_filter_for_linuxs22414.asp")

2) Click on iP1000Linux.tar.gz link

3) Read carefully(! :)) License Agreement blablabla...

4) Download

PS. There are all files needed (i386 arch) in this .tar

---

### Post by zackem on 2006-09-15
some one can help me i lost the driver of my printer canon iP1000 how can i get that frm hir

---

### Post by bonjun on 2006-09-25
> **senorJ said:**
> Hello

I'm looking to enable my canon ip 1000 for printing too.
I tried the steps outlined by Boyzcha but fell down at step 2
This is the error from the terminal window:

Connecting to www.mafia.or.id|207.150.190.69|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:04:48 ERROR 404: Not Found.

Couldn't get any further :(
Any ideas?

Cheers
Jay

> **zackem said:**
> some one can help me i lost the driver of my printer canon iP1000 how can i get that frm hir


for those who are unable to download the files you can get it here: 
[http://www.filefactory.com/file/ce22e0/]("http://www.filefactory.com/file/ce22e0/")

edit:
btw, i have not edited the howto file, you can start with installing the packages (the deb files), disregard installing alien...
and if you have problems with dependency try > sudo apt-get -f install after the process try to reboot to detect properly the printer,  as per mmy installation, after installing the packages it did not detect the printer properly, it was reported as located in LPT1, after rebooting it was detected at USB,,, i hope this will help you... btw, i am on dapper...

---

### Post by amitav on 2006-11-19
The packages are not available in any of the other two links either... Is Canon destroying the repositories of the ip1000 drivers :(( ??

Any ideas how we can get the drivers? Thanks for any help!

---

### Post by bonjun on 2006-11-20
> **amitav said:**
> The packages are not available in any of the other two links either... Is Canon destroying the repositories of the ip1000 drivers :(( ??

Any ideas how we can get the drivers? Thanks for any help!

you can get it here

[http://www.filefactory.com/file/6268fe/]("http://www.filefactory.com/file/6268fe/")

---

### Post by amitav on 2006-11-23
Thank you, Bonjun. 

Now my ubuntu setup is complete!

---

### Post by darknightx on 2006-11-29
hi. I followed each step , and everything got installed. The problem is that when I tried to print something, there comes a message that says: "The job has been send to printer". On the printer Inbox , I can see the job but it is always paused, and I can't get out of these state. What can I do? Thanks !

---

### Post by bonjun on 2006-12-11
> **darknightx said:**
> hi. I followed each step , and everything got installed. The problem is that when I tried to print something, there comes a message that says: "The job has been send to printer". On the printer Inbox , I can see the job but it is always paused, and I can't get out of these state. What can I do? Thanks !

sorry for the very late reply,,, how's your printer?

---

### Post by ReyPeste on 2007-01-09
I am having trouble following these instructions on Kubuntu Edgy.  I try to install the .deb packages but I get a dependency problem.  bjfilter-common depends on libcupsys2-gnutls10 which is not installed and not in the repositories (i do have an installed package called simply libcupsys2).  There are similar problems with the other two packages.  When I try 
> 
sudo apt-get -f install
then apt-get just uninstalls the canon packages (bjfilter-common, bjfilter-pixmaip1000)!!! :-k 

Is there something I can do about this??

---

### Post by ReyPeste on 2007-01-09
Now I got my Pixma ip1000 to work on Kubuntu Edgy! it was really easy after all.  

I found this page with a lot of resources for Canon printers:
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)

**But to explain it briefly:**
1. I added the Ubuntu repository mentioned there:
> deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

2. I installed the following packages:
> sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj

3. Then I went to the Stystem Settings > Printers > Add
I chose the printer location and then it asked me for the manufacturer an model
The Pixma iP1000 **was not** in the list, so I chose **Other...**

4. I found the driver at /usr/share/ppd/pstocanonbj/
it was called *canonpixmaip1000.ppd*

And now I was ready to go! Test page printed without problems!
I hope this is info is helpful.

---

### Post by sudden8 on 2007-01-16
> **'t[h]inker said:**
> Same problem with this "pstocanonbj" stuff for me (Canon i550 PIXMA driver).
On the other hand, printing from any application which *[COLOR="Red"]don't[/COLOR]* uses Gnome printing dialog (gtklp, Firefox, OOo) works great...

PS: Please, don't suggest me KDE instead - I just want to print from Gnome. There must be a solution, I hope.

I experience the same problem trying to print to a Canon iP1500 PIXMA while running Ubuntu 6.06. Has anyone come up with a solution?

---

### Post by simpsonsfan74 on 2007-01-17
> **sudden8 said:**
> I experience the same problem trying to print to a Canon iP1500 PIXMA while running Ubuntu 6.06. Has anyone come up with a solution?

I've had the same problem with my i560.  I still haven't figured this one out!  Anyone had this problem and figured it out?

---

### Post by simpsonsfan74 on 2007-01-24
I finally gave up with getting the i560 working with dapper and did an upgrade to Edgy.  Then, I was able to use the drivers from [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)

Hope this helps for whoever else has this problem!

---

### Post by jerrykenny on 2007-02-01
Bump the above,   mambo is a star :D

---

### Post by starstco on 2007-02-26
it is uses ful

---

### Post by JamesGreenhalgh on 2007-03-05
Thank you ReyPeste!

The drivers on [http://www.canon-europe.com/Support/software/linux/](http://www.canon-europe.com/Support/software/linux/) didn't work for me, though I used alien and followed the instructions by Boyzcha. 

All the drivers from Canon in the iP1000 tgz referred to the iP1500 printer. I used them anyway, and discovered they didn't work. It communicated with the printer (the pretty light was flashing) but just did nothing. 

Anyway, instructions from ReyPeste worked. 

Just thought people might like to know so they don't waste a couple of hours of their life like I did.

Cheers ReyPeste! Thanks for nothing Canon! I shall avoid all your products in the future. :D

Cheers, 
James

---

### Post by sdrambo on 2007-05-31
Mambo is the star, working Pixma IP1000. BTW You can also add the link in Adep:pt Manager and do the install that way if you crave a GUI. The command line is much quicker and its easier to track errors. Thanks guys:p

---

### Post by waryap on 2007-08-25
HI, I've got a IP1000 up and running and I can print.

The only problem is I can't print grayscale only ? Any ideas ?? This is because I want to print black and white documents. The text is printed correctly but not the images.

Thanks !!!
:guitar:

---

### Post by y1dery on 2007-09-10
I solved the Canon Pixma IP1000 printer installation some months ago for my Xandros 4 distro. The takushi file is good and works, but after you have installed it, check the properties, make _sure _ that your paper size is not A4, but "letter." The flashing led is an indication that this is the case. Changing to "letter" should solve it. Also rebooting the IP1000 will help. 

Much luck,

---

### Post by Ozztopia on 2007-09-11
I followed instructions on this site and they worked perfectly for me.
[http://www.sumardi.net/2006/08/24/ip1000-driver-for-ubuntu/]("http://www.sumardi.net/2006/08/24/ip1000-driver-for-ubuntu/")
There is a slight hiccup though. The required files cannot be downloaded from [http://files.alfansa.org]("http://files.alfansa.org") anymore since the sharing site where it directs one to download the files must have stopped hosting the files. But drop the author M. Hansen a mail and he will send you the files. A very helpful guy indeed.
Then just follow instructions and it will work perfectly.

Oh and by the way, I have Ubuntu 7.04 and I love it. I have a 7 year old computer and you wouldn't believe that Ubuntu runs so great on it. On Windows XP it just crawls.

God bless the Ubuntu community! Thank you guys for the great work.:)

I also got my Sony Ericsson Z530i to work as a modem and use GPRS to surf the net. Anyone needs help with that, drop me a message.:)

---

### Post by hendra40 on 2007-11-11
Hello All,
Can you help me to solve this problem :
when I type :
ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2
ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1

There are some error :
ln: creating symbolic link `/usr/lib/libpng.so.2' to `/usr/lib/libpng12.so.0': File exists

Why it is happened ?
Thanks before.:):):)

---

### Post by ahfu on 2007-12-23
Hi all,

I have got my printer up and running using [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/) method..

However, I was unable to do printing on both side of the page.. I hope i am not asking too much...

I was about to do printing on both sides of the page previously using windows... the printer will first print on one side of the page all the odd-numbered pages and then ask me to invert the papers and feed it to the printer again.. then print all the even-pages on the empty side.. 

I would appreciate any reply... Thanks!

Ah Fu

---

### Post by tdm on 2008-02-16
For the iP1000 printer only
**Use this - This is excellent because I made it.**

It's an easy to install driver.
 

[Click Here]("http://ubuntuforums.org/showthread.php?t=730598")

---

