---
title: "Cannot install lsb on Lubuntu 16.04 to use Epson Printer XP-322"
date: 2016-04-23
forum: Hardware
---

### Post by Download_Descenden on 2016-04-23
Tried installing using [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install lsb and get error message -

 [/FONT][/COLOR]Package lsb is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'lsb' has no installation candidate

I assume the same issue will occur on Ubuntu but apologise if putting this in the wrong area.  Looking in Synaptic the lsb base and lsb release is in synaptic and is installed - 9.20160110

There was no problem in 14.04.

Using Epson XP-322 where lsb needs to be installed to use drivers.  From Epson site - [COLOR=#333333][FONT=Tahoma]In order to install these drivers, you need to install LSB package (version 3.2 or later) beforehand.[/FONT][/COLOR]

[COLOR=#333333][FONT=Tahoma]Ubunbu:[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]# apt-get install lsb

[/FONT][/COLOR]

---

### Post by dean-westray on 2016-04-23
I can confirm the issue here with my Ubuntu 16.04LTS install here.  When I've attempted to install both the "proprietary" Epson printer drivers and print utility, it throws up an unmet dependency error message regarding lsb.  I think this is because the numbering convention for the lsb version numbers have been changed in 16.04LTS.  So when you attempt to install the driver, it is looking for  v3.2, v4.1 for example.  It does not recognize the new version numbering convention (in this case 9.20160110).  Note also that the driver installer add entries into Software & Updates for Epson's own driver repositories.

The drivers held in Epson's own repositories will again look for lsb libraries that use the old X.Y convention when you try to install them and fail.   You can remove them by either disabling or removing the Epson lsb3.2 entries in Software & Updates then reloading or running sudo apt-get update again.

I was able to work around it and get my Epson XP-415 All-In-One printing  by installing "printer-driver-escpr" package from Canonical's own  repositories.  

Ideally the ball has to go back to Epson to repackage the drivers so they can properly detect the lsb libraries under the new version numbering convention in 16.04LTS.

As a side note the Iscan packages install OK without any issue either using the install.sh or installing manually in the order below.

```
sudo dpkg -i  iscan-data_1.36.0-1_all.deb
sudo dpkg -i iscan_2.30.1-1~usb0.1.ltdl7_amd64.deb*
sudo dpkg -i iscan-network-nt_1.1.1-1_amd64.deb**
```

*The 32 bit edition of the drivers end in "i386.deb".
** Only required if you plan to use over a wired/wireless network.  You will also need to append the file epkowa.conf  to add the IP address of your device.
     (see below)

```
sudo gedit /etc/sane.d/epkowa.conf
```

Look for the entries in the epkowa.conf file for marked  #net.  Then add a line underneath

```
net <device ip> 1865
```  (eg. net 192.168.2.25 1865)

Save the file and reboot.

---

### Post by Download_Descenden on 2016-04-23
Thanks for your reply.

I tried installing the [COLOR=#000000]"printer-driver-escpr" but could not get it to connect or add the printer via the Printer start menu.   It looks like the the XP series need the lsb.  Glad it worked for your printer

The numbering change makes sense.[/COLOR]

---

### Post by mickee384 on 2016-04-23
I have same issue with Ubuntu 16.04 with Epson XP-410 dependency cannot be met lsb (<=3.2)

---

### Post by dean-westray on 2016-04-23
Download_Desenden
Please can I just ask if your printer connected by USB direct to your PC, or wirelessly on your home wi-fi?  I can offer any further advice, I've had a couple of Epson AIOs running under Ubuntu for a few years now.

---

### Post by dean-westray on 2016-04-23
mickee384
Your best bet would to install the "printer-driver-escpr" package from Canonical's own repositories.  The proprietary blobs from Epson need to be repackaged so they can pick up the new version numbering convention.  

The Iscan packages should install OK.

---

### Post by Download_Descenden on 2016-04-24
It's connected via USB so it's not a connectivity issue - when I tried to connect it, it just said 'There was an error during the CUPS operation: 'failed to connect to server' as if no printer was connected.

I have a dual boot with Windows so it looks like sadly, I will have to boot it into that to do any printing.

 However [COLOR=#000000]"printer-driver-escpr" [/COLOR] did install unlike the driver from Epson's website which was met with the same error message as Mickee above when using Gdebi.

I imagine this is going to be a bit of an issue as there are a lot of these Epson printers around that won't now work.  It's frustrating because if 16.04 would just install lsb ( sudo apt get etc) , the Epson driver would almost certainly work.

Thanks

---

### Post by El Zoido on 2016-04-24
I've just ran into the same issue.
I'm using an Epson Stylus Office BX925, which should be compatible to the Workforce 840.
Installing the escpr package from the repos provided a working driver for basic printing, but that one isn't of much use to me - the functionality is severely limited and most options (duplex printing, changing the paper cassette, etc.) are not available to me.
Up until 15.10, I could use the driver from Epson directly, which provided the missing features.

I would be very grateful for some ideas on what to do to either restore the missing features, or circumvent the lsb issue.

Otherwise, I guess the only hope is updated drivers from Epson themselves?

---

### Post by Download_Descenden on 2016-04-24
Just to confirm the scanner drivers work fine, so it's just the printer drivers that won't install because of not being able to install lsb.

So far, it appears that the escpr driver gives some functionality for some Epson printers, but for others it does nothing without lsb, and this does not install on 16.04.

---

### Post by amalgamas on 2016-04-26
I can confirm the issue with my expensive and nice-printing Epson Stylus Photo 1500W.  Is there nobody that can help with solving, or at least, circumventing this problem?  Is there any hope that Epson or whomever will repackage the drivers anytime soon?

In the meantime I may have to go and buy a cheap printer

---

### Post by Download_Descenden on 2016-04-26
Yes, it seems to be an issue with Epson printers and 16.04.

A thread has been started about it on General Help as well which may be related.

[http://ubuntuforums.org/showthread.php?t=2322155](http://ubuntuforums.org/showthread.php?t=2322155)

I wonder if the developers and Epson know about it?

---

### Post by munchies2 on 2016-04-27
Yep, the above thread link is what I created. I am trying to install the drivers for the Epson NX430, same issues exactly as everyone else in Ubuntu Mate 16.04.

---

### Post by El Zoido on 2016-04-27
I've send a support request to Epson, asking whether there's any chance for updated drivers from them.
The lates esc/p-r driver is from April (but still requires lsb3.2), so it might happen that we see updates with different lsb requirements.
However, I need the non-r version to get support for duplex and such back.
Given that my printer is already 4 years old (and the model even older), it might of course be that they simply dismiss this with the advice to buy a newer model.
On the other hand, it seems this issue might affect newer printers as well.

---

### Post by El Zoido on 2016-04-28
Ok, I received a first answer from Epson support, but it's not exactly inspiring hope.

Basically they just send out a copy-and-paste mail about how Linux is not supported (despite them offering drivers for it on their official sites...) and a couple of links to the (outdated) drivers themselves.
I send them an (polite, don't worry) response asking again for some actual answer to my question, but I wouldn't hold my breath for new drivers from Epson yet.

As an alternative, I wonder if it would be possible to download .deb files of lsb from older versions and install it in Xenial.
I'm hesitant to try it however, since they are depending on each other and I don't know how they work together with the newer packages in Xenial.

---

### Post by Linuxisfast on 2016-04-29
Same issue here, can't install L800 drivers due to lack of lsb.

---

### Post by aljosa2 on 2016-04-29
I have the same problem too (Ubuntu 16.04)... a few days ago I bought new Epson L365 all-in-one printer, both printer and scanner driver doesn't work :(
except the package 'lsb' issue, while trying to install 'deb' driver via software-center, another problem occurs: "GNOME Software does not install third-party .deb packages" [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573206](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573206)

---

### Post by El Zoido on 2016-04-29
> **aljosa2 said:**
> I have the same problem too (Ubuntu 16.04)... a few days ago I bought new Epson L365 all-in-one printer, both printer and scanner driver doesn't work :(
except the package 'lsb' issue, while trying to install 'deb' driver via software-center, another problem occurs: "GNOME Software does not install third-party .deb packages" [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573206](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573206)

You could try installing it with e.g. gdebi or via dpkg in the console.

Of course, if it requires lsb, it still won't help you much.

By the way, I've received another answer from Epson support. Allegedly, no updates are planned, but I suspect that the person behind the mails wasn't exactly very knowledgeable regarding linux and the linux plans of Epson.

---

### Post by munchies2 on 2016-04-30
Thanks for taking the initiative to do that! I guess we will see what happens....

---

### Post by aljosa2 on 2016-04-30
Hi all, what do you think about this as a possible solution for 'lsb' installing problem:

*Install Google Earth on Ubuntu 16.04*
*My system is 64 bit Ubuntu 16.04. The big problem is Ubuntu missing all the “lsb-*” packages which Google Earth depend on. After few hours try-and-fail, finally I have...*
*[http://blog.pztop.com/2016/04/28/Install-Google-Earth-on-Ubuntu-16-04/](http://blog.pztop.com/2016/04/28/Install-Google-Earth-on-Ubuntu-16-04/)*

---

### Post by Download_Descenden on 2016-04-30
I tried something like this from another post last week with no luck.  But it looks a little different so I will give it a go again.

What I have been doing prior to this, is installing Timeshift which is a System Restore utility which you get in Windows but for Linux.  I've used it on Lubntu and Linux Mint and it's never failed me yet.  Do and backup, make the changes and if no luck, restore.  It's saved me a few times when installing unfamiliar software and making changes etc.

Details and ppa here.  

[http://www.teejeetech.in/p/timeshift.html](http://www.teejeetech.in/p/timeshift.html)

---

### Post by Download_Descenden on 2016-04-30
> **aljosa2 said:**
> Hi all, what do you think about this as a possible solution for 'lsb' installing problem:

*Install Google Earth on Ubuntu 16.04*
*My system is 64 bit Ubuntu 16.04. The big problem is Ubuntu missing all the “lsb-*” packages which Google Earth depend on. After few hours try-and-fail, finally I have...*
*[http://blog.pztop.com/2016/04/28/Install-Google-Earth-on-Ubuntu-16-04/](http://blog.pztop.com/2016/04/28/Install-Google-Earth-on-Ubuntu-16-04/)*


Followed the instructions, but got the same lib error when trying to install file.  So didn't work for me.

---

### Post by peter246 on 2016-05-12
Spent the last 20 mins having the same problem with epson escpr driver from the epson site.
Trying to install for an Epson XP-322 on Ubuntu Xenial 16.04.

Firstly, I tried installing lsb to no avail

```
sudo apt-get install printer-driver-escpr


Reading package lists... Done
Building dependency tree       
Reading state information... Done
printer-driver-escpr is already the newest version (1.6.3-2).
The following packages were automatically installed and are no longer required:
  alien at debugedit lib32z1 libc6-i386 librpmbuild3 librpmsign3 ncurses-term pax rpm
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 43 not upgraded.
deirdre@Einstein:~/Downloads$ sudo apt-get install lsb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lsb is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'lsb' has no installation candidate

```


Tried installing the driver anyway, but alas, Epson weren't lying. They do need lsb.

```
sudo dpkg -i epson-inkjet-printer-escpr_1.6.5-1lsb3.2_amd64.deb
(Reading database ... 227435 files and directories currently installed.)
Preparing to unpack .../epson-inkjet-printer-escpr_1.6.5-1lsb3.2_amd64.deb ...
Unpacking epson-inkjet-printer-escpr (1.6.5-1lsb3.2) over (1.6.5-1lsb3.2) ...
dpkg: dependency problems prevent configuration of epson-inkjet-printer-escpr:
 epson-inkjet-printer-escpr depends on lsb (>= 3.2); however:
  Package lsb is not installed.


dpkg: error processing package epson-inkjet-printer-escpr (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 epson-inkjet-printer-escpr
```


but good ould apt did the job

```
sudo apt install printer-driver-escpr
```


tis printing now at least :D

---

### Post by cressrt2 on 2016-05-20
I've been trying all morning to get my XP-322 printer working without any success, found this thread and now it's working!
Thanks!

---

### Post by Mark Phelps on 2016-05-20
Hey folks, I found this thread on the bugs launchpad and post #34 has a short-term workaround that apparently works:  [https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1536353]("https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1536353")

Good Luck

---

### Post by Linuxisfast on 2016-05-20
> **Mark Phelps said:**
> Hey folks, I found this thread on the bugs launchpad and post #34 has a short-term workaround that apparently works:  [https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1536353](https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1536353)

Good Luck


Yep thats what I did, just have to make sure to remove the Trusty repo once lsb is installed.

---

### Post by Download_Descenden on 2016-05-28
I didn't realise that Lubuntu does not install CUPS on 16.04 where it did on my previous Lubuntu 14.04.   ](*,)

So I installed CUPS -[COLOR=#000000][FONT=Verdana]"sudo apt install cups"[/FONT][/COLOR] - and was able to install the printer-driver-escpr via Synaptic Package Manager and, after restarting the computer XP-322  basically works without installing lsb.

---

### Post by El Zoido on 2016-06-02
Installing printer-driver-escpr from the repos is a working solution for some users, sadly not for me.
The functionality provided by this driver is so barebones for my printer that I can do only basic printing jobs.
However, I also need access to duplex, additional paper cartridges, scaling options, etc. 
None of this is working for me currently...

Might check out the workaround linked above.

---

