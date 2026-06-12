---
title: "HOWTO: Canon PIXMA MP600"
date: 2008-07-31
forum: Hardware
---

### Post by easy_target on 2008-07-31
Here are the instructions from [URL="http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html"]this page
[/URL]
Packages can be obtained [here]("http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP600%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&")

> First, you must install the alien utility. From a terminal:
$ sudo apt-get install alien

Then convert the 2 .rpm packages into .deb packages:
$ sudo alien -i --scripts cnijfilter-common-*.rpm cnijfilter-mp600-*.rpm

Install also some additional packages (here for Ubuntu Feisty. On Gutsy, libpng3 becomes libpng12-0, and libtiff3 becomes libtiff4):
$ sudo apt-get install libpng3 libtiff3

Then create a necessary links:
$ sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
$ sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.3

And restart cups:
$ sudo /etc/init.d/cupsys restart

These worked for me. Results may vary.

---

### Post by c-m on 2008-09-10
Doesn't work

```

carl@carl-desktop:~$ sudo apt-get install libpng3 libtiff3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libtiff3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libtiff3 has no installation candidate

```

---

### Post by onurvatandas on 2008-11-30
I am using MP500 driver and it works fine. Try it.

---

### Post by rich1939 on 2008-11-30
I'm using a Canon PIXMA MP610 with Intrepid over my wireless network and it installed just fine. The print server runs Windoze XP, but that didn't seem to bother Intrepid.

Seems like the necessary drivers were readily accessible with this version of the OS.

I haven't tried connecting the printer directly to the USB port on my laptop, however.

Hope you find the answer to your problem.

---

### Post by lscrutton on 2008-12-07
I have tried several of the drivers:

1) the MP600 driver, which is hidden in the list doesn't work at all;
2) the BJC600 driver works but shrinks the printout to A5;
3) the MP500 has printed text and tables and is OK so far. 

Does anyone know if it is possible to get the scanner working?

---

### Post by 5daniil5 on 2009-02-25
I HAVE FOUND THE WONDER SOLUTION FOR THE MP600 PRINTER DRIVER TROUBLE IN UBUNTU 8.10!!! \\:D/  !!! 


Intro: I did every step described here and elsewhere,... and everywhere! ](*,) 
And it did not help.  :sad:  
Then, after a full day of script-wrestling, I had and idea  :idea:  ... 


Development: I've unpacked all the Australians archives, made a search for "MP600.ppd" and the result was: !"canonmp600.ppd"! I did include that file in that post! ;)

Solution!: 
...
  ... 
    :biggrin: "main menu" --->  "System" ---> "Administration" ---> "Printing" 

In the Printer Proprieties window, choose: Settings ---> Make and Model ---> Change ---> Provide PPD file 
And select the "canonmp600.ppd". 

8)

---

### Post by Roboload on 2009-03-11
> **5daniil5 said:**
> I HAVE FOUND THE WONDER SOLUTION FOR THE MP600 PRINTER DRIVER TROUBLE IN UBUNTU 8.10!!! \\:D/  !!! 



Thanx 5daniil5!
I've been trying to install mp600 already for maybe 6 hours on my ubuntu intrepid.. tried all advices could find in posts. Every time with same result: did not print, or printed not the way it should. And suddenly, it started working properly, right after installing the ppd you posted ;)

---

### Post by Roboload on 2009-03-11
After I've got working mp600 with ppd file mentioned above, I folowed update instructions at

[http://mp610.blogspot.com/2007/11/new-ppd-files-providing-more-printing.html](http://mp610.blogspot.com/2007/11/new-ppd-files-providing-more-printing.html)

and got mp600 printing even with 2400 dpi resolution :)

Maybe should mention, that original driver installation instructions from the same site did not work for me, until I have used 5daniil5's ppd file.

---

### Post by akoblentz on 2009-03-24
Has anyone gotten this to work in Intrepid?  Supposedly you now have to use the canon 3.0 drivers, they have an "_" in the device name that cups won't allow anymore.  I can't get the 3.0 drivers to install without requiring libcupsys2, and that doesn't work.

---

### Post by lykwydchykyn on 2009-03-25
I have the MP620 working with my debian server running etch, it serves out to all my ubuntu clients.  I have the scanner working as well with saned.  If memory serves, I had to:
 - install the cnijfilter-common and cnijfilter-mp610series from rpm with alien
 - install a ppd file for the 610 through the cups wizard.
 - fiddle with cups a bunch because things kept locking up
 - For scanning, had to compile sane-backends from svn.  Nobody has an up-to-date enough version.

It was quite a project, I'm afraid it was a little too helter skelter for me to do a howto, but the instructions posted by the OP were mostly what I followed.

But that was on etch, haven't tried directly with intrepid.

---

### Post by veritas20 on 2009-06-24
followed these instructions and tried several others, but still no beans fo 9.04

---

### Post by ShaneL on 2010-05-20
Just an update on this for Ubuntu Hardy with CUPS 1.3.7, as per standard setup mid-2010 (i.e. updated via synaptic etc)

The 'wonder solution' above got me in the right direction - more info and my detailed approach to solving it (not quite plagiarism, more a review heh) on the thread at 
[http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html](http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html)

From there you'll see I made use of a second thread on that site for an 'improved' ppd file too. which is what the 'wonder solution' above references.
[http://mp610.blogspot.com/2007/11/new-ppd-files-providing-more-printing.html](http://mp610.blogspot.com/2007/11/new-ppd-files-providing-more-printing.html)

I found some issues of previous posts here and elsewhere have been resolved with recent updates to hardy, cups, and/or the canon drivers, so just bear that in mind. (e.g. canon-common driver ver 3.0 gets around the 'cups and underscore' issue of ver 2.7)

also another site that gave some insight to the issue but may not have been directly a problem for me (but may help others):
[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/472468](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/472468)
this may be more related to network printing and/or server setup as the issue popped up a couple of times in that vein of discussion.

Now, to get a well deserved sleep, for tomorrow i stock up on ink and get printing!:guitar:

---

