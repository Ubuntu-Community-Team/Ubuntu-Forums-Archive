---
title: "Issues with Avant window manager"
date: 2008-07-14
forum: General Help
---

### Post by nintennuendo on 2008-07-14
In the picture there are some odd bars that are supposed to be applets and things.  Why?.  I did [  sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr  ]  after adding and updating repositories.  Some of the applets work, some don't.  Is there a more recent version, or should i just uninstall the whole thing and retry?

---

### Post by sayakb on 2008-07-14
Try installing AWN following this: [http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

Also, I would recommend cairo-dock: [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by nintennuendo on 2008-07-14
I tried cairo dock just now.  Looks okay but seems way too chunky in the menus.  

when i try those methods for AWN, I get a NOT FOUND error or something to that effect.

---

### Post by SomeGuyDude on 2008-07-14
The last slew of updates has screwed things up. Give it a bit, it'll be fixed soon.

---

### Post by Foster Grant on 2008-07-15
> **nintennuendo said:**
> In the picture there are some odd bars that are supposed to be applets and things.  Why?.  I did [  sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr  ]  after adding and updating repositories.  Some of the applets work, some don't.  Is there a more recent version, or should i just uninstall the whole thing and retry?

Uninstall the version in the repositories, then follow the instructions at the site LinuxIsInnovation posted:

[http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

[LIST=1]
[*]Go to System -> Administration -> Software Sources and enter your password when asked.
[*]A new window appears. Click the second tab ("Third-Party Software") then click the 'Add' button and paste the following lines (one by one):
```
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```
[*]Now click the 'Close' button of the main window. It will ask if you want to reload the information about available software. Click 'Reload' and wait for the Software Sources window to close.
[*]Open a terminal (Applications -> Accessories -> Terminal) and paste the following command:
```
sudo apt-get install awn-manager-trunk awn-extras-applets-trunk
```
[*]Hit the "Y" key when asked, and complete the installation. Close the terminal window. Right-click and delete your lower GNOME panel and start the AWN dock from Applications -> Accessories -> Avant Window Navigator.
[/LIST]

The version in the official repositories has issues, evidently. The version in the AWN repository is better, with one bug: You cannot add application launchers in the AWN-Manager application. Instead, drag them into the dock from the /usr/share/applications directory.

---

