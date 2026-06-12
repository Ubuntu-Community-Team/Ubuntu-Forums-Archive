---
title: "User ID is sent with leading quotes to MultiXpress X4300LX"
date: 2015-11-13
forum: Hardware
---

### Post by Daniel_Noble on 2015-11-13
Hi all,  I've been trying to setup a new MultiXpress X4300LX as a printer for both Linux and Windows users. So far it's working fine for the Windows users, it seems to be more of a challenge for Linux though, and here's why: The printer has one of those silly card readers where it reads your user ID from a chip and prints out  your queued documents for that user. The card is also our door opener, which is handy.  However, using what feels like a hundred different drivers, all I ever get is that Ubuntu 14.04 sends the user name with leading quotes. Any print job is queued as "dnoble or "root. No trailing quotes are present. The problem is, my user ID on the access card is obviously not "dnoble so none of my queued documents are printed when I use my access card.  I've tried setting up the printer in different ways, from the command line, from the setup wizard, from the suldr driver setup wizard, from the cups localhost site, nothing made a difference. I downloaded a PPD which also didn't help and I set up the printer with a user id, using this syntax: lpadmin [ -E ] [-U username ] [ -h server[:port] ] -d destination but that also didn't help.  Has anyone experienced the same issues and/or knows how to get rid of this problem of the leading quotes? Many thanks in advance,  Daniel

---

### Post by Daniel_Noble on 2016-03-09
Solution: 

read -p "Please enter your user id   " userid
sed -i "s/CUSTOMUSERID/$userid/g" Samsung-X4300.ppd

Changing the user id in the PPD file worked fine.

---

