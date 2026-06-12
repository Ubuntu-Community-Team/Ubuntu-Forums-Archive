---
title: "What have I done with my packages?"
date: 2008-10-10
forum: General Help
---

### Post by thonaker on 2008-10-10
Ok, I've been a Windows user for years, so bear with me.

I noticed after I cleaned out some packages, incomplete and/or orphaned, I guess, that many of my games no longer run.  I can completely uninstall them and re-install them, and they still do not run.  I thought they might grab the packages they need again with the package manager, but they don't fix themselves.

I do not know exactly what I have done.  Ubuntu is different than Windows, but I do like many things about it. 

I've lost most of my screen savers too.

But, many programs run just fine.  I have also installed programs from the package manager, only to have them not run at all, or have them not listed in "Applications."

How do I get things back to where they were?  Why don't the packages I need, get installed back on the machine with uninstall and reinstall?  Shouldn't it find them?  Remember, explain things thoroughly, I have been a Windows user.

Troy

---

### Post by cariboo on 2008-10-10
How did you clean out the packages? Do you have any broken packages listed in Synaptic Package Manager-->Edit-->Fix Broken Packages?

Jim

---

### Post by thonaker on 2008-10-10
I followed some advice from the net on how to clean up Ubuntu.  I used the terminal some.  (I don't understand it as easily as I do command line in Windows.)  My system was acting weird.  Some PDF file seemed to be the culprit.  I think I did try to "fix broken packages."

Troy

---

### Post by bodhi.zazen on 2008-10-10
hard to know from what you have described.

What error messages are you getting with your games ?

Do you have a link to the "how-to" you were following ?

In general, software or package management is very different on Ubuntu then Windows. Dependencies are handled "automagically" so any needed applications should not have been removed.

Of course when you "force" apt-get to do something you can have problems.

---

### Post by thonaker on 2008-10-11
I think this is the link.

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

I didn't get all the way through all the stuff.  Not everything seemed to work right for me.

Troy

---

### Post by Mister.Vash on 2008-10-11
Start off with to see if it fixes anything or outputs anything:
sudo apt-get check


After that is done, find the name of a package that isn't working.  I don't know what games aren't working, so let's just pretend it was gedit that isn't working - run a:

sudo apt-get install --fix-broken gedit

Replacing gedit with whatever isn't working and see if that makes any difference in being able to run the application.

Post back with the details of what happens

---

### Post by thonaker on 2008-10-11
First command gave me this

Reading package lists... Done
Building dependency tree       
Reading state information... Done

So far no difference.

The second command, I'm working on Open Arena to see if I can get that fixed.  I'll get back in a bit to let you know what happens.

Ok, so the second command you gave me ended up replacing the data files for Open Arena, it upgraded them.  Still, when I try to start the program, I just get a quick flash of the screen and nothing more happens.  My first person shooters all do not work, if that helps.  So far, looks like all the games that came with the OS work.  And as I have said, in times past, some things I have installed from the Package Manager simply do not work.  The update manager tells me frequently that my system is out of date even though I'm not.

Troy

---

### Post by thonaker on 2008-10-11
You guys got anything else I can try?  Surely I wouldn't have to re-install?  I get the idea, Linux folks try not to do that.  Many things are running fine.

Troy

---

### Post by Riffer on 2008-10-12
Actually more then a few of us re-install.  I know for me I learn by doing and that means at times I get to a point where tons of stuff is broken or not working and its just damm easy to re-install.  So far since I've started (June '07) I've done about 10 re-installs.

You could try re-installing "Ubuntu-desktop" on your present system, just a hunch.

---

### Post by thonaker on 2008-10-12
You may be right.  Something broke, I just don't know how to get things back.  Funny thing is Virtual box just quit working yesterday.  Silly.  I just had it running.

I guess I could back everything up and start over.  Windows is sometimes easier to do this way as well.  It beats wasting hours trying to fix the problem.  I just don't know Linux that deep.

Troy

---

### Post by DirtDawg on 2008-10-12
> **thonaker said:**
> First command gave me this

Reading package lists... Done
Building dependency tree       
Reading state information... Done

So far no difference.

The second command, I'm working on Open Arena to see if I can get that fixed.  I'll get back in a bit to let you know what happens.

Ok, so the second command you gave me ended up replacing the data files for Open Arena, it upgraded them.  Still, when I try to start the program, I just get a quick flash of the screen and nothing more happens.  My first person shooters all do not work, if that helps.  So far, looks like all the games that came with the OS work.  And as I have said, in times past, some things I have installed from the Package Manager simply do not work.  The update manager tells me frequently that my system is out of date even though I'm not.

Troy

Try starting Open Arena in a terminal. You should get an error that will probably contain a hint about what's wrong. Reinstalling might be easier than fixing the problem, but I personally hate doing it unless I have to.

EDIT: I just saw your post about the system claiming it needs an update when it doesn't. Yikes, that's gnarly.

---

### Post by thonaker on 2008-10-12
That's one of my problems.  How do I do I do it with the terminal?  I'm just not used to the Linux terminal.  When I installed Serious Sam 2 with Loki files, I had no real idea how to do what they were telling me to do.  They said type "Serious Sam" or something like that.

Yeah, it's funny, I keep getting my updates but it keeps telling me I'm not up to date.  I've read about others having the problem a little while back.

Troy

---

### Post by bodhi.zazen on 2008-10-12
for your updates try:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by DirtDawg on 2008-10-12
> **thonaker said:**
> That's one of my problems.  How do I do I do it with the terminal?  I'm just not used to the Linux terminal.  When I installed Serious Sam 2 with Loki files, I had no real idea how to do what they were telling me to do.  They said type "Serious Sam" or something like that.
Troy

If you installed openarena through synaptic or with a .deb package, you should be able to run it by opening the terminal and simply entering 'openarena' (w/o quotes, of course). Most apps try to make their commands relatively obvious. It can be a pain when they don't.

If you installed Open Arena locally, you can enter the path to the binary. For example, to run mine I enter:
```
~/localapps/openarena-0.8.0/openarena.i386
```

EDIT: FYI, if you ever want to see a command for a menu item, right-click your 'Applications' menu and choose 'Edit Menus', then choose the application in question, right-click it and choose 'Properties'. There you will see the command to run in a terminal in the 'Command' box.

---

### Post by thonaker on 2008-10-13
Thanks for that info on the commands.

Here's what I get when I try to run Open Arena from the terminal

/home/troy/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak7-patch.pk3 (1 files)
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (226 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (138 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (2033 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (98 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (1035 files)
/usr/share/games/openarena/baseoa/more_crosshairs.pk3 (78 files)
/usr/share/games/openarena/baseoa

----------------------
4509 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 1.333
...setting mode 6: 1024 768
Available modes: '1024x768 320x240 400x300 416x312 512x384 576x432 640x480 700x525 800x600 832x624 640x512 576x384 320x200 640x400 720x450 840x525 640x384 360x200 720x400 320x175 640x350'
Couldn't get a visual
...WARNING: could not set the given mode (6)
Setting r_mode 6 failed, falling back on r_mode 3
Initializing OpenGL display
...setting mode 3: 640 480
Available modes: '1024x768 320x240 400x300 416x312 512x384 576x432 640x480 700x525 800x600 832x624 640x512 576x384 320x200 640x400 720x450 840x525 640x384 360x200 720x400 320x175 640x350'
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
GLimp_Init() - could not load OpenGL subsystem


Looks like something related to display modes and OpenGL.

Troy

---

### Post by thonaker on 2008-10-13
I was just looking at the OpenGL thing and the settings and decided to check on my graphics driver.  You know what?  The Nvidia driver some how got de-selected and was not in use.

I guess that would explain some of the graphically more intense things not running.

Open Arena looks like it is running now.  I may not have to re-install after all.

Troy

---

