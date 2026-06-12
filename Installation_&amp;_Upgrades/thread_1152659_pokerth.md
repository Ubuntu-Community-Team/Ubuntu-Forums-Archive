---
title: "pokerth"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by jazzfan1 on 2009-05-08
How do I install the newest version of pokerth in 8.10?

I have tried apt-get install pokerth but it tells me that I already have the latest version installed.

Thanks in advance

---

### Post by Partyboi2 on 2009-05-08
Hi, you can add a 3rd party repo to upgrade to 0.7.1
[https://launchpad.net/~pkg-games/+archive/ppa]("https://launchpad.net/%7Epkg-games/+archive/ppa")

If you are unsure how to add the 3rd party repo as well as the key let us know and someone can help you.

---

### Post by 600WPMPO on 2009-05-31
Hello there! Can you please tell me how to add a 3rd party repo to upgrade to 0.7.1?

I have Poker-Th 0.6.3 installed via synaptic on Jaunty.

For Intrepid, I think: 

```
 intrepid main deb http://ppa.launchpad.net/sargentd/pokerth-backports/ubuntu 
  deb-src http://ppa.launchpad.net/sargentd/pokerth-backports/ubuntu intrepid main 
```

followed by 

 ```
 sudo apt-get update 
 sudo apt-get install pokerth 
```

But, how do I do it in Jaunty ?

---

### Post by Partyboi2 on 2009-05-31
Open a terminal (Applications>Accessories>Terminal) and open your sources.list with
```
gksu gedit /etc/apt/sources.list
```
at the bottom of the file add
```
deb [http://ppa.launchpad.net/pkg-games/ppa/ubuntu](http://ppa.launchpad.net/pkg-games/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/pkg-games/ppa/ubuntu](http://ppa.launchpad.net/pkg-games/ppa/ubuntu) jaunty main
```
[FONT=Verdana]then save the changes and close gedit, then back in the terminal
[/FONT]```
sudo apt-get update 
sudo apt-get upgrade
``` [FONT=Verdana]
[/FONT]

---

### Post by 600WPMPO on 2009-05-31
Thanks a lot Partyboi2 !! It worked exactly as you told..!!

Thanks again for such a fast reply..

I go on loving ubuntu..!!!

---

### Post by yeayea911 on 2009-06-13
is there a pgp key for this site? thanks

---

### Post by Partyboi2 on 2009-06-13
You can get the pgp from [[COLOR=Blue]here[/COLOR]]("https://launchpad.net/%7Epkg-games/+archive/ppa")

---

### Post by daedalas1981 on 2009-07-21
Uninstall using Synaptic any previous versions.

Visit Here and Download "pokerth-data_0.7.1-1_all.deb".

[https://launchpad.net/ubuntu/+source/pokerth/0.7.1-1/+build/1099113]("https://launchpad.net/ubuntu/+source/pokerth/0.7.1-1/+build/1099113")

Use the Installer (just click on the file or run as you download from the site) the "_data_0.7.1-1_all.deb". Installs fine.

Next download and save "PokerTH-0.7.1-linux.zip" from:
[http://www.pokerth.net/download]("http://www.pokerth.net/download")

Extract to your desktop, rename folder to PokerTH to make it easier.

Open Terminal, and type "gksudo nautilus". Type in your password, and click "File System" on the left.

Open /usr/games

At the same time, open your folder on your desktop call PokerTH, copy the file called "pokerth". Right Click "Copy".

On the /usr/games folder open, right click and paste.

On your Desktop Folder, open "libs", select ALL and right click and copy.

Change the address in the other folder (or click back) and open /usr/lib
and right click paste. I didn't replace any files, I clicked SKIP. You should do the same.

On your Desktop Folder, right click and copy the folder called "data".
On your other Folder, open /usr/share/games
Right click and paste.
Right click on the freshly pasted folder and rename it "pokerth".

Now if your all up to par, you should be able to type "pokerth" in terminal and play the game.

One last step for the NOOBs, A link in the menu.

Click SYSTEM->Prefs->Main Menu
Click GAMES
Click + NEW ITEM

Type: Application
Name: PokerTH
Command: pokerth
Comment: Texas Hold'em

Click on the icon.
Change the address bar to "/usr/share/app-install/icons/pokerth.png"
Look for the PokerTH logo.
Click Close, Click Close.......
Click Applications->Games
Voila!!

Hope this long winded installation helps....next time I think I'll write out the terminal commands instead. :P

---

