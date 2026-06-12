---
title: "[SOLVED] Generating an install script"
date: 2008-09-27
forum: General Help
---

### Post by tommygunner on 2008-09-27
Synaptic Package Manager has a feature called "Generate a package download script." This works fine if you are looking to install stuff but haven't done so. However, I have already installed the packages I want and would like to generate a download script from the list of installed packages. Does anyone know how to do this? I'm thinking that if "select all" was available I could mark for re-installation then try it. However, I don't see the select all option in the menu.

I know aptoncd has something to generate install from CD, but I'm looking for an install from the internet sort of thing.

Also, the script generation thing as it exists now is nice but not ideal. It generates stuff like:

wget -i [http://www.asdfadsf.com/packagname1.02.deb](http://www.asdfadsf.com/packagname1.02.deb)

The following would be more ideal as it would get the most recenter versions;

sudo apt-get install httpd mysql skype 


Has anyone figured out how to do this?

---

### Post by lovinglinux on 2008-09-27
Try this:

```
dpkg --get-selections > ~/my-packages 
```

This will save a "my-packages" in your home directory with the list of all installed applications (except those installed using deb files). Then you can copy it to another machine or back it up, so when you re-install Ubuntu you just have to put this file in the home directory and run the following command

> sudo dpkg --set-selections < my-packages && apt-get dselect-upgrade

This will automatically install all applications you had before.

---

### Post by tommygunner on 2008-09-27
Cool, it looks like that will work great! Thanks!

---

### Post by lovinglinux on 2008-09-27
You are welcome. This tip was provided to me by the **ubotu** irc bot :-)

This is really cool, you just run the command, sit back and relax while the apt download and install everything you had installed before. Now all have to do is create a script to download and install your deb files. I'm still doing this manually, using the deb files saved on my home folder.

If you have a separate /home partition, everything will be pretty much like before re-installing, except for those settings saved on other directories outside home.

Please don't forget to mark the thread as solved if your are satisfied with the solution.

---

### Post by tommygunner on 2008-09-27
Cool. Well I didn't know I could mark posts as solved either. I need to figure out how to do that also, LOL.

---

### Post by drs305 on 2008-09-27
> **tommygunner said:**
> Cool. Well I didn't know I could mark posts as solved either. I need to figure out how to do that also, LOL.

If you are the original poster, go to the top right above the first post. Click on Thread Tools, mark Solved.

---

### Post by tommygunner on 2008-09-27
thanks again.

---

### Post by tommygunner on 2009-02-12
I decided to try this thing now. I made a package file from one Ubuntu computer, installed Ubuntu on a new machine and am now attempting to install all the packages on my other screen using this command:

```
sudo dpkg --set-selections < my-packages && apt-get dselect-upgrade 
```

I keep getting the following errors:

```
Could not open lock file /var/lib/dpkg/lock - open (permission denied) Unable to lock the administration directory /var/lib/dpkg are you root?
```

I don't have Synaptic or any other package manager running? Do I need to be outside of X in order to run the command?

---

### Post by tommygunner on 2009-02-12
I fixed it! I had to do:

```
sudo su
```

then the commands. Regular ```
sudo
``` wasn't good enough!

---

### Post by Slim Odds on 2009-02-12
```
sudo dpkg --set-selections < my-packages && **sudo** apt-get dselect-upgrade
```

the original was missing a sudo

---

