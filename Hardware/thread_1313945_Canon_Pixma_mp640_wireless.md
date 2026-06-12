---
title: "Canon Pixma mp640 wireless"
date: 2009-11-04
forum: Hardware
---

### Post by cclemon on 2009-11-04
Hi. I've recently bought a Canon Pixma MP640 printer, and I'm trying to install it in Karmic Koala. Have someone managed to install this printer with WiFi support?

---

### Post by nigelpugh on 2009-11-23
Canon recently released a printer driver for this printer:
[http://support-asia.canon-asia.com/P/search?model=PIXMA+MP648&menu=download&filter=0&tagname=ca_os&ca_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MP648&menu=download&filter=0&tagname=ca_os&ca_os=Linux)

I've had mixed success with it.  So far I can't get it to duplex and all attempts at colour printing seem to result in a blank sheet of paper being fed out.

The driver appears to support network printing, but I tried various combinations with the cups-bjnp package also:
[http://sourceforge.net/projects/cups-bjnp/](http://sourceforge.net/projects/cups-bjnp/)

For the scanner, the latest build of SANE seems to work fine.  I got the latest tip, and built it according to the instructions on this blog:
[http://mp610.blogspot.com/](http://mp610.blogspot.com/)

Hope this helps!

---

### Post by yellabelly on 2009-11-24
I just got the mp640 printing with Karmic (32 bit) over Wifi. Duplex and colour are fine here. Scangear is working the scanner too.
I haven't had time to upgrade Sane yet.

---

### Post by jmurray123 on 2009-11-25
Hi. I have the exact same printer but am having problems setting it up. As I'm an ubuntu newbie could you post instructions for setting the printer up. Thanks.

---

### Post by t_tovenaar on 2009-12-08
Could you post some instructions about how you managed to get it all working?

---

### Post by avl555 on 2009-12-21
I had the same problem with the mp640 printer.

After a few months (now) I got it working.
The solution was at [http://wiki.ubuntuusers.de/Canon-Drucker](http://wiki.ubuntuusers.de/Canon-Drucker).
And at [http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP640](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP640)

The solution for me was:
Download the printer driver from [http://support-asia.canon-asia.com/contents/ASIA/EN/0100236602.html.]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100236602.html")

I do not know how exactly I have done it, but i first installed a few packages:
Open a terminal (Applications>Assesoires>Terminal)
```
sudo apt-get install libxml1 libglade0 libpng3 libtiff4 
```And then the tricky part. (Is this tricky?)

'cd' to the directory where you saved the files
```
cd Downloads
``` (in my case)
unpack the tar archive (replace the 'x' before the i386 with the actual number, 1 in my case):
```
tar zxvf cnijfilter-mp640series-3.20-x-i386-deb.tar.gz
```And install:
```
cd cnijfilter-mp640series-3.20-x-i386-deb
sudo ./install.sh
```But this didn't work for me.
So I installed the packages manually
EDIT: I don't know if the --force architecture does harm, but I think not. The main part is (as far as i know) the ppd file (**/usr/share/cups/model/canonmp640.ppd**) and that is (i think) platform independent.
I have a amd64 processor with ubuntu 64 bit, so very different from i386. I think it's save to do this.
```
cd packages
sudo dpkg -i --force architecture ./cnijfilter-common_3.20-1_i386.deb
sudo dpkg -i --force architecture ./cnijfilter-mp640series_3.20-1_i386.deb
```
EDIT: to install this driver in Ubuntu 11.04, the dependencies need to be removed (everything it needs seems to be installed).

And then add the printer using the standard printer window (System>Administration>Printing or Systeem>Beheer>Afdrukken in dutch)
Select New (Nieuw). Ubuntu will search for printers, but will likely not find the printer because it is a network printer.
Select Networkprinter (Netwerkprinter) > I didn't find the English version of it, but likely anything like "Search for Network printer" (In dutch: Netwerkprinter zoeken)
Fill in the ip-adress of the printer, click search and follow the instructions.
The default values are likely the best, they worked for me.

I have not set up the scanner, but I didn't need that (It's easier with the computer beside the printer/scanner).

I hope this helps!

And I am dutch, so there could be hundreds of misspells in this reply. This is also my first post at this forum.

---

### Post by t_tovenaar on 2009-12-23
> **avl555 said:**
> 
The solution was at [http://wiki.ubuntuusers.de/Canon-Drucker](http://wiki.ubuntuusers.de/Canon-Drucker).


This German manual is really great!
It appeared that the software for the MP640 can be downloaded on this site: [http://support-asia.canon-asia.com/P/search?model=PIXMA+MP648&menu=download&filter=0&tagname=ca_os&ca_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MP648&menu=download&filter=0&tagname=ca_os&ca_os=Linux).

Just like you said:

[LIST=1]
[*]Install some prerequisite packages, actually I installed libxml2 instead of libxml1.```
sudo apt-get install libxml2 libglade0 libpng3 libtiff4 
```
[*]Unpack the downloaded file
[*]Run the install script```
cd cnijfilter-mp640series-3.20-x-i386-deb
sudo ./install.sh
```
[/LIST]

How simple can it be! This works for me and during installation it even finds the printer on the network.

Thanks for your reply.

---

### Post by griffioen on 2010-01-01
Great,
It worked for me as well.

The 
sudo apt-get install libxml1 libglade0 libpng3 libtiff4
resulted in:
~$ sudo apt-get install libxml2 libglade0 libpng3 libtiff4
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
libxml2 is reeds de nieuwste versie.
E: Kon pakket libglade0 niet vinden

This translates to: 
libxml2 is latest version, so not updated 
E: could not find package libglade0.

Still the install works and finds the printer and it prints!

What is the use/need for libglade0?

I use: Ubuntu 9.10 - Karmic Koala

---

### Post by avl555 on 2010-01-10
See [http://forum.ubuntu-nl.org/hardware-en-drivers/canon-mp640-en-kubuntu-9-10/msg530179/#msg530179](http://forum.ubuntu-nl.org/hardware-en-drivers/canon-mp640-en-kubuntu-9-10/msg530179/#msg530179), if you are Dutch.

---

### Post by henrykay on 2010-01-11
I am having problems printing with mp640 on Ubuntu Jaunty. I installed the driver as per the previous posts and i can scan ok but i can't print more than one or two pages at a time. One page is printed, then a blank page and then the printing process halts for 5-10 minutes.

Maybe the driver is not compatible with Jaunty?

---

### Post by yellabelly on 2010-01-13
Why does Canon Europe still not show that a driver is available for Linux. As we read in this thread a working driver is available for 32 bit Linux.
[http://www.canon-europe.com/Support/Software/Linux/PIXMA/index.asp](http://www.canon-europe.com/Support/Software/Linux/PIXMA/index.asp)

Canon is lagging behind HP in its commitment to Linux.

Did anyone have success finding a driver for 64 bit Ubuntu?
I hope the team in Asia will release one soon.

p.s. sorry forgot to subscribe to this thread otherwise i would have helped earlier

---

### Post by DrTonic on 2010-01-14
I have successfully installed the driver from Canon asia on a 64-bit Ubuntu Karmic by using --force-architecture.
Color printing and duplex works fine.

---

### Post by yellabelly on 2010-01-15
Thanks DrTonic you are right that trick works a treat, now I am well happy using the mp640 with Linux Ubuntu 9.10 64 bit version.

---

### Post by suffer1989 on 2010-01-18
Does it work, if you just plug it into a XBUNTU (9.04) Computer via normal USB ?

Is there any reasons it Wouldn't work ?

---

### Post by suffer1989 on 2010-01-19
Bump ?

---

### Post by sotarokob on 2010-01-23
:D Yeah! Very brill! Thank you very much.
My MP640 wireless is also working fine now.
I am using Ubuntu 9.10 - Karmic Koala.

1. Into the Download directory in my home folder, 
I downloaded 2 driver files.

cnijfilter-mp640series-3.20-1-i386-deb.tar.gz   
scangearmp-mp640series-1.40-1-i386-deb.tar.gz

from [http://www.canon-asia.com/search?q=MP640&filter=p&start=0](http://www.canon-asia.com/search?q=MP640&filter=p&start=0)

2. sudo chmod 777 cnijfilter-mp640series-3.20-1-i386-deb.tar.gz scangearmp-mp640series-1.40-1-i386-deb.tar.gz

3. sudo tar zxvf cnijfilter-mp640series-3.20-1-i386-deb.tar.gz

4. I moved to the extracted driver package folder.
sotaro@tp-ubuntu9:~/Download$ cd cnijfilter-mp640series-3.20-1-i386-deb/packages/

5. sudo dpkg -i --force architecture cnijfilter-common_3.20-1_i386.deb 
    sudo dpkg -i --force architecture cnijfilter-mp640series_3.20-1_i386.deb

6. After I added as a new network printer from
Systems->Systems Administration->Printer

the MP640 wireless printer is working fine.
Many thanks.

---

### Post by emnaki on 2010-03-02
EDIT: sorry everything works now,

---

### Post by yellabelly on 2010-03-27
Does scangearmp still work with the latest 9.10 updates (64 bit)?
I installed with the tricks in this thread. Mine used to work but is now broken. I get a communication error early while scanning or previewing.Printing is fine still.
scangearmp shows the following library errors (they may not be relevant as I can't remember if I saw them before).

/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so

Can xsane and gimp be used to acquire? (probably not)

Thanks

---

### Post by IDodger2010 on 2010-05-16
Thanks for the clear explanation of steps involved.  Installed driver successfully on 3 machines this morning: one running Ubuntu 10_04, the other 2 Linux Mint 7.  For the 2 Mint installs I had to enter the location of the driver when going through the system/admin/printer part, it wasn't found automatically, but once location specified (it seems to default to 'usr/share') all worked fine.

Next step will be getting one of the lap-tops to network to it via wi-fi.  I guess I can go straight to the IP address..

Thanks again.

---

### Post by dbowlin17 on 2010-06-25
I just got it installed and it prints great. my issue, nothing with regards to scanning is working. any help please?

---

### Post by GartenEden on 2010-07-08
Did you install ScanGear?
Maybe you have to update your SANE drivers. There are PPAs available for that. (installation instructions e.g. [here]("http://en.eduard-dopler.de/36/install-canon-mp640-on-ubuntu/"))
For me both scanning (ScanGear and SANE) and printing works.

---

### Post by trjtrj on 2010-07-21
> **GartenEden said:**
> Did you install ScanGear?
Maybe you have to update your SANE drivers. There are PPAs available for that. (installation instructions e.g. [here]("http://en.eduard-dopler.de/36/install-canon-mp640-on-ubuntu/"))
For me both scanning (ScanGear and SANE) and printing works.
The install instructions from "GartenEden" above are excellent.  Download the files he references from the Europe site link and once you unpack them, click on the install icon within each folder and it autoinstalls.  No sudko necessary in terminal.

---

### Post by schurl on 2010-10-01
It is also possible to use the install.sh script in the canon debain package with amd64 by modifying a single line in the script. With this modification you can use the setup program that searches and installs the printer.

1. modify the line with 'dpkg -iG' to 'dpkg -iG --force architecture' in install.sh
2. run the script with sudo ./install.sh

A first simple test print worked in ubuntu 10.04 but I didn't check what printer driver options are available (ppd file seems to need some additions).

---

### Post by petrus66 on 2011-01-12
I did a two day research and 4 hour work to make the Pixma 620 online and
printing over Wlan network. Euphoria is quite near what I'm feeling just now.

---

### Post by DylanRush on 2011-04-17
Okay, I just updated to 11.04 64bit.  When I had 10.10 64bit it was was pretty easy for me to install. I just had to do this basically.  ```
sudo dpkg -i --force architecture ./cnijfilter-common_3.20-1_i386.deb
sudo dpkg -i --force architecture ./cnijfilter-mp640series_3.20-1_i386.deb
```

Now when I try to do that I get soo many dependencies that say I need to have libc6 (>= 2.3.4-1) So i went though and did 
sudo apt-get install for all of the ones that it says I need but they are all up to date, so I don't really know what the problem is.

This is what happens: 
```
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 127962 files and directories currently installed.)
Preparing to replace cnijfilter-common:i386 3.20-1 (using .../cnijfilter-common_3.20-1_i386.deb) ...
Unpacking replacement cnijfilter-common:i386 ...
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1) | libcups2.
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-common:i386

```

---

### Post by mal205 on 2011-06-11
Messed around with this for ages on my 11:04 64 bit machine. All sorts of dependency issues. Eventually I found this page, which describes a PPA that sorted the print side out in a couple of copy and paste actions:

[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html]("http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html")

---

### Post by PapaGary on 2011-06-12
> **mal205 said:**
> Messed around with this for ages on my 11:04 64 bit machine. All sorts of dependency issues. Eventually I found this page, which describes a PPA that sorted the print side out in a couple of copy and paste actions:

[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

WOW! This worked! I now have a fully functioning Ubuntu 11.04 Toshiba laptop and wireless Canon printer.

Gawd, I love this place!

---

### Post by quequotion on 2011-06-22
Any ideas for a Pixus MP460?

I've seen discussion of the Pixma 460 working with the Pixma 160 driver.

The Pixus 460 and Pixma 460 look identical so I think it's just a naming issue (pixus in japan, pixma everywhere else?)

---

### Post by dbowlin17 on 2012-01-02
hi all, i have tried removing dependencies on 64 bit and it still sucks and i can't get it to install. unsure what to do. any help?

---

### Post by librechick on 2012-01-03
The problem with using a repository like that is you don't know if they can be trusted. HP is really the way to go with printers as they make ones which are completely free software compatible.  You can check out their driver web site for a list. Look at where it says firmware required or not and plug-in required or not.  You don't want either.

[http://www.thinkpenguin.com/ ]("http://www.thinkpenguin.com/")also sells the free software ones. Can't be easier than this.

---

### Post by bazzawill on 2012-02-17
I downloaded the package from 
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100236602.html]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100236602.html")
untar the package using 
```
tar xvf cnijfilter-mp640series-3.20-1-i386-deb.tar.gz
```
cd into the packages directory
```
 cd cnijfilter-mp640series-3.20-1-i386-deb/packages/ 
```
Then using videbcontrol remove all the dependencies from both deb files by deleting everything after 
```
Depends:
```
make sure you have similar packages installed though I am pretty sure everything will be installed on a default Ubuntu install.
then install the modified packages using 
```
 sudo dpkg -i  sudo dpkg -i cnijfilter-common_3.20-1_i386.modfied.deb cnijfilter-mp640series_3.20-1_i386.modfied.deb 
```
you may have to clean up some files with incorrect permissions check your /var/log/cups/error_log change any file reported with incorrect permissions to match other files in the folder. In particular change user from your user to root using
```
chown root:root *file*
```
You may then be able to install your printer using the gui or web interface [http://localhost:631]("http://localhost:631")
However I could not so I used
```
cnijnetprn --search auto
sudo /usr/sbin/lpadmin -p canon640 -m canonmp640.ppd -v cnijnet:/00-1E-8F-B8-DA-33
```
replace the cnijnet... with the output of cnijnetprn
I then found more files with incorrect permissions looking at printers in the web interface, fix them with the steps above and again restart cups and resume the printer.

I hope that helps someone sorry it is not all that straight forward I did not exactly document the steps I took so I someone wants to clean up this guide and repost that would help more people. Now if only canon would update their packages to install more easily.

---

### Post by sibertiger on 2012-11-13
> **t_tovenaar said:**
> This German manual is really great!
It appeared that the software for the MP640 can be downloaded on this site: [http://support-asia.canon-asia.com/P/search?model=PIXMA+MP648&menu=download&filter=0&tagname=ca_os&ca_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MP648&menu=download&filter=0&tagname=ca_os&ca_os=Linux).

Just like you said:

[LIST=1]
[*]Install some prerequisite packages, actually I installed libxml2 instead of libxml1.```
sudo apt-get install libxml2 libglade0 libpng3 libtiff4 
```
[*]Unpack the downloaded file
[*]Run the install script```
cd cnijfilter-mp640series-3.20-x-i386-deb
sudo ./install.sh
```
[/LIST]

How simple can it be! This works for me and during installation it even finds the printer on the network.

Thanks for your reply.


Hi,  Newbie to Ubuntu.  Quite versed in Windows, but its too much of a memory hog.  Ubuntu is working great, just cannot install my Canon MP640.  Followed these steps, and it still is not seeing it.  It is wireless.  Could you walk me through what I need to do next?  Thanks.

---

### Post by deadflowr on 2012-11-13
> **sibertiger said:**
> Hi,  Newbie to Ubuntu.  Quite versed in Windows, but its too much of a memory hog.  Ubuntu is working great, just cannot install my Canon MP640.  Followed these steps, and it still is not seeing it.  It is wireless.  Could you walk me through what I need to do next?  Thanks.

This is an old thread, but here goes.

If you've already gone to the printer setup window/page, and clicked new, and selected network and the cji-whateverissays hasn't shown up then do this:
Open the file manager/home folder, go to the folder where you unzipped the package(most likely downloads), you should see a folder with the package name, click on it. You should see three icons, packages, source and install. Click on the packages and you should see four deb files, two common and two with the printer name. first select the common deb for the type of system you're using, 32-bit or 64-bit(i386 is 32-bit, and amd_64 is 64-bit).Clicking on it should open the software center and ask you to install(It might open slowly)So install it. When it is installed go back to folder and click on the deb file for the printer(same as before with the type you're using, and do the same as opening the software center.
Now it has been installed go to the print page again and select new and click network(it might take a minute for it to show up.
When it shows up select the cji-blah-blah and proceed from there.

---

### Post by sibertiger on 2012-11-13
Thank you folks, it is now printing.  Appreciate the help.

---

