---
title: "Can unrar downloaded files"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by ftilli on 2009-09-05
hey guys, i searched a bit and didnt find a solution for my problem.
When I download a torrent and it&#347; separated in .rar files file manager says that It doesnt support that type of file, so then i added 7zip, but after installing there is no 7zip, or choice to use it.:confused:
Im using ubuntu 9.04

thanks

---

### Post by falconindy on 2009-09-05
sudo apt-get install unrar

---

### Post by Partyboi2 on 2009-09-05
If you are wanting to extract rar's you can install unrar and extract them using the terminal (Applications>Accessories>Terminal)
```
sudo apt-get install unrar
```
Then change into the directory where the rar files are eg: If they are on your Desktop
```
cd ~/Desktop
```
then extract them with
```
unrar x filename.rar
``` change "filename" to actually name of the rar file.

---

### Post by ftilli on 2009-09-05
thank you very much guys!:D

---

