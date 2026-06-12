---
title: "Openoffice.org email-merge is the bane of my existence"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by mypetjaws on 2009-10-21
UbuStu- JAUNTY


This little slimebag package freezes my computer on a daily basis. It's not even installed, its the installation process that does it. 

-I have tried purging it. ("must reinstall first because is in a very unstable state etc. etc.- when trying to reinstall in order to then remove, it HANGS)

-Tried removing it, and deselecting it from any updates, to avoid the thing all together and not have it on my system at all.But when I try to update other specific packages, having nothing to do with open office, it automatically "selects previously deselected package openoffice.org email-merge" and HANGS, FOR ETERNITY IF I LET IT. When I try to abort, my computer freezes.


Manually installing, removing/purging, reinstalling, or using synaptic DOES NOT WORK. I can't even install other packages without this thing sneaking into the process and ruining everything. I seriously don't know what to do at this point. 

Forget a successful install/reinstall.Someone please help me permanently remove openoffice.org from my life. On my system, for some reason, it is cancerous sucky garbage. I will be eternally grateful. Thanks in advance!

---

### Post by Scoobie_snack on 2010-04-03
Hey,

I see that this is an old post but I've got this exact problem right now. I've been working on it for a week now and I'm finally asking for help as I can't find a solution.

I have tried EVERYTHING that I've read in other posts and on other forums and this thing is still invading my system.
I too tried to remove it, purge it, reinstall it, manually instal it and I get a the same error as the OP.
When I try to manually install it I get told that the package will conflict with "ure" and the installation ends.

I can't find a fix and I can't update or remove anything because of this. Also, I tried to apt-get the package and now I'm left with "dpkg was interrupted, you must run sudo dpkg --configure -a".. All straight forward, right? 
Wrong! All I get is "Setting up openoffice.org-emailmerge" and some other code in brackets and it just hangs.

Any help on this issue would bee greatly recived.

Thanks in advance!

Edit: I'm using Ubuntu Jaunty 9.04
:guitar:

---

### Post by animedragon67 on 2010-12-09
This post is really old..I am totally having the same problem but can't find a solution on the internet.
I just upgraded to Kubuntu 10.10 and I have 410 upgrades, however all of them require me to update openoffice.org-emailmerge. whether I do it by konsole or packagekit it always hangs when it's updating it, the only way I can stop it is by restarting the computer. Then I have to type 'dpkg --configure -a' like above, and can't update anything else without it wanting to update this thing.

Hopefully someone can offer some help.

EDIT: so I found this link about fixing the broken emailmerge package and successfully removed it.  [http://ubuntuforums.org/archive/index.php/t-1120286.html](http://ubuntuforums.org/archive/index.php/t-1120286.html)
While originally I thought it came back after a restart it seemed to actually work and I successfully updated everything.

---

