---
title: "What to save/archive when upgrading distro?"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by tperwez on 2009-08-27
Hi Everyone,
I am getting the jitters just as I get ready to upgrade from 8.10 to 9.04. I would like to know what data should be saved before embarking on the upgrade. I know I should save/archive my /home but what else needs to be saved? 

Also, what is the best approach to save all data/configurations etc (including all hidden files) on to a USB drive? I believe some command at the commandline will be suited to this. I would appreciate any help.

Regards.

---

### Post by LowSky on 2009-08-27
your /home folder is about it. most of you program config files are saved there.

If you have a specal xorg or GRUB setup then make copies of those as well I guess so you can recreate those.

---

### Post by tperwez on 2009-08-27
> **LowSky said:**
> your /home folder is about it. most of you program config files are saved there.


Thanks for your reply. What command do I need to issue that will copy every file/folder from my home? I mean all my dot files/folders etc. Regards.

---

### Post by ajgreeny on 2009-08-27
If you have a decent sized usb hard drive that will take everything, use rsync, or grsync for a gui, both will do exactly what you want.  I just backup home each time I upgrade distro, including all the hidden files which go by default using grsync, but then am a bit careful which of those I copy back.  You will definitely need all your docs, music, photos etc etc and all files in the root of your home, and of the hidden folders I suggest those which relate to a specific app such as:-
**.openoffice.org**, [B]
.mozilla[/B]
**.mozilla-thunderbird**
**.Skype**
**.purple** if you use pidgin. 
I would be careful copying back things like **.gconf** and other general config folders when you upgrade to a new distro version as you can come unstuck as versions of applications change, but you can always try, and then just delete them if problems occur.

---

### Post by corncob on 2009-08-27
> **tperwez said:**
> Thanks for your reply. What command do I need to issue that will copy every file/folder from my home? I mean all my dot files/folders etc. Regards.

Why not use the graphical interface instead of the command line?  Click on Places to open the File Browser and drag your home folder to your pen drive or whatever you're using (you'll need a big whatever if you have a lot of pictures, videos, etc).  This will copy the folder including the hidden files.

---

### Post by tperwez on 2009-08-27
ajgreeny,

I appreciate your insight and helpful advice. I see now why blind copying of every dot file will be not so wise. I will need to be selective what I copy back after the upgrade. Thanks and many regards.

---

### Post by tperwez on 2009-08-27
corncob,

Thanks for suggesting an easy graphical solution. Regards.

---

