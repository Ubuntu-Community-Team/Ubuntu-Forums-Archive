---
title: "Epson C1100 Laser on 7.10[Solved]"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by plusmore on 2007-10-30
This is a last ditch appeal for help. I have an Epson C1100 colour laser which was working fine on Feisty (with a patch to a script) but it just won't work under Gutsy. The tarball compiles fine and installs and I can set the printer up in Cups but when I send a test page nothing happens. 

Can anyone help?

---

### Post by Marc Higgins on 2007-11-11
Firstly this might not work for everyone & there might be a better way (if you do know of one please share your knowledge & let us know). 

It looks like something that ships with Ubuntu doesn't work with this printer & the source file Epson-ALC1100-filter-1.2.tar.gz from epsons site  [www.avasts.jp](www.avasts.jp)  doesn't work either (well I can't get it to work). However the rpm's available on the same site DO work if they are converted to deb's & installed.

#1 Install the dependencies (this is important, if you don't do this it won't work)

```
sudo aptitude install gcc-3.3-base libstdc++5
```

or you could just use synaptic System > Administration > Synaptic & just search for & install gcc-3.3-base & libstdc++5

From here you can decide to;

OPTION A
install the deb files direct from my site below 

[http://qld.yi.org/it_i/epson-alc1100-filter_1.2-1_i386.deb](http://qld.yi.org/it_i/epson-alc1100-filter_1.2-1_i386.deb)
[http://qld.yi.org/it_i/epson-alc1100-filter-cups_1.2-1_i386.deb](http://qld.yi.org/it_i/epson-alc1100-filter-cups_1.2-1_i386.deb)

Just double click on EACH of these links, that will invoke the Gdebi package installer & install the files.  

Then install the printer normally using System > Administration > Printers (AKA system-config-printer) & hopefully you will be printing happily in seconds:)

OR 

OPTION B

you can make your own install files using Alien

Install Alien

```
sudo aptitude install alien 
```

or just use synaptic  System > Administration > Synaptic & search for & install alien

Then go to [http://www.avasys.jp/english/linux_e/dl_laser.html](http://www.avasys.jp/english/linux_e/dl_laser.html)

download these 2 files

For Turbo/RedHat/Fedora (Epson-ALC1100-filter-1.2-0.i386.rpm)
For Turbo/RedHat/Fedora (Epson-ALC1100-filter-cups-1.2-0.i386.rpm)

then from a terminal run 
```

sudo alien Epson-ALC1100-filter-1.2-0.i386.rpm
```
```
sudo alien Epson-ALC1100-filter-cups-1.2-0.i386.rpm 
```

that will create 2 files 

epson-alc1100-filter_1.2-1_i386.deb
epson-alc1100-filter-cups_1.2-1_i386.deb

you can then use dpkg  -i 

```
dpkg -i epson-alc1100-filter_1.2-1_i386.deb
```
```
dpkg -i epson-alc1100-filter-cups_1.2-1_i386.deb
```

or just double click the deb files with your mouse that will invoke the Gdebi package installer to install the files.  

Then just install the printer normally using System > Administration > Printers (AKA system-config-printer) & hopefully you will be now be printing happily:)

Good luck please let me know how you get on

---

### Post by plusmore on 2007-11-14
That did the trick! Wonder what on earth is the difference between the source tarball and the rpm??? Thanks loads.

---

### Post by Marc Higgins on 2007-11-17
Glad to hear it worked for you

---

### Post by ae+ on 2007-11-28
Thanks for the post - very very useful
I'm been printerless since Dapper :)

To get it to work I had to also download the source tar.gz and use the pdd from in there.

Cheers

andrew

---

### Post by ItsManaged on 2007-12-12
Hi Marc,
Thanks for taking the time to document this for us!
> **Marc Higgins said:**
> http://qld.yi.org/it_i/epson-alc1100-filter_1.2-1_i386.deb[/url]
[http://qld.yi.org/it_i/epson-alc1100-filter-cups_1.2-1_i386.deb](http://qld.yi.org/it_i/epson-alc1100-filter-cups_1.2-1_i386.deb)

.....

OR 
I cannot get to the files - do you have another location for these?

> **Marc Higgins said:**
> 
OPTION B

you can make your own install files using Alien


OK, I installed alien, and downloaded the rpms, but I get a architecture error while using alien on my AMD64 machine (Gutsy);

> 
AMD64:~/Desktop$ sudo alien Epson-ALC1100-filter-1.2-0.i386.rpm 
Warning: Skipping conversion of scripts in package Epson-ALC1100-filter: postrm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/epson-alc1100-filter
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
[b]dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280[/b]

I see there is a bug (and a patch) at [https://bugs.launchpad.net/ubuntu/+source/gcc-4.1/+bug/121834](https://bugs.launchpad.net/ubuntu/+source/gcc-4.1/+bug/121834) 
however I'm not confident enough to try applying the patch (assuming I can find out somewhere what that entails), nor in backtracking in case things go pear shaped.

So, is there another way of setting this printer up you can suggest?
Cheers,
Thanks.

---

### Post by maka2007 on 2007-12-20
I have same problem. Can anyone please find (post) solution for AMD64?

Thanks

---

### Post by pihutch on 2007-12-23
Thank you, thank you, thank you!!  And I thought I'd tried everything....

My printer's now working, thanks again!

---

### Post by Marc Higgins on 2007-12-23
Sorry to ItsManaged & anyone else who has been trying to download the *.deb files. 

We are in the process of moving so our server has been offline. Unfortunately our up time will be patchy until mid Jan 08 when we (& our new connection) are in our new place. If the server is down please try again later.  

At any rate the server is back up at the moment

[COLOR="Sienna"][http://qld.yi.org/it_i/epson-alc1100-filter_1.2-1_i386.deb]("http://qld.yi.org/it_i/epson-alc1100-filter_1.2-1_i386.deb")
[http://qld.yi.org/it_i/epson-alc1100-filter-cups_1.2-1_i386.deb]("http://qld.yi.org/it_i/epson-alc1100-filter-cups_1.2-1_i386.deb")
[/COLOR]

Unfortunately I don't have a 64bit machine that I can play with. I know very little about 64bit architecture so I need someone else to help to try & work this out.

From what I have read it appears that alien doesn't work with 32 bit rpms on 64bit machines & you need to install a 32 bit alien, to convert the 32 bit rpms into 32 bit debs, then sudo dpkg --force-architecture -i 

Assuming that you had no errors when you did this ```
sudo aptitude install gcc-3.3-base libstdc++5
``` Install deb files from [www.qld.yi.org](www.qld.yi.org) but because these debs are built for x86 not the AMD 64bit you probably need to use the switch --force-architecture 
```

[I]dpkg --force-architecture -i epson-alc1100-filter_1.2-1_i386.deb 
``` 
```
dpkg --force-architecture -i epson-alc1100-filter-cups_1.2-1_i386.deb
```[/I]
Otherwise the rpms above were built on a 32bit redhat (or a derivative) from the source file Epson-ALC1100-filter-1.2.tar.gz available at the epson site [www.avasts.jp](www.avasts.jp) It stands to reason that if rpm's were built from source on a 64bit redhat (or a derivative) they MAY also work when converted.

This is probably the right way to approach  things but to do this though we need someone with a 64bit machine that is either already running redhat /CentOS or is prepared to install it & then build the 64bit rpms from the source.

This is a great howto on building rpms here

[http://www.tldp.org/HOWTO/RPM-HOWTO/build.html]("http://www.tldp.org/HOWTO/RPM-HOWTO/build.html")

---

### Post by maka2007 on 2007-12-24
Its working now. To be honest I don' know what did the job. I used force-architecture to install yours i386.deb files. Thank you for that (I'm new to linux, didn't know that). Than I restarted cups

```
sudo killall -HUP cupsd
sudo /etc/init.d/cupsys restart
```

and then I dowloaded new foomatic-rip and foomatic-gswrapper which created new foomatic-rip.1 and foomatic-gswrapper.1 files

```
cd /usr/bin
sudo wget http://www.linuxprinting.org/foomatic-rip
sudo wget http://www.linuxprinting.org/foomatic-gswrapper
sudo chmod 755 foomatic-rip.1 foomatic-gswrapper.1
sudo ln -s /usr/bin/foomatic-rip.1 /usr/lib/cups/filter/foomatic-rip.1
```

(done that because before in cups interface it said, next to printer name, foomatic-rip failed)

Used: 

[http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation]("http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation")

Than I added printer through cups and now its working.

Thanks for help :)

---

### Post by scotc on 2008-03-21
Note that there is a problem converting an .rpm to a .deb using alien if you are running a 64 bit system.

The link below shows the workaround

[http://www.csamuel.org/2007/11/29/installing-lacie-4l-lightscribe-software-on-amd64-ubuntudebian-systems]("http://www.csamuel.org/2007/11/29/installing-lacie-4l-lightscribe-software-on-amd64-ubuntudebian-systems")

Basically, you use alien to convert the rpm to a tar (.tgz), then from a .tgz to a .deb.

Then pick up the thread again.

---

### Post by eexcellent on 2008-07-10
Thanks Marc, the deb packages worked for me. I've been trying to share a c1100 connected to a windows machine for ages!!
Your the best=D>=D>=D>=D>

---

