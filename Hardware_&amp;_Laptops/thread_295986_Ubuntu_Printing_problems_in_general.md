---
title: "Ubuntu Printing problems in general"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by beast2k on 2006-11-08
I have an HP printer that I'm having ongoing problems with only in ubuntu (610 in my case) In ubuntu the hardware detection is there and the tools are there all looks good but will not work. Some have print sharing problems (either from windows or to windows), Some have a good working local printer but the same printer can't be accessed by another PC, windows or Linux, some cant enable their printer, some cant re enable printing. So does anybody see a pattern here? All anyone has to do is search the forums for printer problems or print sharing and it seems obvious that theres a problem in the general area of printing in ubuntu (I'm curious if this problem is in kubuntu as well) Can anyone shed some light on the whole printing issue with ubuntu ? some have problems and some do not. I have never seen anything quite like it before, I just switched to ubuntu from mandriva not long ago and my printer works flawlessly in mandriva if I remember correctly it set itself up. What gives?, As far as I can tell this is ubuntus only weakness (from where I sit) Why do printers work fine and almost set themselves up in other distros (Mandriva, + Fedora to name 2) but in ubuntu, myself and many others must jump through hoops and stand on our heads to make them work?

---

### Post by K.Mandla on 2006-11-08
It's difficult to answer your question without more information about the printers. Chances are someone on the forum has a similar model, and might be able to suggest a solution.

In a larger sense, critiquing Ubuntu for general printer issues is a bit pointless; I would guess as many people had difficulty printing in Fedora or Mandriva that saw their problems disappear in Ubuntu.

Perhaps if another distro works better for you, you should use it.

---

### Post by beast2k on 2006-11-09
> **K.Mandla said:**
> It's difficult to answer your question without more information about the printers. Chances are someone on the forum has a similar model, and might be able to suggest a solution.

In a larger sense, critiquing Ubuntu for general printer issues is a bit pointless; I would guess as many people had difficulty printing in Fedora or Mandriva that saw their problems disappear in Ubuntu.

Perhaps if another distro works better for you, you should use it.

Although I have not given up on the printer problem on this PC getting help was not the point of the post (truckloads of info have already been posted on this problem). Don't get me wrong I welcome any new ideas and yes more than a few people are having the same trouble with similar HP printers with no solution. As I said it was not my intention to troubleshoot the printer but thank you alot for offering help, for not many are willing to tackle this problem. 
In your responce you mentioned "I would guess as many people had difficulty printing in Fedora or Mandriva that saw their problems disappear in Ubuntu" I used to think this same thing but No this is not the case after looking into this issue for some time I found out that in those 2 distros they have somehow made issues like print sharing and to some extent samba usage pretty much mindless as I mentioned it set itself up in the mandriva 2007 distro.  Actually one solution I tried was to set up Mandriva and Fedora on the same system and get the printer all set up and then back up the /etc/cups and /etc/samba folders from those distros and use those backups to compare and possibly hack out a solution. To my surprise after backing up these folders and doing a comparison on the same pc with same folders in ubuntu 6.10 I found the ubuntu and Mandriva+Fedora folders were almost an exact match (minor differences because of distro names). This is what points me to the fact that it may be somehow related to the distro itself what other conclusion can I come to? As for your last comment about going back to that bloated Mandriva or fedora after using ubuntu thats like going from driving a porche to driving a electric smart car. I would rather go without a printer than go back to that mess with their half a dozen cd installs. I'll quit now this is to long already thanks for your comments I just wanted some kind of record on this problem so people are aware there is an issue. ](*,) 

P.S: Kubuntu is next I'm curious if the same trouble exists on the kde side.
P.S.S. I tried Kubuntu it does NOT have this problem and Suse 10 does not either. (I see a pattern here) I don't think it's a ubuntu thing I think it's a Gnome/KDE thing my HP printer works great in all the KDE based distros (when I tried Fedora I used the KDE desktop). Bottom line is it works in Kubuntu and thats as close as I can get to ubuntu without losing my printer so I am now a kubuntu user. I'll sure miss gnome though. If anyone else has this problem try Kubuntu and let me know how it works for you, contact me on the kubuntu forums.

---

### Post by jpyanowski on 2006-11-13
> **beast2k said:**
> Although I have not given up on the printer problem on this PC getting help was not the point of the post (truckloads of info have already been posted on this problem). Don't get me wrong I welcome any new ideas and yes more than a few people are having the same trouble with similar HP printers with no solution. As I said it was not my intention to troubleshoot the printer but thank you alot for offering help, for not many are willing to tackle this problem. 
In your responce you mentioned "I would guess as many people had difficulty printing in Fedora or Mandriva that saw their problems disappear in Ubuntu" I used to think this same thing but No this is not the case after looking into this issue for some time I found out that in those 2 distros they have somehow made issues like print sharing and to some extent samba usage pretty much mindless as I mentioned it set itself up in the mandriva 2007 distro.  Actually one solution I tried was to set up Mandriva and Fedora on the same system and get the printer all set up and then back up the /etc/cups and /etc/samba folders from those distros and use those backups to compare and possibly hack out a solution. To my surprise after backing up these folders and doing a comparison on the same pc with same folders in ubuntu 6.10 I found the ubuntu and Mandriva+Fedora folders were almost an exact match (minor differences because of distro names). This is what points me to the fact that it may be somehow related to the distro itself what other conclusion can I come to? As for your last comment about going back to that bloated Mandriva or fedora after using ubuntu thats like going from driving a porche to driving a electric smart car. I would rather go without a printer than go back to that mess with their half a dozen cd installs. I'll quit now this is to long already thanks for your comments I just wanted some kind of record on this problem so people are aware there is an issue. ](*,) 

P.S: Kubuntu is next I'm curious if the same trouble exists on the kde side.
P.S.S. I tried Kubuntu it does NOT have this problem and Suse 10 does not either. (I see a pattern here) I don't think it's a ubuntu thing I think it's a Gnome/KDE thing my HP printer works great in all the KDE based distros (when I tried Fedora I used the KDE desktop). Bottom line is it works in Kubuntu and thats as close as I can get to ubuntu without losing my printer so I am now a kubuntu user. I'll sure miss gnome though. If anyone else has this problem try Kubuntu and let me know how it works for you, contact me on the kubuntu forums.

I purchased a HP Laserprinter and found that it was one of the few HP models that was not linux friendly. :(  So I brought that back to Compusa and got a Samsung laserprinter that I can use on my Airport wireless LAN. So maybe it's the printer and not the software, you think???:-k

---

### Post by beast2k on 2006-11-13
In my opinion I think it's both lack of drivers for linux and gnome. Most (but not all) problems seem to be with HP printers using gnome I found it impossible to share a printer in ubuntu but the same HP printer works perfect and shares nicely in kubuntu the only difference in my case was the KDE instead of gnome. However the printer type is a big factor of that there's no doubt, so for me I guess I'm a kubuntu user untill this gets looked after in ubuntu. One thing ubuntu needs is a better tool/interface for file and print sharing. So kubuntu it is.

---

