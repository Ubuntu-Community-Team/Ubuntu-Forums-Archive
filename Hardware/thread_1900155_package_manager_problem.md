---
title: "package manager problem"
date: 2011-12-25
forum: Hardware
---

### Post by skaramanger on 2011-12-25
Greetings and Happy holiday, to all on this fine Winter Solstice day,

My Dell D830 laptop has kubuntu 11.10 installed on it.  It runs nicely for the most part.  Except for a problem with package management.  I have been searching this site extensively and am unsure as to a resolution to my issue.

Currently,  When I try to install software, apt-get returns an error regarding a duplicate Manager of a package in /var/lib/dpkg/status file.  I have examined the file and it appears to be corrupted. When I look at it in in kate as super user there are several lines of in decipherable non-ascii characters.  If I try to delete them, nothing happens.  The cursor won't move and text will not be deleted.  This all attempted as Super user (kdesudo kate) and as sudo su - no go.  So my question is:

How can I clean this up?

Thanks In Advance

---

### Post by matt_symes on 2011-12-25
Hi

There should be a backup file here.

```
/var/lib/dpkg/status-old
```

You could use that old file. 

Can you post the part of the new file that is corrupted.

Kind regards

---

### Post by gareththered on 2011-12-25
You could try:-

[http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file](http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file)

or:-

[http://www.linuxquestions.org/questions/linux-newbie-8/synaptic-package-manager-not-working-912217/](http://www.linuxquestions.org/questions/linux-newbie-8/synaptic-package-manager-not-working-912217/)

I'm certain one of those will help.

---

### Post by skaramanger on 2011-12-25
First off thanks for your reply.

Second:

First the error messages:

```
Latitude-D830:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libqt4-designer
The following NEW packages will be installed:
  libqt4-designer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/3,708 kB of archives.
After this operation, 9,204 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error: parsing file '/var/lib/dpkg/status' near line 19269 package 'libmuonprivate1':
 duplicate value for `Maintainer' field
E: Sub-process /usr/bin/dpkg returned an error code (2)
Latitude-D830:~$ 

```

As for the file, I had to do a screen shot, when kate opened file on my workstation it gave me a message that there was non-utf8 characters in the file and it was marked as read only.  They appear as triangles in kates' window.  

It is posted as an attachment:

[http://ubuntuforums.org/attachment.php?attachmentid=209701&stc=1&d=1324856238](http://ubuntuforums.org/attachment.php?attachmentid=209701&stc=1&d=1324856238)

Regards




> **matt_symes said:**
> Hi

There should be a backup file here.

```
/var/lib/dpkg/status-old
```

You could use that old file. 

Can you post the part of the new file that is corrupted.

Kind regards

---

### Post by matt_symes on 2011-12-25
Hi 

Have you considered using sed to delete the lines as super user ? That may work if it cannot be edited using kate.

Kind regards

---

### Post by skaramanger on 2011-12-26
> **matt_symes said:**
> Hi 

Have you considered using sed to delete the lines as super user ? That may work if it cannot be edited using kate.

Kind regards

Matt_symes,

I hadn't considered that.  However,  I moved the original file and copied the status-old file and performed apt-get update apt-get -f install and for now the problem appears to be fixed.

Thanks for your assistance:)

---

### Post by skaramanger on 2011-12-26
> **gareththered said:**
> You could try:-

[http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file](http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file)

or:-

[http://www.linuxquestions.org/questions/linux-newbie-8/synaptic-package-manager-not-working-912217/](http://www.linuxquestions.org/questions/linux-newbie-8/synaptic-package-manager-not-working-912217/)

I'm certain one of those will help.

Garefththered,

Thanks for your reply.  I did check out those links, (after I had copied the status-old over and sudo apt-get update and sudo apt-get -f install).  The problem appears for now to be repaired.  However, from reading the link, this might not be the case.  It does appear that when dpkg data files get corrupted, they can create a myriad of problems.

Tnx

---

