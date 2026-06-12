---
title: "Booting from cd stalls at  * Running local boot scripts (/etc/rc.local)"
date: 2008-09-03
forum: General Help
---

### Post by Sysout on 2008-09-03
I am definitely new to ubuntu and linux in general. I have a seemingly common issue at startup. I don't want to commit in anyway yet to ubuntu because its not practical for me so I figure the best way is to boot from the cd so I can tool around with it. As it starts up and seems to load fine then stalls at 

* Running local boot scripts (/etc/rc.local)

Google led me here in various threads and after reading I can access the terminal with ctrl+alt+F1. Enter brings me no login like it does others. I then tried the various commands people said have helped them 

sudo dpkg-reconfigure xserver-xorg

in doing this I configure everything to default but at the end of it keyboard options stays on screen with a small terminal at the bottom stating 

xserver-xorg postinst warning: overwriting possibly-customised configureation file; backup in /etc/x11/xorg.conf.20080903204716 

with ability to use the terminal so I type 

startx 

and hit enter like people have been saying. I get 

waiting for x server to begin accepting connections giving up. xinit: Connection reset by peer (errno 104): unable to connect to X server
XinitL no such precess (errno3): Server error. Then access to the terminal. 

So someone else says type 

sudo /etc/init,d/gdm restart 

I do that and then I get
 
stopping gnome display manager [ok] 
starting gnome display manager [fail]

I type it again both [ok]. 

I am stuck as to what to do. I don't know how to run in safe graphics mode which is supposed to help.

Could definitely use a push in the right direction. If I understand right this has something to do with my video drivers.

Running xp 1gig of ram intel p4 3.2ghz ati radeon 1900xtx

ubuntu 8.04 desktop.

Thanks for all the help in advance. Let me know if you need any additional information. Sorry for the long post.

---

