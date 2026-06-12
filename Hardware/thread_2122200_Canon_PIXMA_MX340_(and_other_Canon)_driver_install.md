---
title: "Canon PIXMA MX340 (and other Canon) driver installation"
date: 2013-03-04
forum: Hardware
---

### Post by ossgrouch on 2013-03-04
**Background:**

I recently replaced my XFCE Ubuntu 11.04 Natty with LXDE Ubuntu 12.10 Quantal, both 64bit. I have a Canon 
PIXMA MX 340 printer, and as users of Linux and Canon Printers have discovered, support from Canon is at 
least very limited.
When I first tried to get Ubuntu to print to this canon printer I found that out. Canon supplies only 32 bit 
Linux drivers, and only on their overseas webpages, and trying to get them to work can be a chore. Forced 
install of the .deb packages (dpkg --force) didn't work for me, and trying to build from source code didn't 
either. That was when I found Michael Gruz internet repository at: 

[HTML]https://launchpad.net/~michael-gruz/+archive/canon[/HTML]

where he offered compiled drivers for several Canon printers for Ubuntu. So I addded those reposatories to 
Synaptic, and lo and behold, installing the cnijfilter and scangearmp drivers  was as simple as adding a new 
application.
So now I thought that I just add his latest repositories, for Oneric, last updated june 2011  (Canon's date back 
to 2010): 

deb [http://ppa.launchpad.net/michael-gruz/canon/ubuntu](http://ppa.launchpad.net/michael-gruz/canon/ubuntu) oneiric main 
deb-src [http://ppa.launchpad.net/michael-gruz/canon/ubuntu](http://ppa.launchpad.net/michael-gruz/canon/ubuntu) oneiric main

to my software sources in Synaptic for Ubuntu 12.10. **cnijfilter** and **scangearmp** for my printer appeared to 
install fine with their dependencies, but only the scanner worked. The printer looked installed, but didn't print, 
just sent the print file to nowhere I guess. Downgrading ia32-libs to v. 20090808ubuntu26 from 
[http://packages.ubuntu.com/oneiric/libs/](http://packages.ubuntu.com/oneiric/libs/) made the printer work though. 

**More research:**

After reinstalling LUbuntu 12.10 Quantal I tried to find out why the printer didn't work after installing cnijfilter
drivers for my printer from above mentioned reposatory, ia32-libs already installed (needed for another
application I use). Tracing dependencies by ldd on the 'canon driverfiles', in perticular:

```
ldd  /usr/bin/cifmx340
```

showed that** libtiff.so4** and **libpopt.so.0** were missing (not found). libtiff5 and libpopt0 was on my system, but 
a check like this:

```
file /usr/lib/x86_64-linux-gnu/libtiff.so.5.1.0
file /lib/x86_64-linux-gnu/libpopt.so.0.0.0
```

showed them to be 64 bit versions. I went to :

[HTML]http://packages.ubuntu.com/[/HTML]

searched and downoaded the i386 version of **libpopt0** and **libtiff4** from:

[HTML]http://packages.ubuntu.com/quantal/libpopt0
http://packages.ubuntu.com/quantal/libtiff4[/HTML]

to my Download Directory, the files beeing

libpopt0_1.16-7ubuntu2_i386.deb
libtiff4_3.9.6-9ubuntu1.2_i386.deb


GDebi package installer thinks they are already installed
(maybe dpkg --force might work, afraid to try)
so this is how I did it:

**My Fix:**

In a Teminal window go to the directory where the .deb files were downloaded (less typing if you are in that 
directory). Make a directory to extract the .deb files to to:

[HTML]mkdir libpopt0_1.16-7ubuntu2_i386
mkdir libtiff4_3.9.6-9ubuntu1.2_i386[/HTML]

extract:

```
sudo dpkg -x libpopt0_1.16-7ubuntu2_i386.deb ./libpopt0_1.16-7ubuntu2_i386
sudo dpkg -x libtiff4_3.9.6-9ubuntu1.2_i386.deb ./libtiff4_3.9.6-9ubuntu1.2_i386
```

I use the Tab key a lot, so I don't have to type the long names, just the first few letters and the Tab key.
As I am aready in my Download Directory, I now move into the Directories that holds my ibrary files,
and move them into my system:

```
cd /libpopt0_1.16-7ubuntu2_i386/lib/i386-linux-gnu
sudo cp -v libpopt* /lib/i386-linux-gnu
cd ..
cd ..
cd ..
```

the three last commands to move back to my download directory and then :

```
cd /libtiff4_3.9.6-9ubuntu1.2_i386/usr/lib/i386-linux-gnu
sudo cp -v libtiff* /usr/lib/i386-linux-gnu
```

Now the missing 32 bit libraries are in their proper place, and the printer works.
Something happend with the ia32-libs after Ubuntu 11.10 Oneric, these libraries obviously 
disappeared.

*****************************
**Update 4/27/13**

On Ubuntu 12.10 I found that  libjbig0 for i386 was missing as well, so I picked that up from 
[http://packages.ubuntu.com](http://packages.ubuntu.com).

With the arrival of Ubuntu 13.04 Raring Ringtail the files libpopt0:i386, libtiff4:i386 and libjbig0:i386
are available in the standard repositories, which makes it easier.

**To Recap my ramblings:**

Add repository for canon drivers to the system, either with a Package Manager or:
```
sudo add-apt-repository "deb http://http://ppa.launchpad.net/michael-gruz/canon/ubuntu oneric main"
```
With the "   "
Install ia32-libs,  libpopt0:i386,  libtiff4:i386 and  libjbig0:i386  with Package Manager or:
```
sudo apt-get install ia32-libs
```
```
sudo apt-get install  libpopt0:i386
```
```
sudo apt-get install libtiff4:i386
```
```
sudo apt-get install libjbig0:i386
```
If they are already on your system, apt-get will tell you and skip install.
And now install cnijfilter for your printer, in my case cnijfilter-MX340series and then
scangearmp, in my case scangearmp-MX340series, easiest with a Package Manager, or use:
```
apt-cache search cnijfilter
```
```
apt-cache search scangearmp
```
to see a list of available Canon Printers, and then use sudo apt-get install.
Good Luck

1 cup of ubuntu
osscar grouch

---

### Post by pdc on 2013-03-04
congratulations on getting your MX340 to work on your 64bit system;

gosh osscar..............the way you write a post makes it very hard to read ........

seems to me (after pasting it into LibreOffice and adding paragraphs!)........... you are asking

> [COLOR="#800080"]Could there be a problem with ia32-lib and ia32-lib-multiarch in the Quantal repsitories?[/COLOR]

........ you might need to ask the administrators................

the ia32-lib is also needed by the Canon UFR drivers

[http://ubuntuforums.org/showthread.php?t=2021854&p=12541322#post12541322](http://ubuntuforums.org/showthread.php?t=2021854&p=12541322#post12541322)

so it seems a common thread; as does creating symbolic links

---

