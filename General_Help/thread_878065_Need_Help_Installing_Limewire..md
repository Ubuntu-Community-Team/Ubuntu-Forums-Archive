---
title: "Need Help Installing Limewire."
date: 2008-08-02
forum: General Help
---

### Post by 90BL!N on 2008-08-02
Hello every one. This is my First Post so easy on me ;P

Well i have recently tried to install Limewire on my copy of Xubuntu. I tried 

dpkg -i LimeWireLinux.deb

but it says that it cant find it.

So i try to find the location of the my .deb file.
Through FireFox so i right click on the file on the Downloadlist.
Say open containing Folder then it says that i need to find an App to go with it.

90BL!N

---

### Post by K2712 on 2008-08-02
When you click on the Open Containing Folder, hit Choose->File System->usr/bin/thunar->Open.

This will tell firefox to use thunar(Xfce's file manager) to open the folder the downloads are in, which is usually Desktop.

Also, if you want to be able to search for files by right-clicking anywhere inside thunar, do this:

```
sudo apt-get install catfish
```

Open thunar, go to Edit->Configure Custom Actions->Add a new custom action

In the name field:  Search
Description:  Search with Catfish
Command:  /usr/bin/catfish %f

The icon is located in /usr/share/app-install/icons/catfish.svg

Then go to the Appearance Conditions tab and under "Appears if selection contains", make sure the Directories tab is checked.

Hit OK, then Close, and now you should be able to right click anywhere in the thunar window and be able to search for files.

---

### Post by 90BL!N on 2008-08-03
When i do the

sudo apt-get install catfish

it gives me this message:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by comwiz7 on 2008-08-03
Firefox saves to the desktop by default so:

```
cd ~/Desktop

**sudo** dpkg -i LimeWireLinux.deb
```

I think your error message is because some another synaptic is running like possibly the updater.

---

### Post by 90BL!N on 2008-08-03
I am Cool now thx though :D

---

