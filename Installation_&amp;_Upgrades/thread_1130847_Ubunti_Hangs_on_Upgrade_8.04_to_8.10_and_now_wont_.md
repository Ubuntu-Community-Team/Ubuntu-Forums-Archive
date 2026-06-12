---
title: "Ubunti Hangs on Upgrade 8.04 to 8.10 and now wont start after power on/off"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by infocom on 2009-04-20
I ran the upgrade from 8.04 to 8.10 and all seems to be going OK. I left it alone to download the files which would take over an hour. 

Came back to my PC and there is an error saying "An error occured while loading or saving the configuration..." then something about Nautilus. Anyway, the mouse worked but nothing else worked. Ubuntu just sat there, hung. No clicks application, start menu, Ctrl+Alt+Backspace, nothing, just the mouse moving around a hung desktop. So I have to power it off then on. 

Now Ubuntu would not boot up at all. At first the boot up recognised the hard drive but it hand at boot up screen when I had the option to hit Del for setup etc. Then it just restarted itself and it states "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER". I hit Ctrl+Alt+Delete to restart and goes back to the screen where the hard drive is recognised but hangs there. 

Please advise, I had a lot of document/music/images etc.

Thanks

---

### Post by upchucky on 2009-04-20
everything should still be there, either in the form of the backup you did before an upgrade or in the form of a separate home directory, in the event that you did neither, boot the live cd, then download this,



[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh
```

post the results here, I suspect that 8.10 does not like the display and everything is still intact, if true, then this is a great time to do the back up and then either go back to 8.04 or troubleshoot how to get 8.10 working with your pc. keep in mind that 8.04 is a long term supported release, and 8.10 is not.

---

### Post by infocom on 2009-04-20
ok I will try thanks

I think its a bit too techy to expect everyone to take backups or separate partitions before what you would consider an established upgrade especially those like me who are used to Windows, in which backups or partitions were never made. :???:.

---

### Post by upchucky on 2009-04-20
Hmm, the number one thing to do with windows is to backup regularly so everything is restore-able when windows self destructs as it is programmed to do over time.

and the second thing to do with windows is to create a second partition to put files and programs on so when you have to re-install windows, you do not have to re-install programs and windows did not take all your files with it when it crashed.

as in my windows systems, I also have extra partitions in Linux, plus partitioning image software that allows me to restore my entire systems to a prime condition before I do any changes. both systems, Windows and Linux are fully restore-able within 20 minutes. 

the extra partitions and free image software avoids spending entire weekends re-installing windows and its programs.

NTFSclone is free, it makes restorable images of windows
Partimage is the free one for Linux

---

### Post by infocom on 2009-04-20
I agree backup and partitions should be necessary, but I just mean many people trying to move to Ubuntu who are not "techy" wont do this. I dont even know how to backup ubuntu but I have created some partitions, but non-techies wont be able to. I am not overly familiar with it yet, still trying to move from windows but not 100% yet as its still not as easy to use as windows. 

> when windows self destructs as it is programmed to do over time.

I know there is a hate-hate relationship between Linux/Windows users but you cant make exagerated statements about Windows like that. I have had 1000 times more hours spent on Windows, all versions, and I'm sorry to say if this happens it is quite rare ;). It of course sometimes crashes or something :( but then a simple restart or program kill shows my data still intact and 1000 more hours spent on the same OS and PC.

---

### Post by upchucky on 2009-04-20
Ok, assuming that for some reason you can't post the information about the drive geometry, and it is likely that the files you want to recover are on a windows partition, and you do not have access to a manual that tells you how to copy/paste anything to a backup medium, I suggest that you download Knoppix, It is a live cd that can rescue both windows and Linux installs and files. it is also great in the fact that there is very little reading involved to understand how it works. and what to do with it. many times it is the only way to bring a malfunctioning windows machine back from the dead, whether it was brought down by a virus or a corrupt registry.

It was designed for users of the windows world where point and click are not only a way to operate a microwave, but a way to operate a computer too.

good luck

---

### Post by infocom on 2009-04-20
I'll give all suggestions a go, thanks for your help.

Although the data is on the ext3 Ubuntu partition not a windows one. Just saved all data in my user directory in Ubuntu.

---

### Post by infocom on 2009-04-30
I decided to just install 9.04 and it gave me the option of installing it side-by-side with my 8.04. So thats cool, I can now get my documents from 9.04 accessing the 8.04 partition.

---

