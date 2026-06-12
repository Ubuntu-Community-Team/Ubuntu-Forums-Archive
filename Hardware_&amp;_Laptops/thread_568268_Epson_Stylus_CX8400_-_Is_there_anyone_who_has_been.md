---
title: "Epson Stylus CX8400 - Is there anyone who has been successful?"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by Quid on 2007-10-05
Hello Ubuntu Community!

The Stylus CX8400  is a newer Epson Printer.

Before buying, I researched enough to know I may need to do some work, but it looked:confused: good in the forums I reviewed.

 I am getting to the point where it is going to be an XP printer ( spit).

I tried various drivers from the Epson site and advice from the openprint database - eg use Gutenprint v5.1.3 and CX3410 driver etc etc... 

There seems to be disagreement - every time I see a "Success" banner - another user gives the reasons it doesn't work. Unfortunately I read the success before buying!

I did try to compile the gutenprint...But I think I am not nearly competent enough without having my hand held all the way through - 

I have a 64bit Ubuntu and simply wonder -

Has anyone successfully managed to print colour with this device under Feisty 64bit?

Thanks !

---

### Post by pjcarr42 on 2007-10-05
I too am having some issues with this printer. Gnome seemed to recognize it and install drivers, but when I do try to print out a document the printer just spits out some paper. I have become used to things working with ease the last year or two so I did not expect to have such problems with a printer from a major company...so if anyone has any ideas please let us know.....
paul

---

### Post by Quid on 2007-10-11
Sooo.... what steps did you take to make it work.. or is it hooked to a Windows machine?

CUPS version? Driver? 

Any help is greatly appreciated - IF you were successful!

---

### Post by Quid on 2007-10-18
Anyone got one working in Gutsy?

---

### Post by AmonSacha on 2007-10-19
I am having the same problem, I have CUPS and gutenprint v5.0.1 (both are the default ubuntu packages/drivers) All my printer does is print blank pages until I reset it. The impression I am getting is that I need to compile the development version. I have no idea how to compile and install a driver. At all. 

So I guess this is an elaborate bump.

---

### Post by Quid on 2007-11-01
Perhaps with Gutsy out there someone has had the time or the inclination to try it out...

Anyone complie the later CUPS? and a driver for this unit? 

Even negatives are welcome.

Thanks

---

### Post by pjcarr42 on 2007-11-07
The upgrade to Gibbon did me no good...still just spits out paper...but it is recognized in the printer preferences...I guess I could learn to compile a newer version of gutenprint or something along those lines, but jeez  as if I have that time laying around??? I am sure this is a fairly popular model that should work. Any luck anybody???

---

### Post by copycat on 2007-11-10
same here... pls assist

---

### Post by eliasz on 2007-11-14
Hi guys. I recently bought this printer(yesterday) after going to the store and looking up on linuxprinting.org all the printers they had. This looked like the best deal, and it said it worked. Now i get the same thing, just spits out blank pages. 

I was wondering if anyone else has ever gotten this(or a similar model) to work in another distro? Maybe thru cups? I will keep trying and let you guys know.

---

### Post by Kevin Funnell on 2007-11-14
I am currentl evaluating Gusty Gibbon 7.10, I have an Epson Stylus 200 Color printer (it reflection of my age)  Anyway under 7.10 I get a negativeprin-ot,  plenty of black and little readable text.  Printer worked perfectly under CUPS & Feist Fawn 7..04.  Maybe one day Ubuntu will sort ou these problems before releasing a new version, we want people to enjoy using Ubuntu nand not have the tearing their hair out over what should be a simple task in setting up a printer.

Old kevin

---

### Post by eliasz on 2007-11-14
So today i tried to install the driver from the gutenprint site. I removed the package from apt-get and compiled both 5.1.3 and 5.0.1 and both made it even worse. Well it simply did not respond to sending a test page.

I uninstalled the drivers and tried to get a CVS check out, but there was no configure or Make file, so i don't know how to install it.

Anyway, Has anyone had this model working? In any distro?

---

### Post by ezeze5000 on 2007-11-14
I have an Epson Stylus CX5000 that works with Ubuntu-7.10-Desktop.
I had to edit some config files to get the scanner to work.
Your trouble may be a 64bit problem?
Do a forum search on the Epson 4000 through 8000 printers, there may be some help there.
I hope this helps.

---

### Post by Tanker Bob on 2007-11-14
Try installing the sane-extras package to get the scanner to work That worked for my CX7800. As for the printer, try to install directly from the CUPS server at [http://localhost:631/](http://localhost:631/). Some printers that didn't make the ubuntu scripts are available through the server itself. I checked and the CX8400 is available directly through CUPS in gutsy.

---

### Post by signifer123 on 2007-11-15
Alright, to print use the CX5800 drivers, it worked under version 5.1.3 of the drivers.
Then used iscan, as the scanner and it worked.
[http://lx1.avasys.jp/iscan/2.10.0/iscan-2.10.0-1.c2.i386.rpm](http://lx1.avasys.jp/iscan/2.10.0/iscan-2.10.0-1.c2.i386.rpm)

---

### Post by Quid on 2007-11-17
Signifer123
This is great - help me out here. It looks like you may be using CUPS?

I believe the RPM you link to is just the driver you indicate -

Any special steps you performed?  What version of Ubuntu, 64?

Thanks so much. You will be helping many of us out!

Quid

---

### Post by ewr2san on 2007-11-17
I have it mostly working if all you care about is Black and White printing.
Im running stock Kubuntu Gutsy.

I used the CX4700 Foomatic/gutenprint-ijs.5.0

It prints color, but it's way off in correct color and scaling a bit I think.
From what Ive been able to find it seems like this printer is better behaved under gutenprint 5.1 but Installing/compiling that doesn't seem to go well (breaks KDE printer wizard).

If anyone gets a later version of gutenprint that is .deb and works that would be great.

---

### Post by ewr2san on 2007-11-17
I also alien'd the iscan rpm that Signifier mentioned.  It installs but doesnt find the scanner.  I also tried the "Quite Insane" plugin for gimp, no luck there.

---

### Post by Tanker Bob on 2007-11-17
Folks, forget the old drivers. Just follow the direction in post #14 above and both your scanner and print functions will be fully operational. You don't need iscan either. The proper scanner driver is in the sane-extras package.

---

### Post by ewr2san on 2007-11-17
TankerBob,

Cups gets me closer :).

If I use the Epson Stylus CX8400 Foomatic/gutenprint-ijs-simplified.5.0 driver I get the old behaviour of just ejecting blank pages.

However if I point the PPD to /usr/share/cups/model/eklite.ppd I get it printing color correctly but it prints as if it were A4 paper rather than letter....

SO What I think We need is a eklite.ppd which is for Letter.  Im hacking on one based on the example for Laserjet..

[http://www.cups.org/book/examples/chap17/laserjet.ppd](http://www.cups.org/book/examples/chap17/laserjet.ppd)

Ill let you know shortly if it works.


As for scanning, Ive got:
# dpkg -l |grep sane

ii  gimp2.0-quiteinsane    0.3-8     A Qt based SANE plugin for GIMP 2.0
ii  libsane                      1.0.19~cvs20070505-3ubuntu2        API library for scanners
ii  sane                         1.0.14-2                           scanner graphical frontends
ii  sane-utils                  1.0.19~cvs20070505-3ubuntu2

---

### Post by ewr2san on 2007-11-17
Well, when I add the entries to eklite.ppd for letter size paper, CUPS takes them and adds a printer with no errors,  However when I print a test page it fails.

If I just change the dimensions of the entries for A4 it stretches things and isnt quite right either.  Close... The colors are right with eklite.ppd

After 12 printed test pages, Im done wasting ink for the day....  If anyone has a eklite.ppd with Letter entries please let me know..

As for sane-extras I see a lib-sane-extras but not a sane-extras?

---

### Post by Tanker Bob on 2007-11-17
libsane-extras should be right package. That's odd about the 8400 driver.

---

### Post by weston on 2007-11-17
I've got no good news for you.  I tried the same thing: editing the ppd to add Letter sized paper based on another ppd. The job stops and in the log I get this in the error log:

[FONT="Courier New"]E [18/Nov/2007:03:06:17 +0000] PID 9779 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [18/Nov/2007:03:06:19 +0000] [Job 62] Job stopped due to filter errors.[/FONT]

If anyone has any idea what causes this, I'd love to hear it.

Thanks.

---

### Post by weston on 2007-11-17
So I got it working... not EXACTLY sure how.

I believe the key is to run the pipslite-install and let it make you a ppd.

I think went into the cups web admin and there was a new printer, Stylus_CX8400  using the "Photo Image Print System Lite".

Modifying the options it has a large list of paper sizes and print qualities that were not in the original ppd I had attempted to use before running pipslite-install.

So... it is possible. I'll give any other help you want.

I've attached the ppd that I found it to be using.. hopefully it will help.
Remove the .txt extension (added so that I could upload it here) and then select it as the ppd in CUPS.
Let me know if it works. It works for me.

---

### Post by froy02 on 2007-11-18
The US has very poor support for linux on printers.  However Europe and Asia have good support. I think your printer is so new that there's no linux driver yet for it but there is one for cx8300 from a UK website:

[http://esupport.epson-europe.com/SupportHome.aspx?lng=en-GB&data=0ccCGROWIYM58zV3pqc84YT0DcLI1RrpNUFXBv299cYU003D](http://esupport.epson-europe.com/SupportHome.aspx?lng=en-GB&data=0ccCGROWIYM58zV3pqc84YT0DcLI1RrpNUFXBv299cYU003D)

---

### Post by ewr2san on 2007-11-18
Westons solution works beautifully. Perfect printing.  Verified correct printing of color, printing of test page, printing from Firefox, Photos in Gwenview, and from OpenOffice.

So a Summary for those out there trying to get this to work (should work on other distro's that use cups:

1. Download the Stylus_CX8400.ppd.txt file in Weston's posting.
2. Copy the file to /usr/share/cups/model and rename it to Stylus_CX8400.ppd,  Permisssions should be root.root, rw,r,r
3. Use Firefox to browse to [http://localhost:631](http://localhost:631) (this is the splendid CUPS interface).
4. Add Printer, select the USB CX8400, When selecting the printer driver select "Stylus_CX8400 using the "Photo Image Print System Lite" which was added by putting the file in /usr/share/cups/model.

Viola! Printing!  Thanks Weston, Tanker Bob, and Quid!

---

### Post by ewr2san on 2007-11-18
Now on to scanning..

I installed libsane-extra's.
Sane-find-scanner see's the scanner.
Scanimage-L didnt until I edited /etc/sane.d/epkowa.conf
I added:
usb 0x04b8 0x0839

and commented out:
SCSI EPSON

Now I get:
root@desktop:/etc/sane.d# scanimage -L
device `epkowa:libusb:005:002' is a Epson CX8400 flatbed scanner

scanimage -x 100 -y 100 --format=tiff >image.tiff
Works!  B/W scan!

scanimage -x 100 -y 100 --format=tiff --mode=color >imagec.tiff
Works! Color scan!


But I still cant see the scanner in "quite Insane (GIMP)" or Kooka.

---

### Post by Quid on 2007-11-18
Thanks to All who are helping out...

Tanker Bob - your 4 step instructions seem quite straight forward ( maybe I needed to do a step previous?)

I loaded the ppd from Weston - renamed, and checked the permissions, installed with cups. ( Mind you it found the printer and actually installed one before I finished in cups - good old Gutsy ) but I went through the steps and created a second - and they were actually identical .

When I try and print a test page - I get this error in the cups browser:
"/usr/lib/cups/filter/rastertopips failed"

soooo I must be doing something wrong. The printer does not wake up - so it's not gettting to a "send" state. 

dmesg is not helpful ( although it sees my printer when I plug it in).

I hope it is a simple problem. It's been many years since I played with BSD and I was challenged even moving and renaming the files - the clouds of memory slowly parted and I wished I had my printed MAN files :) ..

I await wisdom... 

?? Missing a library?? Download something from CUPs website first??
.

---

### Post by ewr2san on 2007-11-18
Quid,

Try installing pipslite-cups-1.0.1-1.i386.rpm (I alien'd it into a .deb and it worked fine for me).  Perhaps that's the missing thing that was installed in a previous step.

IF that doesnt work, in cups it gives an option to specify the path to the PPD.  Try explicitly telling it the path to /usr/share/cups/model/Stylus_CX8400.ppd

Earlier in testing I got the same rasteriops message when I had a bad .ppd file.. I was trying to convert the A4 PPD to Letter.

---

### Post by ewr2san on 2007-11-18
BTW:  Ive got scanning working when I run as root...

libsane-extras definatley was needed to get it working.  

I installed xsane, and it doesnt see the scanner as my user, but happily sees it and scans running as root.  Im in the group scanner, so it's not the obvious...

Time to sift through the boards and see what needs to be done to get it to run as non-root.

---

### Post by ewr2san on 2007-11-18
OK! Got Scanning working not as root.

1. Make sure that scanning users are added to group scanner
2. Edit  /etc/sane.d/epkowa.conf
add:
usb 0x04b8 0x0839

and commented out:
SCSI EPSON

3. Edit /etc/udev/rules.d/45-libsane.rules
Add:
# Epson CX-8400
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0839", MODE="664", GROUP="scanner"

Reboot and all is well.. Kooka, xsane, and everything else works swimmingly.

---

### Post by Quid on 2007-11-18
Thanks for the tips  - it's late and I am out of town this week - but it all sounds promising!

Will report back frustration or success!

---

### Post by Quid on 2007-11-22
Did anyone do this using 64bit ??

In reading more on Pipslite - there seems to be some concern about this...

[http://www.uluga.ubuntuforums.org/showthread.php?t=576594](http://www.uluga.ubuntuforums.org/showthread.php?t=576594)

am I just being parnoid?

---

### Post by Tanker Bob on 2007-11-22
I don't know about this specific issue, but 64-bit support frays a bit at the margins. That's the only reason I switched back to 32-bit for Gutsy. 64-bit is great in the middle of the road, but there are potholes as you get away from the common, mainstream apps and hardware drivers.

---

### Post by eliasz on 2007-11-24
I am running 64-bit 7.10, and i am able to print using the cx5800 driver installing through CUPS manager on localhost:631
I tried the other methods on here and none of them worked. I am assuming this is because of a 64 bit issue.
When i installed gutenprint 5.1.3 it just made it worse. The printer did not respond at all using that driver.

Anyway, on 64bit using the cx5800 driver i had no problems printing. I was able to scan after folloing the above instructions. Everything works great now. Thanks very much everyone :D

---

### Post by Quid on 2007-11-25
After much work I'd like to report on my progress.

The  pipslight build failed ( as I and **Tanker Bob** somewhat anticipated) as I have the 64 bit 7.10 installed.

I found this instruction from** cotcot**
[http://ubuntuforums.org/showthread.php?t=576594](http://ubuntuforums.org/showthread.php?t=576594)

It gives step by step... how to build and install gutenprint in 64bit 7.10 ( good for we slower types)


Install gutenprint version 5.1.3

> 
```
sudo apt-get -i build-essential libcupsimage2-dev doxygen docbook-utils
cd gutenprint-5.1.3
./configure
make clean
make
sudo make install
sudo mkdir /usr/share/cups/model/gutenprint/5.1
sudo cups-genppd.5.1
```

This did take a bit of time and I had tried this path before with Fiesty.

I was successful in the build and install but as before - on installing in cups - it spit out many pages of incomprehensible noise.

I then tried the CX5800 driver in Gutenprint as others suggested  and the test page printed!! But the colour was all off - as was the greyramp.

I changed the color model to "KCMY" and the color precision to  "Best" and Voila! a pretty close rendition on the Google Logo ( my test gif):KS

In comparing it to the XP driver - the Blue is a bit more purple and the red a bit more orange in hue. 
It also is dumping ink - so much so that the color and black is much more dense under cups and bleeds thorough the page. Not very economical.:confused:

I did a compare on the gutenprint CX8400 and CX5800 pdd and found very few differences - some in resolution and in stepping in parameters. There does not seem to be any hidden coding differences- except to "name" the driver... is there really another driver referenced here or is that strictly a convention? If not, a wise and knowledgeable in the way s of cups person might be able to help me tune the ppd to the device. see below for the diff...

I am happy I can print... but I think I have a few steps yet - including scan testing and maybe samba configuration.
:confused:
**eliasz** - where did you get your CX5800 driver if you are not using gutenprint? I will do a test to see if it is similar to the gutenprint. Perhaps that will staunch the flow of ink!

Thanks gang!
Quid est

Diff from Kompare attached (note is is really the 5800 - the 5400 lable is a typo)

---

### Post by ninja1 on 2007-11-27
Anyone got this working yet? I followed the instructions and couldn't get it to work.

---

### Post by mjpoetic on 2007-11-27
Thanks to this thread for help with getting the CX8400 up and running on my system.  Ubuntuforums is still a priceless resource to the linux community

---

### Post by ewr2san on 2007-11-28
Ninja1, have you installed pipslight?

---

### Post by eliasz on 2007-11-29
Hi guys. SO i was happy for a few days. Now my printer has once again stopped working. Very odd. 
Now when i send something to print, nothing happens. It just says that the job is stopped. Its very frustrating as it worked perfect for a few days. I have tried to remove and reinstall the driver to no avail. 

Now when i bring up the document print status and try to cancel the stopped job i get "There was an error during the CUPS operation "cleint-error-no-possible""....i'm rather confused what that even means as it comes up in a error box ;)

But anyway, as to your questions i simply went through localhost:631 and went to add printer. Then i chose the Epson cx8400 USB#1 printer, and then used went down the list and chose the Epson CX5800 CPUS/Gutenprint driver

it worked fine for a few days... and then just randomly stopped(on a side not the same day my emulation of utorrent stopped working as well, the tray icon just becomes a copy of the last tray icon to load, and it will not come up..) Possibly a upgrade of a lib?

I was also wondering. I tried to install the gutenprint drivers from source, i installed 5.1.3 but it does not work either. I tried to run make uninstall, but the drivers as still in the list. Any advice on how to remove them/try again?

---

### Post by eliasz on 2007-11-29
OK, so i tried to install it once again and now in CUPS manager when i have the printer selected, or try to print a test page, at the top of the page appears a message

""/usr/lib/cups/filter/rastertogutenprint.5.0 failed""

Im not sure what this is. The file is there. Im not sure if it got corrupt or something...
Does anyone know what package i would need to reinstall to get this reinstalled?

---

### Post by leeper69 on 2007-12-02
Hi ewr2san I am using Mepis ver6.0 which is based on Ubuntu. I edited the files in your post and I now have the device in Gimp and Kooka but cant use eather of them. the only step of your post I havent done is to add the users to the group scanner file because I dont know where the file is. pleas tell me where you found the file. 
     
Thanks! ps the Ubuntu forem has ben a lot of help to me in getting this device to work.

---

### Post by coladons on 2007-12-02
I still do not have printing working but thanks to ewr2san's #31 thread, I have scanning working.

When I try to add the printer directly in cups via [http://localhost/631](http://localhost/631), it allows me to add all the necessary information but at the end, it prompts me for a CUPS username/password.  I have supplied the username/password that I used when installing Ubuntu 6.06 LTS (I have subsequently patched everthing to the latest) but it fails and the printer never gets registered.  Can anybody help here?  I have even invoked Firefox with sudo and that does not help either.

Thanks.

Steve

---

### Post by Tanker Bob on 2007-12-02
It should be your root/sudo password.

---

### Post by eliasz on 2007-12-02
Hi Steve.

On my machine i use my regular user nameand password.
I have also set a root password on my machine using the command

sudo passwd

once you set a root password then you can use the username root, and the password you set in cups.

Hope that helps.

-EL

---

### Post by bean77 on 2007-12-03
Anyone have any luck with using this with SANE?

---

### Post by eliasz on 2007-12-03
> **bean77 said:**
> Anyone have any luck with using this with SANE?

You should read the previous posts....
its all there...
it works.

you need sane-extras...

---

### Post by bean77 on 2007-12-03
I will try that-thank you.

---

### Post by coladons on 2007-12-03
Thanks eliasz and Tanker Bob for the hints on the cups username/password.  I actually used a fix by llamakc where you add the cupsys user to the shadow group and then your username/password works.

Howerver, I still cannot print from the Expson Stylus CX8400.  I have downloaded the ppd file by Weston and when I use that, the printer just sits there and the status of the job is "stopped".  When I use the gutenprint 5.0 driver that comes with Ubuntu, the printer spits out pages.  Does anybody have any other clues to get this solved?

Thanks.

Steve

---

### Post by ewr2san on 2007-12-04
leeper,

There are two ways to add users to groups.

You can what groups a user is in by typing:

# groups ewr2san
ewr2san: ewr2san adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev


you can directly edit the /etc/groups file as root,

or 

use the systems settings/ user management gui tool in your distribution.


> **leeper69 said:**
> Hi ewr2san I am using Mepis ver6.0 which is based on Ubuntu. I edited the files in your post and I now have the device in Gimp and Kooka but cant use eather of them. the only step of your post I havent done is to add the users to the group scanner file because I dont know where the file is. pleas tell me where you found the file. 
     
Thanks! ps the Ubuntu forem has ben a lot of help to me in getting this device to work.

---

### Post by ewr2san on 2007-12-04
I think the missing piece is pipslite-cups-1.0.1-1.i386.rpm 

I downloaded it, ran alien on it to convert it to a .deb package and installed it. It installs it's own ppd for the printer so you may need to re-install weston's ppd over it.

Im still printing with that solution and it's working very well.  Ive compared the results to printing from windows and it's very good.


> **coladons said:**
> Thanks eliasz and Tanker Bob for the hints on the cups username/password.  I actually used a fix by llamakc where you add the cupsys user to the shadow group and then your username/password works.

Howerver, I still cannot print from the Expson Stylus CX8400.  I have downloaded the ppd file by Weston and when I use that, the printer just sits there and the status of the job is "stopped".  When I use the gutenprint 5.0 driver that comes with Ubuntu, the printer spits out pages.  Does anybody have any other clues to get this solved?

Thanks.

Steve

---

### Post by coladons on 2007-12-05
ewr2san,

Thanks for hanging in there with me.  I did download the rpm and convert it to a deb file.  I then ran the setup and all was well.  When I tried to run the install, I get a library error.  It is looking for libgtk-1.2.so.0 and I have libgtk-2.0.  Also, I don't see a libgtk-2.0.so.0 but do see libgtk-x11-2.0.so.0 and libgtkhtml-2.0.so.0.  So now I am not sure how to proceed.  I was thinking of creating a soft link but the equivalent file does not seem to be there.

Steve

---

### Post by coladons on 2007-12-05
Additional Info:

I have tried the 5800 and 7800 drivers.  They seem to print black and white ok (did not test extensively) but do not print color.  This is the same as findings in previous threads.  I also tried the 8300 driver but it behaves the same as the 8400 and just spits out paper.

Does anyone have a functioning ppd driver for the CX8400 that they could share?  Other threads indicated that the Weston ppd file works but I have not had any success with it?

Thanks.

Steve

---

### Post by Quid on 2007-12-06
See my post #36 earlier... here is a snippit...

> I was successful in the build and install but as before - on installing in cups - it spit out many pages of incomprehensible noise.

I then tried the CX5800 driver in Gutenprint as others suggested and the test page printed!! But the colour was all off - as was the greyramp.

I changed the color model to "KCMY" and the color precision to "Best" and Voila! a pretty close rendition on the Google Logo ( my test gif)

Maybe give this a try?

---

### Post by coladons on 2007-12-07
Quid,

Thanks for the referral back to your previous thread.  I set up the printer options per your suggestions and I at least can print text and some graphics fairly well.  I have a lot of scanned images I do from watercolor and these are not printing the correct color.  For now, I can deal with that as I am more concerned with scanning the paintings and that works.  I will test regular printing the next few days and if anything major comes up, I will post here.

Again, thanks.  And if anyone comes up with a solution for the CX8400 please let us know.

Steve

---

### Post by ewr2san on 2007-12-07
Here are the GTK packages that I have installed:
ewr2san@desktop:~$ dpkg -l |grep gtk
gtk-qt-engine                              1:0.8~svn-rev36-2ubuntu2           theme engine using Qt for GTK+ 2.x

libgtk1.2                                  1.2.10-18                          The GIMP Toolkit set of widgets for X

libgtk1.2-common                           1.2.10-18                          Common files for the GTK+ library

libgtk1.2-dev                              1.2.10-18                          Development files for the GIMP Toolkit

libgtk2.0-0                                2.12.0-1ubuntu3                    The GTK+ graphical user interface library

libgtk2.0-common                           2.12.0-1ubuntu3                    Common files for the GTK+ graphical user int

libgtkmm-2.4-1c2a                          1:2.12.0-0ubuntu1                  C++ wrappers for GTK+ 2.4 (shared libraries)

libwxgtk2.6-0                              2.6.3.2.1.5ubuntu12                wxWidgets Cross-platform C++ GUI toolkit (GT




> **coladons said:**
> ewr2san,

Thanks for hanging in there with me.  I did download the rpm and convert it to a deb file.  I then ran the setup and all was well.  When I tried to run the install, I get a library error.  It is looking for libgtk-1.2.so.0 and I have libgtk-2.0.  Also, I don't see a libgtk-2.0.so.0 but do see libgtk-x11-2.0.so.0 and libgtkhtml-2.0.so.0.  So now I am not sure how to proceed.  I was thinking of creating a soft link but the equivalent file does not seem to be there.

Steve

---

### Post by leeper69 on 2007-12-08
Thanks ewr2san for your help the scanner part of my CX8400 is now working perfectly!
and another question about getting the cups server to work with my password and user name may have ben answerd in another post I read tonight. your help in getting this device to work has ben fantastic I have the CX8400 working mostly in 3 out of 4 systems. I am going to miss being able to count on the Ubuntu forum for help when the next version of Mepis comes out due to a change back to the Debian core. guss I will just get a copy of Ubuntus latest release and put it on my system too. I am currently running Ubuntu Dapper,Mepis 6.0, Debian, and Windows 2000 on my system.

---

### Post by coladons on 2007-12-09
> **ewr2san said:**
> Here are the GTK packages that I have installed:
<snip>

ewr2san,

Thanks.  Downloaded the GTK 1.2 libraries and installed them.  When I ran the pipslite install utility, it created a ppd file called Epson_Stylus_CX8400.ppd in /etc/cups/ppd and also one called ekscx8400.ppd in /usr/share/cups/model.  Also the pipslite setup was located in /usr/share/pipslite and the pipslite-install was located in /usr/bin.  There was no mention of  EPAva as mentioned in the thread by yahooadm.

Anyway, the printer is now printing correctly both text and graphics (the color is correct).  Howerver, can't get it to work out of GIMP and it will not print on 4x6 paper correctly using Image Viewer (the image is correct but very small, about 2x3-1/8.  That's really two problems... 1) can't print from GIMP 2) can't print on 4x6 paper correctly.

Anyone have any solutions for GIMP printing.  I am more interested in this than the 4x6 issue as I think I could resolve that in GIMP and not worry about the other image utilities.

Steve

---

### Post by cp1969 on 2007-12-09
Well, this is not good news as I just bought a CX8400.  I currently have someone else's CX5000 hooked up to the computer and I didn't have to do a single thing to install it--ubuntu did everything it needed by itself.

Stupid me--I thought the CX8400 would be the same way.

In reading these posts, most of it could be written in hieroglyphics and I would understand it just about as well.  Pipslite...Gimp...cups... none of this has any meaning to me.  I hoped it wouldn't come to this, but I'm afraid I'm going to have to install it under XP and then reboot to XP anytime I want to print.

That's going to take a lot of the fun out of having ubuntu.

---

### Post by cp1969 on 2007-12-09
I installed the CX8400  on XP.  FWIW, the print function seems OK but the scanner is not 100% reliable.  In trying to scan three documents, it failed three times, saying it couldn't communicate with the computer, check cable, etc.  I did nothing other than shut if off and try again and eventually it works.  So, in six tries, I managed to scan three documents.

---

### Post by ewr2san on 2007-12-10
Yea, For someone completeley newb to linux, getting the CX8400 to work inst an easy thing. 

I was about to re-write up a step by step process, but Im still trying to solve the 64-bit issue without the Gutenprint method.  Ive compared gutenprint to the results that I have gotten with pipslite +the custom ppd, vs. XP, and I much prefer the color accuracy of pipslite.

IN short, it's download pipslite, alien it. install the pipslite.deb, copy in the .ppd, and configure it in cups.  I need to go through it again on a virgin machine, take screen shots, and post it.

---

### Post by froy02 on 2007-12-11
If you're using am64 you may have to install the library "ia32-libs" for 64 to 386 compatibility for some drivers.  

That's what i did on my 64 bit installation.

I use a Brother mfc665 and they only have 386 deb drivers so i had to install "dpkg -- force architecture" option when i installed the lpr and cups drivers.

hope it works.

---

### Post by coladons on 2007-12-11
Does anyone know if the recently released Gutenprint-5.1.4 drivers address the problems we have found with the Epson CX8400 printer?  Now that I have a "mostly" functioning CX8400, I'm not going to mess with it for a while.

Steve

---

### Post by cp1969 on 2007-12-11
> **ewr2san said:**
> Yea, For someone completeley newb to linux, getting the CX8400 to work inst an easy thing. 

I was about to re-write up a step by step process, but Im still trying to solve the 64-bit issue without the Gutenprint method.  Ive compared gutenprint to the results that I have gotten with pipslite +the custom ppd, vs. XP, and I much prefer the color accuracy of pipslite.

IN short, it's download pipslite, alien it. install the pipslite.deb, copy in the .ppd, and configure it in cups.  I need to go through it again on a virgin machine, take screen shots, and post it.

If you would do that, I'd be very grateful and I'm sure others will be as well.

Will that make it work as a scanner, too?

---

### Post by cp1969 on 2007-12-11
Well, got around to trying it using ubuntu (7.1).

When I looked in the printers section of System, it's there.  In the make & model line of the printer configuration window, it says:

Epson Stylus CX8400 - CUPS+Gutenprint v5.0.1 Simplified

However, when I ask it to print a test page, all it does is feed paper until the tray is empty.  The only way I could get it to stop was to turn the printer off.

When I hit the 'Print Self-Test Page', it does nothing at all.

If I hit the 'change' button beside the description line, it goes to a server and finds drivers.  If I select Epson, it gives me the choice of two drivers for the CX8400, one of which is the one listed above; the other is the same thing without the word 'recommended' by it.

I guess at this point I don't even have a question to ask.  I'll have to wait for explicit instructions from ewr2san.

---

### Post by nhammer1970 on 2007-12-11
I have had the same issue for months.  I have been trying to install a Stylus CX8400 with a Netgear Print Server model WGPS606.  I have had success installing other printers in a similar fashion.  I have also attempted to install the CX8400 locally, but with the same result.  Continuous Blank Pages are spitting out forcing me to shutdown the printer.

Anyone?

---

### Post by cp1969 on 2007-12-11
> **ewr2san said:**
> Westons solution works beautifully. Perfect printing.  Verified correct printing of color, printing of test page, printing from Firefox, Photos in Gwenview, and from OpenOffice.

So a Summary for those out there trying to get this to work (should work on other distro's that use cups:

1. Download the Stylus_CX8400.ppd.txt file in Weston's posting.
2. Copy the file to /usr/share/cups/model and rename it to Stylus_CX8400.ppd,  Permisssions should be root.root, rw,r,r
3. Use Firefox to browse to [http://localhost:631](http://localhost:631) (this is the splendid CUPS interface).
4. Add Printer, select the USB CX8400, When selecting the printer driver select "Stylus_CX8400 using the "Photo Image Print System Lite" which was added by putting the file in /usr/share/cups/model.

Viola! Printing!  Thanks Weston, Tanker Bob, and Quid!

I feel like I'm having a conversation with myself.

When I try to do step 2, ubuntu tells me I do not have permission to copy to that folder.  WTF.  I feel like I am on my IT-administered machine at work.  I gather that the permissions described in step 2 are essential, but how do I change them?

---

### Post by ewr2san on 2007-12-12
Step 2 must be done as root so you would sudo to do the copy and permisions change.  Weve also found that you need to install pipslite before you copy the files in.  Problem there is that pipslite only comes in a rpm, and to install that you need to convert the .rpm to a .deb using alien.(and pipslite is 32-bit only).

so install alien (again as root).
google for pipslite-cups-1.0.1-1.i386.rpm and download it.
run alien on that rpm and it'll make a pipslite-cups-1.0.1-1.i386.deb
install pipslite-cups-1.0.1-1.i386.deb


> **cp1969 said:**
> I feel like I'm having a conversation with myself.

When I try to do step 2, ubuntu tells me I do not have permission to copy to that folder.  WTF.  I feel like I am on my IT-administered machine at work.  I gather that the permissions described in step 2 are essential, but how do I change them?

---

### Post by cp1969 on 2007-12-12
> **ewr2san said:**
> Step 2 must be done as root so you would sudo to do the copy and permisions change.  Weve also found that you need to install pipslite before you copy the files in.  Problem there is that pipslite only comes in a rpm, and to install that you need to convert the .rpm to a .deb using alien.(and pipslite is 32-bit only).

so install alien (again as root).
google for pipslite-cups-1.0.1-1.i386.rpm and download it.
run alien on that rpm and it'll make a pipslite-cups-1.0.1-1.i386.deb
install pipslite-cups-1.0.1-1.i386.deb

Of all the words in there, I must confess the only ones I truly understand are the ones such as be, and, also, you,....etc.  You get the picture.

However, even being unable to understand what the words are or mean, it looks to me like this set of instructions differs considerably from the four-step instructions posted earlier.

Maybe this is not the place for novices such as me.  I am not a programmer, and have only had ubuntu installed on my system for a couple weeks so all the terms and phrases that make perfect sense to the majority of users of this forum are as foreign to me as if I was trying to read Swahili.

Maybe if I stare at it long enough something will soak in.  The original four-step process now seems fairly straightforward until I reached the point that I didn't "own" the folder into which I tried to copy the file.

I started another thread as to how to change permissions and it is some involved process as well.  Do I understand correctly, that even if I can change the permissions of the model folder and get the Stylus CX-8400.ppd file copied into it, then complete the four steps, the printer is still not going to work?

---

### Post by eliasz on 2007-12-12
Hi guys. I was previously able to print perfectly using 7.10 64 bit using the CX8400 Gutenprint 5.0.1 driver as i described above(Using Cups on localhost). One day it just stopped working. When i add the printer now using the same method and try to print a test page i get this error:
""/usr/lib/cups/filter/rastertogutenprint.5.0 failed"" 
displayed by the printer name at the top of cups. In jobs, the job is marked as stop right away.
Now, I've installed some things trying to follow the directions above to get it working. Could that cause a conflict of some sort? I'm not sure what this error means. What is raster? I tried to apt-cache search it to no avail, or at least i didn't recognize any of the files are relevant to this situation. 

Anyway, any advice would be great, im not really sure where to go. Rebooting to windows to print is a real pain. Anyway, thanks for all the help so far,

-EL

---

### Post by jiro on 2007-12-13
I can confirm that ewr2san's method works perfectly on my Sidux box:

1. download the pipslite rpm package from [avasys.jp/english/]("http://avasys.jp/english/")
2. install alien
3. run alien on the pipslite rpm to convert it to a deb package
4. install the pipslite deb package
5. download the ppd file posted to this forum thread, make sure the permissions are correct
6. add & configure the cx8400 using the CUPS browser interface (localhost:631), using the downloaded ppd file

THANK YOU !!

(I am attaching a pipslite deb package and the ppd file posted earlier. the ppd file needs to be renamed to remove the txt extension. hopefully these will work and save steps 1-3 above)

---

### Post by ewr2san on 2007-12-13
Root=Administrator

SUDO=Program to change the current user to root (like one might change clothes), or perform a single action as root.


> **cp1969 said:**
> Of all the words in there, I must confess the only ones I truly understand are the ones such as be, and, also, you,....etc.  You get the picture.

However, even being unable to understand what the words are or mean, it looks to me like this set of instructions differs considerably from the four-step instructions posted earlier.

Maybe this is not the place for novices such as me.  I am not a programmer, and have only had ubuntu installed on my system for a couple weeks so all the terms and phrases that make perfect sense to the majority of users of this forum are as foreign to me as if I was trying to read Swahili.

Maybe if I stare at it long enough something will soak in.  The original four-step process now seems fairly straightforward until I reached the point that I didn't "own" the folder into which I tried to copy the file.

I started another thread as to how to change permissions and it is some involved process as well.  Do I understand correctly, that even if I can change the permissions of the model folder and get the Stylus CX-8400.ppd file copied into it, then complete the four steps, the printer is still not going to work?

---

### Post by eliasz on 2007-12-13
Hi guys, i have been playing with cups again, im not getting
Does ANYONE know what raster is? it seams to be my issue. 
"/usr/lib/cups/filter/pstoraster failed"

---

### Post by cp1969 on 2007-12-13
> **jiro said:**
> I can confirm that ewr2san's method works perfectly on my Sidux box:

1. download the pipslite rpm package from [avasys.jp/english/]("http://avasys.jp/english/")
2. install alien
3. run alien on the pipslite rpm to convert it to a deb package
4. install the pipslite deb package
5. download the ppd file posted to this forum thread, make sure the permissions are correct
6. add & configure the cx8400 using the CUPS browser interface (localhost:631), using the downloaded ppd file

THANK YOU !!

(I am attaching a pipslite deb package and the ppd file posted earlier. the ppd file needs to be renamed to remove the txt extension. hopefully these will work and save steps 1-3 above)

When I try to install pipslite, from the attachment of this post I get an error message:
Dependency is not satisfiable: libc6

---

### Post by jiro on 2007-12-14
have you tried installing libc6?

---

### Post by cp1969 on 2007-12-14
Nope.

Didn't know I had to; this is the first time I ever heard it mentioned.  If it was in previous posts, I missed it.

I'm tellin' ya---I ain't a geek.  I don't understand this stuff.

How--and for what purpose--do I install libc?  And is this going to be the last of it, or is it going to be a never ending sequence of missing programs, etc?

Thanks.

---

### Post by cp1969 on 2007-12-15
> **jiro said:**
> have you tried installing libc6?

Using Synaptic, it look to me like it already is installed.  Version 2.6.1-1ubuntu9

---

### Post by jiro on 2007-12-15
it may be that the deb package i attached to my first post is incompatible with your computer. i compiled it on my sidux system and you are running ubuntu. try following the steps outlined in my and others' posts, download the rpm package and run alien on it to create a deb package compatible with your system.

---

### Post by cp1969 on 2007-12-15
I have been struggling with this some more.

Since I could not download the .deb file from the post above, I tried doing steps 1-3 on my own. 

(Read that having the .ppd file in the model folder before running the .ppd install was no good, so I took it out via Nautilus.)

1. Went to that site and downloaded the .rpm file to my desktop.

2.  Installed alien.

3.  Tried to run alien  but it says no such file exists even though the file is on my desktop..

Giving up on trying to convert my .rpm to a .deb,  I went back and tried to download the .deb file from the above post (again) and it is now on my desktop.  I don't know if removing the .ppd from the model folder had anything to do with there being no error this time.

Next, I ran sudo dpkg -1 pipslite.......I386.deb and it says 

dpkg: error processing pipslite-cups_1.0.1-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 pipslite-cups_1.0.1-2_i386.deb


Bonus question:  What does the command look like to run alien?  Here's what I used:

sudo alien pipslite-cups-1.0.1-1.i386.rpm and it returns this result:

cep@cep-desktop:~$ sudo -i
root@cep-desktop:~# sudo alien pipslite-cups-1.0.1-1.i386.rpm
File "pipslite-cups-1.0.1-1.i386.rpm" not found.
root@cep-desktop:~#

---

### Post by cp1969 on 2007-12-16
[SIZE="7"]SUCCESS[/SIZE]

It's...a...miracle...It...WORKS!!!!!!!!!!!  

It printed a beautiful test page.  Is it perfect?  Hell if I know, but it is plenty good enough for me.

I am too tired right now to document what it took for a complete, utter, total, know-nothing, hick country bumpkin to make this thing print, but I did it.  And if I could do it, ANYBODY can.

In a nutshell, I followed Jiro's instructions but there are some catches for us newbies.

Thank you all for your help.

---

### Post by cp1969 on 2007-12-16
As promised, here is the step-by-step for how I got it to work.  However, my joy from last night has been somewhat diminished by the fact that I created an Open Office word document that did not print correctly.  And, this thing is SLOOOOOOW and NOISY.  Sounds like a 1930's agricultural implement.  BTW, my equipment is an old 700mHz Dell running ubuntu 7.10.  These steps are simply the same steps listed in jiro's post but with my commentary on how I made them work.  Please note that skipping steps 1-3 is not possible unless you're using the same OS as jiro (Sidux).


1.download the pipslite rpm package from avasys.jp/english/
Go to to the site and click on the Linux driver download tab on left, then on 'all-in-one' 
You can read the license agreement if you want; scroll down the page and select the CX8400.  Under &#8220;distribution&#8221;, I chose "Debian".  Under &#8220;distribution version&#8221; I chose 		"Others".  This will download a .rpm file.  In my case, it downloaded  the file &#8220;pipslite-cups-1.0.1-1.i386.rpm&#8221; to my Desktop.
		
2. install alien
Use Synaptic for this.  Open Synaptic (System-Administration-Synaptic) and do a search on alien, click the little box to the left of it's name and let Synaptic do its thing.  This is the program that will convert the .rpm file to a .deb.  The ubuntu help explains this.  Click on the blue Help button at the top of the screen and do a search on 'alien' if you want to read about it.

3. run alien on the pipslite rpm to convert it to a deb package
You have to make sure you're in the correct directory before you run this command.  In my case, the .rpm file was downloaded to my desktop.  So, first step was to open a terminal (Applications-Accessories-Terminal) and change directories by typing:
cd ~/Desktop    

then type:
sudo alien pipslite-cups-1.0.1-1.i386.rpm
Bingo: A  .deb file is created on the desktop.  pipslite-cups_1.0.1-2_i386.deb in my case.

4. install the pipslite deb package
There are terminal commands you can run to do this, but I just double clicked the file and it did its own installation.  If for some reason double clicking doesn't work, here is the command:
sudo dpkg -i pipslite-cups_1.0.1-2_i386.deb     Again, you have to be in the same directory where the file resides, so precede that command with cd ~/Desktop if necessary.  This action will create, among other things, a file called &#8220;eklite.ppd&#8221; in the file_system/usr/share/cups/model folder.

5. download the ppd file posted to this forum thread, make sure the permissions are correct
This is simple.  Single left mouse click, choose download.  Then find the file, do a right click on it, and choose rename.  Delete the .txt extension and click enter.  Now we need to move the file to the same folder as above: file_system/usr/share/cups/model.  Note:  There are apparently many different paths to a folder(s) called usr/share/cups/model.  Make sure you copy this file into the same 'model' folder where the &#8220;eklite.ppd&#8221; file resides.  You also must change the permissions of this file.  Right click it, select Properties, then Permissions.  You've got to change the owner to &#8220;root&#8221; with read/write access and 'group' and 'others' need to be read only.  I think the way I did this was to open Nautilus on the advice of another poster.  Type 'gksudo nautilus' in a terminal and you will have ability to do this.  I don't think a regular file browser will enable you to change permissions. 

6. add & configure the cx8400 using the CUPS browser interface (localhost:631), using the downloaded ppd file.
Make sure the CX8400 is connected and powered up.  Go to the CUPS website and choose Add Printer, fill in the titles, and choose the Gutenprint USB Printer #1 (Epson USB2.0 MFP(High Speed)).  That choice of Device will NOT be there unless your printer is connected and powered up.  Follow the remaining instructions and when it asks for  model/driver, DON'T select anything from the list&#8212;that file was probably already installed a long time ago and it doesn't work.  Use the browse button on the 'Provide PPD file' option to upload to the Stylus_CX8400.ppd file located in file_system/usr/share/cups/model.  Then go to System/Administration/Printing and print a test page and make the printer default if desired.

Good luck and I hope this helps someone else.  Sorry for it being written in such newbie language but that's what's necessary for we newbs.

---

### Post by cp1969 on 2007-12-16
> **ewr2san said:**
> OK! Got Scanning working not as root.

1. Make sure that scanning users are added to group scanner
2. Edit  /etc/sane.d/epkowa.conf
add:
usb 0x04b8 0x0839

and commented out:
SCSI EPSON

3. Edit /etc/udev/rules.d/45-libsane.rules
Add:
# Epson CX-8400
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0839", MODE="664", GROUP="scanner"

Reboot and all is well.. Kooka, xsane, and everything else works swimmingly.

Now for the scanner....  Again, you can't modify any files as a regular user, so I launched gksudo nautilus to to this:

In my /etc/sane.d folder, there is no such file as epkowa.conf, however there are two .conf files for Epson--epson.conf and epson2.conf.  I did the commenting out of SCSI Epson and edited the usb line to say "usb 0x04b8 0x0839" in BOTH files as I had no idea which one it might actually use or, maybe it uses both of them.

Then I went into etc/udev/rules.d/45-libsane.rules and did a cut and paste of the above line for SYSFS.  

Xsane now works, both in black and white and in color.

---

### Post by eliasz on 2007-12-16
> **cp1969 said:**
> 
1.download the pipslite rpm package from avasys.jp/english/
Go to to the site and click on the Linux driver download tab on left, then on 'all-in-one' 
You can read the license agreement if you want; scroll down the page and select the CX8400.  Under “distribution”, I chose "Debian".  Under “distribution version” I chose 		"Others".  This will download a .rpm file.  In my case, it downloaded  the file “pipslite-cups-1.0.1-1.i386.rpm” to my Desktop.

Is there a 64 bit version of this file?

---

### Post by JT673 on 2007-12-18
This doesn't work.  Even if I install it, rastertopips will still fail D=

---

### Post by JT673 on 2007-12-18
Edit: Never mind, it's just evince -_-

---

### Post by notbitmonk on 2007-12-20
I'm using a Epson Stylus CX7400 and I installed it using pipslite in a matter similar to what has been described in this[ post]("http://translate.google.com/translate?hl=en&sl=it&u=http://forum.ubuntu-it.org/index.php%3Ftopic%3D142737.msg941930&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3DLunix%2BEpson%2BCX7400%2BPPD%26hl%3Den%26sa%3DG") ([untranslated]("http://forum.ubuntu-it.org/index.php?topic=142737.msg941930")).  I had the same rastertopips error when printing an image from Eye of Gnome.  By using GIMP I was able to set up the printer using the ppd file created by following the aforementioned post.  I was able to print the image but the printout color wasn't very good.  The test page was good (at least it appears to me) but printing from Openoffice Writer (I used one of the example files from Ubuntu) didn't yield good results.  The printed page was cutoff at the bottom where the Ubuntu logo is.  Scanning worked great by using the above post instructions.  I'm still figuring out how to make it work Ok.  I'll post something if I get good results.

---

### Post by jkratze1 on 2007-12-24
I've followed the instructions, and when printing, the printer stops printing at the bottom of the page.  I have to turn the printer off to get the printer to form feed the page.  The printer light still flashes like there is more to print but the printer just stops.

Anyone else have this problem?

---

### Post by tom45555 on 2007-12-28
To ewr2san, Quid, Tanker Bob, Weston and the rest in the thread .... a big thanks!!  Got both the printer and scanner to work just fine.  Even though I'm using PCLinuxOS, the information in these postings worked beautifuly.  I'm even sharing the printer through Linux to the rest of the network.  This is a fine example of folks comming to the rescue to help resolve problems in the Linux community.  A Happy New Year to you all .... and again, Thanks!!

Tom

---

### Post by khentiamentiu on 2007-12-29
> **Quid said:**
> Thanks to All who are helping out...

Tanker Bob - your 4 step instructions seem quite straight forward ( maybe I needed to do a step previous?)

I loaded the ppd from Weston - renamed, and checked the permissions, installed with cups. ( Mind you it found the printer and actually installed one before I finished in cups - good old Gutsy ) but I went through the steps and created a second - and they were actually identical .

When I try and print a test page - I get this error in the cups browser:
"/usr/lib/cups/filter/rastertopips failed"


.

Did you ever find the rastertopips filter? I'm getting this error because the filter does not exist on my system, even though gutenprint is installed. 
Where do I get the filter?

---

### Post by toadman on 2008-01-01
> **tom45555 said:**
> To ewr2san, Quid, Tanker Bob, Weston and the rest in the thread .... a big thanks!!  Got both the printer and scanner to work just fine.  Even though I'm using PCLinuxOS, the information in these postings worked beautifuly.  I'm even sharing the printer through Linux to the rest of the network.  This is a fine example of folks comming to the rescue to help resolve problems in the Linux community.  A Happy New Year to you all .... and again, Thanks!!

Tom

 Ive got the printer to work in both ubuntu and PCLinuxOS  but in ubuntu it does the same as with jkratze1,stops at the end.Works great with PCLinuxOS.

 However,i am not able to get the scanner working on either install.I'm sure its probably just a newbie mistake but i can't figure it out .Maybe I'm editing the config files wrong or someting,being that I have never had to do this before and may not be doing something right .Any help would greatly be appreciated.

 The only thing xsane detects is my tvtuner card.

---

### Post by jkratze1 on 2008-01-03
Toadman, modify the libsane-rules file exactly as cp1969 says and the scanner will work fine using XSane, at least with Ubuntu.  I'm still having the printer problem where printing stops at the bottom of the page.  Has anyone found a solution to this printing problem?

---

### Post by toadman on 2008-01-03
Well got scanner working in both installs.It was a newbie mistake not knowing what commenting out really meant.But the scanner is only working in b/w.I'm sure it's just another newbie mistake that I will figure out.

 Without the help from this thread and posters within it I wouldn't stand a chance at figuring any of this out.So would like to give everyone a big Thanks for all your help:)

---

### Post by dvdianov on 2008-01-23
Hi!
1. Excuse me for bad English, but I have no place to address more. It automatically the translated text. 
2. I the usual user from Russia, not the Mafiosi:). I am going to buy Epson Stylus CX8300, but I have doubts in occasion of its work in Ubuntu. I have XUbuntu 7.10. 
The resulted and working PPD-file can not work with CX8300? And, in what instructions for CX8300 can differ? I doubt in particular in deviceId... 
Please, help me!

---

### Post by jkratze1 on 2008-01-26
When I try to print a picture I get the message /usr/lib/cups/filter/rastertopips failed.  Anyone else get this, and if so, how do I fix it?

---

### Post by shmakes on 2008-01-26
I just started getting this also.  

It used to work for me.  Some update must have changed a library, setting or permission.

I will look into it and post back if I figure it out.  

If anyone else has some ideas on where to check, please chime in.

---

### Post by gauss on 2008-02-02
> **signifer123 said:**
> Alright, to print use the CX5800 drivers, it worked under version 5.1.3 of the drivers.


Thanks! I had been using CX3810 and got only black-and-white. The CX5800 drivers work perfectly in color and black-and-white under gutenprint 5.1.4 and, in my case, Gentoo.

---

### Post by exXP on 2008-02-14
I have tried the suggested solution and suspect that I have done something wrong on the way.  After I get onto localhost:631 and select 'Add Printer', I am directed to enter a name (whose?) a location and a description.  Then I am directed to a choice starting with 'Appsocket/HP Direct'   Can anyone tel where I went wrong and how to backtrack?   The printer looks like a winner and I would dearly love to use it Linux as well as XP
exXP

---

### Post by exXP on 2008-02-14
Further to my previous note, I have managed to get the driver from localhost:631 but now seem to need to acquire and install pipslite.  Does anyone know where it can be obtained?
I can't help feeling that this sort of problem (drivers for CX8400) is giving Linux a black eye and discouraging a lot of would-be users.  Heck, I'm discouraged myself at times.  I know the ball really lies in Epson's court but they don't seem to be playing!
exXP
PS  By reading from the Forum I have managed to get the scanner working

---

### Post by exXP on 2008-02-15
I seem to be talking to myself here, however.......I went back to page 9 of this thread and found cp1969's excellent tutorial.  From raw beginner up to semi-expert, this kind of layout of what-to-do is great.  As with some others, I find that sometimes the printer doesn't release the page and hopefully somebody will come up with a fix for this.  But yesterday I couldn't print at all.  Now i can even if there are minor problems.
exXP

---

### Post by gedreosan on 2008-03-23
I followed along the steps throughout this thread.  Finally cp1969's walkthrough worked on my desktop running Mint 3.1.  But my laptop running Ubuntu 7.10 won't alien the rpm correctly.  This is what I get when running *sudo alien pipslite-cups-1.0.3-1.i386.rpm*

Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/pipslite-cups
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find any packages for libgtk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-1.2 (soname 0, path libgtk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-1.2 (soname 0, path libgdk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgmodule-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-1.2 (soname 0, path libgmodule-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libglib-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-1.2 (soname 0, path libglib-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgtk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-1.2 (soname 0, path libgtk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-1.2 (soname 0, path libgdk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgmodule-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-1.2 (soname 0, path libgmodule-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libglib-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-1.2 (soname 0, path libglib-1.2.so.0, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: pipslite-cups-1.0.3: No such file or directory

And I'm left with a locked folder on my desktop called pipslite-cups-1.0.3.  What did I miss/forget?

---

### Post by Dai777 on 2008-03-30
I have both debs and the instructions on setting up sane for DX4800  if you want them just email me 
[email]dai54321@hotmail.com[/email]

---

### Post by alpwazungy on 2008-04-16
I have been using Ubuntu for about 2 weeks.
I moved from Mandrake 10.1. Part of the reason was my CX8400 printer dod not work with Mandrake and I did not like the problems I was having installing mandriva 2008.

Ubuntu does a good job with the way updates are done, but you would think that something might be available for this printer by now.... or am I missing something?

I never was good at granting permissions or compiling things into the kernel, or opening scripts or running scripts.... 
Has to be an easy fix for this???


Alp

---

### Post by exXP on 2008-04-28
I had difficulty printing with my CX8400 but I found the reply by cp1969 (this thread, 16 Dec 2007) solved all my problems. I have upgraded to 8.04 and the printer still works. The scanner gave me a little trouble but I managed to solve that one.

---

### Post by Dai777 on 2008-05-01
[http://dai-videotutes.blogspot.com/2008/05/installing-epson-dx8400-on-ubuntu.html](http://dai-videotutes.blogspot.com/2008/05/installing-epson-dx8400-on-ubuntu.html)

video advice on how to install the printer

---

### Post by toadman on 2008-05-04
After upgrading to Hardy my printer stopped working.I followed instructions on the video in above post and just installed the printer driver,but not scanner driver.Printer and scanner both working perfectly now:)

---

### Post by wheezer on 2008-05-22
> **toadman said:**
> After upgrading to Hardy my printer stopped working.I followed instructions on the video in above post and just installed the printer driver,but not scanner driver.Printer and scanner both working perfectly now:)


The Video referred to above says "DX_8400, not CX_8400"   Forgive me for sounding dumb, but if these are the same model, why then does he call it DX? 

Am I safe buying this printer? Is it going to work in my Gutsy install if I follow this very dense video?  Is there anything easier to follow yet?

---

### Post by toadman on 2008-05-22
CP1969 wrote a very nice guide on how to install the cx8400 printer.It's the first post,on page 9 in this thread.I've used that guide to install on gutsy and also pclinuxos and worked great.After I upgraded to hardy the printer stopped working,that's where the video came in.I would recommend using cp1969's guide for a fresh install.

---

### Post by wheezer on 2008-05-22
> **toadman said:**
> CP1969 wrote a very nice guide on how to install the cx8400 printer.It's the first post,on page 9 in this thread.I've used that guide to install on gutsy and also pclinuxos and worked great.After I upgraded to hardy the printer stopped working,that's where the video came in.I would recommend using cp1969's guide for a fresh install.

Thanks Toad. I am still pretty new to Ubuntu.  I am looking for both a basic text printer for home, for under $150, and an all- in-one printer scanner for under $175.

Do you still recommend this one, or have you heard of a better bet. I really don't want to wrestle with much this week.  Way too much to do, and ubuntu issues have made me kick the chair in the past. I can sacrifice perfection for something that JUST WORKs.   Suggestions greatly appreciated.

---

### Post by toadman on 2008-05-22
I am pretty new to linux myself.I didn't by this printer.My daughter bought it for me.It is a little work to get it running.I am very happy with the printer but probably wouldn't of bought it myself.I would of tried to buy probably a Hp that worked out of the box.Saying that,this printer is pretty cheap right now,bestbuy has it onsell for 79.99.

 If you don't want the hassle of getting this up and running I would find one that you do want and check to see how it works with linux here [http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

---

### Post by wheezer on 2008-05-22
> **toadman said:**
> 
 If you don't want the hassle of getting this up and running I would find one that you do want and check to see how it works with linux here [http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)


The site seems very out of date.  Most of the HPs are really old, or phased out, or only go up to certain series number and stop.  None of the all in ones are there. I will peek at the epsons, but i'm not optimistic.

Thanks

PS
Oh.. maybe not.  I was looking at the wrong table

---

### Post by jkratze1 on 2008-05-22
Ok, I've given up getting this printer to ever work 100% correctly.  I still kept getting "rastertopips failed" message when trying to print from evince or when trying to print pictures.  Only scanning and printer from Firefox worked fine.  Then I upgraded to Hardy and only scanning worked and I could not print at all.  I was fed up.

So, I bought an HP Photo C6250 multifunction printer. Ubuntu comes with HP printer drivers called hplip or you can get the latest from sourceforge.  Let me tell, everything worked the first time.  Epson needs to get their act together and get printer drivers for all of their printers just like HP is doing or they will lose Linux customers.  They have already lost me as a customer as I will buy HP for now on.

---

### Post by wheezer on 2008-05-22
> **jkratze1 said:**
> 
So, I bought an HP Photo C6250 multifunction printer. Ubuntu comes with HP printer drivers called hplip or you can get the latest from sourceforge.  Let me tell, everything worked the first time.  Epson needs to get their act together and get printer drivers for all of their printers just like HP is doing or they will lose Linux customers.  They have already lost me as a customer as I will buy HP for now on.


Great news, assuming that printer isn't a zillion dollars.  Which Ubuntu are you using it with. I am 7.1 and don't want to upgrade yet.

---

### Post by wheezer on 2008-05-22
Jkratz

I am not finding a 6250 in the linxuprinter.org list
[http://openprinting.org/printer_list.cgi?make=HP](http://openprinting.org/printer_list.cgi?make=HP)

Only the 6200.  Are they mostly the same, do you think?

---

### Post by jkratze1 on 2008-05-23
Yes, the C6250 and C6280 use the C6200 series driver.  When HPLIP is installed it will ask you to select the C6200 series driver.

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)


> **wheezer said:**
> Jkratz

I am not finding a 6250 in the linxuprinter.org list
[http://openprinting.org/printer_list.cgi?make=HP](http://openprinting.org/printer_list.cgi?make=HP)

Only the 6200.  Are they mostly the same, do you think?

---

### Post by Quid on 2008-05-25
Sadly, less than a year into the Great Epson Stylus CX8400 attempt at success I have finally folded and purchased an HP.

Hardy Heron broke my hard work... I recompiled with Gutenprint went to print and it said it was out of ink... Not surprising as it bled ink anyway... I wanted to fool it to test if the ink was truly out or just an artifact of the reset.

I shlepped down to to Staples and shelled out 50 for a colour cartridge ( it was not complaining about Black but I picked up 2 high volume for another 50 bucks ) 

I kept getting an error ( cartridges not recognized) and googled that.
Surprise surprise - there seems to be a number of complaints that the printer stops recognizing even valid Epson cartridges!??

I did not want to gamble with 100 bucks - so I now have an HP Deskjet F4180 (75 bucks) with 2 new ink cartridges ( albeit small ones) BUT.

I followed a great link - it walked me through the install and the first page printed  beautifully. Scanning worked with no adjustment.

[http://ubuntuforums.org/showthread.php?t=184838]("http://ubuntuforums.org/showthread.php?t=184838")

Maybe someone out there can tell me a quick fix for the cartridge issue so I can feel badly for Epson. :(

BTW I did send an email directly to the Japaneses President last year. I don't think I will bother complaining again.

For 20 bucks more I could have had a better PhotoSmart 6200 series. But since my kids abuse the printer more than I use photograde, I thought I would reserve the money for the next ink purchase ( 35 bucks for both carts)

:)

---

### Post by jkratze1 on 2008-05-25
> **Quid said:**
> Sadly, less than a year into the Great Epson Stylus CX8400 attempt at success I have finally folded and purchased an HP.

Hardy Heron broke my hard work... I recompiled with Gutenprint went to print and it said it was out of ink... Not surprising as it bled ink anyway... I wanted to fool it to test if the ink was truly out or just an artifact of the reset.

I shlepped down to to Staples and shelled out 50 for a colour cartridge ( it was not complaining about Black but I picked up 2 high volume for another 50 bucks ) 

I kept getting an error ( cartridges not recognized) and googled that.
Surprise surprise - there seems to be a number of complaints that the printer stops recognizing even valid Epson cartridges!??

I did not want to gamble with 100 bucks - so I now have an HP Deskjet F4180 (75 bucks) with 2 new ink cartridges ( albeit small ones) BUT.

I followed a great link - it walked me through the install and the first page printed  beautifully. Scanning worked with no adjustment.

[http://ubuntuforums.org/showthread.php?t=184838]("http://ubuntuforums.org/showthread.php?t=184838")

Maybe someone out there can tell me a quick fix for the cartridge issue so I can feel badly for Epson. :(

BTW I did send an email directly to the Japaneses President last year. I don't think I will bother complaining again.

For 20 bucks more I could have had a better PhotoSmart 6200 series. But since my kids abuse the printer more than I use photograde, I thought I would reserve the money for the next ink purchase ( 35 bucks for both carts)

:)

Another Epson customer lost to HP.  Epson, are you listening?

---

### Post by g45model21 on 2008-05-26
Is there anyway to install it in terminal?  I am severly new at Ubuntu.

---

### Post by shmakes on 2008-06-07
cp1969's procedure on page 9 still worked for me after upgrading to Hardy.

It does not work as well as it did under Feisty, but works about as clunky as it did under Gutsy.  I didn't have to re-install when I upgraded to Gutsy - although I did have to do the "sudo aa-complain cupsd" trick.

After upgrading to Hardy the printer stopped functioning completely (scanning still worked fine).

I had to repeat all the steps starting from step 3 - run alien.  The Deb package created using alien on Feisty/Gutsy would not install on Hardy.

For step 5, I still had the file, but I confirmed it was in the correct directory with the proper permissions.

For step 6, I still had the printer defined in the CUPS browser interface so I chose "Modify" on the printer and browsed to select the PPD file again.

Also, don't forget to do the "sudo aa-complain cupsd" again, as the Hardy upgrade sets this back to "enforce".

I can now print decently from OpenOffice and Adobe Acrobat Reader.
Print jobs from Evince, Firefox, and The Gimp hang in the queue and have to be canceled.

I can live without Evince, I rarely print from Firefox and when I do I can print to PDF then use Acrobat.  Not being able to print from The Gimp stinks, but I can save the image and import it into OpenOffice for printing.

I will continue to look for ways to fix the other limitations, but honestly I have invested more hours in this printer than it was worth!  If anyone else know how to fix some of the other items, please let everyone know!  If anyone wants to see bits of my configuration, package versions, etc. I will be happy to help.

I wish I could roll back time and un-purchase this printer.  I bought it because I had such great luck with an Epson C86 under Linux.  It used to be that Epson Printers cost a bit more, but you got better hardware, performance, and support.  Also the ink cartridges used to cheaper (just ink with very little electronics and no nozzles).  

Now, they seem to have copied HP's model of cheap hardware up-front, and ink cartridges that soon cost more than the printer.  The cartridges are expensive, they still have no nozzles, and the electronics have been upgraded to prevent others from refilling them!

When it comes to "cheap printers" it appears that HP is "The Choice".  Needless to say, I will not be purchasing another Epson printer any time soon.

---

### Post by exXP on 2008-06-09
Since I upgraded to Hardy, I find I can print from Firefox 2 (but not from Firefox 3),Thunderbird, Kooka, Digikam and open Office Suite but not from Adobe or Gimp.  Guess I'll keep watching this thread and CUPS for any developments.  Sometimes the sheet won't release in which I turn off the printer and turn it back on again.
exXP (and not going back)

---

### Post by taysider on 2008-06-14
try this link as it should work
[http://ubuntuforums.org/showthread.php?t=599673&highlight=epson+dx6000](http://ubuntuforums.org/showthread.php?t=599673&highlight=epson+dx6000)

---

### Post by winemaker9 on 2008-06-26
Greetings, after three days and tons of links, finally had success with this.

[http://dai-videotutes.blogspot.com/2008/05/installing-epson-dx8400-on-ubuntu.html](http://dai-videotutes.blogspot.com/2008/05/installing-epson-dx8400-on-ubuntu.html)

It worked the first time, amazing how a video hand holder made it work when all else failed.  Both printing and scanning were successful.  This was actually done in Kubuntu, but should work fine.  The site says it's for the DX8400, but that seemed to make no difference...[COLOR="Lime"]iIT WORKED!!![/COLOR]

---

