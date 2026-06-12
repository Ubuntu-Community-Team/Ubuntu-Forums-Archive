---
title: "Printing issuse: cannot connect to CUPS server...."
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by travisrichardson1980 on 2009-07-24
Xubuntu is so far my favorite version of Linux, and i've used quite a few! I've been astounded at just how well it supports hardware and how well it runs on older computers.

BUT 

I cannot print on my desktop Xubuntu 9.04 installation. I have multiple computers in my house, most of them dual-booted XP and Xubuntu, or with just one or the other. This desktop is the ONLY one giving me trouble.

It seems the CUPS system does not or can not run, and the printer setup cannot connect to it. I try to start the server:
[I]
cuuser@travis-desktop:~$ cupsd
cupsd: Child exited with status 1!
[/I]
and that's what I get. 

When I run live from USB or cd on this computer, the printing setup works flawlessly. My printer is detected, and a few clicks later, I'm up and printing. So I know everything works: computer, cables, printer, drivers - everything.

So I re-installed Xubuntu on this computer, and STILL get the same problem. As soon as it's installed, I try to add my printer, and the "Printer Configuration - localhost" window shows up and says "Not Connected" in the bottom status bar of the window. 

I then click SERVER>CONNECT and get this

`"CUPS server error" window
*There was an error during the CUPS operation: 'httpConnectionEncrypt failed'.*


So I'm stuck. Anyone have any clues??? Thanks! I start my new semester soon and I'm determined to use Linux this year for classes, kind of a proof-of-concept, and I'll be writing up my findings. Looks like the first chapter is writing itself!!

---

### Post by wojox on 2009-07-24
Check you /etc/cupsd.conf file
Make sure you connecting to localhost:631

---

### Post by travisrichardson1980 on 2009-07-24
thanks for the quick response! 

in the "Printer Configuration - localhost" window, i click SERVER>CONNECT and then i can make it say localhost:631 in the box, but it still won't connect.

i don't think it's the port. it seems that cups is just not running.

---

### Post by nike984 on 2010-03-05
as Lutz pointed out in the following link, 
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/335898/comments/7](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/335898/comments/7)
it could be an AppArmor issue. 

Try ```

sudo aa-complain cupsd
sudo /etc/init.d/cups restart
```It worked for me.

---

