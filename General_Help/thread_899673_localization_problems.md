---
title: "localization problems"
date: 2008-08-24
forum: General Help
---

### Post by kaiwan on 2008-08-24
Hi! 

I have Ubuntu 8.04.1. I have changed my default distro language to Croatian, but I have decided to go back to English. However, some folder names in home folder did not translate back to English. Another problem is my keyboard. After each restart it switches back to English layout, I a have to change it back to Croatian.

---

### Post by raphaelr on 2008-08-24
Hi,
For the folder names you can use Symlinks as a temporary solution. For example
```
ln -s CroatianDocumentFolderName Documents
ln -s CroatianProjecsFolderName Projects
...
```
For the keyboard try
```
sudo dpkg-reconfigure xserver-xorg
```
Or edit /etc/X11/xorg.conf (find the line 'Option "XkbLayout" "[..]"' and change it to 'Option "XkbLayout" "en"')

---

### Post by kaiwan on 2008-08-25
> **raphaelr said:**
> Hi,
For the folder names you can use Symlinks as a temporary solution. For example
```
ln -s CroatianDocumentFolderName Documents
ln -s CroatianProjecsFolderName Projects
...
```
For the keyboard try
```
sudo dpkg-reconfigure xserver-xorg
```
Or edit /etc/X11/xorg.conf (find the line 'Option "XkbLayout" "[..]"' and change it to 'Option "XkbLayout" "en"')

```
ln -s CroatianDocumentFolderName Documents
ln -s CroatianProjecsFolderName Projects

```

This will not solve the problem...

```

Or edit /etc/X11/xorg.conf (find the line 'Option "XkbLayout" "[..]"' 
```
This will do...thanks

---

