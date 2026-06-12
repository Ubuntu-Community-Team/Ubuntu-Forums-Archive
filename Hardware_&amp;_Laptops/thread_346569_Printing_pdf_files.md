---
title: "Printing pdf files"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by apowell656 on 2007-01-25
I am trying to print pdf files to paper and my printer always stops. I am new to Linux,so any help would  be appreciated. 
- 6.06 LTS,  Cups 1.2.2 , Envice - directing the file to generic Post Script 
Regular files work 

Andre

---

### Post by K.Mandla on 2007-01-26
So are you converting the PostScript file to PDF and then trying to print it?

---

### Post by apowell656 on 2007-01-26
The files are native PDF , but I did try this option when printing directly to my PSC-1400 the printer always stops.

Andre

---

### Post by K.Mandla on 2007-01-26
Strange. Have you tried printing these PDFs on a different system? I'm wondering if the PDF is damaged at all. 

You could also install the Acrobat package and see if it works better. Maybe evince can't handle it.

```
sudo aptitude install acroread
```

---

### Post by apowell656 on 2007-01-26
I tried
```
sudo aptitude install acroread
```

here is the message that I got

```
ubuntu:~$ sudo aptitude install acroread
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "acroread"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```
I believe that I have all of the repositories available -- please remember I am a Newbie.

Andre

---

### Post by catsanddogs on 2007-01-26
I am having the same problem. I created a pdf file using my scanner. When I try to print it, the printer stops. The file size is 1.2 MB. I can print smaller pdf files. 50kB The os is 6.10

I found acroread in a google search. [www.adobe.com](www.adobe.com) offers their reader 8.0 in .tar.gz or .rpm but no .deb so I didn't try that. Has anyone installed one of these. I have only been using Ubuntu ( or any linux os) for 2 weeks and this I have yet to try 

So I also found acroread in the warty multiverse. it is 5.0

at the termial type

gksudo gedit /etc/apt/sources.list

in this file copy and paste:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

save the file and close the editor and at the terminal type

sudo aptitude update

From System>Administration>synaptic package manager
open package manager  
search  for acroread

mark for install
acroread
acroread-debian-files
acroread-plugin

then apply

This is as far as I got.  Do you know how to execute this program?

I tried sudo acroread
I tried usr/lib/acrobat5/bin/acroread.sh and double clicking
with no results

---

### Post by catsanddogs on 2007-01-26
There is more 

change
/usr/lib/Acrobat5/bin/acroread "$@"
to
/usr/lib/Acrobat5/bin/acroread.sh "$@"
in /usr/bin/acroread

and

install_dir=REPLACE_ME
to
install_dir=/usr/lib/Acrobat5/Reader
in /usr/lib/Acrobat5/bin/acroread.sh
 
to make these changes,  in the terminal type  gksudo gedit 
this opens the editor, then open each file to edit

to execute, type in terminal sudo acroread

It works!  I printed the  pdf I couldn't before

---

### Post by apowell656 on 2007-01-27
Okay that worked I  really appreciate the help, The Plan B of printing as an image from my Mac was not the one that I was looking for.

Thanks
Andre

---

### Post by laidback on 2007-01-28
I found that Acroread sorted my problems. Xpdf didn't allow me controlled printing, e.g. portrate to landscape. It's available from Synaptic, I have all the extra repositories active.

---

