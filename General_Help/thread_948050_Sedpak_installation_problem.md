---
title: "Sedpak installation problem"
date: 2008-10-14
forum: General Help
---

### Post by raguiler on 2008-10-14
Have a problem installing this application in Ubuntu and do not know what is going on.

I have followed these instructions for the developers website: But nothing happens.


1. Verify that OpenMotif is installed on your system.

   Ubuntu -  use the dpkg command:

   $ dpkg --list | grep libmotif
   libmotif3                   2.2.3-1    Open Motif - shared libraries

   Redhat - use the rpm  command:

   $ rpm -qva | grep openmotif
   openmotif-2.2.3-5.RHEL3.2

Contact your systems administrator if openmotif is not installed.


2. Copy sedpak54.tar.gz file to your home directory.

  $ cp DOWNLOAD_PATH/sedpak54.tar.gz $HOME

         where DOWNLOAD_PATH is the directory where you
           saved the sedpak file from the web site.

          
3. Type the following commands in a console. Files         "runsedpak", ".sedpakrc" and a directory
"sedpak54" will be created in your home directory.

   $ cd $HOME
   $ tar xvzf sedpak54.tar.gz

6. Start sedpak. A menu bar should appear at the top of your display.   
 $ ./runsedpak

I will appreciate your help with this and by the way the developers website is [http://sedpak.geol.sc.edu](http://sedpak.geol.sc.edu) in case you need to know anything else.

Thanks

---

### Post by Yellow Pasque on 2008-10-14
So you are having trouble with the last command? Do you get any error messages?

---

### Post by raguiler on 2008-10-15
I do not receive any message. 

Nothing seems to happen.

---

### Post by sbcadieux on 2010-01-22
I am having this same problem. 

I have verified that openmotif is installed, but when I get to step 2-6 have difficulties. 

Did you ever get this resolved?

---

### Post by manuel_ayaknak on 2010-02-09
I am having this same problem... but in last step nothing seems happen...

Any suggestion for 9.10

---

