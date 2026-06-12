---
title: "Edit/read TI 83+ group files"
date: 2008-11-29
forum: General Help
---

### Post by rubenverweij on 2008-11-29
Hi,
I have a Texas Instruments 83+ graphical calculator with a SilverLink usb cable. I used Tilp2 to transfer some group files I need for school tomorrow, but they are in some strange format I can't open... :(
Has anyone a suggestion on how to open these files under Ubuntu?
Any help would be really, really appreciated.
Thanks in advance,
Ruben

---

### Post by TeXtonyx on 2008-11-29
[http://sourceforge.net/forum/forum.php?forum_id=58171](http://sourceforge.net/forum/forum.php?forum_id=58171)
Open Discussion (586 msgs)

The forum is current and deals with TI83->TI89 issues including 
tilp and people who use linux. There probably aren't many users
on this forum who are experienced with your issues.

[http://www.gnu-darwin.org/www001/ports-1.5a-CURRENT/comms/tilp2/work/tilp2-1.07/help/Manual_en.html](http://www.gnu-darwin.org/www001/ports-1.5a-CURRENT/comms/tilp2/work/tilp2-1.07/help/Manual_en.html)
The Tilp2 User's manual is online and may help. Or the mailing list
[email]tilp-xxxxx@lists.sf.net[/email] replace xxxxx with users

In a galaxy long ago I used a ti83+ for a statistics class.

---

### Post by TeXtonyx on 2008-11-29
> **rubenverweij said:**
> Hi,
I have a Texas Instruments 83+ graphical calculator with a 
SilverLink usb cable. I used Tilp2 to transfer some group files 
I need for school tomorrow, but they are in some strange format 
I can't open... :(
Has anyone a suggestion on how to open these files under Ubuntu? 
Any help would be really, really appreciated.
Thanks in advance,
Ruben

If the following information doesn't help, at least you can 
email the author and get an expert opinion.

---------------------------------------

[http://ronortiz.blogspot.com/2007/05/ti-calcs-ti83-asm-on-linux.html](http://ronortiz.blogspot.com/2007/05/ti-calcs-ti83-asm-on-linux.html)


TI Calcs + TI83+ ASM on Linux
So, I have an interest in those Z80 calcs, popular with many students
today. Of course somethings can be a chore to get working on Linux, here
I'll explain how to get the TI calculators working under Ubuntu 
(This will not work on Debian due to udev differences) through TiLP.

1. In a terminal: sudo apt-get install tidev-modules-source
2. In a terminal: sudo mknod /dev/tiusb0 c 115 16
3. In a terminal: sudo chmod 666 /dev/tiusb0

That's only the steps needed to get a TI calc connected to your Linux
(Debian based) system. TiLP needs to be run as root in order for it to be
able to connect through USB. This arises another problem, not being able
to use the home directory (in the TiLP menu, it won't let you move back a
dir, only up) (Since root defaults to /root/). This can easily be fixed
via editing the root account in "/etc/passwd", changing to something like
/home/bob/.

-----------------------------------------

---

### Post by rubenverweij on 2008-11-30
Thanks for your reactions. I still have no solution however. I posted on the forum, still waiting for a reply. There was nothing already posted about the issue. I tried the ungroup option in Tilp, that just creates a directory with another group file in it, which, once ungrouped, creates another folder with a group file in it, and so forth. I also tried a program called GFM, that didn't work either. Any suggestions are welcome.

---

