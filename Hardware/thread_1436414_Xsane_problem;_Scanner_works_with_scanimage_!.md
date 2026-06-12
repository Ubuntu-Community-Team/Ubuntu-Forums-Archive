---
title: "Xsane problem; Scanner works with scanimage ?!?"
date: 2010-03-22
forum: Hardware
---

### Post by twilight_zone on 2010-03-22
Hi,
I ve got some trouble with Xsane 0.996 running on Ubuntu 9.10. 
Problem : starting xsane (icon or in terminal) starts the program; searches for scanner and stops; if I start in terminal I get following message :

WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

(xsane:3221): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3221): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3221): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3221): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

- Scanner is Epson stylus RX500 and is detected by system
- lsusb leads to following output :

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04b8:0807 Seiko Epson Corp. Stylus Photo RX500/510
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

- If I try to scan by using scanimage >filename; I get the file and a properly scanned page ?!?
=> hardware works; connection enabled; XSANE = ??????????????
I tried to un- and reinstall Xsane without changes....

so, if anyone has some good ideas or solutions....
Thanks in advance

---

### Post by ellgor on 2010-03-23
Hi,

Go to the "Avasys" site,its for Epson's, and get there Imagescan package, look for the deb package (way down the download page) as its easy to install (using Gdebi), takes a reboot to start.

Regards, Ellgor.

---

### Post by twilight_zone on 2010-03-24
Hi Ellgor,
thanks for the help. I haven't tried it (yet) The surprising thing for me is, that I can access the scanner via the command "scanimage". The scanner also worked well with Xsane on earlier versions of Ubuntu. So I'd like to understand why it refuses to work with Xsane on Ubuntu 9.10?

Any ideas?

Regards
TZ

---

### Post by ellgor on 2010-03-25
Hi,

I read somewhere that device management changed from Hal to udev, from 9.10 (not sure about 9.04) things that worked with Hal no longer do, = problems.

Regards, Ellgor.

---

### Post by twilight_zone on 2010-03-27
Hi Ellgor,

installed Avasys Imagescan the way you described. Worked very well. Problem solved !

Thanks for your help !

Regards
TZ

---

### Post by euchrid on 2010-04-25
Thanks for this post and the helpful replies. I include the following for the benefit of other Googlers and forum searches: 
I am also using an Epson RX500, and I was getting the same error message in xsane, but also a segmentation fault. I read other posts that suggested changing parts of /etc/init.d and other configuration files, one that advised to change permissions and group settings, and some suggesting that logging in as root would at least allow scanning - but none of it worked.

scanimage and the above mentioned iscan utility worked like a charm. flegita crashed in the same way as xsane on my system, but it looked like it might be worth a shot if iscan ever goes wrong.

I've been using xsane for 5 years with no problem, and can't believe the latest upgrade killed it so badly.

Really, though, something needs to be done about the whole xsane issue, because iscan and scanimage are not solutions for everyone. Maybe simple scan will work better for the next Ubuntu release.

---

### Post by LondonSteve on 2012-01-22
I have lost the will to live with this crap! I have pored through every help page possible for 2 days to find out why xsane no longer works!!!!!!!!!

I couldn't be more pissed off!

Does a later release of Ubuntu fix the problem? I'm currently on Maverick having updated from Hardy Heron.

Should I do a fresh install of a later version?

lsusb reveals:

Bus 001 Device 003: ID 04b8:0838 Seiko Epson Corp. CX7300/CX7400/DX7400

sane-find-scanner revealed similar information.

I tried modifying /etc/udev/rules.d and /etc/sane.d stuff to no avail.

scanimage worked for a bit there but in continuing to problem solve, I broke that too I guess.


I have an EPSON CX7400 via USB which should be typical here! WTF!

---

