---
title: "Can't think of a good title , catch 22???"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by alex+ on 2005-06-08
There's so much information in this forum that to get the benefit from it, I need to print it on paper.  It's very difficult to do much with just the display on the monitor screen. But, I don't know how to set up the printer

All I know is my printer is an HP5551 and I believe the driver is 'hpijs'.  I don't know how to get and install this driver and what else needs to be done.

According to what I've read, this printer should work extremely well in Linux.

---

### Post by cydizen on 2005-06-08
Alex, 

 Assuming you are using Gnome, follow these instructions....

System -> Administration ->  Printing

Double Click 'New Printer'

Printer Type should be 'Local Printer'

I select 'Use another printer by specifying a port' 

Under printer port I select USB Printer #1 (you may still be using a parallel port, choose accordingly)

Click the 'Forward' button

This part is east.... pick HP from the Mfg. List.... then Choose your printer! Actually, there is a driver listed for your EXACT printer in there...

The Driver field (should) automagically be filled in now....

Click apply!

You should be good to go, open up something and print away.  This worked for me on my HP, hopefully it does for you as well.


Cheers,
Bruce

---

### Post by alex+ on 2005-06-09
Thanks, Bruce
When I got to the Printer Connections menu, I selected
'Local'' Printer but then I can't get past the line:
  "Use another printer by specifying a port"

pressing the 'Printer Port' button has no effect although It appears to be active (not greyed out)

and the 'Back' and 'Forward' buttons are greyed
out.--only 'Cancel' is active.

I tried 'Use a detected printer' --didn't work.

So it appears that the printer port is lost somewhere.
Alas, what to do?

alex

---

### Post by cydizen on 2005-06-09
The next step would be to check your /etc/group file to make sure that you are in the appropriate groups. Actually, I just realized that this thread is from the Warty 4.10 (sorry, I picked it from the 'Unanswered Threads' Link). Anyway, I would still check to make sure that you are in the proper groups. If you want, I will post my /etc/group.

---

### Post by cydizen on 2005-06-09
*I am running Hoary 5.04

---

### Post by desdinova on 2005-06-09
[QUOTE=cydizen]*I am running Hoary 5.04[/QUOTE]
 [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_5551](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_5551)

linuxprinting.org is a godsend for checking out printers

---

### Post by alex+ on 2005-06-09
I thought it was beyond my ability but did managed to make a copy of my /etc/group file

[root@ubuntu:/etc # sudo cat group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:alex
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:alex,cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:alex,hal
floppy:x:25:alex,hal
tape:x:26:
sudo:x:27:
audio:x:29:alex
dip:x:30:alex
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:alex
sasl:x:45:
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
crontab:x:101:
ssh:x:102:
plugdev:x:103:alex,hal
messagebus:x:104:
postfix:x:105:
postdrop:x:106:
alex:x:1000:
lpadmin:x:107:alex
scanner:x:108:alex
hal:x:109:
slocate:x:110:
gdm:x:111:
root@ubuntu:/etc #

alex

---

### Post by cydizen on 2005-06-10
Hmm... It's the same as mine, except I have one additional group:

admin:x:109:bruce

Perhaps do a google for that group under ubuntu and go from there. Have you tried to install Hoary 5.04 yet? Maybe that group does not exist in Warty ? 


Let me know,
Bruce

---

### Post by cydizen on 2005-06-12
[QUOTE=cydizen]Hmm... It's the same as mine, except I have one additional group:

admin:x:109:bruce

Perhaps do a google for that group under ubuntu and go from there. Have you tried to install Hoary 5.04 yet? Maybe that group does not exist in Warty ? 


Let me know,
Bruce[/QUOTE]
 Any success with this ?

---

