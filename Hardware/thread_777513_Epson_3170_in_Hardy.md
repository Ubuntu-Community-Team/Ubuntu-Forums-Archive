---
title: "Epson 3170 in Hardy?"
date: 2008-05-01
forum: Hardware
---

### Post by bsulzen on 2008-05-01
Has anyone been able to get the Epson 3170 scanner working in Hardy? In Gutsy, I always used the method at [http://ubuntu.flowconsult.at/en/epson-3170-installation/](http://ubuntu.flowconsult.at/en/epson-3170-installation/) and it always worked perfectly. Trying to install scanner in Hardy has proved unsucessful. The file /etc/udev/rule.d/45-libsane.rules did not exist so I had to create it and manually add the Epson scanner information that would have normally been added by the perl command line at the above mentioned site. Trying to run xsane or iscan returns an error of no scanner found (same result when starting either program as root). I have also added my username to the scanner group. Any ideas? Thanks in advance.

---

### Post by loserboy on 2008-05-01
from googling around it seems that a new version if xsane or iscan needs to be made before it will work, i saw where one guy using slackware looks like he basically built his own... so i dunno...

---

### Post by bsulzen on 2008-05-01
For now i'm running the scanner inside a guest winxp virtualbox. Not exactly ideal but it's working. I dropped an email to the owner of the site I mentioned in my previous post to see if he had a solution. If I get this figured out, I'll make sure to document the steps here.

---

### Post by myoldhouse on 2008-06-16
I don't know if this will help, but I am having the same problems installing the Epson 3170 in Hardy. I can make both iscan and xsane work fine if I run them as the root user eg: $ sudo iscan  or  $ sudo xsane in a terminal.

If I try to run as a normal user in a terminal,eg: $ iscan  or  $ xsane then the program immediately returns a Segmentation fault message in the terminal window and returns to the command prompt. I think this has something to do with file permissions and group membership for the files associated with the USB port that is detected using the hotplug process. I just haven't been able to pinpoint where the problem is. All of the files and scripts used to scan are owned by "root" but some, and I'm not sure which ones, should belong to the group "scanner" rather than the group "root". This is supposed to allow any ordinary user who is a member of the scanner group to be able to use the scanner without having to invoke elevated file priviledges. But it is broken somewhere.

Have you tried to run iscan as the root user? Oh, also system commands like "scanimage -L" will only work as root user (eg. "sudo scanimage -L) but I don't know if this points to a problem with the Hardy sane files or the Epson epkowa ones. Googling hasn't turned up much useful information so far.  :rolleyes:

---

