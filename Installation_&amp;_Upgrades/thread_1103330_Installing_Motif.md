---
title: "Installing Motif"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by pheonixdragon on 2009-03-22
Hi,

Anyone tried to install Motif 2.1 and get a simple example to work?

---

### Post by snova on 2009-03-22
Installation should be as simple as installing the **libmotif-dev** package.

If you're having trouble getting an example to work, how are you trying to compile it and what errors are you getting?

Also, what are you trying to do with it?

---

### Post by pheonixdragon on 2009-03-23
> **snova said:**
> Installation should be as simple as installing the **libmotif-dev** package.

If you're having trouble getting an example to work, how are you trying to compile it and what errors are you getting?

Also, what are you trying to do with it?

I got the package from MotifZone
[http://www.motifzone.net/?gclid=CLXlxN6WspkCFYND3god0jfS5Q](http://www.motifzone.net/?gclid=CLXlxN6WspkCFYND3god0jfS5Q)

There is no installation guide as it different for different vendors. I got cc errors saying it couldn't find the include files and library especially X11/launch.h. I couldn't find launch.h anywhere in Ubuntu. 

This is my first stab at Motif using Knoppix that why I tried Ubuntu, the same problem.

Using python is easy in Ubuntu-Idle.

---

### Post by snova on 2009-03-23
> **pheonixdragon said:**
> I got the package from MotifZone
[http://www.motifzone.net/?gclid=CLXlxN6WspkCFYND3god0jfS5Q](http://www.motifzone.net/?gclid=CLXlxN6WspkCFYND3god0jfS5Q)

There is no installation guide as it different for different vendors. I got cc errors saying it couldn't find the include files and library especially X11/launch.h. I couldn't find launch.h anywhere in Ubuntu.

That's not quite what I meant. ;)

It's in the repositories, so open System -> Administration -> Synaptic, and search for and install 'libmotif-dev'.

---

### Post by sorginal on 2009-06-02
I installed open motif via alien;

> sudo apt-get install alien

download the rpm file from here : [http://rpmfind.net/linux/rpm2html/search.php?query=libXm.so.3](http://rpmfind.net/linux/rpm2html/search.php?query=libXm.so.3)

than 
> 
sudo alien --to-deb FileThatYouDownload.rpm

this will create the deb file you can double click and install it.

---

