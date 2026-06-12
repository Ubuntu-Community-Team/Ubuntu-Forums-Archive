---
title: "Citrix ICA client"
date: 2008-07-29
forum: General Help
---

### Post by mavrick13927 on 2008-07-29
I just switched to Kubuntu from WinXP last week, and am still a novice to Linux admin so please go easy on me.

I am using Kubuntu 8.04 for AMD 64
My system is an Acer Aspire T160
     AMD Athlon 64 3400
     2 GB RAM
     200 GB SATA drive

What I am attempting to do is install the Citrix client so I can work from home.  I have the following installed via the Synaptic Package Manager:
libmotif3
firefox-3.0
java-common
sun-java6-bin
sun-java6-jre

From the Citrix Linux client download site:
[http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323&productID=-1](http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323&productID=-1)

I downloaded version 10.6 of the x86 client as a .tar.gz

I extracted the files, opened Konsole as root and ran the script setupwfc.  During setup, I accepted the default install location and allowed integration with KDE/Gnome.  When I try to open the Citrix Presentation Server, I get the busy hourglass cursor for a while, then it disappears and no application starts.  

I entered the following command at the command line:
/usr/lib/ICAClient/wfcmgr &
Which resulted in:
/usr/lib/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.3: wrong ELF class: ELFCLASS64

I also tried the web interface for work.  I can log in, but when I try to use one of the applications, a separate window appears.  Eventually, I get a message that says "Start: applet not initialized".

Doing some reading on-line and in the forums, I found this:
[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

So I tried placing the symlinks:
ln -s /usr/lib/ICAClient/wfica /usr/local/bin/wfica
ln -s /usr/lib/ICAClient/wfcmgr /usr/local/bin/wfcmgr

Same results.  When I try to open the Citrix Presentation Server, i get the busy hourglass cursor for a while, then it disapears and no application starts. 

I then found this little write up (See the 2nd article):
[http://www.tuxgurl.blogspot.com/](http://www.tuxgurl.blogspot.com/)

So I also added the following softlink:
ln -s /usr/lib/libXm.so.3 /usr/lib32/libXm.so.3

Same results.

I then came across another tutorial on the forum which seemed promising:
[http://ubuntuforums.org/showthread.php?t=768297&highlight=CITRIX](http://ubuntuforums.org/showthread.php?t=768297&highlight=CITRIX)

From this I added the following symlink:
ln -s /usr/lib/ICAClient/npica.so npica.so

Same results.

I've been working on this all day and have no idea what my next step should be.  I really need to get this working ASAP.  Any help or advise would be greatly appreciated.  Thank you.

---

### Post by fbristow on 2008-09-17
Hi there,
The reason that this is occurring is that the ICA Client is an x86 binary and not an x86_64 binary, so it's looking for x86 libraries.  The open motif libraries that you installed with synaptic are x86_64 libraries and cannot be used with this client.
What you will need to do is download the x86 version of this package from here:
[http://packages.ubuntu.com/hardy/libmotif3](http://packages.ubuntu.com/hardy/libmotif3)
selecting the i386 version.  Of course, if you're using something other than the hardy version, choose the appropriate package.

When you've downloaded the package, whip open your terminal and navigate to where the file was saved, then do:

```
sudo dpkg -i --force-architecture libmotif*i386.deb
```

This tells dpkg that yes, in spite of this being the wrong type of architecture for my computer, I do indeed want to use this package.

Hopefully this is helpful to you!

---

### Post by yn0t on 2008-11-05
fbristow,  Thank you!  Perfect!  I did everything that mavrick13927 did and was about to call it quits.

To help the search engines:
I am running Ubuntu 8.10 Intrepid x64 64-bit
and installed Citrix 10.6 Client

---

### Post by bluntknife on 2009-01-23
Thank you. This sorted my Citrix client version 10.6 issue out too.

---

### Post by mavrick13927 on 2009-03-07
Thank you fbristow for the reply.  I ended up having too many x64 issues and switched to the 32 bit version of Kubuntu instead.  I do appreciate your reply.  Thanks again.

---

### Post by Suparious on 2010-12-06
Thank-you for this solution.

I am using 10.10 Maverick 64bit, 

I followed this post:
[https://help.ubuntu.com/community/CitrixICAClientHowTo]("https://help.ubuntu.com/community/CitrixICAClientHowTo")
and the ```
sudo dpkg -i --force-architecture libmotif*i386.deb
``` was the solution.

---

