---
title: "how to: .exe"
date: 2008-08-17
forum: General Help
---

### Post by mack27 on 2008-08-17
Hi! I'm new to Ubuntu. I need to know if it is possible to launch exe files and how to do it. I have a multimedia dictionary and I use it a lot, but now it won't run on Ubuntu. It's a CD with full installation. What should I do to be able to use it?

---

### Post by Sycron on 2008-08-17
Type in a terminal:
```
sudo apt-get install wine
```

Then run your .exe . It should work.

---

### Post by mack27 on 2008-08-17
i typed it and managed to launch installation which was successfully finished. however, on clicking OK to quit the installaton and launch programme - it didn't open. instead, information popped up saying : "reading data failed. install the programme again". Unfortunately, there isn't even an install option any more, only running the programme, and when clicking produces the same effect of the above information. what else can I do?

---

### Post by colobix on 2008-08-17
Yup. WIne will do the job. Wine is a Windows emulator so it will only run windows applications (not DOS).

If you need a DOS emulator for your DOS games for example, it should be listed under Games in your applications menu.

You can download wine, dos emulator and more stuff under add/remove also in your applications menu.

---

### Post by WRDN on 2008-08-17
> **colobix said:**
> Yup. WIne will do the job. Wine is a Windows emulator so it will only run windows applications (not DOS).

If you need a DOS emulator for your DOS games for example, it should be listed under Games in your application menu.

Wine actually stands for "Wine Is Not an Emulator". It provides the libraries for the programs so they can run under Linux, rather than emulating them.

---

### Post by pparks1 on 2008-08-17
> **WRDN said:**
> Wine actually stands for "Wine Is Not an Emulator". It provides the libraries for the programs so they can run under Linux, rather than emulating them.

Thank you, I was just going to post the same thing...but you saved me the time.

---

### Post by mack27 on 2008-08-17
First of all _thank you_ all for your responses! I downloaded DOSBoxEmulator using add/remove, but it didn't help. I still can't get the programme to run. on the cd cover it only says that it runs under Windows, nothing about DOS. BTW, is it the same thing if I type a command, e.g. like the one Sycron gave me, into the Terminal or download sth from add/remove? And what else can I do to get my dictionary running? :-k

---

### Post by alzie on 2008-08-17
You could install VirtualBox and run a virtual windows m/c inside your Ubuntu.  Its an option.

---

### Post by colobix on 2008-08-17
If it's a windows program, u have to open it with Wine, if it's a dos program u have to open it with the dosbox emulator.
Right-click on the exe file to choose a program.

---

### Post by herteljt on 2008-08-17
> **mack27 said:**
> First of all _thank you_ all for your responses! I downloaded DOSBoxEmulator using add/remove, but it didn't help. I still can't get the programme to run. on the cd cover it only says that it runs under Windows, nothing about DOS. BTW, is it the same thing if I type a command, e.g. like the one Sycron gave me, into the Terminal or download sth from add/remove? And what else can I do to get my dictionary running? :-k

Hi Mack27,
There are several ways to install things in Ubuntu from the repositories.  You've discovered the add/remove selection under applications.  You can also click on System > Administration > Synaptic Package Manager.  A third way is to open a terminal window Applications > Accessories > Terminal and type the code in.  

Other ways to install applications are to download deb packages and download source code and compile it.

To check what version of wine you have installed type the following into a terminal window

```
wine --version
```

It should return what version of wine you have installed.  winehq.org says the most current version of wine is 1.0.

If you want to remove wine type the following in a terminal:

```
sudo aptitude remove wine
```

To install the latest version of wine follow the instructions on this page:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by y-lee on 2008-08-17
Wine *does not* as yet run many windows applications. In fact it has been unable to run *any* of the windows applications I care about. It seems mostly oriented towards running games and I could care less about games.

---

### Post by colobix on 2008-08-17
It runs the macromedia software like Dreamweaver MX, FLash MX etc.
It also runs some games but most of todays games are already made to be ren in linux.
More and more software and games will be created for linux users too so you dont really need wine that much.

---

### Post by rustamb on 2008-08-17
CrossOver Office is the best for novice, but it's commercial. It's build on top of wine with all customization needed to smoothly run wide range of win programs. You could download a trial, run your exe and then let it go.

---

### Post by mack27 on 2008-08-18
OK, believe it or not, the programme is still not running.. I would like to uninstall it and then try again, but ... I just can't find it! :shock: it isn't listed with the add/remove. I remember when installing, the programme suggested a folder that began with C:\  and now I realise my disk isn't called C any more. i tried searching it with the 'Find' option in Places, but there were zero hits. what do I do now? :confused:

---

### Post by mb_webguy on 2008-08-18
Wine simulates the C drive you normally have on Windows.  Go to your Applications menu and look for Wine.  You should have several options, including a Programs folder (like you would have on the Start menu in Windows), "Browse C:\ Drive" (which will open the simulated C drive in Nautilus), "Configure Wine" (where you can change your Wine settings), and "Uninstall Wine Software" (which is a bit like the Add/Remove Programs menu in Windows).

First, check to see if your program is listed in the Wine Programs folder.  If it is, try running it from there.  If not, then you can use the Uninstall Wine Software option to uninstall it.  If you install the most recent version of Wine from the Wine HQ website, you might be able to install and run your program if you can't using the version in the Ubuntu repositories.

---

### Post by mack27 on 2008-08-18
So far: found the dictionary within Wine (version 1.0 btw). didnt run. deleted the programme and installed it again. same thing: unable to open data. and this time i tried opening it directly from Wine. :cry:

---

### Post by aktiwers on 2008-08-18
Try first running:
```
winecfg
```

And save it.

Then run:
```
wine /pathtoyourexefile/exefile.exe
```

replace the pathtoyourexefile with the real path 

or place the exe file in your home folder and type:
```
wine exefile.exe
```

---

### Post by LinuxRocks713 on 2008-08-18
> **alzie said:**
> You could install VirtualBox and run a virtual windows m/c inside your Ubuntu.  Its an option.

This defeats the purpose of running Ubuntu in the first place, making you **addicted** to Micro$oft software.

---

### Post by LinuxRocks713 on 2008-08-18
> **rustamb said:**
> CrossOver Office is the best for novice, but it's commercial. It's build on top of wine with all customization needed to smoothly run wide range of win programs. You could download a trial, run your exe and then let it go.

Again, defeats the purpose of free software.

---

### Post by Sef on 2008-08-18
> Again, defeats the purpose of free software.

Free software is software that anyone can see the source code, and modify it.  It does not matter if it is no cost or cost money.

---

### Post by AndyCooll on 2008-08-18
As has been mentioned above, using Wine does **NOT** guarantee that your program will work, it's hit and miss whether some apps work while others don't. It may simply be that there is some incompatability that Wine can't figure out to get your app runnning. You should check [Wine AppDB]("http://appdb.winehq.org/") as guide whether others have had any success.

As was then mentioned, if it doesn't run under Wine you have two choices:
1. If it's a very important app you could go down the virtualisation route with Virtualbox, VMware or something similar. (ignore the above flamebaiting posts!)
2. If it isn't vital, see if you can find an acceptable Linux alternative.

:cool:

---

### Post by mack27 on 2008-08-18
> **aktiwers said:**
> Try first running:
```
winecfg
```

And save it.

Then run:
```
wine /pathtoyourexefile/exefile.exe
```

replace the pathtoyourexefile with the real path 

or place the exe file in your home folder and type:
```
wine exefile.exe
```
 
typing in the path file in the Terminal seems not to be working. where exactly in my home folder do I type in the other option?

---

### Post by mack27 on 2008-08-18
oh sorry, i just got it ... #-o

---

### Post by mordak13 on 2008-08-18
I've been able to successfully run Adobe Photoshop (CS2) with Wine without any tweaking at all. It does use some ram though so the more you have the better.

---

### Post by aktiwers on 2008-08-18
> **mack27 said:**
> oh sorry, i just got it ... #-o

Did it work? :D

---

### Post by mack27 on 2008-08-18
> **AndyCooll said:**
> As has been mentioned above, using Wine does **NOT** guarantee that your program will work, it's hit and miss whether some apps work while others don't. It may simply be that there is some incompatability that Wine can't figure out to get your app runnning. You should check [Wine AppDB]("http://appdb.winehq.org/") as guide whether others have had any success.

As was then mentioned, if it doesn't run under Wine you have two choices:
1. If it's a very important app you could go down the virtualisation route with Virtualbox, VMware or something similar. (ignore the above flamebaiting posts!)
2. If it isn't vital, see if you can find an acceptable Linux alternative.

:cool:

Yeah, you're right. It seems Wine simply will not help this particular programme run (as has been mentioned before, true). I might try the virtualisation route you give in 1. I will definitely shop for a multimedia dictionary that runs on Linux as well. [B]but it is exciting to be learning all this new stuff :mrgreen: [B] Thanks everyone for joining this thread. This has been a very warm welcome. :smile:

---

### Post by mack27 on 2008-08-18
> **aktiwers said:**
> Did it work? :D

nope 8-)

---

### Post by aktiwers on 2008-08-18
Aww..  

Well I am no Wine guru, but what is the name of the app?
And maybe you can copy/paste the output from the terminal here so someone could have a look? (assuming it spits out some errors when you try to run the app)

Sometimes you need to configure wine to make it work with a specific app.

Edit: and welcome by the way! :)

---

### Post by mb_webguy on 2008-08-19
> **Sef said:**
> Free software is software that anyone can see the source code, and modify it.  It does not matter if it is no cost or cost money.
Not true.  There are two definitions of "free software", just as there are two different meanings of "free".  One is "free as in free speech", and the other is "free as in free beer".  The first is nearly synonymous with open-source, and means the software may be freely altered and distributed.  The second means that it may be obtained without charge.

"Free as in free speech" software is almost always "free as in free beer", but occasionally is not.  "Free as in free beer" software may or may not be "free as in free speech".  Both are "free software".

---

### Post by Sycron on 2008-08-21
Software is like the air, I don't understand why people develop closed-source applications...

I don't need extra-modified-patched air to live. I live with air as it is...

---

### Post by vinod.vru on 2008-08-26
sudo apt-get install wine

this method worked for me.
after running the .exe file  the required program was found in top toolsbar application / others menu.

---

