---
title: "Can I Install Windows PC Games into the 8.10?"
date: 2008-11-29
forum: General Help
---

### Post by Matt640 on 2008-11-29
I was wondering if anyone out there could help me get my NBA Live series up and running again on the UBUNTU 8.10. Are there other alternatives other than Wine? Apparently, when I use Wine, my PC's slower than usual. I'm an Addict and I need my dose of virtual hoops, HELP!

---

### Post by damis648 on 2008-11-29
I am afraid Wine and Crossover are your only really feasible solutions.

---

### Post by soro2005 on 2008-11-29
You can run Windows in a virtual machine. It's not the same performance, though, as running it directly on the hardware.

---

### Post by Cresho on 2008-11-29
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8735](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8735)

---

### Post by damis648 on 2008-11-29
> **soro2005 said:**
> You can run Windows in a virtual machine. It's not the same performance, though, as running it directly on the hardware.

Due to how a VM works, they can not really have direct access to the GPU. That being said, games do not work.

---

### Post by Matt640 on 2008-11-29
From the link Cresho gave me, I've got no clue still on how to get it to work.

---

### Post by damis648 on 2008-11-29
In a terminal, run:
```
sudo apt-get install wine
```

Now when it is done, pop in your game CD and run the installer executable from the CD (usually autorun.exe or setup.exe) with wine, which should automatically happen when double clicking on it. The installer for the game should start. The rest is history. :popcorn:

---

### Post by Cresho on 2008-11-29
ya well you need to install wine, learn how to use wine, and make sure you can only launch exe from command line and not by double clicks.  You might want to disassociate wine and exe files.

The learning curve to use wine is short!  it's just getting there.

I currently run..
prey
world in conflict
anachronox
many more games.

---

### Post by Matt640 on 2008-11-29
Alright, how do I launch exe from command and disassociate wine and exe files?

---

### Post by Cresho on 2008-11-29
open terminal

"sudo apt-get install wine"


reboot.

to check if its working, type in terminal winecfg

click on about and post what version you are running.  I need to know.

load up your cd and navigate to your cd and double click exe.

after it installs, you may get some errors...then we can kinda debug it as we go.  you may need to do some modifying of files but this isnt hard at all.  after modded files, if nothing works, well, at least we tried.  winedb has a few users that got it to work.  Ill look at those and see how we can get it to work for you.  You are the first intrepid ibex user so you may want to post in winedb so others can benefit from you if we get this working.

its not hard...just have patience.

---

### Post by Matt640 on 2008-11-29
Thanks. Truth be told, I've only been using Ubuntu for less than a year. It was recommended to me and frankly, I think it outdoes Vista in every aspect except for it's Gaming. Can't wait till they get all that going. My friend who recommended this to me said we'd be able to play Windows Games with much less hassle soon. Hope it's true.

---

### Post by Cresho on 2008-11-29
> **Cresho said:**
> open terminal

"sudo apt-get install wine"


reboot.

to check if its working, type in terminal winecfg

click on about and post what version you are running.  I need to know.

load up your cd and navigate to your cd and double click exe.

after it installs, you may get some errors...then we can kinda debug it as we go.  you may need to do some modifying of files but this isnt hard at all.  after modded files, if nothing works, well, at least we tried.  winedb has a few users that got it to work.  Ill look at those and see how we can get it to work for you.  You are the first intrepid ibex user so you may want to post in winedb so others can benefit from you if we get this working.

its not hard...just have patience.




i just updated this

---

### Post by Matt640 on 2008-11-29
Click on about where? and how do i tell you what version I'm running. I'm currently updating so it'll take a while.

---

### Post by CatKiller on 2008-11-29
> **Matt640 said:**
> Apparently, when I use Wine, my PC's slower than usual.

Not necessarily. Some games work better in Wine than they do in Windows. Some don't work at all.

You seem to be on the right track.

---

### Post by Cresho on 2008-11-29
in terminal you type this


```
winecfg
```

then when it pops up, click on about tab and tell me version.  or in terminal you can also "wine --version"

when you want to uninstall something, type "uninstaller" in terminal and an uninstaller program for windows pops up.

I'm teaching you so ....play along.


right now, i am working on gothic 3.  I am looking for the much needed patch 1.7 that is suppose to come out so i have some time for you.  ill probably install another windows game while im "dicking aroung here".

---

### Post by Matt640 on 2008-11-30
Alright, I'm currently using Wine 1.0.1. Is there a later version? And where do I type uninstaller to uninstall stuff?

---

### Post by Cresho on 2008-11-30
the one you are using is fine.  it is the stable version.  so now all you need to do is double click on the exe and install.  if not, right click on exe and "install with wine".

---

### Post by Matt640 on 2008-11-30
Ok. I've figured the Uninstaller out. I started with some basic games. Installation and launching proceeds smoothly. During gameplay, the Screen flashes non-stop, eventually resulting in graphic errors and eye sore. Any cure for that?

---

### Post by Matt640 on 2008-11-30
I've also discovered some games' .exe won't launch and some even after installation, would not start. So far, all tested games are authentic.

---

### Post by ajcham on 2008-11-30
Which game is causing the flashing graphics? Check the Wine AppDB to which you were referred earlier to see if it is known to be compatible with Wine.

Also, is compiz running?  Try disabling compiz before running the game:
[FONT="Fixedsys"]metacity --replace[/FONT]

---

### Post by Matt640 on 2008-11-30
The game that caused flashing graphics was as basic as Worms Armageddon. Those were just for test. I've just installed King Kong which is pretty much up a notch. I notice that every game requires a reboot to use, but when I agree, not thing happens. I take it that restarting the computer isn't actually restarting the emulator? Now, am I supposed to use "metacity--replace" to disable compiz?

---

### Post by ajcham on 2008-11-30
According to the AppDB, Worms Armageddon is a quite flakey in Wine. It has received mostly Bronze ratings and the odd Silver.  The AppDB rates games as follows:
[LIST]
[*]Platinum: Runs perfectly
[*]Gold: Runs perfectly with a little tweaking
[*]Silver: Runs with minor issues
[*]Bronze: Partly runs, but is very buggy.
[*]Garbage: Doesn't run or is completely unusable.
[/LIST]

> 
...as basic as Worms Armageddon

It is worth noting that the apparent complexity of a game is not a good indicator of whether Wine will run it well or not.

> I notice that every game requires a reboot to use, but when I agree, not thing happens. I take it that restarting the computer isn't actually restarting the emulator?

You shouldn't need to reboot linux - when the installer finishes Wine (which is NOT an emulator, remember) will close automatically which is equivalent to shutting down Windows as far as the game is concerned.

> Now, am I supposed to use "metacity--replace" to disable compiz

That's right, but remember to put a space between metacity and --replace.

---

### Post by Cresho on 2008-11-30
You're jumping the gun.

Anyway! Before you install anything, it's always good to search for your software in winedb for compatibility.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Do a search on your specific software and sometimes they offer solutions and fixes or they just work.

Your compiz needs to be disabled in order for you to run 3d games.  In linux, you may need to create a special launcher, like the ones I use, for playing 3d intense games.  For now, just disable compiz-fusion.

just click on system->preferences->Appearance and click on visual effects and hit none.

try your 3d games and post what your results.

---

### Post by Matt640 on 2008-11-30
Here's the thing. The game installed nicely. Whenever I try to launch the application, a window pops up asking me to reboot. I click yes, but nothing happens. Anyway, around this?

---

### Post by Cresho on 2008-11-30
hmmm...okay  what nba live are you using?  have you checked to see if you have a cd copy protection on it?  The latest wine versions work with copy protected cd's but I just need to make sure we are on the right track before doing something like installing the new wine.

if you do have a cd copy protected game, you should install the latest patch and also try a no-cd exe just for testing purpouses.  make sure you backup the patched exe before overriding it with the no-cd exe.

---

### Post by Matt640 on 2008-11-30
I have NBA Live 07 and I'll be trying to get the 08 soon. Using the AppDB, these 2 scored Gold. I might have come to the worst case scenario where my DVD can't even be read. CDs are read just fine. Could it be because it's a DVD? Say I were to update my Wine, what should I do? How should I know whether my DVD is copy protected and what latest patch am I installing for? Pls break it down to step by steps. Thank you.

---

### Post by Cresho on 2008-11-30
Ya!  Like I said, be patient.  I subscribed to this thread incase you got stuck some where.

Gold in wine means it works but with a few added tweaks.  So there is hope.




Say I were to update my Wine, what should I do?

That's a tough one because I don't use intrepid ibex.  I reverted back since hardy heron is LTS and Intrepid ibex is not which makes it more beta than LTS.

How should I know whether my DVD is copy protected and what latest patch am I installing for?

your NBA live uses SafeDisc 4.60 protection scheme on the dvd.  according to places that I have read, this scheme is not supported yet but you can check out gamecopyworld for a exe fix.  its available and I am not sure how laws work in this case so be careful.

---

### Post by Matt640 on 2008-12-01
Now I've discovered the wonders that GameCopyWorld can do for me, but where do I download the .exe? I won't be playing OnLine with it since this country's got no one to play with anyway. I believe you're pretty close to solving this case, Cresho. Thanks again.I just need my Hoops.

---

### Post by Cresho on 2008-12-01
search for it in the search bar and its in there.

---

### Post by Matt640 on 2008-12-01
I see the v1.1 .exe, but there's nothing I can click to Download it.

---

### Post by ajcham on 2008-12-01
> **Matt640 said:**
> I see the v1.1 .exe, but there's nothing I can click to Download it.

You should be able to click the floppy disk icon to download (see attachment). It's a rar archive so make sure you have unrar installed.

Also be sure to download the correct fix - you only need v1.1 if you've patched NBA live.  If it's a clean install use the v1.0 fix.

---

### Post by Cresho on 2008-12-01
click on the floppy icon like the guy above me says.  then go into your /home/yourusername/.wine/drive_c/Program Files

and that is the windows cd directory aka wine directory.  if you are navigating through nautilus (your folder navigator), click on view and "show hidden files"

---

### Post by Matt640 on 2008-12-01
Ok, I've saved the v1.0 and downloaded the RAR for Linux. Now what? My v1.1 is in my Home Folder.

---

### Post by Matt640 on 2008-12-01
Also, the v1.1's Read-Only. What to do with the Rar?

---

### Post by Slim Odds on 2008-12-01
> **Cresho said:**
> open terminal

"sudo apt-get install wine"

reboot.  <<<<<<<<<<<<<<------------------------------



Man, that's **RIDICULOUS** !!!!!

Why do people keep saying crap like this?

There is **ABSOLUTELY NO NEED TO REBOOT YOUR COMPUTER!!!**

You're gonna have people thinking linux is a windows clone.   Stop it.

---

### Post by Cresho on 2008-12-02
> **Slim Odds said:**
> Man, that's **RIDICULOUS** !!!!!

Why do people keep saying crap like this?

There is **ABSOLUTELY NO NEED TO REBOOT YOUR COMPUTER!!!**

You're gonna have people thinking linux is a windows clone.   Stop it.

reboot is not needed, its a "windows habit"  I am a recovering windows user.  Also, people never seem to recover from addiction.  So you have people who go back to windows, and you have people who say "reboot".

---

### Post by Cresho on 2008-12-02
> **Matt640 said:**
> Also, the v1.1's Read-Only. What to do with the Rar?

so which one do you have?  1.1 or 1?  what version is your game?  did you install a patch?

---

### Post by lukeiscool on 2008-12-02
play on linux has a list of games you can use well, to get play on linux, go to [http://www.playonlinux.com](http://www.playonlinux.com) and download. You must have CDs for most games, but some you don't.

---

### Post by Matt640 on 2008-12-02
How do I find out what Version I'm using? I didn't install a Patch. I have the 1.0 and how do I get PlayOnLinux?

---

### Post by Matt640 on 2008-12-02
Also, a Window pops-up saying that I need to Restart to Install. Man, this is a pain.

---

### Post by Cresho on 2008-12-02
did you extract the rar and replace the exe in the game directory?

---

### Post by Matt640 on 2008-12-02
Ok, extract RAR to where? Cause I can't seem to get it into my Program Files.

---

### Post by Cresho on 2008-12-02
/home/YOURUSERNAMEHERE/.wine/drive_c/Program Files

OPEN UP YOUR PLACES and home.  click on view and put a check on "show hidden files"

---

### Post by Matt640 on 2008-12-02
Alright. Workng on it.

---

### Post by Matt640 on 2008-12-02
When it says that I need to restart my Comp. to install, and I click 'Yes' and nothing happens, what should I do?

---

### Post by Slim Odds on 2008-12-02
> **Matt640 said:**
> When it says that I need to restart my Comp. to install, and I click 'Yes' and nothing happens, what should I do?

That's a "Windows" message. Ignore it.

Don't forget that when you install a Windows program under WINE, etc.  They still think they are running under Windows.

---

### Post by Cresho on 2008-12-03
did you extract the exe file and replaced the nba exe from the install with the no cd exe?  look in a folder in program files.  It is in there where you should find the exe and replace it.

---

### Post by Matt640 on 2008-12-03
So I'm supposed to extract the nba exe from the install with the no cd exe into where I installed my game to replace the original exe file, right? I've found it, but I'm still working on Installation itself. You've been great help Cresho, thanks.

---

### Post by Cresho on 2008-12-03
Ya, i recommend backing up the original exe and put the exe from rar in its place.  Make sure the exe has the same name as the one from the installed exe including case sensitive.

---

### Post by Matt640 on 2008-12-03
Alright, I've finally gotten the game to install and I believe I've got everything I need. Now, all I need is a step by step guide on what to do next in detail so I don't screw up. Thank you.

---

### Post by Matt640 on 2008-12-03
And the Archive Manager is the same as RAR, right?

---

### Post by Matt640 on 2008-12-03
I've extracted the v1.0 into the game directory, which I assume is what I'm supposed to do. When I try to launch the game, the cursor goes into loading mode for a bit then just stops and nothing happens? What have I done wrong?

---

### Post by Cresho on 2008-12-04
what directory did you extract the exe to?  is it doing something different than before?  Make sure compiz is off.

---

### Post by Matt640 on 2008-12-04
I extracted it into my wine./Program Files/EA Sports/ NBA Live 07 file. It's still the same, do I have to off Compiz everytime I launch the game?

---

### Post by Matt640 on 2008-12-04
Also, when Compiz is off, everything else fails to work. Basically, I'm jammed. aMSN and the Fox are examples of things that won't work.

---

### Post by Cresho on 2008-12-04
when you extracted the file, did you over write the original exe or replace it?  Just want to make sure.  What if you used the patch/update for the game and replace the exe with a no cd exe for patch/update version?

what graphics card are you using?

---

### Post by orlox on 2008-12-04
You could try a more recent version of wine. This is the howto:

 1) REMOVE default ubuntu wine... you'll have problems if you do*n't.
```
sudo apt-get remove wine
```

2) install GIT :
```
sudo apt-get install git-core
```

3) fetch wine sources : ([http://www.winehq.org/site/git](http://www.winehq.org/site/git))
```
git clone git://source.winehq.org/git/wine.git ~/wine-git
```

you'll get a subfolder of your home dir called wine-git with all source code.

4) Install dependencies for wine:
```
sudo apt-get build-dep wine
sudo apt-get install fakeroot
```

5) go inside wine-git folder, configure/make/make install:
Code:
```
cd ~/wine-git
./configure --prefix=/usr
make
sudo make install 
```

and that would leave you with the latest version, that has many tweaks that allow you to play many games...

Another important thing, is your video card. Even though an app is marked gold on appDB, it means someone, with certain video card, made the test and it worked. Try running lspci on a terminal and see how your video card is listed in there.

---

### Post by Matt640 on 2008-12-04
Ok, I've gone with getting the latest version of Wine. Before I switched to Ubuntu, my NBA Live 07 worked fine on XP. What I really need are **detailed directions** on what to do to get the game running. That's all I need. I've extracted the v1.0 No CD exe into the Game's directory and yet the game doesn't launch. Have I missed a step or done something wrong? Do tell.

---

### Post by linux_tech on 2008-12-04
Quake 4 Linux
[http://www.linux.com/articles/49600](http://www.linux.com/articles/49600)

---

### Post by Bateluer on 2008-12-04
> **Matt640 said:**
> Alright, I'm currently using Wine 1.0.1. Is there a later version? And where do I type uninstaller to uninstall stuff?

1.0.1 is the most recent stable version, but the development branch is at 1.1.9. Varying titles run better with different versions of Wine, at least, in my experience.

---

### Post by ajcham on 2008-12-04
> What I really need are detailed directions on what to do to get the game running.

As far as I can tell you've done everything you should need to do. Are you sure you copied the crack into the correct place (it should have overwritten the original game exe)?  If so could you try running the game from a terminal, to see if there are any useful error messages:

[FONT="Fixedsys"]wine "/home/*USER_NAME*/.wine/drive_c/*(insert rest of file path here)*"[/FONT]

---

### Post by Cresho on 2008-12-04
Now that we tried running the game with ibex's version of wine, We will need to try a newer version of wine.  I suggest you do what this guy says.


> **orlox said:**
> You could try a more recent version of wine. This is the howto:

 1) REMOVE default ubuntu wine... you'll have problems if you do*n't.
```
sudo apt-get remove wine
```

2) install GIT :
```
sudo apt-get install git-core
```

3) fetch wine sources : ([http://www.winehq.org/site/git](http://www.winehq.org/site/git))
```
git clone git://source.winehq.org/git/wine.git ~/wine-git
```

you'll get a subfolder of your home dir called wine-git with all source code.

4) Install dependencies for wine:
```
sudo apt-get build-dep wine
sudo apt-get install fakeroot
```

5) go inside wine-git folder, configure/make/make install:
Code:
```
cd ~/wine-git
./configure --prefix=/usr
make
sudo make install 
```

and that would leave you with the latest version, that has many tweaks that allow you to play many games...

Another important thing, is your video card. Even though an app is marked gold on appDB, it means someone, with certain video card, made the test and it worked. Try running lspci on a terminal and see how your video card is listed in there.

---

### Post by Matt640 on 2008-12-04
I've gotten the latest Wine. I looked up some Cracks on the Net and I've extracted the v1.0 exe. into the game directory. Could there be anything else? I've tried turning compiz off which hasn't done anything at all, but neutralize my desktop. Maybe I should start from the Top. But I still don't see what i've missed or done wrong.

---

### Post by Cresho on 2008-12-05
what graphics card?

---

### Post by Matt640 on 2008-12-05
Can't tell. I don't know where to read it.

---

### Post by ByteJuggler on 2008-12-05
> **Matt640 said:**
> Ok, I've gone with getting the latest version of Wine. Before I switched to Ubuntu, my NBA Live 07 worked fine on XP. What I really need are **detailed directions** on what to do to get the game running. That's all I need. I've extracted the v1.0 No CD exe into the Game's directory and yet the game doesn't launch. Have I missed a step or done something wrong? Do tell.

Wine by itself (just like a default install of an older Windows) is not neccesarily enough to get games to run - you need to install DirectX as well.  This can be a bit bothersome as DirectX may require other bits and pieces.  Getting a "games ready" Wine setup does unfortunately take a bit of work and technical know how.  

There is however a script on the Wine site, that helps with installing a lot of the dependencies needed for various games and applications, called "winetricks".  Download it [here]("http://wiki.winehq.org/winetricks").  If you run it without any parameters, it should display a simple GUI from which you can select what to install.  Make sure you have DirectX  etc installed then try your game again.  

Aside: To help identify your graphics card, press alt-f2 and paste into the command box:
```

gksudo lspci | grep -i vga >/tmp/gfx.txt; gedit /tmp/gfx.txt

```
It should open up the details of your VGA card in a text editor.

Edit: Just to be clear, is [this]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8735&iTestingId=31548") the game you're trying to get working?

Edit: Further information about installing/configuring DirectX is [here]("http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html").

Edit: Another application that may help install/manage things in wine is Wine-Doors, available [here]("http://www.wine-doors.org/wordpress/?page_id=2").  I've not tried this myself, and will do so later today.

---

### Post by Matt640 on 2008-12-05
Here's what I got. Intel Corporation 82865G Integrated Graphics Controller (rev 02)

---

### Post by Matt640 on 2008-12-05
Here's what I got. Intel Corporation 82865G Integrated Graphics Controller (rev 02). And I've got DirectX

---

### Post by ajcham on 2008-12-05
> **Matt640 said:**
> Here's what I got. Intel Corporation 82865G Integrated Graphics Controller (rev 02). And I've got DirectX

I think your graphics chip isn't up to scratch - unless you've run NBA 07 in Windows on the same box, and thus know different.

Here is Intel's list of games known to work with that chip: [http://www.intel.com/support/graphics/sb/CS-010472.htm?iid=graphics+865main&]("http://www.intel.com/support/graphics/sb/CS-010472.htm?iid=graphics+865main&").  NBA Live 07 is not in the list, and from what I can tell all games in the list predate it by some years.  The list was last updated on 19 November 2008. 

According to the NBA Live 07 minimum specification, you need at least a 64MB card to play the game (and based on my previous experience with minimum specs, you probably need a 128 or even 256MB card to run the game well).

---

### Post by Matt640 on 2008-12-08
Back in XP, this game worked on my Comp. perfectly. I'm not sure what else I gotta do, but take it from the top. Even then, I'm not sure where to start.

---

### Post by archeryguru2000 on 2008-12-08
Matt640, I feel your pain.  I too have tried to get a couple of Windows games to run on linux... not much success either.  I've since resorted to games that are better suited for linux (yeah, I know, I'm a quitter).  Such games as OpenArena, Enemy territory, etc.  However, since many of you seem quite knowledgeable in the gaming sector maybe one (or more) of you could answer a question of mine.  I'm considering purchasing a game controller (for obvious reasons) and I was curious if anybody out there has any tips on a good (linux-compatible) controller.  I wouldn't have much debate on hacking one to work either... so long as others have had similar success.  Any feedback would be greatly appreciated.

Thanks,
archery

---

### Post by Matt640 on 2008-12-08
Nah, man. You're not a quitter, just nothing much we can do about these things. From what've I read, there are really rare posts on this forum about trying ppl to use a Controller for games on Linux. As if getting them installed wasn't a pain enough. Anyway, I don't remember where I've read them, but so far only a couple that I've read has achieved unstable success.

---

### Post by Cresho on 2008-12-09
I have no expirience with intel cards or onboard chips.  SO..I can't go any further.  I use Nvidia.

---

### Post by Matt640 on 2008-12-09
Alright, Cresho. Thanks a lot anyway, you've been big help.

---

