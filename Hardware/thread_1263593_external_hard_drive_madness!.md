---
title: "external hard drive madness!"
date: 2009-09-11
forum: Hardware
---

### Post by goseph on 2009-09-11
Hey everyone,

I have a fine external hard drive from memorex and it used to work fine on windows and ubuntu alike! I would just plug it in and drag and drop my files.

I don't know what I did.. I think I might possibley have started formating it for a couple of seconds and then cancelled, it was a month ago or so.

Anyway it is no longer recognised as mountable media although it is recognised by gparted. Is there an appropriate tool for windows or Ubuntu that can rescue all my prescious data and is there a way to fix the hard drive. Would formatting as NTFS fix it?

tl;dr: How can I recover my data from my unmountable external HD

---

### Post by ottosykora on 2009-09-11
>I have a fine external hard drive from memorex and it used to work fine >on windows and ubuntu alike! I would just plug it in and drag and drop my files.

I don't know what I did.. I think I might possibley have started formating it for a couple of seconds and then cancelled, it was a month ago or so.<

By that, you definitely deleted the partiton table and more on the disk.


 >Anyway it is no longer recognised as mountable media although it is recognised by gparted. Is there an appropriate tool for windows or Ubuntu that can rescue all my prescious data and is there a way to fix the hard drive. Would formatting as NTFS fix it?<

non of it really
however, you should now not use the disk at all and get from net copy of parted magic CD iso. You might be now looking for programm on it called test disk.
I am not sure if this is also included on the more simpler gparted CD, but it is definitely on the parted magic CD which also contains gparted.

The tool test disk is not so clear to use it, you may well better call someone to assit you with that. I managed in past to recover lost partiton tables. It just tries to analyze the disk and will try to create some kind of partition on it which it belives it could fit the original.

Any sort of formating or use from now on will destroy more and more data on it. So boot from the parted magic CD and head for the test disk and see if some partiton table can be recreated.

If it is only about rescuing some data, then some tools from company called ontrack could help, yes they have some free tools too. But I somehow doubt that their free tools will work via usb bus driver.

If the data are very valuable, then send the disk to ontrack or similar company and they will recover most of it for you, well some $$$ to be kept ready...

---

### Post by ahbart on 2009-09-11
Because it is an external drive and it can not be mounted. I assume that you do not have to boot from an external cd to try to fix it.
Testdisk is in the ubuntu repository. So you can install it with synaptic or:
```
sudo apt-get install testdisk
```
It is possible to rescue at least the partition table and maybe with that some files. 
There are other tools that can do the job. I've used commercial stellar phoenix in the past. That worked fine, but I assume there are lots more tools nowadays.

---

