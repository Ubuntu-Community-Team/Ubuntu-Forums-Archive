---
title: "Upgrade: Mostly good except home directory connection and panel problem"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by emanresu on 2009-05-12
i upgraded to Jaunty this past Sunday. everything went pretty well except for my /home directory and what i think are some corrollary issues. 

i had my /home on a separate partition and my laptop is set up as a dualboot with XP. when Jaunty was requesting partition info, i got the all the stuff correct, but on the screen for keeping user's documents, it didn't recognize the /home partition and there were no documents to keep. i finished the install anyway. 

upon restart, the /home partition was still there, but there was a new /home directory. i searched the forums for a way to connect the /home partition and had no luck. a general web search turned up this:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

i skipped to this part:> 
Now, you have to tell Ubuntu to mount your new home when you boot. Add a line to the “/etc/fstab” file that looks like the following:

```
/dev/hda5 /home ext3 nodev,nosuid 0 2
```

... where s/// the correct partition on my computer. that got the /home partition connected. then i had problems with the keyring. found a solution for that somewhere on the forums. 

my current issue is two-fold:
1) upon login, i get an error msg that says:
> the panel encountered a problem while loading 'OAFIID:Deskbar_Applet'.
do you want to delete the applet from your configuration? 

i don't know what that applet is exactly and have so far opted to NOT delete it. how do i fix this problem? 

2) when i start up Rhythmbox, instead of populating the app with music files, it starts emptying them out and the subfolder Missing Files under Library lists all the music files. says something about not being able to connect to the source, which is a separate partition just for various files, such as music and pics. i have to go to Music>Add Folder>(partition) and add all the files again to the Music subfolder under Library. 

any ideas how to fix applet or the Rhythmbox connection?

---

### Post by emanresu on 2009-05-14
Bueller? 

Bueller?

---

### Post by emanresu on 2009-05-22
bump

---

