---
title: "Is there a way to De-Upgrade?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by quietbear on 2009-11-02
Just upgraded to the new 9.10, and it messed a lot of things up, namely my video editing software Kdenlive, and my audio, and when I watch movies I get slow frame rates now (didnt before), and I cant watch DVDs anymore either (could before).

So is there a way to go back to the previous version?

---

### Post by mrdak on 2009-11-03
> **quietbear said:**
> Just upgraded to the new 9.10, and it messed a lot of things up, namely my video editing software Kdenlive, and my audio, and when I watch movies I get slow frame rates now (didnt before), and I cant watch DVDs anymore either (could before).

So is there a way to go back to the previous version?


C'mon........ you don't mean you wanna degrade now..... do you?

How degrading.;) Try the latest driver for your vid card.

---

### Post by Dark_Stang on 2009-11-03
Boot the old live CD and reinstall. Or, you could boot the new version and reinstall. Upgrades are prone to issues and a clean install is usually more desirable.

---

### Post by quietbear on 2009-11-03
That has nothing to do with it, everyone who uses Kdenlive is having problems.

They say to de activate the pulse audio and tell us how, when I do it, even though the terminal says that nothing happened, kdenlive works, but no audio on the rest of the system does, then when I restart, I have to do it all over again.

Yes I am saying that I want to degrade, I liked it better when it actually worked.  It is not just the audio, I cant watch DVDs anymore, when I watch movies I get slow frame rates as well, and I have only been upgraded for a day or so, so I am sure there are more things that are all messed up.

---

### Post by quietbear on 2009-11-03
> **Dark_Stang said:**
> Boot the old live CD and reinstall. Or, you could boot the new version and reinstall. Upgrades are prone to issues and a clean install is usually more desirable.

But then I will have to backup and re install all my stuff, there isnt an easier way to revert my system to when it was working like 2 days ago?

---

### Post by mrdak on 2009-11-03
yeah there's an easy way to re install.... it's not that much of a pain. Just do a fresh install...........

---

### Post by quietbear on 2009-11-03
It is a pain, because I have to then re-install all my programs and all my files, and then I have to spend the day upgrading everything, remembering how I fixed all the old things that where wrong, all in all it takes days.

Isnt there an easier way?

Why release a new edition if it is going to cause all these problems?

---

### Post by Dark_Stang on 2009-11-03
> **quietbear said:**
> It is a pain, because I have to then re-install all my programs and all my files, and then I have to spend the day upgrading everything, remembering how I fixed all the old things that where wrong, all in all it takes days.

Isnt there an easier way?

Why release a new edition if it is going to cause all these problems?
Any time you install a new OS you may have problems. If this was a system you rely heavily on you may want to get a test partition setup to install to before going full gung-ho with it.

---

### Post by quietbear on 2009-11-03
And now flash doesnt work anymore either, and I cant install it as it returns an error code when I try to.  It was working earlier tonight.  How can I get it working back?

> quietbearr@quietbearr-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libavutil-unstripped-49 mplayer-skins mplayer akiradnews
  libavcodec-unstripped-52 libpostproc-unstripped-51 binutils-static
  libavformat-unstripped-52 libgcj-common libavfilter-unstripped-0
  libswscale-unstripped-0 optlibx11-noxcb-data libavdevice-unstripped-52
  optlibx11-noxcb-6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adobe-flashplugin
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following packages will be upgraded:
  adobe-flashplugin
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/4,018kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 157358 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.32.18-1 (using .../adobe-flashplugin_10.0.32.18-1jaunty1_i386.deb) ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing /var/cache/apt/archives/adobe-flashplugin_10.0.32.18-1jaunty1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/adobe-flashplugin_10.0.32.18-1jaunty1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

