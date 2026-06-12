---
title: "Update OpenOffice from Update Manager?"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by upapilot on 2008-12-13
I was just wondering if i could just update my OpenOffice 2.4 to 3.0 directly from the Update Manager/ similar application):P

---

### Post by Partyboi2 on 2008-12-13
You could add 
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```to your sources.list then install open office 3
Open a terminal (Applications Accessories>Terminal)
then ```
gksu gedit /etc/apt/sources.list 
```add the above repos
then save and back in the terminal
```
sudo apt-get update
```then[FONT=monospace]
[/FONT]```
 sudo apt-get dist-upgrade
```

Or open Update manager and install upgrades after adding the above repo to sources.list

---

### Post by inobe on 2008-12-13
you mentioned direct, just to help another way

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

if your running 64bit' you can grab the package here

[ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz/](ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz/)

---

### Post by upapilot on 2008-12-13
> **Partyboi2 said:**
> You could add 
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```to your sources.list then install open office 3
Open a terminal (Applications Accessories>Terminal)
then ```
gksu gedit /etc/apt/sources.list 
```add the above repos
then save and back in the terminal
```
sudo apt-get update
```then[FONT=monospace]
[/FONT]```
 sudo apt-get dist-upgrade
```

Or open Update manager and install upgrades after adding the above repo to sources.list

I feel threatened to use such commands (please don't take it negatively if you're not a crook):?:neutral:.

---

### Post by pjalegria on 2008-12-13
Its safe to update to open office 3 on Interpid?

---

### Post by MonkeyPaw on 2008-12-14
This worked perfectly for me:

[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

I'm running 8.04, and have 0 issues running OoO3. 3 seems a little faster even.

---

### Post by Skripka on 2008-12-14
> **pjalegria said:**
> Its safe to update to open office 3 on Interpid?

So long as you don't have the openoffice.org-kde package installed

---

### Post by abn91c on 2008-12-14
> **upapilot said:**
> I was just wondering if i could just update my OpenOffice 2.4 to 3.0 directly from the Update Manager/ similar application):P

follow this guide [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

