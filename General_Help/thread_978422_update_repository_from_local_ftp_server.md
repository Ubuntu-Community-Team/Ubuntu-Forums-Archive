---
title: "update repository from local ftp server"
date: 2008-11-11
forum: General Help
---

### Post by Battalion on 2008-11-11
Hi,

I'm using ubuntu 8.10 and would like to update my repository using either Synaptic or apt-get konsole from our university local ftp server.  The directory to the ubuntu folder on the ftp is ftp.up.ac.za/ubuntu and would like to use this for updating everything. 

How do i accomplish this?

---

### Post by geirha on 2008-11-11
You want to mirror the package archive? [https://wiki.ubuntu.com/Archive/Mirroring](https://wiki.ubuntu.com/Archive/Mirroring)

---

### Post by Battalion on 2008-11-11
no i don't want to mirror it but want to use the ftp server for updating my repository on my local pc

---

### Post by geirha on 2008-11-12
Well, when there are updates available, open System -> Administration -> Synaptic, click the Mark all upgrades button, then select File -> Generate package download script. Run that script on your ftp-server to have it download the updates, then you can download those packages from your ftp-server and install them. 

If you can install programs on the ftp-server you may want to have a look at [https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo](https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo) for an even easier way.

---

### Post by Battalion on 2008-11-12
I will try this out.  I have identified the main problem with my synaptic...it fails COMPLETELY to connect to the local ftp server although they are using the same proxy.

I have tried to manually update the /etc/apt/sources.list to rather use the lines:
deb [http://ftp.up.ac.za](http://ftp.up.ac.za) 
deb-src [http://ftp.up.ac.za](http://ftp.up.ac.za) 

Then i run >sudo apt-get update< on the konsole but it returns the message that the package list could not be downloaded and many other files could not download

---

### Post by geirha on 2008-11-12
A repository has a specific directory structure and certain files that shows which packages are available and other magic. If you set your sources.list back to default and manually download the deb-files from the ftp-server to /var/cache/apt/archives/, then update-manager should find the files locally and not bother to try to download them from the repository.

---

### Post by Battalion on 2008-11-14
downloading the packages manually is troublesome especially when dependencies are considered. I am still working on the problem but i'm very close to finding the solution.  The main problem is that the server is not dedicated to ubuntu only, but many linux distros.

Can synaptic pick up all the packages downloaded into the /var/cache/apt/archieves?

---

### Post by geirha on 2008-11-14
All package managers (apt-get, aptitude, update-manager, gnome-app-install, synaptic etc) more or less do the same thing. When they are commanded to install a package, or do an update, they first check the package lists (which gets downloaded to /var/lib/apt/lists by apt-get update or the other package managers' equvialents) for the latest version of the packages to be installed, then they check if the packages are available in /var/cache/apt/archives. If they're there, they install, if not, they try downloading them to /var/cache/apt/archives from the repositories.

Unless space is an issue, mirroring sounds like the best way to go.

---

### Post by Battalion on 2008-11-18
Thanks for the information about how package managers work, i think it gives me a better understanding of it. 

Well people, i have solved my problem!!! The issue was that updating from the ubuntu folder on the server (ftp.up.ac.za/ubuntu) just wasn't working, it reported errors for intrepid packages.  What i did to solve the problem was direct the apt-get to where packages for intrepid which was:
>>ftp.up.ac.za/mirrors/ubuntu/ubuntu-archive

This is the line used to change my sources.list in /etc/apt.  This worked perfectly, then i could install AptonCD to take the installed packages and install them on my home PC which had no internet.

I prefer AptonCD, i am still yet to try aptproxy, maybe someday i will.

Thanks geirha for your help

---

