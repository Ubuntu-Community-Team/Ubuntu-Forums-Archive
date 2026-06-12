---
title: "Serious Issues with installing Flash Player in Ubuntu 8.04"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by Newbie1984 on 2009-06-09
I have scoured the forum making sure my answer was not already posted. It was not.

I have tried many different ways to get Flash to work on my computer. I have been using Ubuntu for almost 2 years..but still i know absolutely nothing about it. I had Flash installed once before, when the person who gave me this computer installed it for me, alas now it is so outdated it doesn't work anymore.

I don't know what any commands or anything of that sort mean(yet!) I just want to know how to get Flash working correctly on my Hardy 32 bit Ubuntu.


The few times I have tried I did this a few of the regular sudo commands and nothing works. I tried removing flashplugin nonfree and reinstalling it to try and use the flash program in the repositories...still cannot see video or instant message anyone.

This is all that I have tried so far:

```
crystal@crystal-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

What does "already the newest version" mean? Shouldn't that mean Flash should be working if it's already the latest one?

After that I did this to make sure i had all the other current updates:

```
crystal@crystal-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319) hardy/restricted Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://us.archive.ubuntu.com hardy Release 
Hit http://us.archive.ubuntu.com hardy-updates Release              
Hit http://security.ubuntu.com hardy-security/main Packages         
Hit http://us.archive.ubuntu.com hardy/main Packages                
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Reading package lists... Done
crystal@crystal-desktop:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate

```

The last part of that has completely baffled me(OK, maybe all of it has)


Someone, anyone, if you can take the time to help me learn how to correctly do this, I will be much appreciated.
):P

---

### Post by confused57 on 2009-06-09
Go to the Adobe site & download the "deb for Ubuntu 8.04":
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Next open Synaptic Package Manager, do a search for "flashplayer" & completely uninstall flashplugin-nonfree.

Then double-click on the deb files, which should be on your desktop.  Gdebi will open, select to install flashplayer.

If you want to see if the newest flashplayer is installed, open Firefox, click on Tools--Add-ons--Plugins, Shockwave Flash should now show 10.0...

---

### Post by Newbie1984 on 2009-06-10
> **confused57 said:**
> Go to the Adobe site & download the "deb for Ubuntu 8.04":
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Next open Synaptic Package Manager, do a search for "flashplayer" & completely uninstall flashplugin-nonfree.

Then double-click on the deb files, which should be on your desktop.  Gdebi will open, select to install flashplayer.

If you want to see if the newest flashplayer is installed, open Firefox, click on Tools--Add-ons--Plugins, Shockwave Flash should now show 10.0...

i did everything you said..and after that i went to Tools>Add-Ons>Plugins and Flash is not listed at all..not even an outdated version. This is all the plugins that are listed in the tab:
[B]Default Plugin
Dem Print Plugin for unix/linux
DiVx Web Player
GCJ Web Browser Plugin (using IcedTea) 1.0
Helix DNA Plugin: RealPlayer G2 Plug-in
iTunes Application Detector
QuickTime Plug-in 7.2.0
Totem Web Browser Plugin 2.22.1
VLC Multimedia Plugin 
Windows Media Player Plug-in 10

[/B]still can't use Flash same as before. websites still ask me to install Flash 9(or10)

p.s. I have no idea what any of those plugins that ARE installed do or why they are even there.:(

---

### Post by confused57 on 2009-06-10
I'm not sure what the problem is with your computer, the instructions I provided have worked on several different installations of Hardy 8.04.

Try opening Synaptic Package Manager, search for & install "ubuntu-restricted-extras", then see if flash works.  If it does, then follow the previous directions I gave to install the latest version of flashplayer.

You might want to consider downloading & installing the latest iso for Hardy 8.04.2, especially if you have a separate /home partition.

---

### Post by Newbie1984 on 2009-06-11
Thanks, somehow i must have done something and got it working...when i first did everything you said it didn't work. But now it is working. Thanks so much for your help!!

---

### Post by confused57 on 2009-06-11
Thanks for the update, glad you got it working without too much further hassle "tweeting" your system.

---

### Post by VadimRadionov on 2009-06-13
Hi there,

I have the same problem after upgrade (yesterday) from gutsy to hardy.  I removed flashplugin-nonfree and installed ubuntu-restricted-extras and adobe-flashplugin from adobe site.  

What I see is /usr/lib/firefox/plugins/flashplugin-alternative.so 
that links to /etc/alternatives/firefox-flashplugin 
that links to /usr/lib/adobe-flashplugin/libflashplayer.so
but, unfortunately, Firefox does not -- it shows the same list of 10 plugins mentioned above.

Any further suggestions?

Thank you in advance

---

