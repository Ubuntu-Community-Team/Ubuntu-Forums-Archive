---
title: "Interest in IRDA Send/Receive GUI"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by Lil on 2007-08-25
Hello,

1. I wasn't sure where best to post this, but I guess here is good given that it seems to primarily involve the IRDA  interface (in my case my T40's built in IRDA) and my mobile phone (SE w810i).

2. I have googled and not found an exact 'front end' like my idea so I'm gonna step forward and try myself. Please inform me if something exists already...

Ok scenario:

I have a Philips Velo WinCE PDA which I use for tapping up notes etc. on the move, but most importantly a Sony Ericsson w810i mobile phone which I love. My T40 doesn't have Bluetooth (yet) so when I used Windows and I just wanted one photo, I would send it using IrDA. Job done.

I can now do the same having set up IrDA on my Ubuntu based T40 but it's all done on the CLI which is great, but maybe a GUI would be cool I thought.

I have plenty of programming experience from BASIC, to C, C++,Objective C, VB, ASP, PHP and a whole slew of other stuff, but mostly these days I deal with XHTML, XML, CSS and Javascript. I have taken a liking to Python and therefore PyGTK as I have never programmed for Linux before except for standard command line C based apps.

My only question is, would there be some interest for me to create a little app using Python and PyGTK bindings for the GUI (bear in mind I have no prior experience with Python by syntactically it makes sense to me so I'll be OK... <grin>) that will:

First, receive incoming files from IrDA asking for a destination folder easily.
Secondly, act as either a drag and drop window to send files or perhaps just a file selection dialog that will send the selected files.

How does this sound? :) If there's interest I'll give it a shot and try to do it! I would use existing command line stuff like irxfer etc.

Vicky

---

### Post by CyberCod on 2007-09-01
Sounds like it would be very handy to me!

---

### Post by Vadi on 2007-09-09
T40 here too, and there is definitely need for this.

I might be off your track here, but if you made it work with nautilus - so when it finds an irda device nearby, connects to it, nautilus mounts it in media, and then you can browse the folders on the connected device / transfer them back and forth, that'd be great.

I'll also be willing to help if you need anything :)

---

### Post by duncan.hawthorne on 2008-03-01
there exists one called ircp-tray that looks pretty cool
thanks to the thread [http://ubuntuforums.org/showthread.php?t=364678](http://ubuntuforums.org/showthread.php?t=364678) for letting me know of its existence, and helping me set up infrared
newer version here: [http://www.getdeb.net/app/Ircp-Tray](http://www.getdeb.net/app/Ircp-Tray)
hope this is useful to someone
the package gnome-vfs-obexftp says it supports infrared too but i cant get it to see my phone. Maybe you could put programming efforts into one of these?

---

### Post by dlazesz on 2008-05-20
Personally I prefer Ircp-Tray

But [http://www.getdeb.net/app/Ircp-Tray](http://www.getdeb.net/app/Ircp-Tray) says 
"No version available on this application which is compatible with your Ubuntu version."
(I'm usning hardy)

After googling a lot I've found [This link]("http://www.getdeb.net/download.php?release=953&fpos=0") that worked(don't khow how).

It's work fine under hardy.

I attach the file for sure.

---

### Post by roffik on 2008-07-11
You can obtain newest (0.7.2.1) version here:
[https://launchpad.net/~c-korn/+archive]("https://launchpad.net/~c-korn/+archive")
before it will be available on getdeb.net.

---

