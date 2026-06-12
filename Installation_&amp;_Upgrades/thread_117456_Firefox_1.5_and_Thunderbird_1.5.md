---
title: "?Firefox 1.5 and Thunderbird 1.5?"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by sergio_a80 on 2006-01-14
:confused: I am new to Linux and Ubuntu.   How do I install applications that are not in the repository?  I downloaded firefox 1.5 and thunderbird 1.5 but do not know how to install them.  Thanks

---

### Post by aysiu on 2006-01-14
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
For Thunderbird, just unzip it (double-click, extract) and then double-click the file called *thunderbird*.

---

### Post by ubuntu27 on 2006-01-14
[QUOTE=sergio_a80]:confused: I am new to Linux and Ubuntu.   How do I install applications that are not in the repository?  I downloaded firefox 1.5 and thunderbird 1.5 but do not know how to install them.  Thanks[/QUOTE]

Hi Segio!! Welcome to the Ubuntu community and it's OS.

When you installed Ubuntu, Firefox 1.0.7 was installed with it.
But if you want to upgrade to Firefox 1.5

then Follow this:

[GNOME - HOWTO: Install Firefox 1.5 from mozilla.org](http://ubuntuforums.org/showthread.php?t=79283)

... Or yeah, You could use [AUTOMATIX](http://ubuntuforums.org/showthread.php?t=66563) by arnieboy.
With Automatix, everything will be installed by just a few clicks... 

I've never tried it [ I like to do it everything manually, si I could learn more], but people says that it is wonderful and it saves time.

Check it out: [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)


And about Thunderbird, you can install it using apt or the Synaptic P. Manager:

System/Administration/Synaptic Package Manager  and look for Thunderbird.

---

### Post by sergio_a80 on 2006-01-14
I appriciate the help and apologize for my ignorance.   How do I even get to the camad prompt where I can type in the istallation isntructions?

sudo  ......etc?

I just installed ubuntu today and this is my first time ever using any linux OS.
Thanks again..

---

### Post by aysiu on 2006-01-15
Applications > Accessories > Terminal

I would suggest, since this is your first day, that you stick with 1.0.7 for Firefox and Thunderbird. Give it a week, get more comfortable with the command-line, and then install 1.5 for both. But, of course, you can do what you want.

If you want to install 1.0.7, just open the terminal and type these two commands: ```
sudo apt-get update
sudo apt-get install mozilla-thunderbird firefox
```

---

