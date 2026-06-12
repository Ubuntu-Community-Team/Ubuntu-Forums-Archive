---
title: "Installing OpenOffice 3.0"
date: 2008-10-26
forum: General Help
---

### Post by MeanStreak on 2008-10-26
Could someone please post a tutorial on installing OpenOffice 3.0. The documentation currently available is terminal-based, however the commands do not work if your package is not identical to that discussed in the tutorial.

People often ask why Ubuntu/Linux isn't leading the world in desktop penetration. The fact that I've now spent over 30 minutes trying to install a simple app like OpenOffice 3 would be one reason.

---

### Post by Isilion on 2008-10-26
what tutorial are you following?

I installed OpenOffice 3  days ago without problems. Once you have uncompressed OOo and have the *.deb files, type in console

sudo dpkg -i *.deb (only if you dont have any other deb file in the directory)

---

### Post by noremac on 2008-10-26
> **Isilion said:**
> what tutorial are you following?

I installed OpenOffice 3  days ago without problems. Once you have uncompressed OOo and have the *.deb files, type in console

sudo dpkg -i *.deb (only if you dont have any other deb file in the directory)

I used this same tutorial and was not successful at all. 

I had a bunch of i386 errors, one for each .deb file.

I read a little into it and saw this in a thread from May elsewhere that you had to do this:

```
For those who wish to install on 64 bit;

Download the 32 bit package as described in the tutorial

everything is the same up to the point of installing the packages, so extract etc. the same as described.

before you install the packages make sure you have the 32 bit libs installed;

sudo apt-get install ia32-libs

Then use the same command to install the debs but with ‘–force-architecture’ added, so the install command will become;

sudo dpkg -i –force-architecture ~/Desktop/BEA300_m2_native_packed-2_en-US.9301/DEBS/*.deb


```

Is that still the only way, or is there a 64-bit version now that I am missing?

---

### Post by MeanStreak on 2008-10-26
Thanks, but no joy - there is no .deb. See below:

```
charles@charles-desktop:~/Desktop$ cd 
charles@charles-desktop:~/Desktop$ cd OOO300_m9_native_packed-1_en-US.9358
charles@charles-desktop:~/Desktop/OOO300_m9_native_packed-1_en-US.9358$ sudo dpkg -i *.deb
[sudo] password for charles: 
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
charles@charles-desktop:~/Desktop/OOO300_m9_native_packed-1_en-US.9358$ 
```

---

### Post by ju2wheels on 2008-10-26
Try this, but make sure you completely uninstall your current open office first. By the way dont try what you did before without looking for the proper x86_64 versions if they are available....

```

wget http://mirrors.isc.org/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz
tar xvfz OOo*.gz
cd  OOO300_m9_native_packed-1_en-US.9358/DEBS/
sudo dpkg -i *.deb
cd desktop-integration/
sudo dpkg -i *.deb

```

---

### Post by MeanStreak on 2008-10-26
Question: how do I uninstall OOo 2.4? Add/Remove Applications says there are dependencies preventing removal (I've never infact succeeded in uninstalling anything via this tool), and Synaptic breaks OOo into multiple packages, making a simple uninstall difficult - will I lose Evolution?

---

### Post by ju2wheels on 2008-10-26
I was able to unistall OpenOffice 2.4 without losing Evolution. It will definitely uninstall alot of other dependent packages but if you uninstall it correctly it should not affect any other major packages.

I started by opening synaptic, clicking on search and entering "openoffice.org" as the search term. I then began unchecking the relevant openoffice.org packages. When I do the search now the only packages I have installed (related to open office) that come up on my Intrepid machine are the following:

ooobasis3.0*    [OO 3.0 packages]
openoffice.org3* [OO 3.0 packages]
openoffice.org-base-core
openoffice.org-debian-menus [OO 3.0 menu links]
openoffice.org-ure    [I dont think this one is part of 3.0]


Whatever else you have there now in terms of openoffice.org you can uncheck and tell it ok to removing dependencies.

---

### Post by mosaic2s on 2008-10-26
it required some effort yes, but worth it. the open office 3 is way ahead.

check out following link - 
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

it worked for me.

---

### Post by MeanStreak on 2008-10-26
Will OOo 3 be available via Synaptic in Intrepid? I might wait till then. The idea of individually uninstalling components of OOo without understanding the impact on Evolution, etc. is ridiculous. 

I don't understand how OOo 3 can be considered complete production ready release when this level of complexity constitutes the installation process.

---

### Post by ju2wheels on 2008-10-26
It will be but probably not for a few weeks after the Intrepid release most likely. The developers havent had the chance to rebuild the packages for Ubuntu in a manner that enables upgrading through synaptic. I read somewhere that they changed the packaging scheme or something, theres a thread about it on the forums here somewhere that was posted this week.

Honestly I dont see anything wrong with the install process, like I said I still have Evolution and it works just fine unless I misunderstand what mysterious tie you are talking about here (I dont use it but I can launch it fine so there is no ill side effect)...

---

### Post by ju2wheels on 2008-10-26
Just to soothe your mind here is proof that they do work together:
[[IMG]http://img371.imageshack.us/img371/5106/screenshotbo7.th.jpg[/IMG]](http://img371.imageshack.us/my.php?image=screenshotbo7.jpg)[[IMG]http://img371.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by MeanStreak on 2008-10-29
Thanks for all the replies. OOo 3 didn't make the 8.10 release, so I'll proceed with the command line installation process - uninstall OOo entirely via Synaptic and install OOo3 following the command line.

The complexity with the OOo3 upgrade path is just par for the course when using Ubuntu - in pointing it out I'm attempting a devil's advocate position - developers need to be aware that this complexity is preventing the wider penetration of Linux in the average end user (read: non-technical, GUI-centric end user) market. 

Roll on 8.10!

Edit: I found this upgrade guide for 8.10 - looks like the way to go!
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by mitchellcipriano on 2008-11-04
> **MeanStreak said:**
> 

Roll on 8.10!

Edit: I found this upgrade guide for 8.10 - looks like the way to go!
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Does anyone know if this will present any problems when OpenOffice is backported?

---

### Post by Ryadt on 2008-11-04
Backport updates are quite stable. It should be as stable as installing Oo3 deb.

---

### Post by scouser73 on 2008-11-04
Here's an excellent tutorial for installing OpenOffice 3; [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/")

---

### Post by kaudley on 2008-11-04
> [http://news.softpedia.com/news/How-T...10-96449.shtml](http://news.softpedia.com/news/How-T...10-96449.shtml)

Folks, it doesn't get much easier than that....  Add a repo and do an update - it's not rocket science.

):P

---

### Post by snowpine on 2008-11-04
Agreed; no command line required and it takes just a few minutes (depending on your connection speed) to install OO3.

Kudos to anyone with the patience to install it from the .deb files, but I like the repository method better. :)

---

