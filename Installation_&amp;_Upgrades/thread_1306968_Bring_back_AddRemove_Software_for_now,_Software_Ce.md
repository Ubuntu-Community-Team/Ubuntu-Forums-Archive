---
title: "Bring back Add/Remove Software for now, Software Center is not ready!"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by ninjatiger422 on 2009-10-30
While I think it's great that the good folks at Canonical want to integrate all the package software and make things simple, the software right now is just short of terrible.

Installing software with Ubuntu Software Center is a pain because:

- All the clicking (one at a time) and individual password entering is painful.

- There are no statistics, so I can't easily see what the most popular software is in a category.

- Tons of packages do not even have an "Install" button. 

- The stupid software icon thing is slow and does not actually have software graphics. This is an annoyance.

So I figured I'd just install the old Add/Remove Software app that I have come to like. The problem is when I run:

sudo apt-get install gnome-app-install

it does not work. Not only that but it says "This may mean that the package is missing, has been obsoleted . . ." I bet it's missing because it's obsoleted.

PLEASE bring back the old Add/Remove Software program (for a release or two) or please let me know how I can install it. I'm sure this Ubuntu Software Center will be great in the future, but why do we all have to suffer while you guys develop it?

---

### Post by rey1321 on 2009-10-30
I Agree with you:sad:

---

### Post by wilee-nilee on 2009-10-30
Everything there is in synaptic and via the terminal, you have to know what your looking for. I never use add remove it is there for the inexperienced basically.

---

### Post by fedexnman on 2009-10-30
use the terminal ( sudo apt get ) or synaptic , i hope they'll never remove synaptic, i never used add/remove much ? been using ubuntu since 8.10 n lovin it....

---

### Post by ninjatiger422 on 2009-10-30
> **wilee-nilee said:**
> Everything there is in synaptic and via the terminal, you have to know what your looking for. I never use add remove it is there for the inexperienced basically.

How can I get the usage statistics?

---

### Post by ninjatiger422 on 2009-10-30
I just found out that the old Add/Remove program is still available! It's in the Universe repositories

```

sudo software-properties-gtk -e universe
sudo apt-get update
sudo apt-get install gnome-app-install

```

After you run that go to System > Administration and you should see it.

---

### Post by tmckellar on 2009-10-30
Add/Remove Software is still on my system after the upgrade. Got moved in the menu to Administration. I believe this is where it hangs out on Fedora as well. Kind of makes sense putting it there personally.

---

### Post by ninjatiger422 on 2009-10-30
> **tmckellar said:**
> Add/Remove Software is still on my system after the upgrade. Got moved in the menu to Administration. I believe this is where it hangs out on Fedora as well. Kind of makes sense putting it there personally.

Yea. But if you do a fresh install it is gone unless you re-install it from the Universe repo.

---

### Post by ericab on 2009-10-30
LONG LIVE add/remove!!!

---

### Post by ZaHACKieL on 2010-02-25
> **wilee-nilee said:**
> Everything there is in synaptic and via the terminal, you have to know what your looking for. I never use add remove it is there for the inexperienced basically.

I thought this was a place for helping the guys from Ubuntu Community, not for saying things like: "I'm experienced you are not" and not contributing with a solution. Let ninjatiger422 and the rest decide what is better for them and if you can't help then don't answer. Be part of the solution not part of the problem.

---

### Post by yskyflyer on 2010-04-23
Lucid 10.04 gnome-app-install (add remove) has been replace with a dummy package
I'm probably posting this in the wrong place so just tell me where I should post this.

Update: I got a ppa version working

Ok, so I was trying out Lucid rc and discovered gnome-app-install (The add/remove program we have all grown to love) has been replaced with a dummy package (same for the Debian package). For those who love gnome-app-install this will mean when you upgrade it will remove your existing gnome-app-install.

The release notes for Lucid 10.04 rc do not mention this and they should so this should be updated before day 0.
[http://www.ubuntu.com/getubuntu/releasenotes/1004overview](http://www.ubuntu.com/getubuntu/releasenotes/1004overview)

I found a fix so you can continue using add/remove gnome-app-install thanks to the work of Attila Hammer.
[https://launchpad.net/~hammera/+archive/ppa]("https://launchpad.net/%7Ehammera/+archive/ppa")

Disclaimer
This is unofficial do not try this on your primary computer and do not report any bugs while you use this fix.

More disclaimers
this fix will remove software-center and Ubuntu-desktop (Ubuntu-desktop depends on all recommended programs). This means if you do a distro upgrade it may not update all your program or add required files and may make your installation unbootable

Also the program runs with some DeprecationWarning and GtkWarning s
 

 The version number was bumped high so the dummy package doesn't keep overwriting it.  But this means if it ever gets merged officially back (such as enough users complain) (this is not made by an offical dev) you will need to manually force the package to the hopeful future official &#8220;earlier version&#8221;.
 

 Also with this package you cannot have both software-center and gnome-app-install installed at the same time, at least for now.  The ppa was made by the visually impaired for the visually impaired and because software-center is supposedly inaccessible with Orca Screen reader they fixed the bugs so gnome-app-install works with lucid.  Since the target audience can't use software-center anyway this installer removes it to avoid confusion.  If you want both you can rebuild the package for source or change the dependencies and disable signed code checking.

Step one
Update all your programs
Go to synaptic and update all your programs

```
sudo add-apt-repository ppa:hammera/ppa
```This will add Attila Hammer's ppa repository

Go back to synaptic and upgrade all your programs. You can find it by typing gnome-app-install in the search box. Right click mark for installation right now it's gnome-app-install 2.2.25~ppa1 . It also needs python-gtkhtml2 witch it should get from the ppa (I'm using the karmic 9.10 version but the one in the ppa is newer and should be installed by itself).

The installation will remove software-center and Ubuntu-desktop
Do not do not do not do a distro upgrade without reinstalling Ubuntu-desktop
Before you ask for help from anyone else or post a bug report reinstall Ubuntu-desktop

```
sudo apt-get update
sudo apt-get install -f
Sudo apt-get install ubuntu-desktop
Sudo apt-get install software-center
```You also may want to remove python-gtkhtml2

It's way too late and after the feature freeze to add it to supported and universal repositories. So my best hopes are if they fix it up some more and fast track it to the &#8220;back ports&#8221;.

I can understand them wanting to force everybody to try the software center but for those of us who made up our mind their should be a way of installing it.

Here are some links

Experimental
```
sudo add-apt-repository ppa:hammera/ppa
```Open synaptic search for gnome-app-install
Do not ask for help, upgrade distro or report bugs after installing.

Uninstall before asking for help or reporting bugs
```
Sudo apt-get install ubuntu-desktop
```[http://packages.ubuntu.com/lucid/gnome-app-install](http://packages.ubuntu.com/lucid/gnome-app-install)
[http://packages.debian.org/sid/gnome-app-install](http://packages.debian.org/sid/gnome-app-install)
[http://packages.ubuntu.com/karmic/python-gtkhtml2](http://packages.ubuntu.com/karmic/python-gtkhtml2)
[http://packages.debian.org/sid/python-gtkhtml2](http://packages.debian.org/sid/python-gtkhtml2)
[https://launchpad.net/~hammera/+archive/ppa]("https://launchpad.net/%7Ehammera/+archive/ppa")
[https://launchpad.net/ubuntu/lucid/+source/gnome-app-install](https://launchpad.net/ubuntu/lucid/+source/gnome-app-install)
[https://answers.launchpad.net/ubuntu/+source/gnome-app-install/+question/106440](https://answers.launchpad.net/ubuntu/+source/gnome-app-install/+question/106440)
[https://launchpad.net/~hammera/+archive/ppa/+sourcepub/1085642/+listing-archive-extra]("https://launchpad.net/%7Ehammera/+archive/ppa/+sourcepub/1085642/+listing-archive-extra")
[https://launchpad.net/~hammera/+archive/ppa/+sourcepub/1081619/+listing-archive-extra]("https://launchpad.net/%7Ehammera/+archive/ppa/+sourcepub/1081619/+listing-archive-extra")

---

### Post by aimwin on 2010-04-25
> **tmckellar said:**
> Add/Remove Software is still on my system after the upgrade. Got moved in the menu to Administration. I believe this is where it hangs out on Fedora as well. Kind of makes sense putting it there personally.

I think we should demand "gnome-app-install" back.
I think we should take care new user of ubuntu and linux in general first.
And that is all about UBUNTU for human being.

The "GURUs" can use just terminal, they don't need desktop to look good and ease of use.

Actually they should not use UBUNTU at all.
Since Ubuntu was born for non programmer desktop user in mind.
Ubuntu is for Desktop users, not for programmers nor very experience or advance computer user.

And that is why I use UBUNTU and not even other linux distro.

Add/Remove program Menu,"gnome-app-install", is one of my reason why I used Ubuntu since it gave me "Statistics" and quick info with ease.

I wish they have option for us to install them back into Administration, as the 9.10 beta when I use the software center the first time.
And until now I cannot judge that it is better and easier than the old Add/Remove Program.

I still don't get why? 
Since we use Gnome-Desktop and not Netbook Remix because Gnome-Desktop is easier to use.

Software Center bring Gnome-Desktop closer to Netbook Remix which contradicts to ease of use.

So I vote up for permanent until software center got "Statistics" and ease of use better than present day April 2010, may be with the option,
"choose classic Add/Remove Program",
similar to what new XP has got option to choose classic style for control panel.

Why can't Ubuntu offer the same feature as in XP?
Since we try to win both new user and old user of UBUNTU.

---

