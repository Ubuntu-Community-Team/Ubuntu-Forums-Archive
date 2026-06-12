---
title: "Installing a Canon MP190 in Ubuntu. Is it possible?"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by boredcollegekid on 2009-03-08
Recently bought one of these as it was cheap and I don't print all that often, few papers every now and then, and failed to adequately check if it would work in ubuntu](*,). 

I've googled around looking for an answer and find some stuff on [Openprinting]("http://www.openprinting.org/show_printer.cgi?recnum=Canon-Pixma_MP190") but it didn't seem to work at all.

I'd assume its a stupid mistake on my part as I've never messed around with installing printers in linux. Any help would be great :D

---

### Post by tweaksource on 2009-03-30
Here [http://software.canon-europe.com/products/0010639.asp](http://software.canon-europe.com/products/0010639.asp) are the drivers.

See also this thread [http://ubuntuforums.org/showthread.php?t=953292&highlight=canon+mp190](http://ubuntuforums.org/showthread.php?t=953292&highlight=canon+mp190).

Walk in Love.:P

---

### Post by shamelessnjc on 2009-05-20
The Canon Pixma MP180 driver will work in Ubuntu for printing but I'm having no luck with scanning, still working on it. The driver for the MP180 is in the database, you just have to add the printer and it will guide you through the steps.

---

### Post by Goddard on 2009-05-28
I got the MP190 software to install on my system, but it didn't enable me to use my printer.  I had to use the MP180 drivers as well.  Anyone got the MP190 drivers working from either the European site or the Australian site?

---

### Post by Goddard on 2009-05-28
Another thing I noticed is when you try and print through fire fox and it has a frame strange things happen and it wont print more then a page.  

Is this a Firefox problem? Driver problem? or Ubuntu problem? haha btw I am still using the MP180 drivers.

---

### Post by 37fleetwood on 2009-06-22
I found this to get Xsane working, it works with my Jaunty install 32 bit and a different scanner than referenced in the original post(I also have an MP190) so I'm guessing it's fairly universal as long as your scanner is listed in the backends:
(hope no one minds the quote)

[QUOTE=the_eternal_dark]Go [[COLOR="Red"]here[/COLOR]]("http://alioth.debian.org/scm/?group_id=30186") and pick up the Nightly CVS Snapshot, then get libusb-dev from synaptic if you don't already have it.

The easiest way, save it to your desktop and extract all contents, I have a folder called sane-scm-2009-01-24. Within this folder are multiple other folders, our focus is on "sane-backends".

Open terminal:

Code:

```
$ cd sane-backends
```

Then type:
Code:

```
$ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
```

Now you will have to wait a few moments. Once the wait is through, proceed with:

Code:

```
$ make
```

Wait again, this time for a bit longer, and when its done, run:

Code:

```
$ sudo make install
```

And you should be done, and when you run
Code:

```
$ scanimage -L
```

you should see your scanner listed and then you should be able to use xsane to scan all you could ever want in Ubuntu 8.10 64-bit. Now all we need is a .deb and this will be a walk in the park.[/QUOTE]

---

### Post by coldReactive on 2009-08-16
Doing all that make stuff made my head spin for a while.

sane now recognizes the device, but xsane gives an error:

failed to open device `pixma:04A91734`
Access to resource has been denied.

So now I MUST run xsane as root.

---

### Post by coldReactive on 2009-09-14
After doing those steps again now, the scanner can't be detected, seems to be a regression I can't debug.

D'oh, I forgot to install libusb-dev before ./configure and make.

---

### Post by Nemo_bis on 2010-11-23
I've installed the printer and scanner very easily on Ubuntu 10.10 Maverick Merkaat. 
Now  you can just download the debs from  [http://software.canon-europe.com/products/0010639.asp](http://software.canon-europe.com/products/0010639.asp) ->  [http://files.canon-europe.com/files/soft31326/software/MP190_debian_drivers.tar](http://files.canon-europe.com/files/soft31326/software/MP190_debian_drivers.tar)  .
You need to install the libcupsys transitional dummy package  [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.9_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.9_all.deb)  which I found in [http://security.ubuntu.com/ubuntu/pool/universe/c/cups](http://security.ubuntu.com/ubuntu/pool/universe/c/cups)  (as suggested elsewhere): then I just double clicked on cnijfilter-common_3.00-1_i386.deb,  cnijfilter-mp190series_3.00-1_i386.deb,  scangearmp-common_1.20-1_i386.deb and  scangearmp-mp190series_1.20-1_i386.deb in this order and connected the  printer, which was automatically recognized and added and works like a  charm.
Oh, I had installed Xsane before, I don't know if this matters.

Without  the dummy package, the deb gave me an "error which couldn't be  handled", I was offered to repair the database but that didn't work and  Ubuntu Software Center mentioned some possible cache problem, I tried  also ```
sudo apt-get -f install
``` but it didn't do anything.

---

### Post by cannuck1964 on 2011-07-11
I am trying to install the drivers for the mp190

using :

sudo dpkg -i cnijfilter-common_3.00-1_i386.deb



I get this error :


dpkg: error processing cnijfilter-common_3.00-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 cnijfilter-common_3.00-1_i386.deb


is there a way for me to install?  I remember I did this before, but then lost my set up in a computer crash (newbi time).

thanks

---

### Post by wolfcall on 2012-02-05
I am trying install a a canon MP190 we have the drives but no deb dummy library so it won't install. Similar error to the previous post.

---

### Post by Pizarro on 2012-02-20
[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

This worked for me.

---

