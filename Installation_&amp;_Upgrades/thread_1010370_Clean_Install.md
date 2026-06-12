---
title: "Clean Install"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2008-12-13
Although I  do not want to do a reinstall my upgrade from 8.04 to 8.10 has been a mess from a sound point of view. No sound on flv files. oss4 will not remove and can not get back to ALSA. I have therefore decided to do a clean install of intrepid.

Does a clean install mean I remove the contents of the home directory by reformating it?

My home directory is on a different partition.

Apart from copying to a safe place my etc/fstab and restoring it after the new installation, is there any thing else I should retain and restore from the current root directory?

Robin

---

### Post by cdtech on 2008-12-13
I wouldn't worry about saving any files (fstab) since it will be regenerated upon install. As far as your /home directory for a reinstall I would suggest a reformat so there is absolutly no residual config files left behind. If it was a backup restore then maybe an "fstab" save but not for a reinstall.

---

### Post by Robbyx on 2008-12-13
> **cdtech said:**
> I wouldn't worry about saving any files (fstab) since it will be regenerated upon install. As far as your /home directory for a reinstall I would suggest a reformat so there is absolutly no residual config files left behind. If it was a backup restore then maybe an "fstab" save but not for a reinstall.

Of course you are not suggesting I reformat the /home directory, or are you advising that? I have deliberately split my home directory so that if I have to do a reinstall I have all the data for my programs in a safe place.

Robin

---

### Post by cdtech on 2008-12-13
No just keep your home directory. I thought you wanted to do a "clean" install. You can keep your old configuration files.

**UPDATE::.**
See this post:
[http://www.110mb.com/forum/how-to-on-ubuntu-save-the-package-list-and-use-it-to-reinstall-packages-later-t22332.0.html](http://www.110mb.com/forum/how-to-on-ubuntu-save-the-package-list-and-use-it-to-reinstall-packages-later-t22332.0.html)

---

### Post by Partyboi2 on 2008-12-13
When you get to the partitioning stage when you reinstall choose "manual" then make sure the box to format / is ticked and the mount point is set to /. For your /home partition make sure you **do not **tick the box to format but you set the mount point again for your /home partition to /home. If you do not reset the mount point for your /home partition then you will end up with a /home folder on /

---

### Post by Robbyx on 2008-12-14
I am having serious problems with the sound in 8.10. If I keep the home directory as it is, will I end up with my current default sound settings? 

[I](At the moment I have oss4 which will not play flv files and which will not revert to alsa, even when I unsuccessfully attempt to remove oss4. VLC will not play videos. SMplayer will not open. I am hoping a fresh install with the existing home will enable me to follow one of the guides to correct the sound problem.

I also have a broken package that will not repair. Open office has a nasty habit of crashing before it has saved anything.)
[/I]

Robin

---

### Post by bulldog on 2008-12-14
Format / and do NOT format /home.
I would advice to choose a different username and password,when you do the reinstall.
This will make a second map in your /home,and you have no problems with the 'old' config files.
You can copy your data between the two 'users' in the /home,like your email and bookmarks.

---

### Post by Robbyx on 2008-12-15
> **bulldog said:**
> Format / and do NOT format /home.
I would advice to choose a different username and password,when you do the reinstall.
This will make a second map in your /home,and you have no problems with the 'old' config files.
You can copy your data between the two 'users' in the /home,like your email and bookmarks.


I have the reinstalled system running.

I followed your advice and created a new user. None of my original settings are there, as you advised.

How do I get back to the same layout and settings as before? For example my Firefox and thunderbird settings and bookmarks.

Robin

---

### Post by Robbyx on 2008-12-15
The reinstall has turned out to be a nightmare. Drives are not being mounted. I can't get Thunderbird to access the previous data. I don't know how to handle wine or vmplayer so that the old data is recognised. In short I am in trouble. If anyone is prepared to help please ask. I could do with some support.

Last time I did a clean install upgrade I did not have this trouble.

Robin

---

### Post by cdtech on 2008-12-15
> **Robbyx said:**
> The reinstall has turned out to be a nightmare. Drives are not being mounted. I can't get Thunderbird to access the previous data. I don't know how to handle wine or vmplayer so that the old data is recognised. In short I am in trouble. If anyone is prepared to help please ask. I could do with some support.

Last time I did a clean install upgrade I did not have this trouble.

Robin

What did you do last time you did a clean install/upgrade? Now that you've created a new user, just copy your old "~/" directory to the new user "~/" directory. You'll have to change the owner and group on the files and directories you move but that's as easy as doing a "sudo chown" "sudo chgrp". Didn't the reinstall create an "/etc/fstab" file for you during the reinstall? You may need to edit the file manually.

---

### Post by Robbyx on 2008-12-15
I have indeed a problem about the syntax for mounting the ntfs and reiserfs files in fstab, but I will struggle a bit longer and only if I fail will I come back to you for guidance.

I do have a problem about how to run wine:

I copied over the home directory relating to wine. 


The old .wine directory shows the following files. I do not know how to make it run:

> /home/robin/.wine/userdef.reg
/home/robin/.wine/user.reg
/home/robin/.wine/system.reg
/home/robin/.wine/drive_c
/home/robin/.wine/dosdevices


I think I have the solution to VirtualBox ie reinstall it. Unless this fails to pick up the old data files I will not bother you about VB.


Robin

---

### Post by Robbyx on 2008-12-16
Sorry to bother you with a further question. Currently all my data is on a seperate disk and has become owned by root group root. I would like to change it to rob:rob with +r, +w,-execute and other users -r, -w, -e

How do make the changes?

I keep running pcman with the folder as root. It runs through changing the permissions but when I look at the files they have not changed.

---

### Post by Robbyx on 2008-12-24
> **cdtech said:**
> What did you do last time you did a clean install/upgrade? Now that you've created a new user, just copy your old "~/" directory to the new user "~/" directory. You'll have to change the owner and group on the files and directories you move but that's as easy as doing a "sudo chown" "sudo chgrp". Didn't the reinstall create an "/etc/fstab" file for you during the reinstall? You may need to edit the file manually.

If I was doing this again I would not choose a new user. I have found that some programs and firefox extensions are set up to look in the old user home directory instead of the new one.  Often it is not obvious where the settings are stored.

---

