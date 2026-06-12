---
title: "[SOLVED] Number of questions from a new user :)"
date: 2008-09-02
forum: General Help
---

### Post by balahh on 2008-09-02
I'm posting this in the General Help section because I have a number of questions that I wanted to ask.

1) Is there another way to be able to properly install and use a .exe file without using Wine? I just want to be able to use Yahoo! Messenger (no offence to anyone but Pidgin kind of stinks :-P) and a few downloaded games like the ones from Yahoo! Games.

2) Can anyone tell me how to figure out the destinations? For the Windows users, you're familiar with the destinations like "c: blah blah blah". I do not understand how that works for Ubuntu :confused:.

3) Is Ubuntu capable of playing games? I know this might seem like a crazy/stupid question but, like I said, I'm new to this and I just came from Windows so I wanted to know if Ubuntu is capable of doing the same. I just want to know if it could play games like World of Warcraft or Total War or any kind of game.

4) Speaking of playing games, is Ubuntu able to use .iso? Can I download an .iso and then mount it using Daemon or something tailored to Ubuntu?

Please forgive me if there are things in this post that tick you off because of the wrong place of posting or whatever :lol:. As I said, I'm new to this whole thing so please cut me some slack. And to those that would reply to this, I thank you for making my transition from Windows easier :):D.

---

### Post by signifer123 on 2008-09-02
> **balahh said:**
> I'm posting this in the General Help section because I have a number of questions that I wanted to ask.

1) Is there another way to be able to properly install and use a .exe file without using Wine? I just want to be able to use Yahoo! Messenger (no offence to anyone but Pidgin kind of stinks :-P) and a few downloaded games like the ones from Yahoo! Games.

2) Can anyone tell me how to figure out the destinations? For the Windows users, you're familiar with the destinations like "c: blah blah blah". I do not understand how that works for Ubuntu :confused:.

3) Is Ubuntu capable of playing games? I know this might seem like a crazy/stupid question but, like I said, I'm new to this and I just came from Windows so I wanted to know if Ubuntu is capable of doing the same. I just want to know if it could play games like World of Warcraft or Total War or any kind of game.

4) Speaking of playing games, is Ubuntu able to use .iso? Can I download an .iso and then mount it using Daemon or something tailored to Ubuntu?

Please forgive me if there are things in this post that tick you off because of the wrong place of posting or whatever :lol:. As I said, I'm new to this whole thing so please cut me some slack. And to those that would reply to this, I thank you for making my transition from Windows easier :):D.

1) You need to use wine or one of it's offspring( Cedega, Crossover Office ) to run windows applications.

2) [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)
I guess a loose translation would be: Or if you want what they all do, rather than a rough Windows Equivalent, see 2 posts down on the image.
/bin /sbin /usr/sbin = C:\WINDOWS\
/etc = The Registry - HKEY_LOCAL_MACHINE
/sys /proc = The Registry - HKEY_CURRENT_CONFIG
/home = C:\Users or C:\Documents and Settings
/lib = C:\WINDOWS\system32
/usr/bin = C:\Program Files - But only the executables
/usr/share = C:\Program Files - The supporting files, icons, images, etc..
/usr/games = Games, Like Vista's folder on the start menu, but without all the extra stuff.
/boot = C:\ - Just the boot files.
/tmp = C:\WINDOWS\Temp
/usr/lib = C:\Program Files\Common Files

/media and /mnt are folders for storing the non-main devices (USB Drives, Other Partitions, Other Harddrives, CD, Floppy). Think of it as the other Letters in My Computer (A:, D:, E:, G:, etc...)
/usr/local is pretty much the same as /usr

Everything else I really don't know that windows has an equivalent, like include and src(source) are just source code files, which windows doesn't include. /dev are the devices for the system, which I have no clue how to get a look at without coding something in windows. 


3) To run windows games, you need wine. Otherwise Postal 2, Doom 3, Unreal Tournament 2004 all have linux versions. Then there are linux games if you like multiplayer there are a load of shooters based off Quake 3. Tremulous, World of Padman, Western Quake, and a long list( i guess people liked quake 3).

Look in the Gaming Forum.

4) You can mount it with "mount - o loop -t iso9660 name.iso /media/iso" it will mount name.iso to /media/iso.
There is also a Graphical way: [http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html](http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html)

---

### Post by Nepherte on 2008-09-02
1) No there isn't. Linux doesn't work with .exe files. Wine is just a compatibility layer for windows applications, but try to use as much native linux programs. I don't know if you can run Yahoo Messenger with wine and don't know other programs that can use the yahoo protocol but I'm sure they exist.

2) [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html). You shouldn't really be concerned with it. The most important directory for you is the user directory (/home/username). Ubuntu will take care of the rest when you install programs with the package manager or in the case you compile them yourself.

3) There are some games that have native linux ports: Neverwinter Nights, Unreal Tournament series, America's Army, Enemy Territory, ... Others can work with wine (such as World of Warcraft), other simply don't work. Ubuntu is really much of game platform though.

4) Yes you can use iso (you have to mount them). There's no extra program to be installed to get this functionality. [https://help.ubuntu.com/community/ManageDiscImages#Mount%20ISO%20Files](https://help.ubuntu.com/community/ManageDiscImages#Mount%20ISO%20Files)

---

### Post by forger on 2008-09-02
hey there, welcome aboard :)

1) If you want to use windows-related programs (not games), you could use virtual machine software, such as [virtualbox]("http://www.virtualbox.org"): head to "downloads", "binaries", and choose your operating system, when the .deb package is downloaded you simply double click on it to install it.
When installed, you have to add your user to the vbox group, by executing the terminal command (Applications > Accessories > Terminal):
```
sudo adduser $USER vboxusers
```
You have to log out and log back in for it to take effect, and you can run VirtualBox from Applications > System tools > Sun xVM virtualbox

2) Simple, in ubuntu (or debian-based operating systems) you have 3-4 simple pathways:
**/** = root partition, where everything system-related is saved, loaded and regulated
**/home** = home partition, where your personal files/folders are saved. Also where custom configuration files/folders for each application you start are saved (These begin with a dot "." in front, you can press CTRL+H to see them while in nautilus, the "file browser")
Each user has a different home subfolder, e.g. **/home/jannet**
That's about all you will ever need to know probably, but here's a picture with some more info:
[ATTACH]83748[/ATTACH]

3) There are games that can be played on linux, but not all windows games can be "emulated" to play on linux. You'lll have to search using google to find that out :)

4) Search for  **Gmount-iso** at Applications > Add/Remove
You can install it and start it from Applications > System Tools > Gmount-iso

---

