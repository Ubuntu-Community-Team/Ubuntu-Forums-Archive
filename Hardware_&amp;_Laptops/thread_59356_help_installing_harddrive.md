---
title: "help installing harddrive"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by kennny2004 on 2005-08-23
k fist of all i connected hard drive one slave one master now i had to disconnect my cd r and i do not know how to get it to work because the cord pug in the motherboard one is black one is blue and one is small one and if i connect a cord into blue it screws up and don't boot right anyone? and what is fdisk for linux

---

### Post by glug101 on 2005-08-23
[QUOTE=kennny2004]k fist of all i connected hard drive one slave one master now i had to disconnect my cd r and i do not know how to get it to work because the cord pug in the motherboard one is black one is blue and one is small one and if i connect a cord into blue it screws up and don't boot right anyone? and what is fdisk for linux[/QUOTE]
 Ok, second question first.  fdisk is a utility in unix (and to a lesser extent, dos;) ) that is used to partition a new and unitialized hard drive into useable sections (basically splitting up a physical drive into logical drives).  For usage, type 'man fdisk' into any unix system.  Or for the online info, her is a link to the online man page :

[http://www.cs.biu.ac.il/cgi-bin/man?fdisk+1M](http://www.cs.biu.ac.il/cgi-bin/man?fdisk+1M)

For the slave/master cabling question: I'm not sure what you are asking.  It sounds like you had a hard drive and a cdr on the same cable for installation.  Then you removed the cdr and added a second hard drive.  Now, I gather that you are trying to put the cdr back in, but it's not working?

You might have removed the jumper that set the cdr as slave when you put in the second hard drive.  Make sure that the cdr has a jumper on the slave setting if it is on the same cable as the booting hard drive.  I am curious as to what you mean by one of the cables being small.  The plugs should all be the same size.  If the plug is smaller then it's the wrong kind of cable. (if the cable is shorter then it doesn't make a difference)

Hope this helps! :)

---

