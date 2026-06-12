---
title: "Download stalls after 50-60 KB  (Kubuntu 9.04)"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by bumpkin on 2009-07-12
I have a problem that only occurs with the ubuntu repositories. When I download a package with apt-get or PackageManger the download stalls after 50-60KB. I have to then restart the process over and over to get it to complete. 
 
I also tried to install with apt-get libapache2-mod-wsgi_2.3 and getting the following

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libapache2-mod-wsgi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-wsgi has no installation candidate

I was able to download this just two months ago. I was able to manually download but can't get apt-get to recognize it. 

Somehow I messed up the repository list but with the download problem I can't get packagemanager to download  package information. It no longer lists libapache2-mod-wsgi.

---

### Post by Partyboi2 on 2009-07-12
> I have a problem that only occurs with the ubuntu repositories. When I download a package with apt-get or PackageManger the download stalls after 50-60KB. I have to then restart the process over and over to get it to complete.

Hi, try changing your download server to another one.

> This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-wsgi has no installation candidate
Check that you have the universe repo enabled under the package manager.

---

### Post by bumpkin on 2009-07-12
I tried changing my download server and a check was performed by PackageManager to find the best server but the result was no server was satisfactory and that I should check my network connection.

The strange thing is that I have no problem downloading files from anywhere else only Ubuntu repositories. 

Is it possible to download the package lists manually? I have been trying to download the main package list w/o success. What file do I need to download at us.archive.ubuntu.com?

---

### Post by skotu on 2009-08-01
> I have a problem that only occurs with the ubuntu repositories. When I download a package with apt-get or PackageManger the download stalls after 50-60KB. I have to then restart the process over and over to get it to complete.I'm using Xubuntu 8.10 and had the same problem recently... files were downloading at about 25% of my usual speeds and would stop downloading very soon after starting. This was only happening with Synaptic Package manager, Add/Remove, or apt-get. Downloading via Firefox was fine, no problems. I changed the download server using Synaptic Package Manager: Applications > System > Synaptic, click Settings > Repositories, then select a different download server in the dropdown menu. I was having problems on the main US and Canada servers (I'm in the US). I manually selected a different server near where I live and now my downloads are back to normal. Speeds are 100%, downloads are fast and don't stop anymore.

---

