---
title: "Mupen64Plus-1-5 wont install!!!!!!!!!!!!!!!!!"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by philipballew on 2009-01-20
i am trying to install Mupen64Plus-1-5 on ubuntu 8.10. i downloaded Mupen64Plus-1-5-bin-32.tar.gz and ran the shell script in the terminal and then again setting it as an exe file.somehow one of those made the file somewhat install. it has a link in apps-games but nothing, and when i run it in the terminal i says it cant find the bianery file. i went to where its looking for the file and there's a file there named Mupen64Plus-1-5. i need to know how to install this program. please help this idiot figure it out.

---

### Post by Partyboi2 on 2009-01-21
Make sure you have installed the required dependecies
```
sudo apt-get install libsdl-ttf2.0-0 libsdl-ttf2.0-dev
```[COLOR=Blue][Downloaded]("http://forums.ngemu.com/emulation-news-submissions/116787-mupen64plus-v1-5-ready.html")[/COLOR] and change to where the downloaded file is eg
```
cd ~/Desktop
``` if the file is located on the Desktop.
then extract with
```
tar xvzf Mupen64Plus-1-5-bin-32.tar.gz 
```then enter the newly created directory
```
cd  Mupen64Plus-1-5-bin-32
``` and run the install script
```
sudo ./install.sh
``` Once it is done you can start the program by typing
```
/usr/local/bin/mupen64plus
```You can make a launcher for it by
right click on the Desktop and select "Create Launcher"
then fill in the details
Name: mupen64plus
Command: /usr/local/bin/mupen64plus
Comment: Leave blank or add something.

---

### Post by philipballew on 2009-01-21
Downloaded and change to where the downloaded file is eg?

---

### Post by philipballew on 2009-01-21
thank you so much!!!!!! that helped!

---

