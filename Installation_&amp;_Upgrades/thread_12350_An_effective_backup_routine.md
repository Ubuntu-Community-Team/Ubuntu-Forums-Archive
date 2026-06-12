---
title: "An effective backup routine"
date: 2005-01-24
forum: Installation &amp; Upgrades
---

### Post by loninappleton on 2005-01-24
This is the install forum, but backup is something I need to know about right away.


I have a Fedora Core 3 Setup using 2 15g drives.  

the program qtparted shows the following which I wrote out by hand and will get juiced copyingit in here:

I'm printing what qtparted says about my drive and then I have
some Q's.

   key:  * indicates where Qtparted displays a penguin

hdb


  #    Partit'n  Type  Stat    Size       Used    Start    End       Label

  01  /dev/hdb1  Free  Hidden   0.03mb    N/A     0.0mb    0.03 mb   None

* 02  /dev/hdb1  ext3  Active  13.96Gb   747.06   0.03mb  13.96 Gb   None

  03  /dev/hdb1  Free  Hidden   5.3 mb    N/A    13.96 Gb 13.97 Gb   None


hda


  01 /dev/hda1   Free  Hidden  0.03 mb    N/A     0.00 mb   0.03 mb  None

* 02 /dev/hda1   ext3  Active 98.41 mb   13.03 mb 0.03 mb  98.44 mb  /boot

* 03 /dev/hda1   ext3 (blank) 13.48 Gb    3.62 Gb 98.44mb  13.57 Gb  /

* 04 /dev/hda1 linux swap    767.81 mb     0      13.57Gb  14.32 Gb

* 05 /dev/hda1   Free  Hidden 2.46 mb     N/A     14.32Gb  14.33 Gb



   The question:


  Is the hdb configured correctly to be the backup drive ready
  for a dump command or whatever I can use to make a click and clone
  mirror backup?


  Note:  this question was originally asked at the 
qtparted forum but they seem to answer few basic questions and I do not go there much anymore.


  [email]lon@athenet.net[/email]

---

