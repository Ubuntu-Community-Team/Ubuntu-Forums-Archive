---
title: "Problem with ufraw"
date: 2008-08-14
forum: General Help
---

### Post by _sAm_ on 2008-08-14
I want to convert some NEF(raw) files from a Nikon D70 on Ubuntu, with ufraw. Every time I open a NEF picture the program close it self. The terminal is saying: "Segmentation fault". 

Something I can do?

I have removed ufraw and installed it again, but same thing happens. I have also build ufraw from a tarball I got from ufraw homepage, but with the same result. 

I am running Ubuntu 8.04.

---

### Post by alexvorn2 on 2008-08-14
Try to change your converter program.

---

### Post by _sAm_ on 2008-08-14
I really don't want to change it since I got the best results with it(it worked under Ubuntu 7.10).

---

### Post by sillyxone on 2008-08-14
I've been using ufraw from Feisty, and now Gutsy for my D40 NEFs, no problem so far. Could it be the dependence library? are you running 32 or 64 bit version? 

Can you try it from LiveCD or a different computer with the same NEF files? Just want to figure out what might be the cause.

---

### Post by _sAm_ on 2008-08-14
I am using Ubuntu 32 bits(Linux ubuntu 2.6.24-19-server)


I tried to convert the same NEF files on a second Ubuntu pc in the house with ufraw - and without any problems(but this is an old pc that I cant really use for this stuff).

---

### Post by sillyxone on 2008-08-14
so it's just that computer ...

try to remove ufraw completely from Synaptic and install again (not likely to solve the problem).

also, install gimp-ufraw plugin and see if you can open the NEF with GIMP

How about ufraw-batch, does it work OK (I guess not)? Can you try something line this in the terminal (with your NEF file) and see if it'll give the same error:

```

ufraw-batch  --wb=camera --exposure=1 --out-type=tiff8 --output=sample.tiff sample.NEF

```

---

### Post by _sAm_ on 2008-08-14
I removed it with sudo apt-get --purge autoremove ufraw and installed it again but got the same error. I downloaded the lastest from the homepage and(thanks to the guide) I build and installed it. Same error. 

The gimp-ufraw plugin dos not work, see image.

ufraw-batch on the other hand did work just fine(?)(but I really want the gui here).

---

### Post by _sAm_ on 2008-08-16
Still hoping for some help:-)

---

### Post by kelsey.chris on 2008-09-29
I had this same problem, and tried the complete removal and installation with no luck. 
  Deleting the .ufrawrc file from my home folder got it working again.
  Somehow I must have set it up with a configuration that made it trip.
  Lesson learned:  Complete removal and re-installation does not remove the pesky config file that is causing the trouble.
  Chances are, I'll get it to break again, and this time I'll post the problem config file here and at the developer's site.
  I really like ufraw!  Even with the quibbles, it is a great program.

---

### Post by allankelly on 2012-03-23
Hi, several years later (!) I had the same problem. By running ufraw-batch I could see that it was failing to load an OutputProfile that is specified in ~/.ufrawrc - for some reason, ufraw-batch survives that but ufraw GUI seg faults.

I removed that section from the .ufrawrc file (It's an XML format) and all's well.

Cheers, al.

---

