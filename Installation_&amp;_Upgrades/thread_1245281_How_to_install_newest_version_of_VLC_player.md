---
title: "How to install newest version of VLC player?"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by JohneG on 2009-08-20
Can anyone tell me how i can install the newest version of VLC player on Jaunty? Thanks

---

### Post by matthewbpt on 2009-08-20
Add this ppa [https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc) it has the latest VLC version (note this may be unstable since it's not an official ubuntu package)

---

### Post by JohneG on 2009-08-20
Tried adding that but it wont allow me to click on the "add source" button for some strange reason

---

### Post by matthewbpt on 2009-08-20
You can also do it via the command line, type the following in the terminal
```
sudo nano /etc/apt/sources.list
```
This will open a command line text editor to edit your sources file,add this line to the bottom of the file
```
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
```
Then press Ctrl+x on the keyboard, then press y and Enter. Then add the repository key by typing this in the terminal,
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7613768D
sudo apt-get update
sudo apt-get upgrade
```

This should upgrade you to the latest version of VLC (if you already had the Jaunty version installed) otherwise change the last line to:
```
sudo apt-get install vlc
```

---

