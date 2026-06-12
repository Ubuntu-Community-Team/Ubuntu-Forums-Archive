---
title: "Gzip problem"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by mjleedam on 2009-04-03
Hi,

I am a complete newbie to linux so please bear with me.

I am trying to install my maudio midisport 4x4 interface.

I have found instructions on one of the threads and when I get to the unzip part I get an error message telling me that the file is not in gzip format:

matt@MES:/tmp$ tar xvzf usbmidi-20040829.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
matt@MES:/tmp$ 

Any help would be greatly appreciated.

Matt

---

### Post by taurus on 2009-04-03
What's the output of this command?

```
file usbmidi-20040829.tar.gz
```

---

### Post by mjleedam on 2009-04-03
The output is: 

matt@MES:/tmp$ file usbmidi-20040829.tar.gz
usbmidi-20040829.tar.gz: ASCII text

---

### Post by taurus on 2009-04-03
It's a text file.  Where did you download it?

---

### Post by mjleedam on 2009-04-03
This is the link for the instructions:

[http://ubuntuforums.org/showpost.php?p=6224184&postcount=60](http://ubuntuforums.org/showpost.php?p=6224184&postcount=60)

The location as specified in those instruction is:

[http://homepage3.nifty.com/StudioBreeze/software/bin/usbmidi-20040829.tar.gz](http://homepage3.nifty.com/StudioBreeze/software/bin/usbmidi-20040829.tar.gz)

---

### Post by taurus on 2009-04-03
You may want to try to download it again because here is what I got after I downloaded it.

```
$ file usbmidi-20040829.tar.gz 
usbmidi-20040829.tar.gz: gzip compressed data, from Unix, last modified: Sat Aug 28 23:47:51 2004
```
So I unpacked it with

```
tar xvzf usbmidi-20040829.tar.gz
cd usbmidi-20040829
ls -la
```
and here's the output.

```

drwxr-xr-x 3 taurus taurus  4096 2004-08-28 23:47 .
drwxr-xr-x 3 taurus taurus  4096 2009-04-03 13:58 ..
-rw-r--r-- 1 taurus taurus  6735 2004-08-28 23:45 ChangeLog
-rw-r--r-- 1 taurus taurus  2440 2002-09-23 03:40 Makefile
-rw-r--r-- 1 taurus taurus 10786 2001-12-11 10:05 Makefile.RedHat
-rw-r--r-- 1 taurus taurus  2538 2004-06-25 10:12 Makefile.zaurus
-rw-r--r-- 1 taurus taurus  3142 2004-05-16 00:35 README
drwxr-xr-x 3 taurus taurus  4096 2002-01-20 08:01 testing
-rw-r--r-- 1 taurus taurus 56617 2004-08-28 23:44 usb-midi.c
-rw-r--r-- 1 taurus taurus  5835 2004-05-16 00:35 usb-midi.h

```

---

### Post by mjleedam on 2009-04-03
Thanks.

Will give it a try.

---

### Post by mjleedam on 2009-04-03
Don´t understand this one.

It still comes back as an ASCII file.

Any ideas?

---

### Post by oldos2er on 2009-04-03
How are you downloading it?

---

### Post by taurus on 2009-04-03
Try downloading it from a terminal.

Applications -> Accessories -> Terminal
```
wget -c http://homepage3.nifty.com/StudioBreeze/software/bin/usbmidi-20040829.tar.gz
tar xvzf usbmidi-20040829.tar.gz
cd usbmidi-20040829
```

---

### Post by mjleedam on 2009-04-03
I had been using the command terminal originally.

I have just tried the command with the -c extension and got this:

matt@MES:/tmp$ file usbmidi-20040829.tar.gz
usbmidi-20040829.tar.gz: data
matt@MES:/tmp$ tar xvzf usbmidi-20040829.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

For some reason it does not want to download as a zip file!?????

Out of interest, I have just downloaded another .gz file from sourceforge.net and that extracted fine.

---

### Post by mjleedam on 2009-04-03
Thanks for your help so far.

I have managed to get the midi interface working by using a different firmware download. 

However, when I unplug and reconnect the device it isn´t recognised automatically and, of course, it is reassigned different bus and device numbers.

There are instructions here [http://ubuntuforums.org/showpost.php?p=4007105&postcount=37](http://ubuntuforums.org/showpost.php?p=4007105&postcount=37) for creating a hotplug, but I don´t know how to adapt these for my situation.

The interface firmware MidiSport4x4.ihx is in /etc/firmware.

What is the best way to go about this?

Thanks in advance.

---

### Post by mjleedam on 2009-04-03
With a little trial and error, I think I have solved my problem.

Thanks for your help.

:p

---

