---
title: "Installing Repos located on USB Disk with no internet"
date: 2008-07-13
forum: General Help
---

### Post by NavyAE on 2008-07-13
I&#8217;m a Newbie trying to setup Unbuntu with little support. I have successfully installed Ubuntu 8.04 on my 32bit Intel. Since I&#8217;m currently deployed Internet connectivity is non-existent. I have managed to get the REPO on my external drive under six folders labeled Disk 1-6. I know I have to edit the sources.list file in /etc/apt/sources.list to fetch the Repos from my H/D vice the internet or a CD. I have created the following lines to accomplish this however apt continues to fail to fetch the files. Can someone tell me what is wrong in my sources.list?

deb file:"/media/My Big Book/Linux/Disk 1" main multiverse restricted universe
deb file:"/media/My Big Book/Linux/Disk 1" hardy hardy-backsport hardy-security hardy-updates
deb file:"/media/My Big Book/Linux/Disk 2" main multiverse restricted universe
deb file:"/media/My Big Book/Linux/Disk 2" hardy hardy-backsport hardy-security hardy-updates
deb file:"/media/My Big Book/Linux/Disk 3" main multiverse restricted universe
deb file:"/media/My Big Book/Linux/Disk 3" hardy hardy-backsport hardy-security hardy-updates
deb file:"/media/My Big Book/Linux/Disk 4" main multiverse restricted universe
deb file:"/media/My Big Book/Linux/Disk 4" hardy hardy-backsport hardy-security hardy-updates
deb file:"/media/My Big Book/Linux/Disk 5" main multiverse restricted universe
deb file:"/media/My Big Book/Linux/Disk 5" hardy hardy-backsport hardy-security hardy-updates
deb file:"/media/My Big Book/Linux/Disk 6" main multiverse restricted universe
deb file:"/media/My Big Book/Linux/Disk 6" hardy hardy-backsport hardy-security hardy-updates

The thumbnail is the error I receive when trying to reload the update on gnome.

---

### Post by daleus on 2008-07-13
My first guess would be the path, the 'drive' you have it on (for example) is "my big book" now, normally in a terminal if you were going to cd there, you'd have to put

cd /media/my\ big\ book/

or something like that, I assume what you are trying to do also has problems with file spaces.

but that's just a guess.

---

### Post by rraj.be on 2008-07-13
you can store all packages in the form of local repos's as you save softwares in windows.

All you need is a system where all required packages are installed.

Go to such system and install aptoncd

here is an excelent GUI application for helping you.

```

Aptoncd
```

To install this type this in terminal


```

sudo apt-get install aptoncd
```

this will be much useful to create local repos in GUI way.

burn it t a disk.

take it to your system and you can use it to install your required packages from that disk.



```

[http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html]("http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html")


```

---

