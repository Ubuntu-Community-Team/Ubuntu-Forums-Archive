---
title: "Canon PIXMA iP4300"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by craftbrewer on 2006-10-29
My old Epson Stylus Photo 820 is in dire need of an overhaul and as luck would have it there's a sale on the Canon PIXMA iP4300 this week.  I thought the duplex & CD/DVD printing would be nice to have on top of the photo printing... 

Does anyone have any experience with this printer under Ubuntu to share?

---

### Post by kalon33 on 2007-01-07
Using the turboprint driver (which is sold about 30 euros, 39 US dollars) it seems to work (automatic duplex too) but I can't make it working with CD/DVD printing function (I had an ugly dark CD and the CD tray to wash... :/). Maybe there is a way to make it working, but I don't found the good one. Usually Canon provides linux drivers for their printers, but the IP4300 one is not yet available. Hope that it helps you.

---

### Post by Sajzlo on 2007-02-23
Check this drivers out
[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

Hope it will help mate ;-)

---

### Post by Erlander on 2007-03-08
I haven't tried it yet but this guide says it also works for the Pixma iP4300:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

Rob

---

### Post by svenster on 2007-03-08
> **Erlander said:**
> I haven't tried it yet but this guide says it also works for the Pixma iP4300:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

Rob


Hello,

I have followed these instructions to the letter and they work fine with my Pixma iP4300. So far I have only tried printing colour documents, which works fine. Haven't gone into any more detail yet.

Hope this helps!

---

### Post by Erlander on 2007-03-08
That's great.

I bought an iP4300 yesterday and expected that I might not be able to get it going under Linux.

I'll have a try later.

Rob

---

### Post by Erlander on 2007-03-09
Hasn't worked for me but I will keep trying.

Rob

---

### Post by Erlander on 2007-03-10
Success at last.

I tried to un-install all the packages that were installed in the guide but Synaptic told me I had to repair the broken packages before I could un-install.  So instead I reinstalled all of them and then worked through the guide.

I did notice the alien line of code produced an error message that scripts included in the cnijfilter-ip4200-2.60-1.i386.rpm had not been converted so I ran it again just for cnijfilter-ip4200-2.60-1.i386.rpm and included the "-c" option immediately after the alien command.

 ```
sudo alien -c cnijfilter-ip4200-2.60-1.i386.rpm
```

I've even been able to print across my network with the Win XP pc but at present that isn't working like it was.  Something else to look at!!!

But the main thing is that the printer works on the Ubuntu Edgy pc.

Thank you.

Rob

---

### Post by pellgarlic on 2007-04-18
@erlander - can i ask if the print quality from linux is comparable to when printing from windows? i am considering buying this printer because of its good photo printing quality, but am concerned it might not achieve the same quality in linux... have you compared them side-by-side?

---

### Post by Erlander on 2007-04-18
pellgarlic,

Sorry to take so long to answer.

The short answer is I don't know.

After getting it going I formatted my hard disc, installed Feisty and have been busy getting Mythtv running and tweaked for picture quality.

Since seeing your post I have reinstalled it under Feisty on my dual boot pc and have been trying to print some photos jpg images.

I'm having problems as the functionality offered by the image programs offered in Ubuntu is not great and to print to a 4'' x 6'' glossy paper has so far eluded me.  I did get one full size A4 print on plain paper and its quality is good.

I've tried Gimp and although it will allow you to select the main paper tray or the casette where I keep my photo paper the print quality was not as good as F-Spot and G-Thumb produced on the A4.

I feel that provided we can find a suitable application it will be good but with the applications installed by default it is difficult to do.  I've had a look through Synapatic and ADD/Remove Programs and not seen anything that inspires me.  Guess its time for a Google search or to ask on these forums.

Print quality using Windows applications is terrific.

Rob

---

### Post by Erlander on 2007-04-19
Further progress report:

I've been trying out photo printing applications.  Photoprint seems the most hopeful.  General quality on glossy photopaper is good but the prints so far are washed out and too light.  However there are lots of settings for adjusting colour.  An adjustment of gamma to about 0.5 has just about got the same quality as I get from Canon's Windows software.

Haven't managed a borderless print yet though even though onscreen it looks as though that's what I'll get.

My test image is 2274 x 1704 pixels in a jpg at 965.4 KB.

So far I haven't got Gnome Photoprinter to work.

Rob

---

### Post by pellgarlic on 2007-04-19
thanks for the replies erlander :) very informative.

however, i have decided against the canon - i think it'd be more sensible to go for an hp, who supply linux drivers for almost all of their printers. it's a shame, as i was really impressed with the quality of printouts my friend got from his vista-ip4300 setup, but as i wouldn't go near windows with a barge-pole, and the ip4300 isn't fully supported under liux, the decision has kind of been made for me. 

now it just remains to settle on a model of hp...

---

### Post by king minger on 2007-04-19
Hi there
I have this printer and a bunch of 'doze machines.
I've recently installed feisty on a laptop and haven't been to too concerned with getting the two to work. however i would be interested if it can be done, so i can guinnea pig stuff if need be.
Cheers
Al

---

### Post by Erlander on 2007-04-19
I've set it up twice now using the guide mentioned in post #4 with the one variation I listed in Post #8.

However the is no nice Canon Toolbox application so I been trying a few Photo Printing applications and as in Post #11 Photoprint seems the most hopeful except that for photos I had to drop the gamma across the whole range down to about 0.5 or 0.55.

Rob

---

### Post by king minger on 2007-04-19
I'll give it a try this evening :)

---

### Post by renderedbrian on 2007-04-26
Any progress on the IP4300 photo printing?


Cheers

-- 
Brian

---

### Post by Erlander on 2007-04-26
I haven't done anything since my last post.

However the photo print quality I got then was similar to under Windows provided I dropped the gamma setting to about 0.5 or 0.55.

Anyone else ahd any luck?

Rob

---

### Post by Martin T Wirth on 2007-04-29
Canon PIXMA iP4300 does not work on Linux Ubuntu Edgy Eft 6.10. I bought one because the comments above suggested that it would work. I followed the instructions from post 4, even trying --scripts on the alien extraction into deb files before installation, and adding the printer in the usual way after de-installing the old one. The driver seems to expect the printer to be attached to a parallel port as /dev/lp0. There doesn't seem to be any way to reconfigure the driver to scan USB devices. The Canon PIXMA iP4300 has no parallel port connection, only USB.

Canon does not provide any Linux drivers. It works fine if I boot my old Win2k (and have a siesta while Kaspersky AV scans the disk) but I do much of my work on Linux these days. Even a hardware scan on USB will not see this printer while my old HP Scanjet 5400C shows up as did my worn out HP Deskjet 3820.

TurboPrint lists the Canon as one that will work on their drivers. It would be worth the price of the software if I could get it to do so. Alas, this is not the case. It also looks to lp0 by default. I tried every USB device under /dev to no avail. It was unable to connect.

While this printer does a fine job under Win2k, I would not recommend it for Linux until Canon gets with it and publishes a Linux driver. If anyone has any viable suggestions as to how to jury rig this printer to work under Linux, I'm all ears and willing to admit that I might have missed something. But this one might be headed back in exchange for another HP because those seem to work with Linux.

---

### Post by Erlander on 2007-04-29
I had it working under Edgy and now have it working with Feisty.  Even to the extent that I can print over the wired network from a second Ubuntu pc and over wireless from a Win XP Pro laptop.

Canon does provide a driver for the iP4200 and that is what I'm using as per the above posts.

The guide at [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)
works provided you change the Code:

```
sudo alien cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip4200-2.60-1.i386.rpm
``` 

 to:

```
sudo alien -c cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip4200-2.60-1.i386.rpm
``` 

In addition as per the guide the installation of libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common is essential.

Hope this helps.

Rob

---

### Post by The Pinny Parlour on 2007-05-19
Maybe of interest:  [http://www.canon.com.au/support/wsss.aspx?id=ip4300&m=DR&r=http://www.canon.com.au/products/printers/colour_bj_printers/ip4300.aspx?m=support&h=http://www.canon.com.au/products/printers/colour_bj_printers/ip4300.aspx?m=support](http://www.canon.com.au/support/wsss.aspx?id=ip4300&m=DR&r=http://www.canon.com.au/products/printers/colour_bj_printers/ip4300.aspx?m=support&h=http://www.canon.com.au/products/printers/colour_bj_printers/ip4300.aspx?m=support)

---

### Post by Erlander on 2007-05-19
Thank you for that.

Last I checked it wasn't available anywhere but I see on the Japanese site that its been there since April 19.

Have downloaded from [http://www.canon.com.au/support/wsss...aspx?m=support](http://www.canon.com.au/support/wsss...aspx?m=support) but will wait until I have time to install in case I have trouble as the printer is currently working well for me on 2 networked Ubuntu pc's and a Windows laptop.

Thank you.

Rob

---

### Post by The Pinny Parlour on 2007-05-19
> **Erlander said:**
> Thank you for that.

Last I checked it wasn't available anywhere but I see on the Japanese site that its been there since April 19.

Have downloaded from [http://www.canon.com.au/support/wsss...aspx?m=support](http://www.canon.com.au/support/wsss...aspx?m=support) but will wait until I have time to install in case I have trouble as the printer is currently working well for me on 2 networked Ubuntu pc's and a Windows laptop.

Thank you.

Rob

When you get it working please share. [http://ubuntuforums.org/showthread.php?p=2682541#post2682541](http://ubuntuforums.org/showthread.php?p=2682541#post2682541)

---

### Post by Erlander on 2007-05-19
Yes,  will let you know.

I imagine it is very similar to installing the iP4200 driver.  Least ways thats how I will start as per earlier posts in this thread.

I should be able to get to it in the next day or so.

Rob

---

### Post by ultrageeky on 2007-05-20
Hope this helps.  I have the same printer (PIXMA iP4300) and use Kubuntu (well Ubuntu with an added KDE front end).  Couldn't find a driver for it on the Canon European site so searched the web.  Found this forum and followed the installation instructions unfortunately the address given for the drivers lead nowhere.  The correct details I found were:

1 Drivers (common and iP4300 specific) can be found at - 

   [http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx](http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx)

2 To install the drivers use Alien -

   sudo alien -i cnijfilter-common-2.70-1.i386.rpm cnijfilter-ip4300-2.70-1.i386.rpm

3 To install the printer - 
   
   Navigate to the printer program by clicking on KMenu/ System/Printing.  This will bring up a list of available printers.  Click Add/New Printer and follow the instructions.


I'm new to Linux and grateful for the help provided by these forums.

---

### Post by The Pinny Parlour on 2007-05-20
> **ultrageeky said:**
> Hope this helps.  I have the same printer (PIXMA iP4300) and use Kubuntu (well Ubuntu with an added KDE front end).  Couldn't find a driver for it on the Canon European site so searched the web.  Found this forum and followed the installation instructions unfortunately the address given for the drivers lead nowhere.  The correct details I found were:

1 Drivers (common and iP4300 specific) can be found at - 

   [http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx](http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx)

2 To install the drivers use Alien -

   sudo alien -i cnijfilter-common-2.70-1.i386.rpm cnijfilter-ip4300-2.70-1.i386.rpm

3 To install the printer - 
   
   Navigate to the printer program by clicking on KMenu/ System/Printing.  This will bring up a list of available printers.  Click Add/New Printer and follow the instructions.


I'm new to Linux and grateful for the help provided by these forums.

Thanks but doesn't work.  I get this when I use your Step 2: "File "cnijfilter-common-2.70-1.i386.rpm" not found".

---

### Post by Erlander on 2007-05-20
The Pinny Parlor,

The drivers do work but my installation where I had the printer working with the iP4200 drivers is not the same as starting from scratch.

However I do believe that if you use the Ubuntu instructions for the iP4200 and make the necessary changes it will work.  The guide is at:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

Steps 1 & 2 of the guide should be followed as they are.  If you have already downloaded the 2 driver files (cnijfilter-common-2.70.i386.rpm & cnijfilter-ip4300-2.70-1.i386.rpm) then you can skip step 3.

To unpack the 2 tar.gz guide folders just double click on them in the browser.

Step 5 should be changed to:
```

sudo alien -c cnijfilter-common-2.70.i386.rpm cnijfilter-ip4300-2.70-1.i386.rpm
```
but to do this in Terminal you will have to first cd to the folder where you downloaded the 2 driver files to.

Steps 6, 7, 8 & 9 are as in the guide except that in step 9 you are looking for canonip4300.ppd and iP4300 Ver.2.70

If you follow the guide making the above changes it should work for you.

Rob

---

### Post by Erlander on 2007-05-20
> **The Pinny Parlour said:**
> Thanks but doesn't work.  I get this when I use your Step 2: "File "cnijfilter-common-2.70-1.i386.rpm" not found".

In Terminal you will need to first change directories with the cd command to the folder where the 2 rpm's are.

eg for me I have them in a folder canon/2.70  off my Home folder.  So in Terminal I use
```

cd canon/2.70
```
to get there.

Rob

---

### Post by The Pinny Parlour on 2007-05-20
> **Erlander said:**
> The Pinny Parlor,

The drivers do work but my installation where I had the printer working with the iP4200 drivers is not the same as starting from scratch.

However I do believe that if you use the Ubuntu instructions for the iP4200 and make the necessary changes it will work.  The guide is at:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

Steps 1 & 2 of the guide should be followed as they are.  If you have already downloaded the 2 driver files (cnijfilter-common-2.70.i386.rpm & cnijfilter-ip4300-2.70-1.i386.rpm) then you can skip step 3.

To unpack the 2 tar.gz guide folders just double click on them in the browser.

Step 5 should be changed to:
```

sudo alien -c cnijfilter-common-2.70.i386.rpm cnijfilter-ip4300-2.70-1.i386.rpm
```
but to do this in Terminal you will have to first cd to the folder where you downloaded the 2 driver files to.

Steps 6, 7, 8 & 9 are as in the guide except that in step 9 you are looking for canonip4300.ppd and iP4300 Ver.2.70

If you follow the guide making the above changes it should work for you.

Rob

Thanks mate but no go again.  Cheers for trying though.

---

### Post by The Pinny Parlour on 2007-05-20
-desktop:~/canon$ sudo alien -c cnijfilter-common-2.70.i386.rpm cnijfilter-ip4300-2.70-1.i386.rpm
File "cnijfilter-common-2.70.i386.rpm" not found.

---

### Post by The Pinny Parlour on 2007-05-20
Will try downloading them again

---

### Post by The Pinny Parlour on 2007-05-20
No that didn't work either.  Oh well.  Thanks for the help.  Will use it on windows only then.  Printer setup is not easy on Linux.  Mr. Shuttleworth has got alot of work to do.

---

### Post by The Pinny Parlour on 2007-05-20
This worked to convert them:
```
sudo alien -i cnijfilter-common-2.70-1.i386.rpm cnijfilter-ip4300-2.70-1.i386.rpm

```

---

### Post by Erlander on 2007-05-20
> **The Pinny Parlour said:**
> This worked to convert them:
```
sudo alien -i cnijfilter-common-2.70-1.i386.rpm cnijfilter-ip4300-2.70-1.i386.rpm

```

Good.  I'm new to Linux (6 months) so had to look up man to see what that does.  Looks good.

Rob (Shutting Down for the night now)

---

### Post by The Pinny Parlour on 2007-05-20
Well it's installed but Test Page does not print at all.  It's so difficult this setting up of printers.

---

### Post by The Pinny Parlour on 2007-05-20
When sending anything to the printer, the light on the printers blinks and that's it.

---

### Post by Erlander on 2007-05-20
In Printer/Properties/Driver does the driver show as ip4300 Ver.2.70?

If not then you need to go through the last step of Add New Printer routine again.  That is to select iP4300 Ver.2.70 from the list of printers.

ie after you select select /usr/share/cups/model/canonip4300.ppd then in the drop down menu of printers iP4300 Ver.2.70 should now be there too so at this stage you select it and not Pixma ip4300.  I found this step confusing too.

Rob

---

### Post by The Pinny Parlour on 2007-05-20
> **Erlander said:**
> In Printer/Properties/Driver does the driver show as ip4300 Ver.2.70?

If not then you need to go through the last step of Add New Printer routine again.  That is to select iP4300 Ver.2.70 from the list of printers.

ie after you select select /usr/share/cups/model/canonip4300.ppd then in the drop down menu of printers iP4300 Ver.2.70 should now be there too so at this stage you select it and not Pixma ip4300.  I found this step confusing too.

Rob

Yes.  It shows ip4300 Ver 2.70

---

### Post by The Pinny Parlour on 2007-05-20
As usual networking and printers don't work in ubuntu.  *shakes head*

---

### Post by Erlander on 2007-05-20
Stay working on it.

My iP4300 is on a dual boot pc and works from both Ubuntu and Win XP Home.  It also works from a second wired network Ubuntu pc and from a wireless connected laptop running XP Pro.

Rob

---

### Post by Erlander on 2007-05-20
Try moving the printer to the Ubuntu pc and setting it up as a local printer before trying to get it going over the network.

Removes one variable.

Rob

---

### Post by The Pinny Parlour on 2007-05-20
> **Erlander said:**
> Try moving the printer to the Ubuntu pc and setting it up as a local printer before trying to get it going over the network.

Removes one variable.

Rob

Yeah tired that already.  Doesn't work.  I wish I could totally rid the entire ubuntu OS of printer/s then reinstall all of it from factory defaults.  Maybe that would help.  It just deosn't work for some reason.  grr grr grr networking and printers on ubuntu.

---

### Post by Yettie on 2007-05-25
> **The Pinny Parlour said:**
> -desktop:~/canon$ sudo alien -c cnijfilter-common-2.70.i386.rpm cnijfilter-ip4300-2.70-1.i386.rpm
File "cnijfilter-common-2.70.i386.rpm" not found.

The problem is with a typing error. There should be '-1' after '2.70', in other words it should be:-

'cnijfilter-common-2.70-1.i386.rpm'

---

### Post by koshari on 2007-05-26
these drivers work a treat for me and they come in deb packages.

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

also ubuntu and shuttleworth arnt to blame, the blame lies with canon.

---

### Post by jekberdo on 2007-06-28
Hi, I'm new in writing on ubuntuforums, I hope these informations can be usefull to someone.
I've a Canon Pixma IP4300. It worked fine under Windows Vista on my Laptop, but I use my main Desktop with Ubuntu Fiesty as a Printer Server, so I'm trying to make the printer work on it.
These are the steps I made:
[LIST=1]
[*]Download the drivers and the help guide fron Canon Australian Web Site [http://www.canon.com.au/support/wsss...aspx?m=support](http://www.canon.com.au/support/wsss...aspx?m=support)
[*]Create a new directory where to work and move there all the files:
```
jek@jek-desktop:~$ mkdir canon
jek@jek-desktop:~$ mv <downloadpath>/cnijfilter-common-2.70-1.i386.rpm gutenprint-5.0.1-1lsb3.1.i486.rpm faq-pd-2.70-1 cnijfilter-ip4300-2.70-1.i386.rpm  guideip4300-pd-2.70-1 ~/canon/

```
[*]Install alien and some other packages you will need via apt-get
```
jek@jek-desktop:~$sudo apt-get install alien libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common

```
[*]Convert rpm packages into deb packages
```
jek@jek-desktop:~$cd canon
jek@jek-desktop:~/canon$ sudo alien --to-deb --scripts cnijfilter-common-2.70-1.i386.rpm cnijfilter-ip4300-2.70-1.i386.rpm 

```
[*]Install packages with dpkg.
Please **watch closely your filenames**. They could be different from mine!
```
jek@jek-desktop:~/canon$sudo dpkg -i cnijfilter-common_2.70-2_i386.deb
jek@jek-desktop:~/canon$sudo dpkg -i cnijfilter-ip4300_2.70-2_i386.deb

```
You can also open your ~/canon with nautilus and double click on your .deb files.
If you choose this way remember that first of all you have to change the owner of the deb files:
```
jek@jek-desktop:~/canon$sudo chown <your_username>:<your_group> *

```
And then you can double click on the files without any problem.
Remember also that you have to install the common file (actualy: cnijfilter-common_2.70-2_i386.deb) **before** the ip4300 file.
[*]The packages need the following links:
```

jek@jek-desktop:~/canon$sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
jek@jek-desktop:~/canon$sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3
jek@jek-desktop:~/canon$sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1
jek@jek-desktop:~/canon$sudo ldconfig 

```
[*]Restart cupsd
```
jek@jek-desktop:~/canon$sudo /etc/init.d/cupsys restart

```
[*]Install your printer using the GUI (System->Administration->Printers --> New Printer), choosing the new IP4200 driver (for newer driver it will be IP4300).
If you can't find driver in the list, then you have to select Canon as manufacturer and click on "Install Driver..." and select /usr/share/cups/model/<driver_name>
[*]You're done!
[/LIST]
Hope it could work for you, I've jus printed my first test-page, I don't already know anything about cd printing and double-side printing, I will report as soon as I will give a try.
Thanks for anybody tha would/could help with this printer.;)
Bye!
Jek

---

### Post by The Pinny Parlour on 2007-06-28
I hope you have more success than I have had in trying to get it to work.  Try printing out a document and report back.

---

### Post by jekberdo on 2007-06-28
I printed some openoffice documents and it worked fine, even the duble-side printed worked for me. No luck with cd printing.
What kind of process did you follow to install the printer? What version of Ubuntu?

---

### Post by The Pinny Parlour on 2007-07-21
I can't get past the second line.  No such directory exists blah blah blah. 

 `gutenprint-5.0.1-1lsb3.1.i486.rpm': No such file or directory
mv: cannot stat `faq-pd-2.70-1': No such file or directory
mv: cannot stat `cnijfilter-ip4300-2.70-1.i386.rpm': No such file or directory
mv: cannot stat `guideip4300-pd-2.70-1': No such file or directory
-desktop:~$ mv /home//Desktop/Canon/cnijfilter-common-2.70-1.i386.rpm gutenprint-5.0.1-1lsb3.1.i486.rpm faq-pd-2.70-1 cnijfilter-ip4300-2.70-1.i386.rpm  guideip4300-pd-2.70-1 ~/canon/
mv: cannot stat `gutenprint-5.0.1-1lsb3.1.i486.rpm': No such file or directory
mv: cannot stat `faq-pd-2.70-1': No such file or directory
mv: cannot stat `cnijfilter-ip4300-2.70-1.i386.rpm': No such file or directory
mv: cannot stat `guideip4300-pd-2.70-1': No such file or directory
-desktop:~$ mv '/home//Desktop/Canon' /cnijfilter-common-2.70-1.i386.rpm gutenprint-5.0.1-1lsb3.1.i486.rpm faq-pd-2.70-1 cnijfilter-ip4300-2.70-1.i386.rpm  guideip4300-pd-2.70-1 ~/canon/
mv: cannot stat `/cnijfilter-common-2.70-1.i386.rpm': No such file or directory
mv: cannot stat `gutenprint-5.0.1-1lsb3.1.i486.rpm': No such file or directory
mv: cannot stat `faq-pd-2.70-1': No such file or directory
mv: cannot stat `cnijfilter-ip4300-2.70-1.i386.rpm': No such file or directory
mv: cannot stat `guideip4300-pd-2.70-1': No such file or directory
-desktop:~$

---

### Post by The Pinny Parlour on 2007-07-21
There has to be an easier way.

---

### Post by The Pinny Parlour on 2007-07-21
Is there any easier,simpler way to install this printer.  Please.

---

### Post by Erlander on 2007-07-21
The guide works every time for me with my iP4300.

I had a graphics card fail a couple of weeks ago and after buying a new one decided to re-install Feisty on both pc's.  Then installed the printer as a local printer on one pc and as a network printer on the other.  Works well including from a windows laptop through wireless and to the ubuntu pc the printer is on.

As someone said earlier be very careful with file names in your code.

Rob

---

### Post by The Pinny Parlour on 2007-07-21
I cant even get past the first line of code.

There must be an easier way  please help me with this.

---

### Post by The Pinny Parlour on 2007-07-21
I know it's not windows but heck it's easier than this.

---

### Post by The Pinny Parlour on 2007-07-21
mv <downloadpath>/cnijfilter-common-2.70-1.i386.rpm gutenprint-5.0.1-1lsb3.1.i486.rpm faq-pd-2.70-1 cnijfilter-ip4300-2.70-1.i386.rpm  guideip4300-pd-2.70-1 ~/canon/

<downloadpath>   I think this is where I fail.  What on earth goes here?  I have tried the directories of where I have the canon files I downloaded but I get errors.

 `gutenprint-5.0.1-1lsb3.1.i486.rpm': No such file or directory
mv: cannot stat `faq-pd-2.70-1': No such file or directory
mv: cannot stat `cnijfilter-ip4300-2.70-1.i386.rpm': No such file or directory
mv: cannot stat `guideip4300-pd-2.70-1': No such file or directory
-desktop:~$ mv /home//Desktop/Canon/cnijfilter-common-2.70-1.i386.rpm gutenprint-5.0.1-1lsb3.1.i486.rpm faq-pd-2.70-1 cnijfilter-ip4300-2.70-1.i386.rpm guideip4300-pd-2.70-1 ~/canon/
mv: cannot stat `gutenprint-5.0.1-1lsb3.1.i486.rpm': No such file or directory
mv: cannot stat `faq-pd-2.70-1': No such file or directory
mv: cannot stat `cnijfilter-ip4300-2.70-1.i386.rpm': No such file or directory
mv: cannot stat `guideip4300-pd-2.70-1': No such file or directory
-desktop:~$ mv '/home//Desktop/Canon' /cnijfilter-common-2.70-1.i386.rpm gutenprint-5.0.1-1lsb3.1.i486.rpm faq-pd-2.70-1 cnijfilter-ip4300-2.70-1.i386.rpm guideip4300-pd-2.70-1 ~/canon/
mv: cannot stat `/cnijfilter-common-2.70-1.i386.rpm': No such file or directory
mv: cannot stat `gutenprint-5.0.1-1lsb3.1.i486.rpm': No such file or directory
mv: cannot stat `faq-pd-2.70-1': No such file or directory
mv: cannot stat `cnijfilter-ip4300-2.70-1.i386.rpm': No such file or directory
mv: cannot stat `guideip4300-pd-2.70-1': No such file or directory
-desktop:~$
_______________

---

### Post by The Pinny Parlour on 2007-07-21
Think I may have some success in installing.  Test pages sent and pages sent to printer from Open Office don't print however.  I get the message,  Stopped: Job-stopped   

Any ideas?

---

### Post by Erlander on 2007-07-21
Check the driver in Printer Properties.

System/Administration/Printers.  Right click the printer and select Properties.

Then select the Driver tab.  It should show iP4300 Ver.2.70 as selected.

Rob

---

### Post by The Pinny Parlour on 2007-07-21
> **Erlander said:**
> Check the driver in Printer Properties.

System/Administration/Printers.  Right click the printer and select Properties.

Then select the Driver tab.  It should show iP4300 Ver.2.70 as selected.

Rob

Yep.  In printer windows it says it's read.  Properties, its all set.  I double click on the printer icon on the taskbar and Stopped: job-stopped    POS thing it is.  :mad:

---

### Post by jekberdo on 2007-08-13
I had to re-install my whole system due some troubles I experienced with my hard-disk (Damn it!).
Now I'm facing a strange problem with the printer: I installed it following the steps I wrote before in this thread, the printer installed correctly and I expected no problems, but now it doesn't print anymore. I think I got the new version of the drivers (I think it's the only change I could have made from the last time I installed it) and maybe this new version doesn't work anymore.
The fact is that I shared this printer with my Windows laptop and the printer works, with the windows driver, via the network.
Any suggestion?

---

### Post by Erlander on 2007-08-13
I had to reinstall recently too and also had a bit of trouble.

in my case because I still had the ,deb files I skipped the early parts of the guide and missed the  downloads and installs in step 2 of the guide.

Other than that be sure to change iP4200 to iP4300 in all the scripts.

Rob

---

### Post by jekberdo on 2007-08-14
So you used the old packages?
Does the printer worker that way?
Can you e-mail me the packages?
I'm sure I did not commit any mistakes, or spell-errors.

---

### Post by Erlander on 2007-08-14
I used the iP4300 2.70-1.i386.rpm files downloaded from the Canon Australia site:  [http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx](http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx)

Then I used the iP4200 guide at  [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

I always have 3 windows open when installing:

1.    a terminal window
2.    a file browser (through Places/Home Folder
3.    a firefox window with the guide open

I copy and paste the code from firefox to the terminal to be sure I haven't any typos.

in the browser window I check the file names and locations to be sure I have both correct and avoid file not found errors.

The changes I make to the guide are on account of the different file names and locations seeing as I'm using the iP4300 files and not iP4200 as in the guide.

As I explained in an earlier post I change 
sudo alien -c cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip4200-2.60-1.i386.rpm
```
sudo alien cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip4200-2.60-1.i386.rpm
```

to 

```
sudo alien -c cnijfilter-common-2.70-1.i386.rpm cnijfilter-ip4300-2.70-1.i386.rpm
```  

(addition od "-c", "2.60" changed to "2.70" and "ip4200" changed to "ip4300".

Perhaps I should write all this up as a How To.

I have the printer on one pc that is running Feisty 7.04 on a wired network to another Feisty 7.04 pc and a wireless network to a Windows XP laptop.  All can print well.

Rob

---

### Post by Erlander on 2007-08-14
> **The Pinny Parlour said:**
> Yep.  In printer windows it says it's read.  Properties, its all set.  I double click on the printer icon on the taskbar and Stopped: job-stopped    POS thing it is.  :mad:

I've been thinking about this.

I had similar errors at one time in Firefox printing.  It was because the printer was set to A4 paper size and Firefox was set to Letter size.

Check your paper sizes in Printer Properties and in Open Office Print Setup.

Rob

---

### Post by jekberdo on 2007-08-16
Thanks Erlander.
I skipped the part of the links.
Now it works.
Very thanks to you.
Jek

---

### Post by 2CV67 on 2007-08-21
A few days ago, Erlander said: "Perhaps I should write all this up as a How To."
I would really, really appreciate that! 
Thanks in advance - especially if it can be in small beginner-oriented steps :)

I am now at the stage of needing a new printer & had decided on an iP4300 until I saw it was not supported by Linux.
Then I saw Canon Australia offered drivers, so thought it was OK.
Then I saw all the problems in this thread (& others) and feel doubtful again.
I looked further on the .au site & was confused to find 3 .rpm downloads & 2 tar.gz downloads but no instructions. This is obviously not aimed at people like me!

First question: Does iP4300 print at full quality or only at 600dpi with Australian driver?

Second question: How long before the "How To" ?

Third question: I suppose GUI method would be way too much to ask...?

Thanks !

---

### Post by Erlander on 2007-08-21
I will try and write up a HowTo over the next week.  However I have a bit on my plate at the moment and cannot guarantee that time frame.  As someone who only started with Linux 9 months ago I understand the problems facing newcomers.  I do have the advantage that I used to use the command line in MSdos!!!!

It will need use of the terminal.  I remember spending weeks wondering how to enter the code different people on this forum said to use for different things so will get down to that level.  Rather than typing in code the easiest way is to copy and paste.  - Gets rid of small typos.

I believe that it does offer the full range of print quality but how do you tell whether they are actually working?  They are in the drop down menus.

Having said that the print quality of photos I've printed seems the same as under windows except I had to tweak the gamma setting.

Rather than putting a mail up on the forum I'll put the guide on my website as I will be able to include screen shots that way.  I don't know how to get on the official Ubuntu Help site but if that is possible then it would be better still there.

Rob

---

### Post by 2CV67 on 2007-08-22
Thanks & I look forward to the "How To".

Hope you will indicate in this thread where & when it is available.

Good to hear that quality is apparently OK.

Agree that copy/paste is better than live typing, but only if what you copy is exactly what you need...

I wrote programs when they were on punched cards, but I still think GUI was a HUGE leap forward & that Linux needs to catch up if it wants to extend it's user base to non-geeks.
Sorry for that lapse!

Thanks again :)

---

### Post by jekberdo on 2007-08-22
For the moment you can see on of mine previous post in this thread. I made a merge from different guides and from the suggestions Erlander gave me.
Hope it can help.
Bye.
jekberdo

---

### Post by Erlander on 2007-08-26
First draft of the guide is now at:

[http://www.erlandertervueren.com/ubuntu/ip4300_guide/](http://www.erlandertervueren.com/ubuntu/ip4300_guide/)

Because I already have the printer installed I had trouble going through the last steps of Add Printer.  To do it well it really needs a clean install and I didn't want to lose all my other Ubuntu setup.

So please advise me of any problems and hopefully all of us here can work out what to do.

I am very open to suggested improvements.

Rob

---

### Post by 2CV67 on 2007-08-26
Rob,

Thanks for that great guide!

For various reasons I will not be able to try it for several days, but already I would like to say how much I appreciate the level of detail & illustration, which is just what I need.

Thanks again!

---

### Post by Muchacho_Gasolino on 2007-08-26
That guide is great, Erlander. Worked perfectly. Thanks!

---

### Post by Erlander on 2007-08-26
Thank you for the feedback.

I was worried that there may have been an error or 2 as the computer behaves differently in the "Add Printer" stage when the driver is already installed.  I did that part from memory and edited one or 2 of the images.

Rob

---

### Post by 2CV67 on 2007-09-19
HUGE THANKS to Erlander for the great work on that Installation Guide !
I finally got round to trying it and the results are excellent. :)

Without this thread, I would NEVER have dared buy this printer for use with Ubuntu.
Why on earth do Canon not make these existing drivers more obviously available – and increase their sales?

Does anybody have more information on the ‘Print Resolution’ question at the end of the Installation Guide?
In other words, is it helpful or harmful or just unnecessary to add the ‘Print Resolution’ lines as well as the ‘Quality’ lines?

Erlander: you asked for feedback on using the installation guide, so here is my experience – don’t take this as criticism, this is WAY the BEST guide I have seen for anything in Linux so far. The minor snags probably just reflect my level of incompetence with Ubuntu today.

1.	At step 2, I believe I copy/pasted the 2 lines of code at the same time, but after “enter” +  password + “enter” then only the first line was executed, so I had to copy/paste the second line & try again. Not sure if this means I did not copy both lines first time, or if terminal will only accept one item at a time?
2.	At step 3, I thought I had renamed my new folder ‘canon’ but could not find it anywhere. This was because I thought renaming worked like in Windows, where if you insert the new name then click elsewhere then the new name sticks, but in Ubuntu it reverts to ‘new folder’ so you have to “enter” after inserting new name…
3.	Under ‘Advanced features’, you say ‘back up your ppd file’ but as a novice it took me some time to work out which file & where it was & how to back it up. It sure would bring this section up to the fantastic level of the rest if you spelled that out fully for us dummies!

Grateful thanks again!

---

### Post by The Pinny Parlour on 2007-09-19
Just revisited this thread.  Sweet guide there.  Can't wait to try it.

Thank you.

---

### Post by The Pinny Parlour on 2007-09-20
Packages from Canon have been updated 2.70-2.  The guide could be updates to reflect this.

---

### Post by Erlander on 2007-09-20
Thank you 2CV67 and Pinny Parlor.

I will try and get those changes made.

Rob

---

### Post by measekite on 2007-09-21
After you do all this can you then install Gutenprint?  Is Guten print basically a GUI that operates this print driver or does Gutenprint bypass the driver and use something of its own?

---

### Post by Erlander on 2007-09-21
> **measekite said:**
> After you do all this can you then install Gutenprint?  Is Guten print basically a GUI that operates this print driver or does Gutenprint bypass the driver and use something of its own?
I'm sorry.  I don't know.  I've been using linux for less than 12 months and haven't used Gutenprint.

If its just another print driver then you should have a choice when you print.

Rob

---

### Post by measekite on 2007-09-21
Why the change in code?  What does the -c do?

---

### Post by Erlander on 2007-09-21
From the man alien page:

 > to convert the scripts that are meant to be run when the pack&#8208;
           age is installed and removed

It goes on to say that the -c option should be used with caution but I found that the driver didn't work for me if I didn't run it.    Instead I saw a message when alien was running to the effect that scripts were not being run.  See earlier posts in this thread.

Rob

---

### Post by delfick on 2007-09-22
> **The Pinny Parlour said:**
> Packages from Canon have been updated 2.70-2.  The guide could be updates to reflect this.

how do these ones work for people ?? :D

and anyone able to get a resolution greater than 600 dpi ??

I'm thinking of buying this printer..... :D

---

### Post by The Pinny Parlour on 2007-09-30
> **delfick said:**
> how do these ones work for people ?? :D

and anyone able to get a resolution greater than 600 dpi ??

I'm thinking of buying this printer..... :D

I personally haven't been able to get over 600dpi but the duplexing works great however.

---

### Post by botheredbybees on 2008-03-22
bit of an anti-climax actually. Read through a couple of threads, found and downloaded the drivers, and then (belatedly) plugged the printer into my Gutsy install... printer found, recognised and set up automagically (duh)

---

### Post by maxpathan on 2008-07-09
When I installed Hardy, I just connected the printer and it just worked. I dont recall downloading any drivers.

HOWEVER, yesterday I tried printing a poster (colour text and graphics) and the output was not very good. I printed the same doc in windows and it was as expected.

I'm not sure if it's the settings for the driver, I tried CMYK, CMY, RGB, but none of them performed satisfactorily.

Any one had a similar experience ?

---

### Post by Erlander on 2008-07-09
Yes.  I've had similar experiences.  I've yet to spend a lot of time adjusting the Ubuntu supplied drivers.

Unfortunately the drivers supplied by Canon don't work when installed by the method described in this thread when used with 8.04 Hardy Heron.

Again with perseverance they might but I haven't found a way yet.

Rob

---

