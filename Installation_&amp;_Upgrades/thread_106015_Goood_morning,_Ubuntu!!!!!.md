---
title: "Goood morning, Ubuntu!!!!!"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by shirike on 2005-12-19
Hello,

I'm a user of Windows since I first used a PC over 15yrs ago and I'd consider myself to be an intermediate/advanced user (I'm happy editing registry, built my own PC systems, and know enough to have solved any issues I've had with Windows).

However, I recently decided to give Linux a bash - not because I think it is better than Windows bu simply because I wanted to know what the big deal with Linux was :)

I'm rather impressed - the installation process was easy (apart from a bit of confusing over the partition etc but that was soon sorted) and, after glancing through these forums, decided to use Automatix to save a bit of time. It all went very smoothly :)

I've even managed to install the latest ATI drivers \o/

System specs are:


ASUS A-7N8X-E Deluxe
AthlonXP 3200+
Audigy 2 Soundblaster
ATI Radeon X800 XL
2x 36GB WD Raptor HD



I have a couple of questions though. Apologies if they've been answered before or appear stupid :)

1) My login screen resolution/freq is different to the res/freq after logging in - how can I fix this?

2) I notice that various pieces of hardware are not configured specifcally - my logitech laser keyboard/mouse, my logitech webcam, and other things (I'm typing this from Windows and can't check 'em at the mo)

Is all hardware supported in Linux (through specific or generic drivers) or are some functions "emulated" by software?

3) Is the get-apt update command like "Windows Update"?

4) Can drivers be installed like they are in Windows (i.e just double-click an .exe (.run for Linux) or do all installations go through many typed commands in Terminal/GEDIT?


Sorry if these questions are a bit "noobtard" but as a native Windows user accustomed to my point'n'click Windows GUI (with only passing knowledge of DOS for troubleshooting) I feel like I'm a fish that is suddenly in the territory of birds...and falling fast from 100feet :)

---

### Post by tehwa on 2005-12-19
> 2) I notice that various pieces of hardware are not configured specifcally - my logitech laser keyboard/mouse, my logitech webcam, and other things (I'm typing this from Windows and can't check 'em at the mo)
Mouse/keyboard should work. Are they working at all? Or are there specific functions that the mouse performs in Windows that aren't happening in Ubuntu?

Also, check if your webcam is listed here:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

It's a pain in the bum, but Logitech aren't the kind of people to offer support for anything but Windows.
> 3) Is the get-apt update command like "Windows Update"?
apt-get update will update the status of your package repositories and report the status to your local package database. From this information, Ubuntu will know whether anything can be upgraded.

You might mean apt-get dist-upgrade. It will update _everything_ that can be updated at that time, according to the state of the repositories that are activated, not just base OS stuff like Windows Update, it will include all applications installed from your repositories. It will also allow you to update to a newer release, without doing a clean install.

Kind of like running Windows update from XP after Vista is released and getting the update at no charge. Only you know, with our way, the OS doesn't suck. :)

The Debian apt-HOWTO is a good read:

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)
> 4) Can drivers be installed like they are in Windows (i.e just double-click an .exe (.run for Linux) or do all installations go through many typed commands in Terminal/GEDIT?
No .exe's, automated installs are rare. I'm no authority on these things, but it basically boils down to the fact that there are so many unique Linux distributions out there, that to make these things automated would be too much  work, since each has it's own way to handle things.

With terminal/gedit things are pretty generic, and work on varied installations.

Hope this info helps.

---

### Post by varunus on 2005-12-19
1)
This usually requires some messing around with a configuration file, unfortunately (the one place ubuntu really shows a weakness is in graphical configuration).

2)
The multimedia keys on your keyboard should be working; if not, open up "System->Preferences->Keyboard Shortcuts" and try to set your keys to what they should do.

For the logitech mice, its a bit difficult to configure them, but here's a nice howto:
[http://www.ubuntuforums.org/showthread.php?t=65471&highlight=logitech+mx]("http://www.ubuntuforums.org/showthread.php?t=65471&highlight=logitech+mx")

3 and 4)
Everyone here will tell you to use "apt-get" since its easier to type out console commands.  Ubuntu includes a utility very similar to windows update to upgrade your system in the event of bugfixes, newer versions, etc; it'll make a red icon appear in your system tray and tell you that updates are available.

For installing software, ubuntu takes a very different approach than windows does.  Instead of having to go hunt down programs you want, try something interesting:
Open up "Applications->Add Applications"
This is very similar to add-remove programs in windows, but:
IF YOU WANT A PROGRAM YOU DON'T HAVE, AND UBUNTU KNOWS WHERE IT IS ON THE INTERNET, IT'LL DOWNLOAD AND INSTALL IT FOR YOU!

Sorry to yell, but I just love this feature (known as a package manager).

A more advanced version of the software installation GUI can be found in:
"System->Administration->Synaptic Package Manager."
This will let you get everything you'll need to write your own programs, compile programs other ppl have written from source, and just a bunch of programs that might not show up in Add Applications (as only approved applications show up there, I think...there are many applications which may not be there).

The apt-get command does the same thing as Synaptic; its just that its easier to tell someone "type this" instead of "find the box on your screen that is labelled this, and click it."

To let Ubuntu know where programs are on the internet, you need to add things called "repositories."  You can do this in synaptic, or through the file /etc/apt/sources.list
For help doing this, click the help icon on your panel, choose "Ubuntu 5.10 starter guide", and go to "installing applications."  It'll show you there how to add repositories in synaptic.
(It also has a wealth of useful information...)

You'll want to enable the universe, multiverse, and backports repositories.  These three will let you get extra software packages and upgrades to packages you already have, allowing you to get 16,000 with a couple of clicks!

---

### Post by shirike on 2005-12-20
Thank you! varunus, your reply was especially helpful :)

[B]Monitor
[/B]

I'm not sure what to do to sort out my monitor position with ubuntu - the **xvidtune** command in termional brings up a rather worrying warning message before the main program but, when I click left or right or up or down, the monitor position does not move at all - is there anything else I can try or am I forgetting something simple?

**Logitech Mouse**

thanks for the guide - I'll give it a go

**Sources.list**

I have enbaled Universe as part of installing the latest ATI drivers - how do I enable multiverse and backport list?

---

### Post by Perfect Storm on 2005-12-20
source list:

```
sudo gedit /etc/apt/sources.list 
```

add:
> 
## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse


## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted


```
sudo apt-get update
```

---

### Post by shirike on 2005-12-21
thank you - all issues in this thread have been resolved :)

---

