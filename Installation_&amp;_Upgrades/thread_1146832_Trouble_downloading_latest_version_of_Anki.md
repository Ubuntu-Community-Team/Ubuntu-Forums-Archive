---
title: "Trouble downloading latest version of Anki"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by ericstrom on 2009-05-03
I go to Anki site and download their latest version because Jaunty Add/Remove does not download the latest version. Older version of Anki has a bug. I double click on the Debian / Ubuntu versio and get the following message .....

/tmp/anki_0.9.9.7.7-1_all-1.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

The anki download site also says the following ....

f you are a Debian, Ubuntu or Redhat user, Anki is already available in your distribution, but chances are it is an old version that does not support syncing and has some known bugs. Installing the latest version from this site is recommend.

Anki depends on libraries that were released about a year ago. Unfortunately many distributions have not yet upgraded to these libraries, so you need to install them separately. The best way to tell if you have everything is to download the Anki package above and try to install it. The packager will tell you if you are missing anything.

Some people will need Qt4.4. Ubuntu users can get it by adding the following line to their /etc/apt/sources.list file:

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main


I'm new to Ubuntu and Linux and have no idea what this means or what to do. Would you please suggest what I should do.:(

---

### Post by Monkeybells on 2009-05-20
Have you tried following the instructions and adding the line to your sources.list file?
In Kubuntu you open a command line interface e.g. Konsole and type ```
kdesudo kate /etc/apt/sources.list
```
You'd be asked for your password, which you type and then press ENTER. (Be warned you won't see any effect of your typing e.g. little stars!)

If you are using Ubuntu then you will use some basic text editor other than 'Kate' to edit the list.

If you are using Hardy, add the line: 
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main
Click on save and close the editor.
In the command line editor type
```
sudo apt-get update
```

I hope this is of some help to you.

---

