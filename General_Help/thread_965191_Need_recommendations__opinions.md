---
title: "Need recommendations / opinions"
date: 2008-10-31
forum: General Help
---

### Post by sandpvrr on 2008-10-31
Hello All,
      Here is the situation - I have my father's computer running Ubuntu 8.04 and Windows 98 SE. I have upgraded his ram to make Ubuntu run faster, but in the process I've knocked Windows 98 completely out, 2 GB is more than it can handle apparently :-) Both Windows and Ubuntu are sharing a common FAT32 data partition, so we have all the files, but one a mail merge database runs only in Microsoft Works. I am not opposed to using OOo to do the mail merge, but as of yet have been unable to figure out a way to avoid retyping the entire database! 
      The way I see it, I have a couple alternatives - get him a different Windows based computer to run this one app, (!) figure a way to run Microsoft Works in Ubuntu or figure a way to call his existing Windows 98 SE install from within Ubuntu. 
      I'm looking for ideas, suggestions, opinions. Although I make a living as an IT Technician, he is border on a techno phobe, so the end result should be as easy as possible...
      Thanks!
        -Joey

---

### Post by joey-elijah on 2008-10-31
Bit of a n0ob, but does Works not run via wine or cross over?

---

### Post by alienprdkt on 2008-10-31
did you try running the app in WINE?

[http://ge.ubuntuforums.com/showthread.php?t=709360](http://ge.ubuntuforums.com/showthread.php?t=709360)

go to Terminal and type: 
winefile 
when the console of winefile open you have to find the .exe file to install :)

---

### Post by sandpvrr on 2008-10-31
All,
    I will try Wine when I get the chance - but I was wondering about different alternatives, last time I tried Wine it almost crashed the system - but that was 7.04. 
       I'll give it another whirl. While we are on the subject, any other different non wine suggestions????
        -Joey

---

### Post by anjilslaire on 2008-10-31
Install virtualbox, and run 98 in a virtual machine within Ubuntu maybe?

---

### Post by sandpvrr on 2008-11-01
Hello All,
      Partial success:
      I have Microsoft Works 4.5 (For windows 95!) running under Wine. However, I cannot get printing to work. Wine has identified and seems to be ok using my Dad's printer (HP PSC 1510) it has it in the virtual registry, but when Works is loaded, it tells me the default printer hasn't been selected and to use the windows control panel to select it. This of course doesn't exist! 
      Any thoughts? Help!!
      Thanks!
        -Joey

---

### Post by TeXtonyx on 2008-11-01
[http://www.geocities.com/rloew/Programs/Patchm01.htm](http://www.geocities.com/rloew/Programs/Patchm01.htm) $20

This overcomes the 512mb ram limitation of Windows 98. He has a
demo file to download to test this, which quits after ten minutes.

I think an XP upgrade might be a good idea,
[http://www.winsupersite.com/showcase/windowsxp_sg_9xupgrade.asp](http://www.winsupersite.com/showcase/windowsxp_sg_9xupgrade.asp)
"Also, by default, XP Setup will backup your existing 9x system so 
you can uninstall XP and go back if you have problems. I  strongly 
recommend allowing it to do so (you'd have to go out of your way to
prevent it), because this gives you an out if anything goes wrong.
And trust me, with a move between two very different technologies, 
something very well could go wrong."

TeX: Do you have an extra drive? What I would do is install XP (dual
boot) fresh and then install Microsoft Works, you may have to enable
legacy OS programs. Then import (or back them up beforehand) the
database from the Win98 install. I was reluctant to switch from
Win98se but I finally did, to XP Pro, and it was a good switch.
It is not that hard to get used to the changes. I hope you have
the Works database already backed up or you may have to uninstall
the ram to make win98se work again to make the database backup.
Or maybe you can backup database from a Virtualbox to a usb stick?

---

### Post by sandpvrr on 2008-11-01
TeX - 
    The database is located in a shared FAT32 partition - I have the database, also backed up on a thumb drive. 
    I would rather move away from the Win 98 idea and don't want to go the XP route as we are only looking at this one application / database.
    If anyone has gone from a Works database to OOo I'd like to hear about it, any suggestions, issues, etc. I think this would be the final solution since OOo is cross platform and at some point in the rather near future I anticipate this database will have to be maintained by someone other than my Father.
    In the mean time, any suggestions on printing from Wine? I have googled it and found nothing useful.
    Thanks all!
     -Joey

---

