---
title: "Canon Pixma MG54500 is showing but not working"
date: 2014-07-31
forum: Hardware
---

### Post by Vivien_Scane on 2014-07-31
Hello everyone, it's my first time here so please be gentle.

I have a Pixma MG54500 printer and it is showing when I search for printers in the system settings, however when I try and do a test print, nothing and when I try to print from an office document nothing.  I have downloaded some drivers from the Canon site for Linux but not sure if/how they have installed. Any help and advice would be appreciated, do I need to type something into the terminal perhaps?

Thank Viv

---

### Post by kc1di on 2014-07-31
Hello Vivien_Scane and welcome to Ubuntu forums,

Sometimes the installer doesn't get the printer drivers correct. before having to install the drivers you downloaded lets try to reinstall the printer.

go to system setting > printer  then remove the printer that is setup there.  

now select add a printer and following the instruction on the screen, when it's finished try printing a test print again. see if it works
if not let us know we will walk you through install of printer drivers you downloaded. 

good luck ;)

---

### Post by Vivien_Scane on 2014-07-31
Thank you Dave, I have done this several times but I will go and do it once again and if nothing I will get back to you.

Thanks again

Viv

---

### Post by Vivien_Scane on 2014-07-31
Ok so I've done all that, again. I know it's the right printer because it even gives the same number as appears on the printer name displayed on the printer screen.

Please, what now?

Waiting anxiously for any help.

---

### Post by kc1di on 2014-07-31
ok lets try this first.
open web browser and in the address line type the following address.
```
http://loacalhost:631
```

when the cups page comes up select Adding printers and classes.
Follow the instructions and add the printer again. See if it offers you any different drivers for your printer.
once the printer is added - go to Printers tab , Maintenance and print test page, make sure your selecting the printer you just added. 
give that a try.

---

### Post by Vivien_Scane on 2014-07-31
OK, so it's asking me for a username and password, which would these be for??

---

### Post by Vivien_Scane on 2014-07-31
OK so now used correct user name and gone through the process and taken automatically to the printer tab and it says this:  what next please

[COLOR=#000000][FONT=lucida grande][TABLE]
[TR]
[TH]Description:[/TH]
[TD]Canon MG5400 series[/TD]
[/TR]
[TR]
[TH]Location:[/TH]
[TD][/TD]
[/TR]
[TR]
[TH]Driver:[/TH]
[TD]Canon MG5400 series - CUPS+Gutenprint v5.2.10-pre2 (color, 2-sided printing)
[/TD]
[/TR]
[TR]
[TH]Connection:[/TH]
[TD]dnssd://Canon%20MG5400%20series._ipp._tcp.local/[/TD]
[/TR]
[TR]
[TH]Defaults:[/TH]
[TD]job-sheets=none, none media=iso_a4_210x297mm sides=one-sided[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida grande][h=3]Jobs[/h][/FONT][/COLOR]
**Search in Canon_MG5400_series:**   
[COLOR=#000000][FONT=lucida grande][/FONT][/COLOR][COLOR=#000000][FONT=lucida grande] [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida grande]No jobs.



[/FONT][/COLOR]

---

### Post by Vivien_Scane on 2014-07-31
Went to maintenance and did print test page, now it looks like this:

[COLOR=#000000][FONT=lucida grande][h=2][Canon_MG5400_series]("http://localhost:631/printers/Canon_MG5400_series") (Idle, Accepting Jobs, Not Shared, Server Default, Color-Managed)[/h] Maintenance Print Test Page   Pause Printer Reject Jobs Move All Jobs Cancel All Jobs   Administration Modify Printer Delete Printer Set Default Options Set As Server Default Set Allowed Users [TABLE]
[TR]
[TH]Description:[/TH]
[TD]Canon MG5400 series[/TD]
[/TR]
[TR]
[TH]Location:[/TH]
[TD][/TD]
[/TR]
[TR]
[TH]Driver:[/TH]
[TD]Canon MG5400 series - CUPS+Gutenprint v5.2.10-pre2 (color, 2-sided printing)
[/TD]
[/TR]
[TR]
[TH]Connection:[/TH]
[TD]dnssd://Canon%20MG5400%20series._ipp._tcp.local/[/TD]
[/TR]
[TR]
[TH]Defaults:[/TH]
[TD]job-sheets=none, none media=iso_a4_210x297mm sides=one-sided[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida grande][h=3]Jobs[/h][/FONT][/COLOR]
**Search in Canon_MG5400_series:**   
[COLOR=#000000][FONT=lucida grande][/FONT][/COLOR][COLOR=#000000][FONT=lucida grande] [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida grande]No jobs.[/FONT][/COLOR]


I have also been back to the printer settings, made the 'new' printer my default, do print test sheet and it's again, jut showing as idle. Yes I have switched it on ;-)

This will make job 13!!

Viv

---

### Post by buzzingrobot on 2014-07-31
Don't have a Canon, but...

Did those drivers come from here: [http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG5540.aspx?type=download](http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG5540.aspx?type=download)?

I believe the printer is an "all-in-one", so seperate drivers for scanning and printer are needed.  Use the Debian files, not the rpm's. 

Probably best to clear all those backlogged print jobs, too.

FWIW, this is a reasonably common problem with printers that require a proprietary driver from the manufacturer.  Many HP printers are in that category, as well. HP does, however, provide a simple GUI app to Linux that can be used to download and install the correct driver from their servers.  As far as I know, Canon ha never done that.

---

### Post by Vivien_Scane on 2014-07-31
OK so I've binned all the other stuff I downloaded from the UK site and have now gone to the above download site and downloaded, to my download folder all of the six recommended ones for Linux.

Please advise what to do next.  I have cleared all backlogged print jobs, at least when I go to print queue it doesn't show anything waiting.

Viv

---

### Post by kc1di on 2014-07-31
if they are .deb files you just have to click on them to install.  or you can install with gdebi which may or may not be installed on your version of Ubuntu.

---

### Post by buzzingrobot on 2014-07-31
Only attempt to install the two packages labeled as "Debian" packages.  The others are the same files packaged for other version of Linux and won't install on Ubuntu. (And one is just an archive of the source code.)

However, I downloaded one of the Debian packages and it turns out to be a compressed tar archive (filenames ends in "tar.gz") So, Canon did not make this very easy, at all.  

You'll need to locate the two Debian packages with the file manager (Files), right click on each icon, one at a time, and select "Extract Here" from the choices that pop up. That will uncompress and unarchive each and you will see similarly named icons representing folders. Inside each folder will be, among other things, a script called "install.sh".  Looks like you need to run them and respond to the questions they ask.

Open a terminal and navigate to each folder. (Presumably they're in your Downloads directory. So "cd ~/Downloads" to get there and then "ls" to list the folder and file names.  Then "cd <TheFolderName>" into the right folder. Another "ls" should verify that there is an "install.sh" file there.

Run that install script by entering this: "./install.sh", and cross your fingers. If it appears to complete successfully, open "Printers" in settings; you may see a new printer has become available, or you may find that the existing printer now works.

And, yes, this is pretty much an obnoxious way to install software in the year 2014, especially because you really don't know if it will work. Canon's method dates from the 1980's.

---

### Post by george-domijan90 on 2014-08-01
I also have a Caqnon printer/scanner/copier, Model MG5520, and have encountered the same problem.  Printer showing but not connecting. Like Vivien, I welcome any advice on this.  May we both solve the problem.

Thanks, George

---

### Post by pdc on 2014-08-02
Hi Vivien;

so I am assuming that your printer is an MG5450.............. important thing is that it is a member of the 5400series: ............in some countries it will be sold as an MG5470

How to find a Canon printer driver? If one goes here [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal) to the Canon Asia website, .............you follow the clicks........for the MG5450 .....is a multi-function..............it's a PIXMA and then the model number ...

so you get to here [http://support-asia.canon-asia.com/P/search?model=PIXMA+MG5470&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MG5470&menu=download&filter=0&tagname=g_os&g_os=Linux) for the **LINUX** page



________________________________

and we need the debian package for Ubuntu [SIZE=3]**so here is the link**[/SIZE] [http://support-asia.canon-asia.com/contents/ASIA/EN/0100467602.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100467602.html) [COLOR="#EE82EE"]**Please click**[/COLOR] to **DOWNLOAD** and select **SAVE** as download commences

You will be downloading [COLOR="#008000"]cnijfilter-mg5400series-3.80-1-deb.tar.gz[/COLOR] which as you can see is for the 5400 series ........

________________________________

first though you need to download libtiff4 from here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and scroll down about 14 to find the 32bit or 64bit file you need: 32bit ubuntu needs 386 and 64bit ubuntu needs amd64

click to download and hopefully your system will offer to "open" the file as it comes down and that should offer an install option.........

If you can open a terminal Vivien: please ask if you need guidance or your Dash search function will find it;

use the mouse and the menu top line of the terminal.............

check it is installed with > [COLOR="#FF0000"]dpkg -l | grep libtiff4[/COLOR]

______________


If you **copy and paste** the commands that are below into the terminal:*** line by line; ***hit the ENTER key after each paste ; 

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mg5400series-3.80-1-deb.tar.gz
cd cnijfilter-mg5400series-3.80-1-deb
./install.sh[/COLOR]

the last command will ask you for your sudo password and start the install script

__________________________________________________________________________________________________________________________________________________
_________________________________________________________________________________________________________________________________________________-

Hi [SIZE=4]**george-domijan90**[/SIZE] and welcome to the forums also: for your MG5500 series device (I see it is sold as MG5520 but elsewhere it might be ..MG5570 or MG5540..........) 

............ you don't need libtiff4 ..............seemingly Canon drivers from version 4 and on do not use libtiff4 .............

go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100550602.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100550602.html) and do as above: but you will be downloading [COLOR="#008000"]cnijfilter-mg5500series-4.00-1-deb.tar.gz[/COLOR]
so .........

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mg5500series-4.00-1-deb.tar.gz
cd cnijfilter-mg5500series-4.00-1-deb
./install.sh[/COLOR]

---

### Post by Vivien_Scane on 2014-08-03
Hello again, sorry I haven't responded again but have been/am busy with visitors at the moment so not a lot of time to administrate the lap top!!

@pdc, thank you so much for your very descriptive help. I will follow and try to carry it out, it might take me a while so need to wait till I've got a spare few hours, I can be a little slow at times, but blame my age!! ;-)

However, I will get back and let you all know how it goes, once again thanks a lot for all the feedback and suggestions.

Viv  :-)

---

### Post by Vivien_Scane on 2014-08-03
[COLOR=#FF0000]*.*[/COLOR]

---

### Post by Vivien_Scane on 2014-08-03
O.M.G!!! I've done it and it works!!! I am so so happy, thank you @pdc you are a complete star!!!

I am one happy lady!!!

Viv :-)

---

### Post by pdc on 2014-08-03
well done......you're the star!! Enjoy

..........and if at some stage in the future you want to use the scanner side of the device, Canon supply [COLOR="#0000FF"]ScanGearMP[/COLOR] to drive the scanner!! [http://support-asia.canon-asia.com/contents/ASIA/EN/0100470502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100470502.html)

it installs in the format of the printer; and you run it with > [COLOR="#FF0000"]scangearmp[/COLOR] in a terminal till you set up a launcher

---

### Post by kc1di on 2014-08-03
so glad Vivien_Scane  that you stuck with it and it's working for you :)
this is an wonderful forum ;)

---

### Post by Vivien_Scane on 2014-08-03
> **pdc said:**
> well done......you're the star!! Enjoy

..........and if at some stage in the future you want to use the scanner side of the device, Canon supply [COLOR=#0000FF]ScanGearMP[/COLOR] to drive the scanner!! [http://support-asia.canon-asia.com/contents/ASIA/EN/0100470502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100470502.html)

it installs in the format of the printer; and you run it with  in a terminal till you set up a launcher

I have downloaded the file, which is a tar.gz file. Could you explain further please how to 'run in within a terminal till I set up launcher.

Thanks again for all your help, this forum is a wonderful place!

Viv

---

### Post by Vivien_Scane on 2014-08-04
OK, so I got the scanner to work via the terminal but when I closed it down I couldn't see how to do it via the computer. I found something called Simple Scan but that said no scanners connected and the scanner isn't showing up in my system settings, so how will I use the scanner in future. Also I used to be able to tell the scanner to scan to my computer, which it did. My computer is still showing but it doesn't work from the printer screen like it used to.

Edit:  I have just downloaded XSane and that doesn't/wont detect either.

Viv

---

### Post by pdc on 2014-08-04
so you need to create what is called a launcher .............to launch the programme ................. (see attached thumbnail)

if you copy and paste these commands into the terminal

> [COLOR="#FF0000"]sudo apt-get install gnome-panel[/COLOR]

> [COLOR="#FF0000"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR]

that will open a dialogue window and into it you must have the **COMMAND** as > [COLOR="#008000"]scangearmp[/COLOR]    but the rest are optional: you can change the icon if you wish to find another; 

It should create an icon on your desktop for you to "launch" the programme [COLOR="#0000FF"]ScanGearMP[/COLOR] .............

________________________________________________________________

Simple Scan is the front end for sane; an open-source scanning programme; [COLOR="#0000FF"]ScanGearMP[/COLOR] has been written by Canon for their products: yours is tailored for your 5400 series;

__________________________________________________________________

while you are on a roll..............create a second launcher to edit your Canon printer 

> [COLOR="#FF0000"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR]

and the command to paste into the section that says **COMMAND** is > [COLOR="#008000"]cngpij -P MG5400USB[/COLOR] and call it whatever you like .......... but the screen that opens should help you edit settings on your printer .....................

---

### Post by Vivien_Scane on 2014-08-04
OK, did both of those things but when I clicked on the desktop icon for scanner, it said no scanners detected. Remembering of course that it is wireless, as is the printer, and not usb connected.

The printer icon doesn't seem to work at all!

What now please lovely person?

Viv

---

### Post by Vivien_Scane on 2014-08-04
It's me again, sorry to be a pain, but I can't even operate the scanner from the terminal either now with the command scangearmp.

:-(

Viv

---

### Post by Vivien_Scane on 2014-08-04
From bad to worse!! The printer wont work now either!!!

:-(

Edit: The printer is now telling me, from the printer display panel, that it is out of the main black ink, could this be the cause?? I have ordered more online so have to wait till it arrives and am away for a few days but any advice or comments would be appreciated, and I'll keep checking.

Thanks again, and yes, this is a wonderful forum.

Viv

---

### Post by Mike_Walsh on 2014-08-04
> **Vivien_Scane said:**
> From bad to worse!! The printer wont work now either!!!

:-(

Edit: The printer is now telling me, from the printer display panel, that it is out of the main black ink, could this be the cause?? I have ordered more online so have to wait till it arrives and am away for a few days but any advice or comments would be appreciated, and I'll keep checking.

Thanks again, and yes, this is a wonderful forum.

Viv

Hi, Vivien.

You're finding out the same thing that I did a few months ago when I started using Linux (after migrating from Windows XP); it's a WEE bit different from Windows!

Yes, a lot of stuff you CAN simply 'click on' and download from the Software Centre; but these are usually applications. Utilities are a WHOLE different ballgame...

When I began with Ubuntu, back in April, I used the forum to enquire about printer setup, since it's one of the first things I like to get sorted. I use an Epson. You think Canons are problematical? Epsons are a nightmare..!

Every time I posted, some kind soul would direct me to the Epson website; every time, I would follow the link, which took me to the Epson download page. And every time I entered the printer details, the search would return a big fat zero...nada. Zip. Zilch.

I had an online chat with one of Epson's customer service reps, a very nice lady, who kindly informed me that Epson don't actually DO a Linux driver, and directed me to the Avasys website (a Japanese company who USED to do Linux drivers for Epsons). When the page came up, it informed me that the rights to the Epson Linux drivers had been transferred BACK to Epson themselves.....

I was going round and round in circles for months.

I eventually came across openprinting.org ( [http://www.openprinting.org/drivers ]("http://www.openprinting.org/drivers")), 
where I tracked down an Epson Linux driver.....DIGITALLY SIGNED BY AVASYS THEMSELVES. It must have been acquired from Avasys before they gave up the rights to the programming...

My machine (an Epson Stylus SX218) is an all-in-one. I've been able to print for a few weeks now; like you, I couldn't test the driver when I'd installed it because I, too, was out of ink..!

I was looking around for a scanner driver the other day, thinking "I MUST be able to get this thing working, surely"; once more, I decided to look at Epson's download page. Once again, I entered my printer details, and, once again.....nothing.

You'll howl at this next bit..!

I thought for a moment, and then, instead of 'Epson Stylus SX218', I simply entered 'Stylus SX218', and.....up popped a huge list of drivers.

The search box on their download page doesn't make it at all clear quite WHAT you should enter.....just says to enter printer details.

Well; to cut a long story short,  my scanner is now up and running, and working as well as, if not better, than it was with the Windows drivers. You need to download at LEAST 3 files, and they MUST be installed in the correct order, or else it doesn't want to know..!

I've not only now got the official Epson Scanner utility (for LINUX, natch!), but 'Simple Scan' ALSO now works perfectly, too!

Moral of the story; keep plugging away. If a large number of people say that a method for doing something works, then it probably will.....EVENTUALLY.

BTW; despite facing conundrums like the afore-mentioned, I STILL maintain that Ubuntu has put the fun back into computing. For me, at any rate.

They ARE a MARVELLOUS bunch of folks on here.....and oftentimes, they will bend over backwards to help people out with problems. Trust me, you WILL get it sorted.

I know this hasn't helped with your problem; but it just serves to illustrate the hoops you sometimes have to jump through to sort things out in Linux. But it's ALWAYS worth it, in the end.


Regards,

Mike.

---

### Post by Vivien_Scane on 2014-08-04
> **Mike_Walsh said:**
> Hi, Vivien.

You're finding out the same thing that I did a few months ago when I started using Linux (after migrating from Windows XP); it's a WEE bit different from Windows!

Yes, a lot of stuff you CAN simply 'click on' and download from the Software Centre; but these are usually applications. Utilities are a WHOLE different ballgame...

When I began with Ubuntu, back in April, I used the forum to enquire about printer setup, since it's one of the first things I like to get sorted. I use an Epson. You think Canons are problematical? Epsons are a nightmare..!

Every time I posted, some kind soul would direct me to the Epson website; every time, I would follow the link, which took me to the Epson download page. And every time I entered the printer details, the search would return a big fat zero...nada. Zip. Zilch.

I had an online chat with one of Epson's customer service reps, a very nice lady, who kindly informed me that Epson don't actually DO a Linux driver, and directed me to the Avasys website (a Japanese company who USED to do Linux drivers for Epsons). When the page came up, it informed me that the rights to the Epson Linux drivers had been transferred BACK to Epson themselves.....

I was going round and round in circles for months.

I eventually came across openprinting.org ( [http://www.openprinting.org/drivers ]("http://www.openprinting.org/drivers")), 
where I tracked down an Epson Linux driver.....DIGITALLY SIGNED BY AVASYS THEMSELVES. It must have been acquired from Avasys before they gave up the rights to the programming...

My machine (an Epson Stylus SX218) is an all-in-one. I've been able to print for a few weeks now; like you, I couldn't test the driver when I'd installed it because I, too, was out of ink..!

I was looking around for a scanner driver the other day, thinking "I MUST be able to get this thing working, surely"; once more, I decided to look at Epson's download page. Once again, I entered my printer details, and, once again.....nothing.

You'll howl at this next bit..!

I thought for a moment, and then, instead of 'Epson Stylus SX218', I simply entered 'Stylus SX218', and.....up popped a huge list of drivers.

The search box on their download page doesn't make it at all clear quite WHAT you should enter.....just says to enter printer details.

Well; to cut a long story short,  my scanner is now up and running, and working as well as, if not better, than it was with the Windows drivers. You need to download at LEAST 3 files, and they MUST be installed in the correct order, or else it doesn't want to know..!

I've not only now got the official Epson Scanner utility (for LINUX, natch!), but 'Simple Scan' ALSO now works perfectly, too!

Moral of the story; keep plugging away. If a large number of people say that a method for doing something works, then it probably will.....EVENTUALLY.

BTW; despite facing conundrums like the afore-mentioned, I STILL maintain that Ubuntu has put the fun back into computing. For me, at any rate.

They ARE a MARVELLOUS bunch of folks on here.....and oftentimes, they will bend over backwards to help people out with problems. Trust me, you WILL get it sorted.

I know this hasn't helped with your problem; but it just serves to illustrate the hoops you sometimes have to jump through to sort things out in Linux. But it's ALWAYS worth it, in the end.


Regards,

Mike.

Thank you Mike, I will keep plugging away at it. The most frustrating thing is that the printer worked yesterday!! Well with a test print! Then I got the scanner working by typing a command in the terminal, now that doesn't work either!! I'm going to wait till the ink arrives and give it another try, if not I'll start the process given by @pdc all over again.  

Thanks for your words of encouragement, I too enjoy the 'getting involved' more with the Linux set up, but even that can get a tad frustrating when things begin to fail.

Viv

---

### Post by Vivien_Scane on 2014-08-04
> **Mike_Walsh said:**
> Hi, Vivien.

You're finding out the same thing that I did a few months ago when I started using Linux (after migrating from Windows XP); it's a WEE bit different from Windows!

Yes, a lot of stuff you CAN simply 'click on' and download from the Software Centre; but these are usually applications. Utilities are a WHOLE different ballgame...

When I began with Ubuntu, back in April, I used the forum to enquire about printer setup, since it's one of the first things I like to get sorted. I use an Epson. You think Canons are problematical? Epsons are a nightmare..!

Every time I posted, some kind soul would direct me to the Epson website; every time, I would follow the link, which took me to the Epson download page. And every time I entered the printer details, the search would return a big fat zero...nada. Zip. Zilch.

I had an online chat with one of Epson's customer service reps, a very nice lady, who kindly informed me that Epson don't actually DO a Linux driver, and directed me to the Avasys website (a Japanese company who USED to do Linux drivers for Epsons). When the page came up, it informed me that the rights to the Epson Linux drivers had been transferred BACK to Epson themselves.....

I was going round and round in circles for months.

I eventually came across openprinting.org ( [http://www.openprinting.org/drivers ]("http://www.openprinting.org/drivers")), 
where I tracked down an Epson Linux driver.....DIGITALLY SIGNED BY AVASYS THEMSELVES. It must have been acquired from Avasys before they gave up the rights to the programming...

My machine (an Epson Stylus SX218) is an all-in-one. I've been able to print for a few weeks now; like you, I couldn't test the driver when I'd installed it because I, too, was out of ink..!

I was looking around for a scanner driver the other day, thinking "I MUST be able to get this thing working, surely"; once more, I decided to look at Epson's download page. Once again, I entered my printer details, and, once again.....nothing.

You'll howl at this next bit..!

I thought for a moment, and then, instead of 'Epson Stylus SX218', I simply entered 'Stylus SX218', and.....up popped a huge list of drivers.

The search box on their download page doesn't make it at all clear quite WHAT you should enter.....just says to enter printer details.

Well; to cut a long story short,  my scanner is now up and running, and working as well as, if not better, than it was with the Windows drivers. You need to download at LEAST 3 files, and they MUST be installed in the correct order, or else it doesn't want to know..!

I've not only now got the official Epson Scanner utility (for LINUX, natch!), but 'Simple Scan' ALSO now works perfectly, too!

Moral of the story; keep plugging away. If a large number of people say that a method for doing something works, then it probably will.....EVENTUALLY.

BTW; despite facing conundrums like the afore-mentioned, I STILL maintain that Ubuntu has put the fun back into computing. For me, at any rate.

They ARE a MARVELLOUS bunch of folks on here.....and oftentimes, they will bend over backwards to help people out with problems. Trust me, you WILL get it sorted.

I know this hasn't helped with your problem; but it just serves to illustrate the hoops you sometimes have to jump through to sort things out in Linux. But it's ALWAYS worth it, in the end.


Regards,

Mike.

Thank you Mike, I will keep plugging away at it. The most frustrating thing is that the printer worked yesterday!! Well with a test print! Then I got the scanner working by typing a command in the terminal, now that doesn't work either!! I'm going to wait till the ink arrives and give it another try, if not I'll start the process given by @pdc all over again.  

Thanks for your words of encouragement, I too enjoy the 'getting involved' more with the Linux set up, but even that can get a tad frustrating when things begin to fail.

Viv

---

### Post by Mike_Walsh on 2014-08-04
Hi again, Vivien.

Well, you sound as though you're a fairly "hands-on" sort of lass.

I assume you're running 14.04, yes? If it's of any help to you, have a look at this link:-

[http://linux.wikia.com/wiki/Getting_Canon_PIXMA_to_work_on_Linux](http://linux.wikia.com/wiki/Getting_Canon_PIXMA_to_work_on_Linux)

It may be of some use, it may not. I don't mind admitting, the terminal is not my favourite part of Linux...although very often, it gets the job done where other options won't touch whatever it is you're attempting to fix! I'm slowly becoming more at ease with it as time goes by...

I'll be honest; you're the first lady 'geek' I've ever encountered! By and large, it seems to be an almost exclusively male preserve. A couple of the moderators on here are girls, but they ARE the exception rather than the rule...!

All credit to you! We'll see if we can't get this sorted out, one way or another.

BTW, if you DO copy and paste this into the terminal (or type it, if you're that confident!), don't forget to alter where it says 'mx860 series', and change it for your own (that's just an example). According to the blog, this should take care of printer AND scanner together.

Give it a shot, and let us know if it does any good. You may have to do some purging first, though; and THAT is something I don't know much about, I'm afraid. Might need to get some advice from the experts on that..!

Regards, 

Mike.

---

### Post by Vivien_Scane on 2014-08-04
> **Mike_Walsh said:**
> Hi again, Vivien.

Well, you sound as though you're a fairly "hands-on" sort of lass.

I assume you're running 14.04, yes? If it's of any help to you, have a look at this link:-

[http://linux.wikia.com/wiki/Getting_Canon_PIXMA_to_work_on_Linux](http://linux.wikia.com/wiki/Getting_Canon_PIXMA_to_work_on_Linux)

It may be of some use, it may not. I don't mind admitting, the terminal is not my favourite part of Linux...although very often, it gets the job done where other options won't touch whatever it is you're attempting to fix! I'm slowly becoming more at ease with it as time goes by...

I'll be honest; you're the first lady 'geek' I've ever encountered! By and large, it seems to be an almost exclusively male preserve. A couple of the moderators on here are girls, but they ARE the exception rather than the rule...!

All credit to you! We'll see if we can't get this sorted out, one way or another.

BTW, if you DO copy and paste this into the terminal (or type it, if you're that confident!), don't forget to alter where it says 'mx860 series', and change it for your own (that's just an example). According to the blog, this should take care of printer AND scanner together.

Give it a shot, and let us know if it does any good. You may have to do some purging first, though; and THAT is something I don't know much about, I'm afraid. Might need to get some advice from the experts on that..!

Regards, 

Mike.

Hello again Mike

Thanks for all this help, this is really a brilliant place for support.  As the printer is out of the main black cartridge it wont work anyway so I am going to have to wait till it arrives and try again. I shall certainly also look into your advice above.

I am going to be away for a about a week so will give this a rest till I return.  So when I disappear you'll know why!

Thanks again

Viv

---

### Post by pdc on 2014-08-04
I see you write:

> Remembering of course that it is [COLOR="#EE82EE"]wireless[/COLOR], as is the printer, and not usb connected

for these devices, the Canon needs to be recognised by the router: Epson have an older system ...that works well...with a keyboard and you can tap into your router; 

________________

the IP address of the device is likely to change: so the device is no longer seen; some assign a static IP address to the Canon; having first had it seen by the router; you have to allow access to the router by pressing the access button; and then pressing the wireless button on the Canon; 

The device must be seen by the router: so I guess the IP address is changing.........

---

### Post by pdc on 2014-08-04
to Michael of King's Lynn: sorry to hear of your difficulties in finding the Epson Linux page: here is a link [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) 

If you search on the Epson site for any device; and search for drivers for that device; and then select LINUX as the operating system, I find it takes you to this page: so Epson supply drivers; they actively maintain this;

---

### Post by Mike_Walsh on 2014-08-04
Hi, pdc... Thanks for that!

Yep; that's the exact same page that everybody else directed me to. The printer IS up-and-running, and has been for about 6 or 7 weeks now. I couldn't print the test page to try it out when I first installed it, because, like Vivien, I too was out of ink...

And as you say; there IS a list of Linux drivers and stuff. I just couldn't access the blasted page, simply because I was always entering 'Epson' in front of the 'Stylus SX218'; my own fault entirely..... :grin: 

Cheers!

Regards,

Mike.

---

### Post by Vivien_Scane on 2014-08-05
> **pdc said:**
> I see you write:



for these devices, the Canon needs to be recognised by the router: Epson have an older system ...that works well...with a keyboard and you can tap into your router; 

________________

the IP address of the device is likely to change: so the device is no longer seen; some assign a static IP address to the Canon; having first had it seen by the router; you have to allow access to the router by pressing the access button; and then pressing the wireless button on the Canon; 

The device must be seen by the router: so I guess the IP address is changing.........

Hello again @pdc  The router does see the printer, in fact in the old days of windows (wash my mouth out!!!) I could scan from the scanner directly into my laptop!! I did do a test print to start with and like Mike I have now run out of ink and the printer wont print at all, I'm hoping that's the reason.  Because the printer is in the hall and I'm in the lounge the message could've come up on the printer and I obviously didn't see it till I tried to do a copy from the scanner, just to see if it was working full stop!! Again, with the old software that was installed on my laptop that message would also have come up on the laptop as well.

I will be trying again so thanks again for all your help.  Please keep an ear out as I might be shouting again in a week or so when I return from the Bristol Balloon Fiesta!!

Viv

---

### Post by nick135 on 2014-08-12
Hi Viv, 

I had the same problem with my Canon MG5450. After installing the new Canon drivers I noticed the installation had failed, due to a missing dependency - libtiff4. [ See this thread on how to install the driver - [here]("http://ubuntuforums.org/showthread.php?t=2179354&highlight=canon+MG5400") - you only need the debian package archives ] There is some advice on another post on how to install the dependency on 14.04 - [here]("http://ubuntuforums.org/showthread.php?t=2220935&highlight=canon+MG5400"), which I followed. Once this package is installed, I could re-run the Canon driver , and have now happily been printing from Ubuntu 14.04 to my networked Canon MG5450

---

### Post by nick135 on 2014-08-12
Oops - looks like I posted too soon, without paging through the full thread!

Looks like you got your printer working with similar instructions

---

### Post by Vivien_Scane on 2014-08-14
Hello again 

Well I'm back, new ink cartridge installed and I'm pleased to say the printer is working.

The scanner is also, and I can launch it from the new launcher icon on the desktop, thanks again pdc for those instructions.  However, it wont create a launcher for the printer, goodness knows why but I'm hoping I can do the printer settings some other way, I'll keep you all posted.

Thanks again for all the friendly help and advice.

Viv   :-)

---

### Post by pdc on 2014-08-14
glad it is all working for you; enjoy

you can usually edit the title of the thread as SOLVED ...............it is under thread tools at the top of the page

---

### Post by Vivien_Scane on 2014-08-15
Thanks for the heads up pdc, will do.

Viv

---

