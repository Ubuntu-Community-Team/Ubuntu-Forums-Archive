---
title: "Driver for Kodak ESP C310 All-In-One printer?"
date: 2011-03-20
forum: Hardware
---

### Post by Gogeden on 2011-03-20
Has anyone made any drivers for this printer? I know the a******* at Kodak don't support GNUx (GNU/Linux). I tried the drivers from this page: [http://sourceforge.net/projects/cupsdriverkodak/](http://sourceforge.net/projects/cupsdriverkodak/). I didn't get very much but the ESP 5200 driver only got the printer to pull the paper down but not print. And I refuse to go back to Windows just for a printer.

---

### Post by fyfe54 on 2011-03-21
> **Gogeden said:**
> Has anyone made any drivers for this printer? I know the a******* at Kodak don't support GNUx (GNU/Linux).

I have the same printer.  Wife uses Win7, and I use XP in VirtualBOX to print.  I REALLY want to be able to go native as this is a really nice photo printer.

---

### Post by coreytrice on 2011-04-27
I have the same printer and I would like to be able to print from my Ubuntu machines. Does anyone have any idea about where to get a driver for this? Thanks for any help...

---

### Post by SpatryX on 2011-05-08
the cups driver on sourceforge did not work for me either,,, I have this same printer,,, Looks like I have to email docs to a windows machine,,, I will never buy from kodak again

EDIT: Since I have WindBLOWS XP installed as a virtual machine within VMWARE, I found that the virtual appliance recognises my printer and with driver installed, it runs flawlessly... it sucks that I must run XP to use my printer though... I guess it will have to do until a linux driver is made for this printer...

---

### Post by Tootler on 2011-06-07
I just bought this model, had problems setting it up so I had a look round the internet and it seems that Kodak do not provide Linux drivers for their printers. There are some third party drivers from sourceforge but they seem only partly functional - printing but no scanning or wifi, so I took it back and exchanged it for an HP Photosmart which I know will work with Ubuntu as I have been using an HP printer up to now.

---

### Post by Gogeden on 2011-06-23
Just so you all know, this printer ripped me off. Won't even allow me to scan something unless I change the color ink cartridge because the printer tells me it is qua is empty. P.O.S. Anyone have any luck under 11.04?

---

### Post by guyrichie@hotmail.com on 2011-07-16
Hello All,

Kodak did email me saying that they don't currently support linux.  However, they have generated an Android app, "Kodak Pic Flick" that can print via Wi-Fi to any ESP C3xx model.  This would suggest a relevant linux driver does exist in some form; with Google Android being based on a linux kernel.  Is anyone able to peek inside this Android app for a PostScript Printer Description (.ppd) file?  Or is it possible to install this Android app on Ubuntu and print via it somehow?

Thanks.

---

### Post by ken bright on 2011-07-20
The driver from source forge appears to work ok for me on an esp 5250 thanks to whoever wrote it. Going to start pestering Kodak now!

---

### Post by ewan86 on 2011-08-03
Doesn't work for me on kodak c310....so annoying!!!!

---

### Post by kerjava on 2011-08-13
here is a chat i had with a Kodak help assistant   do with it what you will 
:KSemail me if u have any developments to this topic or solutions 






kerjava : I'm trying to find a .ppd file for the Kodak ESP C310 Wi-Fi All-In-One Printer[All of our specialists are assisting other customers. We apologize for the delay and appreciate your patience. Please continue to hold and your chat will be answered by the next available specialist.](8:19:20 PM)[You are now chatting with 
Gourishankar B.]
Gourishankar B (8:19:38 PM): Welcome to Kodak, my name is Gourishankar . Please wait while I review your question.
Gourishankar B (8:19:51 PM): May I please know the country that you are from?
kerjava (8:19:56 PM): usa
Gourishankar B (8:20:03 PM): Thank you.
kerjava (8:20:10 PM): welcome
Gourishankar B (8:21:17 PM): I apologies as I am not able to understand what type of file is it. Could you please let me know what file is it ?
Is it some kind of driver file ?
kerjava (8:21:49 PM): yes it is a ppd
kerjava (8:23:19 PM): PostScript Printer Description
kerjava (8:24:55 PM): are you still there?
Gourishankar B (8:25:15 PM): Kodak All In One Printers have .inf driver files . I will assist you in locating those files. However before that could you please help we with some information ?
kerjava (8:25:43 PM): ok
Gourishankar B (8:26:30 PM): May I please have the Kodak Service Number for your printer? You can find this number by opening the printer access door like you are going to change the ink cartridges. This number will be located on the right hand side.
kerjava (8:26:53 PM): I'm not looking for an inf file though I'm looking for a PostScript Printer Description file or ppd
kerjava (8:26:59 PM): ok one sec
kerjava (8:28:31 PM): where would i find this number?
Gourishankar B (8:31:34 PM): You will find the number when you open the printer access door to change the ink cartridges. It will be on the right hand side.
kerjava (8:32:25 PM): 02f1783Gourishankar B (8:33:12 PM): Thank you.
Gourishankar B (8:33:23 PM): May I please know when and from which store did you buy the printer?
kerjava (8:34:08 PM): tuesday last week
kerjava (8:34:12 PM): walmart
Gourishankar B (8:34:51 PM): May I please know the operating system on the computer?
Is it Windows XP or Windows Vista or Windows 7?
kerjava (8:35:06 PM): y
kerjava (8:35:08 PM): why
Gourishankar B (8:36:29 PM): It is because that the post script drivers are already in the operating system above Windows Xp but it is not installed in operating system below Windows XP.
kerjava (8:37:30 PM): it is not those
Gourishankar B (8:40:28 PM): Okay.
kerjava (8:40:56 PM): is there a generic driver
kerjava (8:41:01 PM): a ppd
Gourishankar B (8:41:09 PM): I would like to tell you that the ppd files are already embedded in the inf files.
Gourishankar B (8:41:16 PM): May I please know the operating system on the computer?
kerjava (8:41:38 PM): how can i un embed it
Gourishankar B (8:42:30 PM): We can not do that
kerjava (8:42:36 PM): why
kerjava (8:42:56 PM): not
kerjava (8:43:44 PM): it asks for a ppd not an idf
Gourishankar B (8:44:48 PM): I do understand but we do not have the ppd file.
kerjava (8:45:12 PM): could you generate one
Gourishankar B (1:47:00 PM): I will pass this concern of yours to my supervisors however as of now we do not have any ppd file.
kerjava (1:47:40 PM): ok thank you
kerjava (1:49:07 PM): I appreciate your patience
Gourishankar B (1:49:23 PM): For a reference to this chat, please keep this number 8672081 .
kerjava (1:49:44 PM): ok thank you
Gourishankar B (1:49:51 PM): Is there any other support I may provide you with today?kerjava (1:50:29 PM): what duse idf stand for?
kerjava (1:50:36 PM): *inf
kerjava (1:51:59 PM): what duse inf stand for in the context of an inf file 
Gourishankar B (1:53:31 PM): It stands for information file and it contains all the information for the printer.
kerjava (1:53:51 PM): how can i read this file
Gourishankar B (1:55:35 PM): You can gain access to the file by browsing to C:\Program Files\Kodak\AIO\PrinterDriver2 and then Select the EKAiO2.inf  file
kerjava (1:55:56 PM): thank you but how can i open it
Gourishankar B (1:57:52 PM): Inf files are encrypted files and it might be only in a read only format and you can open it with the help of a note pad.
Gourishankar B (1:58:01 PM): You can not edit it.
kerjava (1:58:12 PM): y not
kerjava (1:58:23 PM): why not
kerjava (1:58:40 PM): can I convert it to a ppd
Gourishankar B (1:59:10 PM): I am sorry you will not be able to do it because those files are encrypted files.
kerjava (1:59:58 PM): can you provide me with the encryption algorithm 
kerjava (2:00:44 PM): to unencrypted 
kerjava (2:00:48 PM): it
Gourishankar B (2:01:58 PM): I will love to assist you in that but however I do not have the information on how to do it.
kerjava (2:02:28 PM): ok do you know of a way i can obtain that information 
Gourishankar B (2:04:40 PM): I am sorry however that information is confidential.kerjava (2:06:10 PM): do can you provide me with the driver for the android phone app kerjava (2:06:37 PM): or a way to obtain it 
Gourishankar B (2:07:29 PM): Yes sure.
Gourishankar B (2:07:33 PM): Please allow me a minute
kerjava (2:07:39 PM): thank you
Gourishankar B (2:10:54 PM): You can download the application for Android Phone by going to the link [www.kodak.com/go/android](www.kodak.com/go/android) or from Android Market. The name of the application is PicFlick.
kerjava (2:11:30 PM): ok can you give me just the driver from it?
Gourishankar B (2:12:33 PM): Only the drivers are not available . If you download the application then you will get the drivers within it.
kerjava (2:13:01 PM): and i take the aplication appart
kerjava (2:13:07 PM): *apart
kerjava (2:13:33 PM): with a normal comp os
kerjava (2:13:44 PM): *computer 
Gourishankar B (2:15:31 PM): I do appreciate your knowledge. I do not that much information on how to do it.
kerjava (2:16:31 PM): is there a eay to run the application not on the android phone
kerjava (2:17:23 PM): *way
Gourishankar B (2:18:33 PM): To run the application you would require the android OS and to my extent of knowledge I dont think it is possible. However I can not commit the same. I do not have any knowledge about the Android OS.
kerjava (2:20:44 PM): ok thank you can you connect me to someone that knows the android os or would i have to go back to the help form and select it from there and if so where would i do that
Gourishankar B (2:24:28 PM): I do apologise however as a Kodak All In One Printer technical support associate the best we can assist you with is installing the Android Application on the android phone
.kerjava (2:25:31 PM): ok thank you for your time ill look at the forms and try to find help with the app
kerjava (2:25:49 PM): could u point me in the right direction

---

### Post by kerjava on 2011-08-14
> **guyrichie@hotmail.com said:**
> Hello All,

Kodak did email me saying that they don't currently support linux.  However, they have generated an Android app, "Kodak Pic Flick" that can print via Wi-Fi to any ESP C3xx model.  This would suggest a relevant linux driver does exist in some form; with Google Android being based on a linux kernel.  Is anyone able to peek inside this Android app for a PostScript Printer Description (.ppd) file?  Or is it possible to install this Android app on Ubuntu and print via it somehow?

Thanks.
i went through the app as best i know how and could not find a ppd file i think they fond a way to have it use the inf file instead

---

### Post by guyrichie@hotmail.com on 2011-09-03
Hello All,

Found .PPD file on OSX today.  However, it calls for a cups filter unique to OSX.  I tried copying the OSX filter to ubuntu but it can't read the binary file - no suprise there as it is compiled for OSX.

Thought I would try changing the .PPD filter line in gedit to...

*cupsFilter: "application/vnd.cups-raster 50 /usr/lib/cups/filter/c2esp"
*cupsFilter: "application/vnd.cups-command 50 /usr/lib/cups/filter/command2esp"

... as these filter lines appear in the working .PPD files contained in paulnewall's "Kodak CUPS driver for Kodak ESP 5xxx AiO" ([http://sourceforge.net/projects/cupsdriverkodak/?showfeed=code](http://sourceforge.net/projects/cupsdriverkodak/?showfeed=code))

Replacing these lines did not work either.

I will attach the PPD file and the OSX cups filter for what its worth.  My limited knowlege of getting this printer to work is now exhausted.

Good luck everyone,
Cheers.

---

### Post by walt.smith1960 on 2011-09-03
When I look at hardware like Kodak and find no manufacturer support, I find the name of the CEO, write (snail mail) and tell him/her WHY I bought their competitor's product. I don't know if it helps but it make me feel better :) and if a number of people do something similar,  perhaps manufacturer's attitudes will evolve a bit.

---

### Post by scunner3 on 2011-09-13
If you don't mind not using a driver, you can register with the Kodak/Google cloud and ask for an email address for your printer. Then you can print from any device anywhere via the net.
This solves my problem. Hope it's of use to others.

---

### Post by SpatryX on 2011-09-14
scunner3, Thank you for sharing that tidbit of info. I read the information on setting up cloud printing but the Kodak website indicates that you need to have the printer plugged in to your computer with drivers installed. Since there are no Linux drivers, what steps did you go through to set-up cloud printing?

---

### Post by alayahlan on 2011-09-19
Luckily our home network includes at least one Windows computer. Our living room media player is windows 7, so we installed the kodak esp c310 on it, then installed the Google Cloud connector. We can print from all the computers now with the cloud email, it just takes a bit of time.

---

### Post by SpatryX on 2011-09-21
After updating the firmware on this unit I am unable to print in my virtualbox XP installation... Even with a USB cable... I could not get cloud printing to work at all... Kodak PIC Flic works from my android phone for printing through wifi... 

To print text documents here are the steps when using Kodak Pic Flic

1. make sure you have imagemagick installed (you should be able to get it from synaptic)

2. Compose your text document in OoO or Libre Office and export as PDF.

3. Open terminal and navigate to the folder where you saved the PDF file

4. Issue the following command 
```
convert -density 300 sample.pdf sample.jpg
```  
Note: you will want to set the density to 150 0r 300 to get sharp text to print. The larger the number, the larger the file... If there is more than one page it will create a separate JPG for each page which must be printed individually.

5. Transfer the created files to your droid and send to wireless printer through Pic Flic

Setting up Pic Flic is easy so I am not including instructions for that here...

I know there are a few hoops to jump through, but at least I can now get critical documents printed. <sigh> It took me all darned night trying to get some documents for work printed!

[http://www.youtube.com/watch?v=32xPryT8I_Q](http://www.youtube.com/watch?v=32xPryT8I_Q)

---

### Post by paulnewall on 2011-10-08
You may be able to use the latest c2esp20a with the espC310
[https://sourceforge.net/projects/cupsdriverkodak/files/](https://sourceforge.net/projects/cupsdriverkodak/files/)
but you have to compile and install it.

---

### Post by SpatryX on 2011-10-10
> **paulnewall said:**
> You may be able to use the latest c2esp20a with the espC310
[https://sourceforge.net/projects/cupsdriverkodak/files/](https://sourceforge.net/projects/cupsdriverkodak/files/)
but you have to compile and install it.

IT WORKS! But only in Black and White... This is fine for printing text documents though... I still have to use my aforementioned workaround to print pictures. At least this is a step in the right direction!

---

### Post by paulnewall on 2011-10-21
Now there is a new version of c2esp21~rc1 which includes colour, however I have 1 report of it not working. It would be good to have more reports.
 
Be prepared to go back to c2esp20a though!
 
If it does not work I'd appreciate a copy of the log file in /tmp emailed to [EMAIL="quandry@ntlworld.com"]quandry@ntlworld.com[/EMAIL]
 
Thanks

---

### Post by SpatryX on 2011-11-17
There is a new driver at

[http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)

And this one now prints in color! It works great on my system.
Using Pinguy OS 11.04 (Based on Natty)

Also a Video on installing and compiling the driver is on my Youtube Channel
[http://www.youtube.com/watch?v=wsBL6LbJvbQ](http://www.youtube.com/watch?v=wsBL6LbJvbQ)

---

### Post by gc23 on 2011-11-20
Just wanted to pop in here and say that I got the newest driver working on Linux Mint for my ESP C315.  Works nicely in color (from the test page it printed out).  I followed the directions in the INSTALL file and they worked fine.

---

### Post by MikeB23930 on 2011-11-27
:) Installed the c2esp22 from sourceforge as per the Install file Ubuntu notes.  Works great (at least printing the test page) using a Kodak esp 9 Aio wireless network printer with the Kodak 9200 driver chosen from the drop down list of Kodak printers.

Persistence and patience along with a healthy portion of steam-relieving cursing does work eventually.

Good Luck,

Mike

---

### Post by TroN-0074 on 2011-12-26
Just got the Kodak ESP-C130 as a Christmas present and went to download this driver and I got the wrong architecture error.
I am using Ubuntu 10.04 LTS, 64 bits. Any advices? I will highly appreciate it
Thank you!

---

### Post by paulnewall on 2012-01-02
You would need to download the source code and compile it yourself - instructions in the install file that downloads with the source code

---

### Post by workshoppete on 2012-01-02
As a newby to this distro i thought i would give it a try, however i am a bit disappointed, for instance ........

I thought this distro was supposed to be user friendly and easy to configure. Here we are have to compile complicated source code just to get a printer working on it (And a printer that has been selling in very large volumes over the last 3 - 4 years at that!). It hasn't given me much faith to try installing the rest of my equipment.

It would'nt shut itself off after completing installation, I had to shut it down manually.

It doesn't look as though it has any support for the N -Videa geforce 6200 drivers

Rant over ....day wasted....back to the drawing board.:(

---

### Post by Gannin on 2012-01-30
It's not the operating system's fault if a hardware manufacturer chooses not to support it.

So instead, some members of the community have stepped up and tried to create their own support for it.  Because it's a community-driven driver, and not provided, or helped by, the manufacturer, sometimes there are more hoops to jump through to get it working.

If you want to complain about such things, complain to Kodak instead.  Maybe that way they'll eventually create a Linux driver that can be included in the kernel.

---

### Post by guyrichie@hotmail.com on 2012-01-31
> **Gannin said:**
> It's not the operating system's fault if a hardware manufacturer chooses not to support it.

So instead, some members of the community have stepped up and tried to create their own support for it.  Because it's a community-driven driver, and not provided, or helped by, the manufacturer, sometimes there are more hoops to jump through to get it working.

If you want to complain about such things, complain to Kodak instead.  Maybe that way they'll eventually create a Linux driver that can be included in the kernel.

I have tried complaining to Kodak, however they said they were not interested and that the Linux market is too small for them to consider.  It's that kind of attitude and narrow mindness that makes a company bankrupt!  Oh Kodak is bankrupt ([http://www.guardian.co.uk/business/2012/jan/19/kodak-files-for-bankruptcy](http://www.guardian.co.uk/business/2012/jan/19/kodak-files-for-bankruptcy)).  Perhaps with their bailout money, their new business plan will include for the Linux community; because let’s face it although we all share freeware software we don't pour biro ink into our fully supported HP printer cartridges!

---

### Post by guyrichie@hotmail.com on 2012-02-09
> **workshoppete said:**
> As a newby to this distro i thought i would give it a try, however i am a bit disappointed, for instance ........

I thought this distro was supposed to be user friendly and easy to configure....

Hello All,

Please see attached a script that will install version 23 of Paul Newall's driver for this printer ([http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)).  On install of the driver, you will need to manually add the printer to the system.  This script offers a guide on doing this.

Once you download the script you must make it executable.  You can do this by right mouse clicking on the file and selecting 'Properties'.  Under the 'Permissions' tab tick the check box 'Allow executing file as program', then click the 'Close' button.  To run; simply double click on the script and click 'Run in Terminal' - you will be asked for your password.

I do recommend you read the script in a text editor (double click and click on 'Display').  Reading the script will give an insight into what is going on - and maybe let you can let me know if there are any mistakes!!

Many thanks,
Guy

---

### Post by Falwheel on 2012-02-15
Thanks Guy,

Followed the script that you wrote and it appears that laptop communicates with printer and I have managed to print several test page, however, unable to print photo.  The paper loads about 1/4 and message on printer shows printing, however, nothing else happens but printer spits out paper.

Any Idea what I may be doing wrong.

running laptop with Ubuntu Linux


John (Newbie)

---

### Post by guyrichie@hotmail.com on 2012-02-16
> **Falwheel said:**
> ...unable to print photo.  The paper loads about 1/4 and message on printer shows printing, however, nothing else happens but printer spits out paper....running laptop with Ubuntu Linux


Hello John,

I'm glad to hear the script has worked for you - well the test pages printed anyhow.  

I have had success in printing web pages, word processing documents, spreadsheets and desktop publishing.

 - I have just tried to print a photo on my printer (connected via USB cable) and it too failed.  The image was .jpeg, 2818 x 2122 and 2.5 MB in size.  

However, I then reduced the image to 800x600 pixels, the file size reduced to 95 KB by doing this.  This smaller size in terms of pixels and bytes printed correctly.  I used a program called "Phatch" to achieve this downscale, however there are many other methods to manipulate digital photos - see: [http://ubuntuforums.org/forumdisplay.php?f=16](http://ubuntuforums.org/forumdisplay.php?f=16).

As this driver is developed by the Linux community it will take a while to 'perfect' the working operation.  This driver is being developed here: [https://sourceforge.net/projects/cupsdriverkodak/](https://sourceforge.net/projects/cupsdriverkodak/).  Reading the support forum ([https://sourceforge.net/projects/cupsdriverkodak/forums/forum/1107085/topic/4596586](https://sourceforge.net/projects/cupsdriverkodak/forums/forum/1107085/topic/4596586)) more feedback is being requested by the developer to improve the driver.

It is unfortunate that Kodak will not release a certified driver, but in time the community will get there.

Many thanks,
Guy.

---

### Post by Falwheel on 2012-02-23
Okay Guy,

Yes I also have had success in printing web pages, word processing documents, spreadsheets and desktop publishing.

Thanks for all the info..I am now meddling with different ways to manipulate photo and hope to be able to print photo soon.

"
However, I then reduced the image to 800x600 pixels, the file size  reduced to 95 KB by doing this.  This smaller size in terms of pixels  and bytes printed correctly.  I used a program called "Phatch" to  achieve this downscale, however there are many other methods to  manipulate digital photos - see: [http://ubuntuforums.org/forumdisplay.php?f=16](http://ubuntuforums.org/forumdisplay.php?f=16)."

Thanks for your help and support..

John H

---

### Post by paulnewall on 2012-02-23
Re the problem printing high res photos.
Using my Hero 9.1 printer, I can print a 2000 x 3000 photo. It's very slow but it prints.
If you are having this problem which printer model do you have?
The ESP xxxx models use a different filter from the Hero, so that could perhaps explain why it works for me and not for you.

---

### Post by guyrichie@hotmail.com on 2012-03-05
> **guyrichie@hotmail.com said:**
> Hello All,

Please see attached a script that will install version 23 of Paul Newall's driver for this printer ([http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)).  On install of the driver, you will need to manually add the printer to the system.  This script offers a guide on doing this.

Once you download the script you must make it executable.  You can do this by right mouse clicking on the file and selecting 'Properties'.  Under the 'Permissions' tab tick the check box 'Allow executing file as program', then click the 'Close' button.  To run; simply double click on the script and click 'Run in Terminal' - you will be asked for your password.

I do recommend you read the script in a text editor (double click and click on 'Display').  Reading the script will give an insight into what is going on - and maybe you can let me know if there are any mistakes!!

Many thanks,
Guy

Hello All,

Please see attached a new script that will install driver version 24.  This script now includes an install log.  If upgrading from version 23 it would be best to delete the existing printer from you system first.

Thank's to the developers, this new driver appears to have solved the printing of large images.

Many thanks,
Guy

---

### Post by vancejo on 2012-03-05
> **guyrichie@hotmail.com said:**
> Hello All,

Please see attached a new script that will install driver version 24.  This script now includes an install log.  If upgrading from version 23 it would be best to delete the existing printer from you system first.

Thank's to the developers, this new driver appears to have solved the printing of large images.

Many thanks,
Guy

Worked great for me.  :D
Thanks Guy

---

### Post by Jimbo60 on 2012-04-11
Guy,
I used your script but ran into a problem. A bit of searching lead me to the missing package (libpng12-dev_1.2.46-3ubuntu1.2_i386.deb) which I downloaded and installed manually.
When I re-ran the script it went through without a problem and I am now successfully printing. Hurrah!
Thanks for all your work on this.  

This was the output from the failed attempt:

  	 	 	 	 	 	   Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 build-essential is already the newest version. 
 build-essential set to manually installed. 
 cups is already the newest version. 
 The following package was automatically installed and is no longer required: 
   sdparm 
 Use 'apt-get autoremove' to remove them. 
 The following extra packages will be installed: 
   comerr-dev krb5-multidev libgcrypt11-dev libgnutls-dev libgnutlsxx26 libgpg-error-dev 
   libgssrpc4 libjpeg62-dev libkadm5clnt-mit8 libkadm5srv-mit8 libkdb5-5 libkrb5-dev 
   libpng12-dev libtasn1-3-dev libtiff4-dev libtiffxx0c2 zlib1g-dev 
 Suggested packages: 
   gettext krb5-doc libgcrypt11-doc gnutls-doc gnutls-bin guile-gnutls krb5-user 
 The following NEW packages will be installed 
   checkinstall comerr-dev gxmessage krb5-multidev libcups2-dev libcupsdriver1-dev 
   libcupsimage2-dev libgcrypt11-dev libgnutls-dev libgnutlsxx26 libgpg-error-dev 
   libgssrpc4 libjpeg62-dev libkadm5clnt-mit8 libkadm5srv-mit8 libkdb5-5 libkrb5-dev 
   libpng12-dev libtasn1-3-dev libtiff4-dev libtiffxx0c2 wmctrl zlib1g-dev 
 0 upgraded, 23 newly installed, 0 to remove and 0 not upgraded. 
 Need to get 207 kB/2,914 kB of archives. 
 After this operation, 10.8 MB of additional disk space will be used. 
 Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates/main libpng12-dev i386 1.2.46-3ubuntu1.2 
   404  Not Found 
 Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/main libpng12-dev i386 1.2.46-3ubuntu1.2 
   404  Not Found [IP: 91.189.92.167 80] 
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.46-3ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.46-3ubuntu1.2_i386.deb)  404  Not Found [IP: 91.189.92.167 80] 
 E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? 
 Kodak-ESP-C310-Ubuntu-v24.sh: line 15: gxmessage: command not found 
  
PS: When the first attempt failed the terminal window automatically closed. It then took a noob like me a while (it wasn't that long really) to find out how to run the script from an already open window so I could see what was going on.

---

### Post by Gogeden on 2012-04-16
Just wanted to pop in after awhile and say thank you to those who have worked on a driver for this printer. You have NO idea how much I appreciate it. Now I can blow away Winblows HeXP and once again have freedom. Thanks comrades! :)


:lolflag:

---

### Post by Gogeden on 2012-04-16
By the way, I recommend sending the driver(s) to Torvalds so they can be included in the Linux kernel :) If you haven't done this yet anyway. :P

---

### Post by Gogeden on 2012-04-16
> **TroN-0074 said:**
> Just got the Kodak ESP-C130 as a Christmas present and went to download this driver and I got the wrong architecture error.
I am using Ubuntu 10.04 LTS, 64 bits. Any advices? I will highly appreciate it
Thank you!


You will have to compile and install the driver. Paul is correct. This will configure the install for your architecture.

---

### Post by Gogeden on 2012-04-16
> **guyrichie@hotmail.com said:**
> Hello All,

Please see attached a new script that will install driver version 24.  This script now includes an install log.  If upgrading from version 23 it would be best to delete the existing printer from you system first.

Thank's to the developers, this new driver appears to have solved the printing of large images.

Many thanks,
Guy

Hey! I ran your script and all is good. But when I was reading some of the prompts, I noticed a typo.

Here's the original section, it's on line 76:

```
 After a while a list of printers, divided by by their physical connection method will appear.
```

Here's my fix:

```
  After a while, a list of printers, divided by their physical connection method, will appear.
```


Cheers!

---

### Post by markwadams on 2012-05-18
Thanks all. Always impressed at open source community efforts and what great minds working in consort can accomplish.  Bought a refurbished 310C for half price, knowing that the folks here had reported they could get her working.  It did -- like a champ -- right out of the box.  Didn't even plug it into any computer.  Plugged it into the wall, downloaded the driver from sourceforge and the script guyrichie posted, made it executable and VIOLA!

I'm proficient in android but a linux n00b ... and an old hand a Macs who's most likely never going back now that I'm getting the hang of the open source world.

Thanks so much everyone, for all your time and efforts. :)  You seriously rock!
:guitar:

---

### Post by Ycanti on 2012-05-28
After downloading these drivers that will make my printer work do i just leave them on my desktop or do i go inside them and cut and paste code into a terminal window then press return after entering my password?

Things seem to work very differently in linux. Will receive kodak 310 printer tomorrow i wonder if i should take it back to the shop or return to win7 completely? I could cancel order am very worried that i will lose another weekend trying to make something work

#


> **guyrichie@hotmail.com said:**
> Hello John,

I'm glad to hear the script has worked for you - well the test pages printed anyhow.  

I have had success in printing web pages, word processing documents, spreadsheets and desktop publishing.

 - I have just tried to print a photo on my printer (connected via USB cable) and it too failed.  The image was .jpeg, 2818 x 2122 and 2.5 MB in size.  

However, I then reduced the image to 800x600 pixels, the file size reduced to 95 KB by doing this.  This smaller size in terms of pixels and bytes printed correctly.  I used a program called "Phatch" to achieve this downscale, however there are many other methods to manipulate digital photos - see: [http://ubuntuforums.org/forumdisplay.php?f=16](http://ubuntuforums.org/forumdisplay.php?f=16).

As this driver is developed by the Linux community it will take a while to 'perfect' the working operation.  This driver is being developed here: [https://sourceforge.net/projects/cupsdriverkodak/](https://sourceforge.net/projects/cupsdriverkodak/).  Reading the support forum ([https://sourceforge.net/projects/cupsdriverkodak/forums/forum/1107085/topic/4596586](https://sourceforge.net/projects/cupsdriverkodak/forums/forum/1107085/topic/4596586)) more feedback is being requested by the developer to improve the driver.

It is unfortunate that Kodak will not release a certified driver, but in time the community will get there.

Many thanks,
Guy.

---

### Post by Ycanti on 2012-05-28
I downloaded same. how did you make it executable? Like to do same so when my kodak i ordered arrives can get it working without a lost weekend. you have to make it executable when it is plugged in or can you do so before? sorry for being a dummy.

> **markwadams said:**
> Thanks all. Always impressed at open source community efforts and what great minds working in consort can accomplish.  Bought a refurbished 310C for half price, knowing that the folks here had reported they could get her working.  It did -- like a champ -- right out of the box.  Didn't even plug it into any computer.  Plugged it into the wall, downloaded the driver from sourceforge and the script guyrichie posted, made it executable and VIOLA!

I'm proficient in android but a linux n00b ... and an old hand a Macs who's most likely never going back now that I'm getting the hang of the open source world.

Thanks so much everyone, for all your time and efforts. :)  You seriously rock!
:guitar:

---

### Post by Ycanti on 2012-05-29
After the downloads you geniuses created it all works really well on my dual boot ubuntu/Win7 systems. Many thanks and sorry for being a dummy.

---

### Post by edcompsci on 2012-07-31
[http://ubuntuforums.org/showthread.php?t=2026500&highlight=kodak+esp+c310](http://ubuntuforums.org/showthread.php?t=2026500&highlight=kodak+esp+c310)

---

### Post by paulnewall on 2012-08-01
ycanti - did you get scanning working as well as printing?

---

