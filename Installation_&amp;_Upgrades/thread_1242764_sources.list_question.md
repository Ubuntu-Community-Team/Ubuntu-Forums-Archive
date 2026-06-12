---
title: "sources.list question"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by klaus0009 on 2009-08-17
Hello,
 
I'm using Ubuntu 9.04.
 
I recently downloaded a repository mirror using apt-mirror. I have moved all the data to a portable harddrive. I'd rather not burn dvds and would like to just be able to pull the data off of the harddrive, which is currently connected via usb.
 
The drive mounts fine and can be seen in the /dev/ and the /media/ dirs.
 
What should the path look like in sources.list to point towards this drives and so I can just: apt-get install <package> ?
 
Thanks in advance...
 
Klaus

---

### Post by klaus0009 on 2009-08-17
[SIZE=1]I came up with something that works for me and thought I'd post it.
Please post improvements.
---
# First create a mirror using apt-mirror (plenty of tutorials on this)
# In my case, I wanted to have a portable repository that did not consist 
# of dvds or cds, could easily be used cross different hosts, in different
# labs, and one that did not rely on any type of network (inter/intra)
# connection.
# Once apt-mirror concluded I placed the content on an External HDD
# with a usb interface
# Extract *.deb packages from the mirror created with apt-mirror and
# create an archive on the external HDD (local repository)
 
find /media/EXT_HDD/apt-mirror/mirror/ -iname *.deb | xargs cp -t /media/EXT_HDD/apt-mirror/archives 
 
# On the host, rename the package archive /var/cache/apt/archives to
# something like /var/cache/apt/archives.orig to preserve current state
 
sudo mv /var/cache/apt/archives/ /var/cache/apt/archives.orig/
 
# On the host, create a symbolic link that allows cross device linking
 
ln --symbolic /media/EXT_HDD/apt-mirror/archives /var/cache/apt/archives
 
# On the host, save the original sources.list file to preserve current state
 
sudo mv /etc/apt/sources.list /etc/apt/sources.list.orig
 
# On the host, modify /etc/apt/sources.list get from HDD only
###############################################################
#
# source.list for local repository
# Modify as needed depending on where source is stored
#
# Author: klaus
# Aug 17, 2009 -- 10:31
#
###############################################################
 
# Probably best to keep dynamic stuff like security updates out of here.
 
deb file:///media/EXT_HDD/apt-mirror/mirror/archive.ubuntu.com/ubuntu/ jaunty main
 
deb file:///media/EXT_HDD/apt-mirror/mirror/archive.ubuntu.com/ubuntu/ jaunty universe
 
deb file:///media/EXT_HDD/apt-mirror/mirror/archive.ubuntu.com/ubuntu/ jaunty multiverse
 
# EOF
--------------------------
That seemed to work for me. You can toggle sources.list.orig and archives.orig very easily to revert
[/SIZE]

---

### Post by stlsaint on 2009-08-17
Thanks for the tutor..i never really thought about doing that but it sounds like a great idea!!

---

### Post by klaus0009 on 2009-08-18
[FONT=Arial][SIZE=1]One last update on this tek.[/SIZE][/FONT]
[FONT=Arial][SIZE=1][/SIZE][/FONT] 
[FONT=Arial][SIZE=1]After getting all the deb packages and creating the archives folder on the external usb, and then creating the symbolic link to the archives on the host at /var/cache/apt/, you may recieve the following error:[/SIZE][/FONT]
[FONT=Arial][SIZE=1][/SIZE][/FONT] 
[FONT=Arial][SIZE=1]<Archive directory /var/cache/apt/archives/partial is missing.>[/SIZE][/FONT]
[FONT=Arial][SIZE=1][/SIZE][/FONT] 
[FONT=Arial][SIZE=1]To fix this:[/SIZE][/FONT]
[FONT=Arial][SIZE=1][/SIZE][/FONT] 
[FONT=Courier New][SIZE=1][FONT=Arial]1. cd <your external hdd>/apt-mirror[/FONT][/SIZE][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=1] [/SIZE][/FONT][/FONT]
[FONT=Courier New][SIZE=1][FONT=Arial]2. Type ls check to make sure archives folder is displayed in case you dont see the archives folder create the folder[/FONT][/SIZE][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=1] [/SIZE][/FONT][/FONT]
[FONT=Courier New][SIZE=1][FONT=Arial] sudo mkdir archives if you already have the archives folder then skip this step.[/FONT][/SIZE][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=1] [/SIZE][/FONT][/FONT]
[FONT=Courier New][SIZE=1][FONT=Arial]3. type cd archives , create the partial folder by typing sudo mkdir partial[/FONT][/SIZE][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=1] [/SIZE][/FONT][/FONT]
[FONT=Courier New][SIZE=1][FONT=Arial]4. type sudo apt-get autoclean to make sure apt is working properly.[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=1][/SIZE][/FONT] 
[FONT=Arial][SIZE=1][/SIZE][/FONT] 
[FONT=Arial][/FONT]

---

