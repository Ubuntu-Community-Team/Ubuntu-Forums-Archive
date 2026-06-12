---
title: "Linux Games"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by PandabeaR on 2006-02-01
I have many PC games that I used to play when I ran windows. I am just wondering if any of them will be able to run in linux? Is there an emulator that I can use? Is there any kind of tool that i can download that will let me play my games? (mainly quake 4 and Rainbow Six 3: Raven Shield)

---

### Post by az on 2006-02-01
Look in the gaming section of the forums.

You can use Cedega to run direct-X windows games.  You can also run native-linux games.

---

### Post by firetux on 2006-02-01
You can run Quake4 natively on linux see: [http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)

for Rainbow Six 3: Raven Shield you could use cedega ([www.transgaming.com](www.transgaming.com)) but I see that's not gonna work, maybe you can try wine.

---

### Post by Josef K. on 2006-02-01
all idsoftware based games are linux native
for others you can try cedega
(I've also read good reviews about wine with DX9 patch but I didn't try yet cause I've no idea how to patch wine :-k )

---

### Post by PandabeaR on 2006-02-01
Cool. So quake yes. But cedega wont work with Rainbow Six? Im kind of confused and to be frank I am an utter noob when it comes to linux. Can you explain what I need to do to be able to run Raven Shield?

---

### Post by Sutekh on 2006-02-01
Cedega is provided by transgaming
[http://transgaming.org/gamesdb/]("http://transgaming.org/gamesdb/")

They have a database for *many* games, where you can check for compatibility and to find out which version of Cedega is best for running that game

Raven Shield doesn't seem to have that great a rating.  [Transgaming Database - Raven Shield]("http://transgaming.org/gamesdb/games/view.mhtml?game_id=2944")

You could always ask on the Transgaming Foums for people who might havbe played it, and what their experience was like.

---

### Post by PandabeaR on 2006-02-01
Ahh. Ok. What about wine? 

Also, I am following the installation instructions for Q4. But when I insert the second cd it wont let me see the files because it says I dont have permission to see it...

---

### Post by Sutekh on 2006-02-01
[Wine Application Database]("http://appdb.winehq.org/")

[Wine - Rainbow Six - Raven Shield]("http://appdb.winehq.org/appview.php?appId=1655") - not too much info I'm afraid but it might work for you.

---

### Post by PandabeaR on 2006-02-01
[QUOTE=Sutekh][Wine Application Database]("http://appdb.winehq.org/")

[Wine - Rainbow Six - Raven Shield]("http://appdb.winehq.org/appview.php?appId=1655") - not too much info I'm afraid but it might work for you.[/QUOTE]

Okay, thanks. I have have installed the package in the APT program with ease. Alas, confusion has ensued. After installing the package... where do I go to actually "run" the application??

---

### Post by Sutekh on 2006-02-01
First run 'winecfg', either in a terminal window or by pressing Alt+F2

winecfg will setup the configuration for wine.

Check the Wine User Guide for some more details on what you should consider setting up.

[Wine User Guide]("http://www.winehq.com/site/docs/wineusr-guide/index")

Then to run a program (again using the terminal or Alt+F2), the command
```
wine /path/to/application/setup.exe
```
will run your program.  (Obviously change the path to what is appropriate for the program you want to use)

You don't actually 'run' wine so to speak, but wine becomes a 'command' if you want to think of it like that.  So youneed to supply the options to the wine command, which is the path to the .exe that you want to run.

---

### Post by PandabeaR on 2006-02-01
OH! I think i get it... wine is a command like "less" or "more" when navigating the terminal in darwin on OSX? It says that it cant find winecfg when i run 'winecfg'.

---

### Post by Josef K. on 2006-02-02
I suggest to install winetools and run wt instead of winecfg cause it
is more intuitive and let you install _fast_ most common windows stuff (like installers, IE or wmplayer)

---

### Post by PandabeaR on 2006-02-02
[QUOTE=Josef K.]I suggest to install winetools and run wt instead of winecfg cause it
is more intuitive and let you install _fast_ most common windows stuff (like installers, IE or wmplayer)[/QUOTE]
Ok. I find that using the terminal to install packages works better for me than using the repository for some reason. Is there a terminal command to get and install winetools?

---

### Post by Sutekh on 2006-02-02
[QUOTE=PandabeaR]Ok. I find that using the terminal to install packages works better for me than using the repository for some reason. Is there a terminal command to get and install winetools?[/QUOTE]
This would probably require you to download the source and compile it yourself.  I can't find any debian packages for winetools, so unles someone else does you'll have to do it all manually.

First make a temporary directory on your deskop or similar
```

mkdir ~/Desktop/winetemp
```

Then download the source code for wine tools version 0.9x
```
wget http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz
```

Then you will need to decompress and install it (using **sudo** according to wine tools webpage [Wine Tools download)]("http://www.von-thadden.de/Joachim/WineTools/index.html#download")

```
sudo tar xvzf winetools-0.9jo-III.tar.gz
cd winetools-0.9jo-III
sudo ./install.sh

```

Once its installed, you can run it with 
```
wt
```

and then a stern warning from Joachim (guy who continued wine tools)
[QUOTE=Joachim]**Note that you should definitely start with the menu entry "Base setup" and create a new fake Windows drive.** If you want to save your old .wine directory, you can use the backup funktion of WineTools. **Do not use as root. Do not use as root. Do not use as root.** [/QUOTE]

Good Luck! :KS

---

### Post by Sutekh on 2006-02-02
It may also be in the WineHQ debian repository (from what I hear).  This would require apt-get, which I understand you would rather not use.  If you wish to use it however, here's how...

Backup your sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_03022006
```
or something that is unique (I just used today's date, here in Aus)

Edit the sources.list and add the WineHQ repository

```

sudo gedit /etc/apt/sources.list

```

Then in the text editor
```
## The wine sources
deb http://wine.sourceforge.net/apt binary/
deb-src http://wine.sourceforge.net/apt source/

```

Then you have to refresh your sources
```
sudo apt-get update
```

Then install winetools using apt-get
```

sudo apt-get install winetools
```

And fingers-cros[LIST=1]
[/LIST]sed you're away.

---

### Post by PandabeaR on 2006-02-02
Great, It all works up untill the last step, 'sudo apt-get install winetools'

I get this response
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package winetools

```

---

### Post by Sutekh on 2006-02-02
[QUOTE=PandabeaR]Great, It all works up untill the last step, 'sudo apt-get install winetools'

I get this response
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package winetools

```[/QUOTE]

Then its not in the WineHQ repository and you'll have to try the method I put in the previous post.

---

### Post by PandabeaR on 2006-02-02
```
Version: winetools-0.9
Release: 0.9
You do not have gettext installed on your system. WineTools will not run in your native language. Rather it will use english.
Installing WineTools to /usr/local/winetools...
You already installed WineTools. Uninstall the old installation first and come back.

```
I get this... I am for sure I have it installed... but Im soooo confused x_x

---

### Post by Sutekh on 2006-02-02
It looks like its installed, just in English, so I hope that's okay for you.

Just type **winetools** in a terminal window.

---

### Post by PandabeaR on 2006-02-03
You don't have wine installed on your computer it says. Go to winehq.org and download the appropriate distro... I did this. I added the repository and downloaded the wine-doc package... but it still says this.

---

### Post by Sutekh on 2006-02-03
[QUOTE=PandabeaR]You don't have wine installed on your computer it says. Go to winehq.org and download the appropriate distro... I did this. I added the repository and downloaded the wine-doc package... but it still says this.[/QUOTE]

Ok the fact that winetools can't find wine and winecfg doesn't run means I need to ask if you're sure that you installed wine properly?

You can check with the code
```

wine --version

```
If this doesn't give you anything then read on.

Here's how I'd do it, so see if you followed similar steps

I have to add the WineHQ repository to my sources.list by first editing it using sudo
```

sudo gedit /etc/apt/sources.list
```
then adding the repository URL to my list, (just paste it in the file will do)
```

deb http://wine.sourceforge.net/apt/ binary/

```
Then save the sources and refresh the repositories
```

sudo apt-get update

```
So if I get this far and no errors I can use apt to isntall wine

Using apt-get should install the latest version of wine (0.9.6) 
[Edit:  No it seems that today wine 0.9.7 is available)
```

sudo apt-get install wine

```
Once this is done then I run winecfg to setup wine
```

winecfg

```
And then I should be ready to try some applications.

---

### Post by PandabeaR on 2006-02-03
I get to the part that where i do apt-get install wine... then i get this

```
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

```

---

### Post by DoorGunner on 2006-02-03
Hey dont forget.... americas army is free and a pretty good first person shooter...... 

as well there is a gaming comunity as well 
[http://www.ubuntugaming.org/community/](http://www.ubuntugaming.org/community/)

---

### Post by PandabeaR on 2006-02-04
If it makes any difference I am using AMD64 architecture...

---

### Post by leech on 2006-02-04
That makes all the difference.  Since you're runnng amd64, wine is compiled for 32 bit only.  You should be able to get it installed, but I just can't recall the command for it at this point in time.  Check out the amd64 forums, they'll tell ya.

Leech

---

### Post by PandabeaR on 2006-02-04
I took the easy route... got 32 bit version. So now its installed, but I keep getting the error saying to 'unload the debugger'. What does this mean and how do I do it?

---

### Post by Josef K. on 2006-02-05
[to install wine (or cedega) on amd64]("http://ubuntuforums.org/showthread.php?t=96620")
> sudo apt-get install linux32
download wine for i386
> sudo dpkg -i --force-architecture wine*.deb
with wine you'll get an error for missing libraries,
download the 386 packages that contain your missing libraries
**extract** (not install!) that files to your /lib32 directory, and then run ldconfig

---

