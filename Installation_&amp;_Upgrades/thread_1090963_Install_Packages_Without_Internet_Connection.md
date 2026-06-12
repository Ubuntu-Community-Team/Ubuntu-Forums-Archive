---
title: "Install Packages Without Internet Connection"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by sweeny_here on 2009-03-08
Recently I was backing up Ubuntu 8.10 when it crashed out.On restart the Network Manager was no longer available.I attempted to reinstall Network Manager using Synaptic package manager.It is unable to detect the packages related to Network Manager.

I also tried loading the original installation CD via the third party software option in Synaptic, but it is unable to read the packages from the original installation CD.

Is there a workaround to this issue in the form of downloading all Ubuntu 8.10 packages from a central repository and installing these packages and any dependencies from a harddisk / CD in offline mode?

---

### Post by Neo_The_User on 2009-03-08
Well the only way you could do this would be to install the Ubuntu repos on a DVD or something and then go edit sources.list and scan the CD for packages rather than a server.

[ftp://ftp.heanet.ie/pub/ubuntu/](ftp://ftp.heanet.ie/pub/ubuntu/)

or...

[http://www.linuxcd.org/caddie.php?id_version=3690&PHPSESSID=7d6b96c01b6b7b66890fe628d960d924&id_version=3690](http://www.linuxcd.org/caddie.php?id_version=3690&PHPSESSID=7d6b96c01b6b7b66890fe628d960d924&id_version=3690)

---

### Post by ugm6hr on 2009-03-09
debmirror allows you to create a local repository on your network.

This tutorial explains how to turn them into DVDs (if you want)
[http://www.howtoforge.com/dvd_images_of_ubuntu_repositories](http://www.howtoforge.com/dvd_images_of_ubuntu_repositories)

---

### Post by sweeny_here on 2009-03-14
Thanks for the replies guys and sorry for taking so long to respond (new job and up the walls).

Right - I found a solution, to reinstall core Ubuntu packages from a CD, for the network manager application as it was accidentally corrupted during a system backup. Here are they steps that worked on Ubuntu 8.10 -

1.Download ["Ubutnu Alternative CD"]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") and select your operating system version.The regular Ubuntu iso image which most system are installed from,will not work in this example, but the alternative iso will!

2.Burn the alternative iso matching your system type (Xubuntu,Kbuntu...) and version (7.10,8.04...) to cd.

3.Edit the apt-get source repositories reference file, by commenting out all sources except for the cdrom option,using the hash (#) symbol. 
> sudo gedit /etc/apt/sources.list

4.Try command
> sudo apt-cdrom add

If the system is unable to mount the cd,the workaround could be to mount the cd manually.The following command may vary depending on your filesystem naming convention.
> sudo mount /dev/cdrom /media/cdrom0

5.If manually mounted,run apt-cdrom telling it that the cd device is already mounted,and to add an entry for this cd to the /etc/apt/sources.list
> sudo apt-cdrom -o APT::CDROM::NoMount=True add

6.Packages can now be installed either from the command line or by using Synaptic Package Manager
> sudo apt-get install <package-name>

Once your back online, remember to uncomment to the lines edited in etc/apt/sources.list so that your automatic updates will be maintained!

---

