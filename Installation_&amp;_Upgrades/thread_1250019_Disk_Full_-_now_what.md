---
title: "Disk Full - now what?"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by ttocScott on 2009-08-26
Hello. I'm new to Linux and Ubuntu. I had a 5 gig / partition, which I thought would be enough. However, I got carried away with all the free apps, and in particular I was trying to install Kubuntu on top of regular Ubuntu to check it out. In the middle of the install, it bombed out because the / partition filled up. I then changed the partitions around using the Partition Editor off the install disk (I thought that would be safer than using the HDD version) so I now have 15 gigs on the / partition. 

Question: I'm not sure what happened to all the stuff I downloaded and was in the middle of installing previously. Is there a way to pick up on that installation, or get it going again without downloading everything again? I'm afraid if I use 'sudo apt-get kubuntu-desktop' again, it will download all the apps again and not overwrite the previous download, so I'll have orphaned original stuff - not to mention the install had started, so I don't know what affect that may have. Although, the system still seems to be working just fine. 

I guess a major part of my problem is I don't understand the file system and organization in Linux. I'm very new to this, so I don't know what goes where, folder-wise... like, /bin, /mnt, etc. In Windoze, had an installation failed, it would probably have rolled back the install, but I am pretty sure Kubuntu just bombed when the disk got full.

Thanks for any help.

Regards,
Scott

---

### Post by Cybie257 on 2009-08-26
If you start it over again, it shouldn't download anything that was already downloaded and should continue to download what is left then install. You will encounter some broken things (programs that used to work) as they are written for one or the other. I won't get into that, but wanted to let you know that it 'should' continue. I have run into problems with installing Kubuntu Desktop on top of Ubuntu/Gnome and was able to recover and continue. There are also some commands to fix broken packages within apt-get, so check into that. I don't recall right away what they are, but search for it on here and you will find it. :)

Hope this helps a little until better information comes around. 

-Cybie

---

### Post by ttocScott on 2009-08-26
Cybie257, I tried your suggestion and I was prompted with a message saying the install was interrupted and to run 'sudo dpkg --configure -a' which I did and it started going again! I love this! It's like a whole new, wonderful world!

Thanks,
Scott

---

### Post by Bartender on 2009-08-26
> **ttocScott said:**
> I guess a major part of my problem is I don't understand the file system and organization in Linux. I'm very new to this, so I don't know what goes where, folder-wise... like, /bin, /mnt, etc.

Unless you really want to explore how Linux works, you don't need to worry about these other folders.  Your Home folder is where all your personal data goes, and the vast majority of applications that you install will show up in "Applications" or in some cases System>Administration.  The rest of the folders should not be messed with unless you've got a test PC for experimentation or you have a very specific task in mind.

A few days ago I posted directions for saving wallpaper in the folder where the system's original wallpaper is stored.  [Post #12]("http://ubuntuforums.org/showthread.php?t=1245089&page=2")

That's an example of a specific task where you could go into the file system.  It'd be easier to create a "wallpaper" folder in Home and that would work as well, but I thought it was kind of cool to use the original folder and it's a fairly painless command line project.

Troubleshooting tasks might take you into /var or /boot.  I don't know much about that.  I'm sure there are all kinds of wonderful things to learn in those folders, but for the newcomer to Linux it's not something you need to worry about.

---

### Post by ttocScott on 2009-08-26
I'm not sure if I should start a new thread for this, but since I installed Kubuntu the computer will not hibernate or shut down correctly. I don't know if this is because of the fact that the disk got full and all that, or not. Now the screen goes black but the mouse is still on the screen, but cannot bring up any menus. 

Any suggestions on how to diagnose or fix?

Thanks,
Scott

---

