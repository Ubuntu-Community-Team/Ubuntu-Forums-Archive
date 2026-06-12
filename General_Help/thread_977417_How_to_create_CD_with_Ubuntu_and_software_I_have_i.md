---
title: "How to create CD with Ubuntu and software I have installed/uinstalled?"
date: 2008-11-10
forum: General Help
---

### Post by abcuser on 2008-11-10
Hi,
I have installed Ubuntu 8.10, uninstall software that I don't need and install new packages like OpenOffice 3.0 etc. I have install/uninstall more then 50 applications. So I polished Ubuntu to my needs.

Is there any simple way of saving this "my new distribution" to CD and install it on another PC at my friends? I just don't like to install/uninstall all 50+ applications over again at my friends - it would be just nice if "my distro" could be installed/restored on any other computer. It would be nice to have some kind of silent install, that I could just give CD to my friend and say: "Put CD in CD-drive and don't touch anything until install/restore finishes."

Any idea how to make a my own distro with 100% compatibility with Ubuntu repository.
Regards,
Abcuser

---

### Post by scouser73 on 2008-11-10
> **abcuser said:**
> Hi,
I have installed Ubuntu 8.10, uninstall software that I don't need and install new packages like OpenOffice 3.0 etc. I have install/uninstall more then 50 applications. So I polished Ubuntu to my needs.

Is there any simple way of saving this "my new distribution" to CD and install it on another PC at my friends? I just don't like to install/uninstall all 50+ applications over again at my friends - it would be just nice if "my distro" could be installed/restored on any other computer. It would be nice to have some kind of silent install, that I could just give CD to my friend and say: "Put CD in CD-drive and don't touch anything until install/restore finishes."

Any idea how to make a my own distro with 100% compatibility with Ubuntu repository.
Regards,
Abcuser

What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by philinux on 2008-11-10
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by abcuser on 2008-11-10
@scouser73, thanks for help. I don't understand, is installing APTonCD really necessary? Why not just install [Remastersys](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)?

BTW, I am reading [Remastersys wiki](http://klikit.pbwiki.com/Remastersys+tutorial+by+dedoimedo) and there is a note: "Please note that you must close all windows and **unmount network shares while running the utility**". What is "network share"? Is this samba directory, network mount of remote file system...?
Thanks,
Abcuser

---

### Post by scouser73 on 2008-11-10
APTonCD is used for all the stuff you have downloaded from the repositories.
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

> What is APTonCD?

APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs (you choose the type of media) with all of the packages you've downloaded via APT-GET or APTITUDE, creating a removable repository that you can use on other computers.
APTonCD will also allow you to automatically create media with all of your .deb packages located in one especific repository, so that you can install them into your computers without the need for an internet conection. 

I recommend that it's used with Remastersys.

I'm unsure what it means by Network Share, I've had no problems using both of the products.

---

### Post by abcuser on 2008-11-12
Hi,
I used "backup" from GUI and iso image was created. I tested this iso image, but my userid home directory was not included in backup image. I would also like to include my home direcotry, because I have installed wine which is in my home .wine directory.

Is there way to include all!!! files when making backup?
Regards

---

### Post by eaglemystic69 on 2010-03-08
Hmm, anyone on this thread any longer . . ..

I want to do the same.  Although APTonCD only clones what is in /var/cache/apt/archive.  Presently there are very few packages listed/saved in it which means that does not back up all installed packages as much as duplicates whats in that folder.  

What are my options now?

Is there a way to simply drag and drop a folder or folders with all apps in them onto my external and after reinstallation copy in the new apps?

---

### Post by sgosnell on 2010-03-08
One way is to open a terminal and enter ```
dpkg --get-selections > ~/my-packages
```That will save a list of all your current packages to a file named 'my-packages'.  Save that file elsewhere, as a backup, in addition to that, just in case.  To restore your packages, put the file into your new home directory, and then enter ```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```.

You can also use mondo to make a backup of your entire system, and restore it later to a blank drive.  It will restore partitions, files, everything if that's what you need.  Remastersys is also a possibility.

---

### Post by eaglemystic69 on 2010-03-08
Thank you for your response [sgosnell]("http://ubuntuforums.org/member.php?u=774876").  

I have used that command and it only creates an output of installed packages.  Yes, I can then use synaptic or CL to reinstall, though it still requires an internet connection . . . fast reliable one.  

Im looking to create a repos DVD so I can reinstall all my packages into which ever dist  I prefer and when a restore is needed.  Right now Im over buggy karmic, and prefer to go back to Jaunty and restore my packages and home/. . . just like "abcuser" who started this thread.  

Im checking out Remastersys to make an ISO, though it used to backs up a happy system, Karmic $%#@*%!  All I want are the important custom apps and settings.  I realize all app preferences are stored in home/ as hidden files.  

Can I just make a drag/drop copy of all my apps and configs ?. . . Apple had them all contained in one folder unlike W.  That would be easier than experimenting with code and backup apps right now.  Been around with a handful of backup apps that are not specifically what I want to have.

---

### Post by sgosnell on 2010-03-08
The first command makes a list of installed packages.  You can edit it as necessary, to delete things you don't need or are already installed.  The second one downloads all the packages listed in 'my-packages' and installs them.  It can take awhile, but it works.  Have you looked at mondo?  I don't think there is a way to just drag and drop everything you have installed, because it goes to different places.  You can use grsync, which is a graphical frontend for rsync, and get much of the same thing, if you know where everything is.  Most of it should be in /usr, but there are settings in /etc and other places, too.  If you want everything, you need to back up your entire system.

---

