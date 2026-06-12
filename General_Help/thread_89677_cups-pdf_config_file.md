---
title: "cups-pdf config file"
date: 2005-11-13
forum: General Help
---

### Post by hazza96 on 2005-11-13
I have installed the cups-pdf package and configured a printer using the HP ColourLaserJet 5M drivers. I can send it a test page or anything else and it creates a PDF for me in $HOME. Now I want to make it create the PDF's in a sub-directory of home.

First let me explain why, my server is a samba and IMAP server. The IMAP folder is ~/Maildir and if I let the users map their H drive to home instead of ~/samba/ they end up deleting the "directory with heaps of files I can't open".

Now this presents a problem when they use the PDF printer because they can't see the PDF's created in their home dir.

When the cups-pdf package is intalled it does not include a "cups-pdf.conf", so I created one in the /etc/cups directory. I don't know how the developers compiled the cups-pdf package but it seems to ignore all the settings I place in there.

I have the following settings in my /etc/cups/cups-pdf.conf file:
> 
### Key: Out
##  CUPS-PDF output directory 
##  special qualifier: $HOME will set output directory dynamically
##         to the user's home directory (also true for an anonymous 
##          user - make sure the home directory exists and is accessible!)
##  in case it is an NFS export make sure it is exported without
##  root_squash! 
### Default: /var/spool/cups-pdf

Out $HOME

### Key: HomeSub
##  CUPS-PDF subdirectory for output in a user's home directory
##  only required if Out is set to $HOME 
##  can be empty or a single RELATIVE directory name
### Default: cups-pdf

HomeSub samba

I have even created a symbolic link in /etc to the cups-pdf.conf in case it wants to read it from there instead of the cups dir.

Does anyone know how to get cups-pdf to put the output in a subdir of $HOME on Ubuntu?

---

### Post by hazza96 on 2005-11-14
Please don't tell me I have to download the source and compile it myself just to get it to work properly.......

Maybe I should just go back to the printpdf script I had before that uses ps2pdf....

---

### Post by hazza96 on 2005-11-14
Well I found a half-arsed answer. I downloaded the Debian package from the [Debian repo]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fc%2Fcups-pdf%2Fcups-pdf_1.7.3-7_i386.deb&md5sum=10fd1e00551c6d9e81634ca7b89f3aaa&arch=i386&type=main") and installed it.

It's output is hardcoded to ~/PDF/ (yes their package is compiled to ignore the cups-pdf.conf as well) To get around this stuffup I created a symbolic link to ~/samba/ and it puts the PDF output in their H drive.

I guess you could create that symbolic link to point to anywhere (eg. /home/shared/pdf_docs) but if you want to change the location it would be a right pain in the rear to have to change every single users symbolic link than one config file.

---

### Post by hazza96 on 2005-11-14
Ahhhhhhhhhh....... the things you notice when you read everything.

I read the cups-pdf web site to find out about how to configure it and that is where I learnt about the cups-pdf.conf, so I copied and pasted their sample, seems simple enough and you would expect it to work.

When I looked closer I noticed this:
> Version history:
cups-pdf.c :

    * 2005-10-23 : 2.0beta2
       - added support for post-processing script
       - fixed a bug when parsing cups-pdf.conf

    * 2005-09-18 : 2.0beta1 (SRPM)
       - added support for runtime configuration
       **- introduced cups-pdf.conf**
       - made AnonDirName an abolute path

So the Ubuntu package is currently at version 1.7.1-1 and the Debian package is at 1.7.3-7 and the conf file was not introducted until the 2.0beta1.

---

### Post by ka1axy on 2006-02-20
I tried a bunch of things, and what finally worked, was to change a line in /etc/cupsd.conf:

RunAsUser No

and to install a copy of cups-pdf.conf from [http://cip.physik.uni-wuerzburg.de/~vrbehr/cups-pdf](http://cip.physik.uni-wuerzburg.de/~vrbehr/cups-pdf), and changing the line:

#Out /var/spool/cups-pdf/${USER}
Out $HOME/temp

These two changes allowed me to print.  I have the Generic/Postscript printer configured to use the "detected printer/PDF Printer" in the System/Administration/Printing menu.
("use another printer by specifying a port"/Virtual PDF Printer
option did not work for me)

I'm now printing from Firefox, and the output is going to the "temp" subdirectory of my home directory.

This is with Ubuntu 5.10 and all the latest updates.

Peter

---

### Post by ka1axy on 2006-02-20
...it turns out (I swear they were in the "temp" directory) that the created PDF files go to my "home" directoy.  

Apparently the previous poster is correct...the "cups-pdf.conf" file is a no-op for the Ubuntu version of cups-pdf.

However, the "RunAsUser No" fix did let me create PDFs, so I consider it worth doing.
And at least some graphics are being rendered.

Peter

---

### Post by B7may on 2006-03-12
I can make the PDF files and it puts them in the Home directory.  I made a cups-pdf.conf file and pasted everything in there from the [http://cip.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/](http://cip.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/) website.  I changed the out line to say:
OUT: $home/PDF

However, it still does not work.  Do I need to upgrade my CUps-PDF program?  If so, how do I do that?

My goal is to print to the PDF directory

---

