---
title: "making offline repositories"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by knit.manish on 2009-10-06
hiii i was wondering that is there some method by which i can make repository on my system and then use it on some other ubuntu system which is not connected to internet.
we can do these things in windows

---

### Post by samigina on 2009-10-06
Try AptOnCD, is in synaptic. 

Or just install all the software that you want and then copy the content of /var/cache/apt , you will find all the deb packages. In this way you will need to copy the etc/apt/sources.list too.

---

### Post by knit.manish on 2009-10-06
i had tried this method it is somewhat longer
can i have something like that we have repository some where in my system and i can add that source list.
i used one such method for the feisty fawn 
the apt line was 
deb file:///home/user/all feisty local
i got it from my friend but lost those softwares
currently i m using jaunty edition

---

### Post by samigina on 2009-10-08
Look here, from [http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/](http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/), remember that the three ways (aptoncd, copy cache, and this) just will works in same ubuntu releases and architecture (32, 64), so with Karmic coming soon, maybe you will want to wait a little. Excuse me for my english, i use to speak spanish.

> I was going through my ***/var/cache/apt/archives*** folder the other day and I thought to myself, “So will I have to re-download all these packages if I do a clean install? It’d be cool to build my own APT repository with the 3000+ packages in my local cache.” I mean, internet access is not cheap here in Ghana and the speed is nothing to write home about. The only snag was I didn’t know how to do it. So I went hunting on google and it turned out a lot has been published on this topic. I found it all rather confusing, mostly geeks talking to other geeks in geekish, so I decided to write my own how-to for my much simpler mind.
 If your roaring to go and know what you’re doing, skip down to the [summary]("http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/#summary"). If you want to take things slow however, read on. Okay, enough talking already, let’s get our hands dirty…
 1) Create folders for the package files you plan to keep in your repository. Here is an example: in your home folder, create a new folder called ***repository*** in which you will keep all your downloaded packages. If you plan to burn the package files onto a CD, I suggest you create separate folders for each disk. The naming is up to you – **disk_1, disk_2**, etc (I’ll assume this naming convention throughout the rest of the tutorial). This is just to ensure that you use the next folder once your cache reaches the size of a CD (usually 700MB). If you are using a local hard drive or a DVD, you obviously have higher limits to keep in mind. If you do not plan to create a CD/DVD, you may simply dump all the files in the ***repository*** folder.
 2) The next step is to copy all your ***deb ***files ***(those files that end with .deb)***  to the repository folder(s). Open Nautilus, navigate to ***/var/cache/apt/archives*** and copy all the ***deb*** files to the appropriate folder(s). For instance, ***/home/<username>/repository/disk_1*** – keep an eye on the size of the folders. To do it in the terminal:[INDENT]**cp /var/cache/apt/archives/*.deb ~/repository/disk_1** 
[/INDENT]*If you have many files, it may take quite a while so be patient.*
 3) Change into your repository folder:[INDENT]**cd ~/repository/disk_1**
[/INDENT]4) Now do the following command to create the ***Packages.gz*** file that is needed to for Synaptic to “see” your repository:[INDENT]**sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz**
[/INDENT]I suggest you copy and paste this to avoid any typos.
 
[LIST]
[*]*Please note that every time you add any more .deb files to this folder, you have to create a new Packages.gz file using the above command before the new file(s) will show up in Synaptic (or Aptitude).*
[*]*Be sure to install the **build-essential** package **(sudo aptitude install build-essential) **before running the above command.*
[/LIST]
 There are several ways of using your newly created repository.
 **I) Keeping the files on a local hard disk…**
 Edit your ***/etc/apt/sources.list*** file like so:[INDENT]**gksudo gedit /etc/apt/sources.list**
[/INDENT]And insert this on a new line (preferably the first):[INDENT]**deb file:/home/username/repository/disk_1/ /**
[/INDENT]*Remember to replace **username** with your real username.*
 Reload your package index like this:[INDENT]**sudo aptitude update**
[/INDENT]**II) Using a CD/DVD as a repository:**
 a) Burn the ***repository*** folder onto a CD/DVD
 b) With the disc loaded in your drive, fire up Synaptic and click through the menus like this:
 Edit –> Add CD Rom.
 c) You will be asked to type in a description for the disc; type in anything, for instance: ***Offline Repository Disk 1***.
 d) Click Ok.
 [B]Summary
[/B]Go to **/var/cache/apt/archives** and copy your debian packages to a folder of your choice, for example, **/home/<username>/repository/**
 
[LIST]
[*]Change into the repository directory
[/LIST]
[INDENT]**cd /home/username/repository**
[/INDENT]
[LIST]
[*]And generate a **Packages.gz** file like this:
[/LIST]
[INDENT]**sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz**
[/INDENT]*Make sure **build-essential** is installed (**sudo aptitude install build-essential**) before you run the above command.*
 
[LIST]
[*]Add the following line to your sources.list file (**/etc/apt/sources.list**)
[/LIST]
[INDENT]**deb file:/home/username/repository/ /**
[/INDENT]*Remember to replace **username** with your real username*
 
[LIST]
[*]Reload your package index like this:
[/LIST]
[INDENT]**sudo apt-get update**
[/INDENT]That’s it… sit back, relax and enjoy the ride.
 I found the following tips for using Synaptic very useful:
 
[LIST]
[*]You might want to check out the online [sources.list generator]("http://www.ubuntulinux.nl/source-o-matic"). It will let you select various repositories for your sources.list. Once you get the output, simply replace the contents of your /etc/apt/sources.list file with it.
[/LIST]
 
[LIST]
[*]Now have a loom at the Synaptic settings (**Settings –> Repositories –> Settings**).
[/LIST]
 
[LIST]
[*]I suggest you decide if you always want to get the highest/latest version or if you want to stick to the feisty version.
[/LIST]
 
[LIST]
[*]Also, ensure that you have checked the option that allows downloaded packages to be kept in the cache, otherwise you will just have to download them again if you accidentally do an ***apt-get autoclean*** or something similar. Have fun. [IMG]http://s.wordpress.com/wp-includes/images/smilies/icon_smile.gif[/IMG]
[/LIST]
 Cheers,
Odzangba


---

### Post by a2z on 2009-10-08
Hey Samigina great method.

I was thinking of putting my archive on a 32G usb drive.
I don't quite understand yet how to make synaptics look to the usb drive. 
To me, your instructions appear to be using a terminal to tell it where to look?

I see there isn't a choice to add usb to synaptics. Surely there has to be another way to 
read these packages from a memory stick. Anybody? 
How about the import key? 


Thanks

a2z

---

### Post by samigina on 2009-10-09
For synaptic looking the usb just change the line (**deb file:/home/username/repository/disk_1/)** in the sources.list with the route to your usb, it look something like this **/media/sdb/.. **or wherever are mounted your usb stick.

The key is not needed.

Another way is just make an iso file and add this to synaptic like a cd, [B]sudo synaptic --add-cdrom /media/iso/
[/B]
And yes, many comands are for use in the console; read carefully the instructions and you will have no problem.

Cheers

---

### Post by samigina on 2009-10-09
I did a search in the forums and found this

[http://ubuntuforums.org/showthread.php?t=1045375](http://ubuntuforums.org/showthread.php?t=1045375)

Look at the section about how to mount the usb like a repository. At the final part dont erase ALL the content of your sources.list, just add the new lines.

---

### Post by a2z on 2009-10-09
> **samigina said:**
> I did a search in the forums and found this

[http://ubuntuforums.org/showthread.php?t=1045375](http://ubuntuforums.org/showthread.php?t=1045375)

Look at the section about how to mount the usb like a repository. At the final part dont erase ALL the content of your sources.list, just add the new lines.

Wohooo Excellent work samigina.
This is awsome!

a2z

---

### Post by ptn107 on 2009-10-09
[_debmirror_]("https://help.ubuntu.com/community/Debmirror")

---

### Post by lykwydchykyn on 2009-10-09
I just use apt-mirror.  Pretty easy to set up.

[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

---

### Post by a2z on 2009-10-09
Thank you all for helping.

---

