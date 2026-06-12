---
title: "Canon PIXMA IP3600"
date: 2008-10-15
forum: General Help
---

### Post by vicpen on 2008-10-15
Anyone got the new Canon PIXMA IP3600 printer working?

---

### Post by crkack on 2008-12-07
You may want to look at the following canon site.

[http://software.canon-europe.com/software/0031336.asp?model=]("http://software.canon-europe.com/software/0031336.asp?model=")

Thanks to Canon as they have provide a driver for the IP3600! =D>

---

### Post by FunkyFrank on 2009-04-02
Hi all,

I used the driver from here, and it worked a treat:
[http://support-nz.canon.co.nz/contents/NZ/EN/0100159003.html](http://support-nz.canon.co.nz/contents/NZ/EN/0100159003.html)

Just had to specify the ppd file and it worked

Cheers

---

### Post by Fanas on 2009-11-11
Anyone got it working on 64bit?

---

### Post by automaton26 on 2009-12-09
> **Fanas said:**
> Anyone got it working on 64bit?

I'd like to know this too.

---

### Post by wmgcf on 2010-01-03
Joining the conversation late, but yes, ip3600 i386 driver works on amd64 for me. 

For the last several months I was using canon pixma ip3600 with xubuntu on an i386 machine. This weekend, my CPU on the old i386 box roasted itself so I went and bought an AMD64 mother and CPU for my box. I am running xubuntu 8.04.3.lts on my AMD box.

Here is how I installed the ip3600 an my new 64 bit machine (somebody please say if I used the wrong folders):

downloaded ip3600_debian_printer.tar from [Canon Europe]("http://software.canon-europe.com/software/0031336.asp?model=") and saved it in /usr/local/src for safekeeping.

Made a temporary folder (I used /tmp/installing), and then used these commands to unpack the tar file: 

cd /tmp/installing
sudo tar -xvvf /usr/src/ip3600_debian_printer/ip3600_debian_printer.tar 

Next I had two .deb files and also another .tar.gz file. The .tar.gz file has a certain ppd file that the printer needs. So I ran the next commands to put stuff into my /usr/local tree:

cd /usr/local/lib
sudo mkdir /usr/local/lib/ip3600_driver
cd /usr/local/lib/ip3600_driver

Since I used this location I didn't have to manually set the ppd file, eliminating a later step because ubuntu found it automatically for me: 

sudo tar -xvvzf /tmp/installing/cnijfilter-common-3.00-1.tar.gz

Finally, I installed the .deb packages. The first time I clicked on them you will get a message saying "Error: Wrong Architecture i386". So I referenced other ubuntu forums and eventually found this [good explanation]("http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/") of what that message means. After reading that and the man page section covering "--force" I ran this command in a terminal:

sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb cnijfilter-ip3600series_3.00-1_i386.deb

Which did install the packages in about 1 second.

Then I turned on the printer and xubuntu instantly recognized it, and so I started printing and it works great.

Thanks Canon and xubuntu and ubuntuforums!

---

### Post by TheAconda on 2010-01-03
I tried doing just that, but the .deb files won't install.

This is the output I get:
Selecting previously deselected package cnijfilter-common.
(Reading database ... 167908 files and directories currently installed.)
Unpacking cnijfilter-common (from cnijfilter-common_3.00-1_i386.deb) ...
Selecting previously deselected package cnijfilter-ip3600series.
Unpacking cnijfilter-ip3600series (from cnijfilter-ip3600series_3.00-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cnijfilter-common:
 cnijfilter-common depends on libcupsys2 (>= 1.2.1); however:
  Package libcupsys2 is not installed.
dpkg: error processing cnijfilter-common (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cnijfilter-ip3600series:
 cnijfilter-ip3600series depends on libcupsys2 (>= 1.2.1); however:
  Package libcupsys2 is not installed.
 cnijfilter-ip3600series depends on cnijfilter-common (>= 3.00); however:
  Package cnijfilter-common is not configured yet.
dpkg: error processing cnijfilter-ip3600series (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-common
 cnijfilter-ip3600series

However, I can't seem to install this 'libcupsys2' file...Can anyone help??

---

### Post by wmgcf on 2010-01-03
I was careful to write my post as what worked for me. I am not a ubuntu expert. One thing that I can tell you about libcupsys2 is that I ran the following shell command on my system (where I have the ip3600 working flawlessly with xubuntu 8.04.3 on an AMD64 machine as described above):

aptitude show libcupsys2

and the output of the "show" command says that libcupsys2 is installed on my system. I am unsure what you have tried to do to install libcupsys2, on my system, if I wanted to install that file I would type this command into a shell:

sudo aptitude install libcupsys2

And if that doesn't work - allowing you to install the .deb files for the ip3600 printer -then I would keep searching the forums and asking for help and someone who knows more than I do will help you.

---

### Post by TheAconda on 2010-01-04
Output of 'aptitude show libcupsys2':
No current or candidate version found for libcupsys2
Package: libcupsys2
State: not a real package
Provided by: libcups2

Output of 'sudo apt-get install libcupsys2':
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcupsys2 is a virtual package provided by:
  libcups2 1.4.1-5ubuntu2.1
You should explicitly select one to install.
E: Package libcupsys2 has no installation candidate

So I tried installing libcups2, and got this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcups2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.

Still no idea what's wrong.

---

### Post by Malta paul on 2010-01-04
I had the same problem trying to install my Canon printer in Karmic. Wish I knew the answer.
All I know is libcupsys2 has been changed in Karmic to libcups2 and my printer did not work. I went back to Jaunty which has libcupsys2 and my printer works again! :confused:

---

### Post by guruchomp on 2010-01-04
I'm not an expert either but I have a Canon Printer and up until Jaunty it worked with the drivers provided by Canon. With Karmic I had to install libcupsys2_1.3.9-17ubuntu3.4_all.deb from [http:///packages.ubuntu.com/jaunty/all/libcupsys2/download]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download")  which is a dummy package. After intstalling this I was able to install the printer. Hope this helps.

---

### Post by Malta paul on 2010-01-04
Thanks guruchomp your fix looks good, I will give it a try and let you know the results.
Paul

---

### Post by TheAconda on 2010-01-05
Trying that now...will let you know...:)

---

### Post by TheAconda on 2010-01-05
It worked! Thank you SO much....fantastic! So happy now :P

---

### Post by Malta paul on 2010-01-05
Yes it worked, many thanks,
Paul

---

### Post by stegouin on 2010-02-07
Thanks for that! I've been on Karmic for 3 weeks now, with no printer! 

I have a Canon MF4150... installed the package, then the Drivers (v1.90e) from Canon Asia site, and voila! Happy printing.

Gained some points with my wife as well. ;-)

---

### Post by Bryan55 on 2010-05-08
Hi
Though my pc recognizes my printer it will not print and after looking around I thought I would give the below a go but because I am new to command lines I get stumped. Could someone explain, in very simple steps, what I should do please? I know it must look straight forward to many but I could not even do the first step and save it to /usr/local/sre.


[wmgcf]("http://ubuntuforums.org/member.php?u=631583") wrote in post #6

> Here is how I installed the ip3600 an my new 64 bit machine (somebody please say if I used the wrong folders):

downloaded ip3600_debian_printer.tar from [Canon Europe]("http://software.canon-europe.com/software/0031336.asp?model=") and saved it in /usr/local/src for safekeeping.

Made a temporary folder (I used /tmp/installing), and then used these commands to unpack the tar file: 

cd /tmp/installing
sudo tar -xvvf /usr/src/ip3600_debian_printer/ip3600_debian_printer.tar 

Next I had two .deb files and also another .tar.gz file. The .tar.gz file has a certain ppd file that the printer needs. So I ran the next commands to put stuff into my /usr/local tree:

cd /usr/local/lib
sudo mkdir /usr/local/lib/ip3600_driver
cd /usr/local/lib/ip3600_driver

Since I used this location I didn't have to manually set the ppd file, eliminating a later step because ubuntu found it automatically for me: 

sudo tar -xvvzf /tmp/installing/cnijfilter-common-3.00-1.tar.gz

Finally, I installed the .deb packages. The first time I clicked on them you will get a message saying "Error: Wrong Architecture i386". So I referenced other ubuntu forums and eventually found this [good explanation]("http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/") of what that message means. After reading that and the man page section covering "--force" I ran this command in a terminal:

sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb cnijfilter-ip3600series_3.00-1_i386.deb

Which did install the packages in about 1 second.

Then I turned on the printer and xubuntu instantly recognized it, and so I started printing and it works great.I have managed to put this dummy package in as sugested in post #11
> I'm not an expert either but I have a Canon Printer and up until Jaunty it worked with the drivers provided by Canon. With Karmic I had to install libcupsys2_1.3.9-17ubuntu3.4_all.deb from [http:///packages.ubuntu.com/jaunty/all/libcupsys2/download]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download")  which is a dummy package. After intstalling this I was able to install the printer. Hope this helps.Thanks for any help.

Bryan.

---

### Post by Bryan55 on 2010-05-11
After failing to get the "cnijfilter-common-3.00-1.tar.gz" to install but getting the " cnijfilter-common_3.00-1_i386.deb cnijfilter-ip3600series_3.00-1_i386.deb" it worked. Strange?

However the crucial move was to first delete the none functioning printer from the system to allow the new drivers to take effect.

Bryan.

---

### Post by jakennan on 2010-05-11
Hi 

I am a complete beginner and I am trying to get my Cannon IP3600 working. I am on Ubuntu 10.4

I have understood the gist of the posts and have downloaded the linux driver from Cannon. 

The problem I have is understanding how to a manipulate the cannon files for instance the TAR file. I know it describes this in the post but there are a few steps left out for me. 

Please could somebody help

regards

James

---

### Post by XenosD on 2010-06-03
Hi!
I was trying for a couple of weeks to install my Canon Pixma IP 3600. Finally, after reading this thread I managed to install it, but when I try to print, the botom led (orange) keeps blinking and i cannot print.
The steps I followed to install the printer was:
1) I downloaded [ip3600_debian_printer.tar]("http://software.canon-europe.com/software/0031336.asp?model=") and I extracted its contents in my home folder.
(Three files was extracted: cnijfilter-common-3.00-1.tar.gz, cnijfilter-common_3.00-1_i386.deb and cnijfilter-ip3600series_3.00-1_i386.deb.)
2) I saved [llibcupsys2_1.3.9-17ubuntu3.6_all.deb]("http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.6_all.deb") in my home folder too.
3) I created the directory /usr/local/lib/ip3600_driver and I extracted the contents of cnijfilter-common-3.00-1.tar.gz in it. 
sudo su
sudo mkdir /usr/local/lib/ip3600_driver
cd /usr/local/lib/ip3600_driver
sudo tar -xvvzf cnijfilter-common-3.00-1.tar.gz
4) I installed the remaining deb files
sudo dpkg -i libcupsys2_1.3.9-17ubuntu3.6_all.deb
sudo dpkg -i cnijfilter-common_3.00-1_i386.deb
sudo dpkg -i cnijfilter-ip3600series_3.00-1_i386.deb
5) I plugged in the printer and the system recognized the printer after afew seconds

What went wrong?
Have in mind that I run Ubuntu 10.04 and I installed it through windows.

---

### Post by Bryan55 on 2010-06-04
The orange flashing light usually means no paper in tray or the front of the printer is not open to allow the printed copy to come out.

Bryan.

---

### Post by lotv on 2010-06-07
The dummy package was essential, other than that everything worked, no more reboot and windows to print, happy to find a solution :)

---

### Post by XenosD on 2010-06-11
Sorry for not replying earlier, but I had problems accessing the internet. 
Anyway, Thanks for your immediate response.
The problem was that I had paper only in the rear tray (I never use the cassete of the printer). Now that I configured the printer to always use paper from the rear tray, everything seem to be OK.

---

### Post by AnteZG on 2010-07-04
Hi guys,

Reading this thread and using the dummy package, I managed to install the drivers for IP3600 on my HP Laptop with Ubuntu 10.4.

However, I will not use the printer by having it attached to
the laptop. The printer is attached to another (windows) PC and
I want to print from my laptop via the home network.

When I go to System->Admin->Printers and click to add a printer,
I can browse and locate the printer on the network. How do I proceed from there?

I get three options

[] Select printer from database
[] Provide PPD file
[] Search for a printer driver to download

The first option does not let me choose Canon IP3600. I did install the driver using the instructions in this thread, but it somehow didn't register in the database of drivers?

The second option doesn't work since I don't have a PPD file.

The third option does not return any results.

What should I do?

Thanks in advance.

---

### Post by pardoed on 2010-07-05
guruchomp, you rock.  running ubuntu 10.04 LTS and an Canon Pixma ip2600 and the dummy package worked perfectly.

For everyone else...

Go here and get the dummy...

[http:///packages.ubuntu.com/jaunty/all/libcupsys2/download](http:///packages.ubuntu.com/jaunty/all/libcupsys2/download)

Then go here to get the driver...

[http://software.canon-europe.com/index.asp](http://software.canon-europe.com/index.asp)

Thanks a bunch to everyone who helped.  I am now sane again.

---

### Post by Opti_Rick on 2010-11-22
Thanks for all the input on this page, finally got my ip3600 printing.

Am I to guess though that it will not be printing at full resolution and will be limited to 600 dpi?

---

### Post by Bryan55 on 2010-11-22
Yes you will be stuck with 600.

Also I have never found any software to check ink levels but it's no big deal to open the top to have a look. An empty one will flash.

Bryan

---

### Post by jcd29 on 2010-11-25
Any idea how to make it work with 64 bit architecture?

---

### Post by Bryan55 on 2010-11-25
jcd29 wrote 
                       "Any idea how to make it work with 64 bit architecture?"

Have you looked at post #6 in this thread?

---

### Post by johanbove on 2011-06-27
Today the printer drivers kicked-in or something since all of a sudden I have a working printer. Not sure what made it work though.

> Anyone had any success getting the printer to work on 11.04 Natty release? I have run into dependency problems trying to install the printer in Linux Mint 11.

Posted info about the problem here: 

[http://ubuntuforums.org/showthread.php?t=1427098]("http://ubuntuforums.org/showthread.php?t=1427098")

*I'm really considering going for a printer that is fully supported on linux...*

---

### Post by Bryan55 on 2012-02-04
I came across this on another thread and it will even give you all the DPI the printer is capable of.
So simple to do as well. Remember to delete old printer first.


> No more fooling around with making any files.

This site shows you how to do the ppa route and install what you need no matter x86 or x64.

[http://www.ubuntubuzz.com/2011/06/do...er-driver.html](http://www.ubuntubuzz.com/2011/06/do...er-driver.html)

---

