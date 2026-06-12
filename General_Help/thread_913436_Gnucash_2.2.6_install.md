---
title: "Gnucash 2.2.6 install"
date: 2008-09-07
forum: General Help
---

### Post by duchesnen on 2008-09-07
I'm a new ubuntu user and would like a finance app replacement for Quicken under windows.  I installed Gnucash 2.2.4 and imported my transactions (QIF) but several are missing (???).

I just saw the announce of Gnucash 2.2.6 ([www.gnucash.org](www.gnucash.org)). Talks about improvements in the import function (bugs fixed).  I understand only the source is available,so I must compile it however I have no idea about how to do that, any help will be appreciated.  

Also, I downloaded the file gnucash-2.2.6.tar.gz but when I try to open it with Archive Manager I get an error message, command line outuput:
[INDENT]tar: Skipping to next header

gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
tar: Child returned status 1
tar: Error exit delayed from previous errors[/INDENT]

I'm running Ubuntu release 8.04.1(hardy) with Gnome 2.22.3.

Thank you.

---

### Post by Rayaz on 2008-09-07
Have you tried downloading again? That should help with the error report. After extraction you could either have a ./configure file or an install.sh file. Generally there is a readme fie that tells you how to proceed further. You'll have to enter either ./configure or install.sh in a terminal, within the directory of the extracted files. Install.sh will take care of the rest of the process. For a ./configure one after you've configured the file you'll have to type" make" in the terminal and when that is finished "make install". Hope that helps.

---

### Post by duchesnen on 2008-09-07
Actually yes I tried to download again, however it looks like the file is cached somewhere and rather then downloading it again it just tells me the download is complete, even after I delete it from the tmp directory.

---

### Post by Sef on 2008-09-08
Moved to general help.

---

### Post by rbmorse on 2008-09-08
First, if Gnucash has been installed from Debian or Ubuntu repositories I would suggest you uninstall it using aptitude (or Synaptic GUI) as follows. 

sudo apt-get purge gnucash   <--- will NOT remove your data file(s)

First install all dependencies

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get build-dep gnucash
sudo apt-get install ofx libofx4 libofx-dev

> NOTE:  The first time I did this on Hardy it worked fine. But, on a subsequent attempt(after some updates) I received a broken dependency error during the apt-get build-dep gnucash stage. If that happens to you, stop. You will not be able to continue until the  package causing the broken dependency is fixed in repository. 

You can reinstall Gnucash 2.2.4 from repository (sudo apt-get install gnucash) to get you back to where you were. 

download source and docs from Gnucash web site (in my case to my desktop) [http://sourceforge.net/projects/gnucash/](http://sourceforge.net/projects/gnucash/)

unpack (creates 2 directories) - modify the file names as necessary (e.g. ...2.2.5 etc)

 $ cd Desktop
 $ tar -xf gnucash-source/gnucash-2.2.X.tar.bz2
 $ tar -xf gnucash-source/gnucash-docs-2.2.X.tar.gz

Installation instructions are in /home/username/gnucash-source/gnucash-2.2.X/INSTALL which you may wish to read.

Now move into the directory you are going to compile from:

 $ cd ~/Desktop/gnucash-2.2.X

First you run the ./configure script. I am advised that you can get a cleaner install if you add --prefix in order to install in a separate directory i.e.

 # ./configure --prefix=/opt/gnucash-2.X.X (where X.X is the version number)

This means that gnucash will install into /opt/gnucash-2.X.X instead of the default /usr/local. 

./configure --prefix=/opt/gnucash-2.x.x --enable-ofx
make
sudo make install

Also you will need to build the docs as they are a separate package

cd ~/gnucash-docs-2.2.0
# (if you want to use the --prefix make sure you use the same
# directory as above i.e. ./configure --prefix=/opt/gnucash-2.X.X
./configure --prefix=/opt/gnucash-2.X.X
make
sudo make install

If you need to find the binary it should be in /opt/gnucash-2.2.X/bin or /usr/local/bin depending on whether or not you used the --prefix with ./configure.

When running Gnucash for the first time you will have to go through the setup - I chose default values

Optional cleanup: First you might want to archive the downloaded source if you want to be able to reinstall it later

   $ mv /home/username/Desktop/gnucash-source /whereever/.

Then you can remove the compile stuff by:

   $ cd ~/gnucash-2.2.4
   $ make clean
   $ make distclean
   $ cd ~/gnucash-docs-2.2.0
   $ make clean
   $ make distclean

Retrieved from "http://wiki.gnucash.org/wiki/Debian"

---

### Post by duchesnen on 2008-09-14
Thank you very much for this detailed answer.  

I followed the procedure and it seemed to work, I have the bin file created and didn't see error messages.  However when I start the gnu-cash.bin application from the /opt/bin directory it quickly shows the splash screen, beep and exit!  I checked the logs and didn't find any message.

---

### Post by mmcmonster on 2008-09-14
One thing you may consider is using the [Gnucash PPA]("https://launchpad.net/%7Egnucash/+archive").

Simply add the following lines to /etc/apt/sources.list :
```
deb [http://ppa.launchpad.net/gnucash/ubuntu](http://ppa.launchpad.net/gnucash/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/gnucash/ubuntu](http://ppa.launchpad.net/gnucash/ubuntu) hardy main
```

Then run synaptic and install as usual.

---

### Post by duchesnen on 2008-09-14
Worked perfectly, thank you so much!

---

### Post by Mercurio82 on 2008-10-14
I followed the instructions here and installed Gnucash 2.2.6 in Kubuntu (Hardy) 8.04.

Everything seemed to be ok but I am unable to download my transaction using the ofx backend.

I am trying to use the Online Banking Wizard. I select 'Start AqBanking Wizard' and then the 'Backends' tab. The instructions on the wiki are to enable the ofx backend but this option is not there?

New version perhaps?

I then create a new user in the 'Users' tab. I select the 'aqofxconnect' backend and enter all my bank details.

I am pretty sure they are correct as I did have this working before and I wrote down the back account settings. 

I try the 'Get Accounts' button on the OFX tab and I am requested for my password, a message flashes by (its to quick to read but I think it is failing to connect) and my accounts are not retrieved!

One thing I note is that I can not select the 'Test' button for the 'Connection Settings' connection. Is that right?

I have tried to get this working in Ubuntu Intrepid and reach exactly the same dead end and I have installed in XP (I'm getting desperate!) without success.

So can anybody help me here? I know this can work as I managed to compile my own version before, but lost my settings after my hard drive failed

Thanks

M.

---

