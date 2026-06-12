---
title: "Filezilla not opening"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by jan23778 on 2009-01-28
Hi Everyone,

I am a beginner on Ubuntu, but have recently started to try my hand at web design. In order to download the files to the internet I believe I need to download filezilla client. I go to the website and click on the file marked "FileZilla_3.2.0_i586-linux-gnu.tar.bz2" but it will not open. A message pops up stating 

"/tmp/FileZilla_3.2.0_i586-linux-gnu.tar.bz2 could not be opened, because the associated helper application does not exist. Change the association in your preferences." 

I am not sure exactly what I have to change in my preferences or where I have to go. Is this version of filezilla compatible with Ubuntu?

Any help anyone could give me would be greatly appreciated.

---

### Post by icheyne on 2009-01-28
In Linux it is better to install software using a package manager, rather than from a file downloaded from the web.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

By the way, you can do FTP transfers using Nautilus, the Ubuntu file manager. Look for Connect to Network on the menus.

---

### Post by jan23778 on 2009-01-28
Hi icheyne,

I have tried to do FTP with Nautilus but I cant seem to work it out. Please have patience, I am very new at both webs (in fact this is my first one and I wanted to follow the book I have recently bought to the letter, hence wanting to install Filezilla) AND Linux but I am trying my best to learn.

When I go to Connect to Server, it displays a box with the following:

Server:
Port:
Folder:

I hope I don't sound very stupid here, but the information I have from the web hosting company is:

Hostname
Database Name
Password

Which do not correspond to any of previous boxes.

I have tried to download both ncftp and gftp in the hope that they would be a little closer to the instructions in my book, but when I download them (via synaptic)  I seem never to be able to find them again. This is not the first time I have lost a program. Is there an easy way of searching for new programs as I do have the search tool but it will not find programs.

I would really appreciate any more help anyone can give me.

---

### Post by icheyne on 2009-01-28
Use the link I sent you to install Filezilla.

If you want to keep trying Nautilus:

Server --> Hostname
Port --> Leave blank
Folder  --> Leave blank

---

