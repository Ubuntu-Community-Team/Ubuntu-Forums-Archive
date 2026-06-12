---
title: "[SOLVED] How do you install new systemsounds?"
date: 2008-08-27
forum: General Help
---

### Post by d0nut on 2008-08-27
I downloaded a couple of system sounds from [http://www.gnome-look.org/](http://www.gnome-look.org/) and would like to get them installed. I am running Ubuntu Hardy Heron 8.04 and using Gnome. To get to my sound folder I go to usr/share/sounds/ and I tried to replace the default sounds with the new sounds but it says I don't have permission.  How do I get permission?  Thanks.

---

### Post by lynx_hanan on 2008-08-28
Goto system->preferences->sounds

make sure system sounds is checked
and from here u can select an browse sound file for any event u want

for the permisiions u were asking, i dnt know if it can be done by using a GUI or graphics

goto accessories terminal 

u have to use this command

cp -rv ur SOURCE DESTINATION

here source and destination are the pah of ur sound files

e-g if the sounds were placed on the desktop of a user say "abc" and the sound files u downloaded were in a folder "soundxyz" then the complete command will be

sudo cp -rv  /home/abc/Desktop/soundxyz/ /usr/share/sounds/

eneter ur password after this

---

### Post by d0nut on 2008-08-28
Thanks Lynx.  That enabled me to place those sound files into the sounds folder.

I see where to select the sounds now, however when I do so they are not working...even after I reboot.  In fact, I don't have any startup or shutdown sounds when I enable them now.  The only sound I get at first is the original bongo drums at the login and thats not what I have checked.  ...soooo, i'm still at a loss...anyone else have ideas? thx

---

### Post by lynx_hanan on 2008-08-28
What Method Did u follow ?

Placing the sounds file in the /usr/shar... directory
or Selecying the sound File From the GUI ???

---

### Post by lynx_hanan on 2008-08-28
If u followed the graphical method of Setting the Sounds from the preferences by Individually selecting them then make sure that these sound files are in ur "/" partition. 8.04 Doesnt mount partitions by default. So it doesnt find those files when it starts.

---

### Post by d0nut on 2008-08-28
I followed all of your instructions above and it put the sounds into the appropriate directory.  But that alone did not change to the new sounds.  So, I went with the graphical way to individually select the sounds, which isn't working.  

How do I partition them if they are not already done by default in 8.04?  Thanks.

---

