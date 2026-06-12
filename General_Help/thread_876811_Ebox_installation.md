---
title: "Ebox installation"
date: 2008-08-01
forum: General Help
---

### Post by gpb on 2008-08-01
Has anybody installed ebox-all on Ubuntu Server 8.04 (Hardy H)????
My box does not have internet access. How do I go about it???

Thanx

---

### Post by forger on 2008-08-01
You'll have to download the packages somehow:
[http://packages.ubuntu.com/hardy/ebox](http://packages.ubuntu.com/hardy/ebox)

Each of the dependencies should be installed. If you're lucky enough, you won't have to install the dependencies of the dependencies :D

You can download the packages in the "Download" section of that site (click on amd64 for 64-bit ubuntu or i386 for 32-bit ubuntu) and choose a download mirror.

Want a better solution?
1) Get a USB flash disk
2) get your ubuntu live cd and boot with it, load it in a computer with internet connection
3) make sure you have checked **multiverse** and **universe** in System > Administration > Software sources. Click "Close" and "Reload", wait until it's finished.
4) open Applications > Accessories > Terminal and execute:
```
sudo apt-get update
sudo apt-get install ebox
```

Wait until it installs it.

5) The packages will be in directory **/var/cache/apt/archives**

This will copy them on your Desktop, in folder "eboxpackages":
```
mkdir $HOME/Desktop/eboxpackages/
sudo cp /var/cache/apt/archives/*.deb $HOME/Desktop/eboxpackages/
sudo chown -R $USER:$USER $HOME/Desktop/eboxpackages/

```

6) Now you can move the folder "eboxpackages" in your usb flash drive and transfer it to wherever you want to install ebox.
Install by double-clicking each package
Install the dependencies first!

---

