---
title: "Samsung CLP-315 Printer Problem"
date: 2008-07-14
forum: Hardware
---

### Post by RamonBianco on 2008-07-14
Greetings.  I'm running Feisty, and I hope this is the "right place" for this question.

I got a CLP-315 printer, and I tried to do a "minimal" install from the CD (which is up-to-date), because the printer will be on a network print server if I can get it working, so I won't have access to the printer with the Samsung "Smart Panel" software, which uses the USB connection.

I have asked about this in the [thread=341621]_[COLOR="DarkOrchid"]HOWTO Install Samsung Unified Printer Driver[/COLOR]_[/thread] thread, but I haven't gotten any response.

I went through the menu system, System>Administration>Printing, and then used the New Printer icon.  I found the PPD file for the printer on the CD and used that.  This didn't work, so I searched and found the above thread, which recommended to try > 
sudo cp ./cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsungsplc /usr/lib/cups/filter/Now the printer prints, but only in a half/double way.  It prints two duplicate, identical, narrow columns, each a half-size version of the page, separated by a series of white bands every 3 mm or so.  I'm attaching a pic below, for your information and amusement.

I hope someone here can help solve this problem.

Thanks.

---

### Post by RamonBianco on 2008-07-17
[INDENT][INDENT]

[INDENT][INDENT][COLOR=RoyalBlue]**[SIZE=5]Now![/SIZE]**[/COLOR]
[/INDENT][/INDENT][/INDENT][/INDENT]


See a larger image of the problem in [post=5406553][COLOR=Navy]_[SIZE=4]this post in that thread[/SIZE]_[/COLOR][/post].  *  [SIZE=1]([COLOR="Red"]The image has sometimes been unavailable in that post, but you can see it by the thumbnail above.[/COLOR])[/SIZE]*

Tell me if you've *ever* seen *anything* like it.  And how it got fixed.

Thank you for your consideration.

---

### Post by RamonBianco on 2008-07-23
Does anyone have suggestions for other places to look to solve this problem?

Thanks.

---

### Post by RamonBianco on 2008-07-31
BTW, I have tried contacting Samsung *twice* already about this half/double printing issue, with no response.

---

### Post by RamonBianco on 2008-08-08
Are there any alternative locations that might have information on how to correct this printer semi-duplication?

---

### Post by mmoelle1 on 2008-12-07
Hi all,

have you been able to solve the double-half problem without using the binary installer from Samsung?

I use clx-3175n connected by ethernet to a Gentoo box and an Ubuntu laptop. Installation by hand worked fine on both machines, but I see the same strange behavior

> It prints two duplicate, identical, narrow columns, each a half-size version of the page, separated by a series of white bands every 3 mm or so.


Many thanks for your help

Matthias

---

### Post by digiapb on 2009-01-31
Greetings all.

I am having the same issue with my  Sylvania G Netbook Meso....
Ubuntu 8.04 (netbook remix)

I had no issues when I installed the driver on my other laptop, running Linux Mint4 (based on Ubuntu 7.10) 

any ideas or options would be greatly appreciated....

---

### Post by digiapb on 2009-01-31
FYI, I was able to get it up and running using foomatic and foo2qpdl

by following the step by step instructions at:


[http://foo2qpdl.rkkda.com/](http://foo2qpdl.rkkda.com/)

Cheers

---

### Post by jochen on 2009-02-03
Had the same problem (duplicate, identical, narrow columns, each a half-size version of the page, separated by a series of white bands every 3 mm or so) after we had installed the driver from the CD.

It looks like the permissions are set somewhat odd, which is also mentioned here: [http://ubuntuforums.org/showthread.php?t=341621]("http://ubuntuforums.org/showthread.php?t=341621")

What it got going for us is to set the permission for
/usr/lib/cups/filter
/usr/lib/cups/filter/pscms
/usr/lib/cups/filter/rastertosamsungpcl
/usr/lib/cups/filter/rastertosamsungspl
/usr/lib/cups/filter/rastertosamsungsplc
and some more files installed in /usr/lib/cups/filter (which you can find since they have the same date and the same permissions) to read/executable for all. After changing that printing worked.

We may have changed the permission/ownerships of some files before as well. You might have to look at the files installed by the install-programm which you can find using the checkinstall script on the CD in the Linux directory.

---

### Post by RamonBianco on 2010-08-22
It's been a while, but I had originally solved the problem by downloading Samsung's UnifiedLinuxDriver and following some forum advice.

But I did the network upgrade from Fiesty to Lucid yesterday, and my CLP-315 started having the same problem again.

A little Googling lead me to [COLOR="Teal"]_[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)_[/COLOR], which solved the problem.  I used his **IIc.** method.  Since I had used the Samsung drivers previously, I followed the advice, "**Very important:** you **must** have completely removed all prior installations of the Unified Linux Driver before using the .debs; see Section IV.".

---

### Post by rav0r on 2010-10-21
I could not solve the problem neither in ubuntu 10.10, nor in 8.10 or Fedora 12. I think I'll just thow my clp-310 printer away. 
The funny thing is, it worked at some point for me, on an Ubuntu install. 
I have now set all filter permissions to 755, but I still got the same funny double striped column problem.

Foo2js provides poop color quality, it actually messes up all the print. 
I now managed to install using the samsung installer under ubuntu 8.10 but I would like to install without it, as the installer does not work under my Fedora 12.

---

### Post by lhamada on 2011-03-06
Hi all,

I'm seeking volunteer to test a new code that will bring splix package to support the clp-315 and similar devices.

Just follow the link: [https://sourceforge.net/tracker/?func=detail&aid=3196609&group_id=175815&atid=874747](https://sourceforge.net/tracker/?func=detail&aid=3196609&group_id=175815&atid=874747)

Good luck!

---

### Post by hungrywolf99 on 2011-06-30
This is the easiest way I found of installing drivers for the Samsung CLP-315W on Ubuntu 10.10 and 11.04. This also assumes that you have already set up the following printer in your network and is ready to be used.
 

 Firstly download your drivers from the following page:
 

 [http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP00&prd_ia_cd=&prd_mdl_cd=CLP-315W/XEU&prd_mdl_name=CLP-315W&srchword=CLP-315W%2016/4ppm%20-%20%20Mono/Colour%20Network%20&%20Wireless%20Ready](http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP00&prd_ia_cd=&prd_mdl_cd=CLP-315W/XEU&prd_mdl_name=CLP-315W&srchword=CLP-315W%2016/4ppm%20-%20%20Mono/Colour%20Network%20&%20Wireless%20Ready)
 

 You can get away with only downloading the Unified Driver but if you want you can download the Smart Panel as well. Expand one or both of the files by right clicking them and choosing Extract Here option.
 

 Make sure you know where you download it to. For this example all files were downloaded to Downloads/Samsung/ The full path would be given below for ease of access.
 

 **/home/<user name>/Downloads/Samsung/cdroot/Linux/**
 

 Obviously <user name> would be your account name so replace that with your account name. If that is confusing you just go to places and then Downloads and right click on any of the directories and get the properties and you will be able to see the direct path to this area.
 Please note that the second extracted folder will have the name “cdroot 2”. I changed it to “cdroot2” for ease of access.
 

 Now open your terminal by choosing the Ubuntu icon (top left), Accessories, Terminal.
 

 Please key in the following:
 

 ***cd /home/<user name>/Downloads/Samsung/cdroot/Linux***
 

 then key in this:
 

 ***ls***
 

 you will now see the list of files in that directory. One of which will be **install.sh**
 

 Now just key in the following:
 

 ***sudo sh install.sh***
 

 you will now be asked for your admin password. Once you key that in there will be some process and a popup window will appear. Here you will make your choices and detect your printer and and finally it will give you the opportunity to send a test print.
 

 This will conclude the installation of your printer driver.
 If you want to install the Smart Panel, just change directory to:
 

 ***cd /home/<user name>/Downloads/Samsung/cdroot2/Linux/smartpanel/***
  

  and key in the following:
 ***sudo sh install.sh***
  

  this will install the Smart Panel as well. But I found out that this is not really that necessary.
  

  I would like to thank Samsung US help desk for **NOT** helping me with solving this problem. I was requested to call Samsung UK during office hours.
  

  Please feel free to comment on my notes and thank you for reading.
  

  The Hungry Wolf

---

### Post by jackbkjack on 2011-07-01
Previously I have problem with it but after search on Google I got solution.

---

### Post by laercio on 2011-12-27
Friends,

Since the last cup upgrade, I have conection problem to clp-315. I've tried to install samsung driver once again, but during install a message alerts "SANE" problem (sane must be installed, and it is!!!). Everything was fine till this last cups upgrade. Someone knows what changed? I noticed "sane" was mentioned in a hp package....

Tks for help! My daughter uses this printer for homework!!!

---

