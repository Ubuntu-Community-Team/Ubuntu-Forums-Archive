---
title: "Why doesn't Firefox 3.5 install???"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by phinn on 2009-07-04
This is 2009, seriously? It really won't install? Seriously?

I tried like 3 PPAs none of them work or they have beta versions. This is ridiculous its so hard to install it with a great system like apt-get and it doesn't even work.

This is one of the biggest problems with Linux (and while it lasts it'll never go mainstream). There is no unified packaging system and I can't just grab an executable off Firefox's site like Windows and Mac users and install it.


Anyone have a ubuntu 9.04 firefox PPA? I searched everywhere for over an hour.

---

### Post by darolu on 2009-07-04
OK first you need to relax; every distro has different features and that include the way they manage software; this is a good thing, it keeps stuff improving and moving on, they are only ways to make it easier for you to get the applications you need.

I honestly don't know why it is taking Ubuntu developers so long to release a Firefox 3.5 binary (.deb), I don't have full insight on how it works but my guess is the new gecko version may be causing issues as other programs use it. we have no choice but to wait until the package is ready if we want to install it with aptitude/synaptic/dpkg.

But is not your only option, it is very simple to "install" Firefox when you download it from the mozilla site, you just have to untar the file and you are set, it is already compiled and ready to use.

Follow this steps:

1.- Go to [http://www.firefox.com](http://www.firefox.com) and download the Linux version of Firefox, you can find different languages and versions here: [http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

2.- Once you have the .tar.bz2 file, just untar it either using the GUI (simpler way is to right click) or "tar -xf filename.tar.bz2" on your console.

3.- You should have a "firefox" directory now, all you have to do now is run the "firefox" file with: "$~/firefox./firefox" on your console (make sure you use ./firefox or you'll run the 'regular' one); you can create a launcher with the command "~/firefox/./firefox" if you like.

4.- Enjoy. You can now safely watch naughty sites with the privacy thingie!

I hope this helps.

---

### Post by phinn on 2009-07-04
Okay thanks for the info, I've done that and moved this Firefox 3.5 into the /usr/lib directory with the other Firefox and created a symlink to /usr/bin/firefox for the binary.  It's working well now. Unfortunately I'll have to manually update it this way when updates come out but oh well.

On a side now, Firefox 3.5 has a lot of little improvements including nice javascript speed.

---

### Post by darco on 2009-07-04
> **darolu said:**
> 

Follow this steps:

1.- Go to [http://www.firefox.com](http://www.firefox.com) and download the Linux version of Firefox, you can find different languages and versions here: [http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

2.- Once you have the .tar.bz2 file, just untar it either using the GUI (simpler way is to right click) or "tar -xf filename.tar.bz2" on your console.

3.- You should have a "firefox" directory now, all you have to do now is run the "firefox" file with: "$~/firefox./firefox" on your console (make sure you use ./firefox or you'll run the 'regular' one); you can create a launcher with the command "~/firefox/./firefox" if you like.

4.- Enjoy. You can now safely watch naughty sites with the privacy thingie!

I hope this helps.

well thats good to know as I am running a x64 bit system and was just informed that tracemonkey is not included in FF 3.5 x64. I saw this how-to ([https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#Installing%2032-bit%20Edition%20of%20Firefox](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#Installing%2032-bit%20Edition%20of%20Firefox)) and it trashed my FF in a vm OS. I now d/l Minefield 3.6a1pre x64 which includes tracemonkey so we will see how it goes...thxs

darco

---

### Post by soho2014 on 2009-07-04
If you go here:

[http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html)

it will show you how to easily install it, such that your upgrades will also upgrade Firefox 3.5. It only takes a few minutes. Just copy and paste the commands into the terminal.

---

### Post by soho2014 on 2009-07-04
I forgot to warn you that this way of install it leaves behind Firefox 3.0 ,such that the icons can confuse you because the new Firefox is called: "Minefield 3.5" in Ubuntu, and it has a blue icon. 

You can manually uninstall the old version of firefox using Synaptic Manager.

---

### Post by aysiu on 2009-07-04
Ubuntu has a six-month release schedule. So every six months your entire system will be updated.

There are other Linux distros that are on "rolling releases," which means as soon as a newer version of the package is available, you can upgrade to it through the package manager. PCLinuxOS and Arch Linux are rolling releases. Maybe you would prefer to use those?

I love getting my whole system updated twice a year through Ubuntu's package management system.

If you want the latest Firefox in Ubuntu, though, this is probably the simplest way to get it:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by JoeNZ on 2009-07-04
I found that using Ubuntuzilla to install Firefox 3.5 was easy. Just follow the instructions and you'll be sweet.

[http://ubuntuzilla.wiki.sourceforge.net]("http://ubuntuzilla.wiki.sourceforge.net/#tochome6")

---

### Post by darolu on 2009-07-05
> **aysiu said:**
> Ubuntu has a six-month release schedule. So every six months your entire system will be updated.

There are other Linux distros that are on "rolling releases," which means as soon as a newer version of the package is available, you can upgrade to it through the package manager. PCLinuxOS and Arch Linux are rolling releases. Maybe you would prefer to use those?

I love getting my whole system updated twice a year through Ubuntu's package management system.

If you want the latest Firefox in Ubuntu, though, this is probably the simplest way to get it:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Yes but Ubuntu normal releases are supported for 1,5 years, you are supposed to receive software updates for those 18 months and in my opinion Firefox 3.5 should be one of this updates, is not Firefox 4 so that argument is not valid in my opinion (like it happened with Gutsy which was stucked with FF 2).

Anyways, according to this link, FF 3.5 will come out for Jaunty "soon":
[http://www.asoftsite.org/s9y/](http://www.asoftsite.org/s9y/)

---

### Post by aysiu on 2009-07-05
> **darolu said:**
> Yes but Ubuntu normal releases are supported for 1,5 years, you are supposed to receive software updates for those 18 months You do receive support and updates for 18 months. Those are security updates, though, not "get the latest version for new features" updates. > and in my opinion Firefox 3.5 should be one of this updates, Well, it appears it may happen as an anomaly, but as I said before, if you're really impatient, the link I gave will work for you on Ubuntu for Firefox. If you want this sort of instantaneous latest version in Linux, then there are other Linux distros that do this, not Ubuntu. > is not Firefox 4 so that argument is not valid in my opinion (like it happened with Gutsy which was stucked with FF 2). I don't know what you're talking about.

> Anyways, according to this link, FF 3.5 will come out for Jaunty "soon":
[http://www.asoftsite.org/s9y/](http://www.asoftsite.org/s9y/) Great. But, as you can tell from recent postings in the Ubuntu Forums, "soon" isn't soon enough for a lot of people, in which case I advise either sticking with Ubuntu and installing the Mozilla version of Firefox and updating that as updates come immediately... or using a rolling release distro like Arch or PCLinuxOS.

---

### Post by darolu on 2009-07-05
> **aysiu said:**
> You do receive support and updates for 18 months. Those are security updates, though, not "get the latest version for new features" updates.  Well, it appears it may happen as an anomaly, but as I said before, if you're really impatient, the link I gave will work for you on Ubuntu for Firefox. If you want this sort of instantaneous latest version in Linux, then there are other Linux distros that do this, not Ubuntu.  I don't know what you're talking about.

 Great. But, as you can tell from recent postings in the Ubuntu Forums, "soon" isn't soon enough for a lot of people, in which case I advise either sticking with Ubuntu and installing the Mozilla version of Firefox and updating that as updates come immediately... or using a rolling release distro like Arch or PCLinuxOS.

I think you got me wrong, I'm not in the "whinner" side of this "mini-drama"; I know updating xulrunner 1.9 to 1.9.1 is not as simple as it sounds as other software than firefox use it in Ubuntu. My point was that I believe Firefox 3.5 should be in the included software updates, besides (as you very well pointed) security updates, after all FF 3.5 fix security issues present on 3.0; I mentioned the Firefox 4 part and the gutsy case as some people could get to a wrong conclussion from your (and my others') post that 3.5 will never come out for Jaunty or Hardy, I even read that "[firefox 3.5 will not be on Jaunty](http://ubuntuforums.org/showpost.php?p=7562078&postcount=24)" so I thought it was relevant to mention it.

I agree with you about installing the mozilla version of firefox, I actually am recommending to download the version available at firefox.com and just untar and run, doing this allow you to have both Firefox versions using the mozilla version while the Ubuntu version comes out; I don't agree with you when you recommend Arch to people who may not have enough experience to use a gnu/linux distro that requires experience with manual installations though (based on the fact than many of them find "difficult" to install FF 3.5 from other source than regular repositories).

---

### Post by enli on 2009-07-05
firefox-3.5 is already in Ubuntu repositories. I installed it yesterday.
```
sudo aptitude install firefox-3.5
```

I will confirm after I reach home.

---

### Post by chromedome on 2009-07-05
> **enli said:**
> firefox-3.5 is already in Ubuntu repositories. I installed it yesterday.
```
sudo aptitude install firefox-3.5
```

I will confirm after I reach home.

I did that and it appeared to be successful, but 3.5 is nowhere to be found on my system and 3.0.11 is still my browser.  Should I have deleted the current Firefox first?

---

### Post by enli on 2009-07-05
Its in Applications -> Internet but it has different name Sharitako or something. ( I am not on Ubuntu right now ). You dont need to delete older firefox but it may overwrite your current profile.

If you dont want that download firefox 3.5 manually and use profile manager with script. Google it.

---

### Post by phinn on 2009-07-05
Well with an update as massive as Firefox 3.5 (or Openoffice 3.0, etc) no one should have to wait for the next Ubuntu release for it. I always wanted something you could check in Ubuntu to have it install the latest updates. For example "jaunty-backports" that it actually installed all of this stuff. Or some new feature that did, like automaticaly turned on all the important PPAs to get this stuff.  In the meantime manual install of Firefox 3.5 works, but its a bigger pain in the *** for most other things.

---

### Post by chromedome on 2009-07-05
> **enli said:**
> Its in Applications -> Internet but it has different name Sharitako or something. ( I am not on Ubuntu right now ). You dont need to delete older firefox but it may overwrite your current profile.

If you dont want that download firefox 3.5 manually and use profile manager with script. Google it.

That was it.  Thanks!

---

