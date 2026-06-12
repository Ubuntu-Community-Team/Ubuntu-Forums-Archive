---
title: "Few Fluxbuntu's newbie question"
date: 2008-08-10
forum: General Help
---

### Post by LitusMayol on 2008-08-10
Hi!

I've an old laptop that I've triyng to improve its performance by installing a non-heavy system. I finally installed ***Flux*buntu** (the reasons and how I've arribed to it in [this]("http://ubuntuforums.org/showthread.php?p=5559113#post5559113") post)


OK. I've installed it and it is running so faster than before. But is my first time with *Fluxbox* and I'm having some newbie troubles. Will you help me?


[LIST=1]
[*]**How can I select the language?** I'm from catalonia and I'd like to have the laptop in catalan. While I was installing ***Flux*buntu** it asked me about language and I've selected "catalan", but the system is on english. Any idea about how to set it in catalan? Thanks!
[*]**The USB media are not being recognized.**I've plugged a pendrive and it is not recognized...Have I to do something special to get it recognized? I would like to get proffit of have speed up the computer, and I'll probably work a lot with flash memories.Any idea? 
[*]**Can you give me some starters advices?** Can you give me some starting stuff? What will you say to some that have just started for first time with a Fluxbox? (Like me!)
[/LIST]




Thanks everyone! :D

---

### Post by mikjp on 2008-08-10
- Maybe nobody has translated Fluxbox?
- You might have to do as we all did a few years ago: we mounted USB sticks by hand... (sudo mount /dev/sda1 /some/directory)
- try googling [fluxbuntu automount usb](http://www.google.fi/search?q=fluxbuntu+automount+usb&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:fi-FI:official&client=firefox-a)
- Fluxbuntu is pretty close to Debian, so you might find help in [http://qref.sourceforge.net/](http://qref.sourceforge.net/) (at least in English & Spanish!)


mikko

---

### Post by Stunts on 2008-08-10
1. Try and check for a solution in fluxubuntu's forums. They are somewhat more specific...
2. In order to automount drives you need to manually correct a bug in fluxubuntu install. Just open a terminal and type in:
```
 mkdir ~/.ivman 
```
That should take care of your automounting issues.
3. As for some advices... well I installed fluxbuntu in a few old deasktops in my university that were going to be recycled. They are now in good use. Some things I did:
```
sudo atp-get install xfe
```
This will install a simpler file manager, sort of like the file manager in win3.1. My coulegues found it simpler to use then rox.
```
sudo apt-get install feh
```
I found this picture viewer much better then the built in choice.

One more thing, when you install new programs, the menus won't update automatically. You have to open a terminal and type in ```
 sudo update-menus 
```

Good luck with your new install. The project isn't dead, btw, it's just slow moving =-)

Hope this helps.

---

### Post by snowpine on 2008-08-10
Stunts is right, 'mkdir ~/.ivman' should automount USB devices.

The #1 tip I can give? If you learn how to edit the text files in your ~/.fluxbox folder, you can easily customize Fluxbox however you like. For example, you can add apps like conky to the startup file to make them auto-load. Learning to edit the menu file is important, too, because you can make your favorite apps easier to execute.

Also, in Fluxbuntu, you can drag applications from Rox (most of them are in /usr/bin) to the desktop to create icons.

---

### Post by LitusMayol on 2008-08-10
Oh my god!

Thanks **Stunts**! Thanks **snowpine**! Thanks both!
I though it was gonna be difficult to find people with ***Flux*buntu** knowledge! Thanks, anyway: perfect!


About the language package I'll investigate in fluxbuntu forum and in the free software organizations from here (Catalonia).

About the pendrive... Right now isn't working. I'll reboot and try it again. If it still unworking ([COLOR="Silver"]Is "*unworking*" a correct word? xD[/COLOR]) I'll say something.



Anyway thanks both!

---

### Post by LitusMayol on 2008-08-10
USB solved!

After rebooting it works perfectly! Thanks! ;)

---

### Post by LitusMayol on 2008-08-10
Another question...

I've seen it have all the programs I need. But I've tried several times to open a ".png" or a ".doc" or a ",abw" and it shows me a message like this:

```
No run action specified for files of this type (image/png) - you can set a run action by choosing `Set Run Action' from the File menu, or you can just drag the file to an application
```

I know: it say WHAT I must do. But when I arrive there it asks me for "shell command" (supose the command of the abiword/viewer/openoffice/whatelese). But I don't know what to write: "abiword"? Doesnt works...


Does anyone knows how do I pre-set the programs that must open each file?

Thanks again, pardon me: I'm a ***Flux*buntu**'s newbie...
Sorry for bothering...!

---

### Post by snowpine on 2008-08-10
> **LitusMayol said:**
> I've seen it have all the programs I need. But I've tried several times to open a ".png" or a ".doc" or a ",abw" and it shows me a message like this:

```
No run action specified for files of this type (image/png) - you can set a run action by choosing `Set Run Action' from the File menu, or you can just drag the file to an application
```

I know: it say WHAT I must do. But when I arrive there it asks me for "shell command" (supose the command of the abiword/viewer/openoffice/whatelese). But I don't know what to write: "abiword"? Doesnt works...


Yes, this is one of the reasons I've heard people say Fluxbuntu "isn't user friendly." :) It will take some time for Rox-Filer to "learn" which applications are your favorite. Once you've set apps for most common file types, you won't have to worry about it any more. 

In this example, we are going to open a file named 'document.doc' using Abiword. 

In Rox, right click on the file and choose "Set Run Action." 
Notice the cursor is blinking in "Enter a shell command," so all you need to do is type 'abiword' so it says 'abiword "$@"' 
Press Enter (or click Use Command).
Now, double click on document.doc (or any other .doc) and it will open with Abiword.

You can also do it with "Drop a suitable application here." Let's say you want to open page1.htm with Kazehakase. Right click the document and choose "Set Run Action." Drag the Kazehakase icon from your desktop to the box. Easy!

---

### Post by Stunts on 2008-08-11
Snowpine's got it all covered.
=-)
BTW, a bit more costumizing:
You can edit menus using from a terminal:
```
leafpad ~/.fluxbox/menu 
```
Look at your menu and look at the file. It's quite simple to use once you figure it out. And it only takes like 5-10 minutes of paying attention to the syntax to understand how it works.
Good luck. If you need anything else we'll be right here.

Edit:
Networking with windows computers is not as simple with fuxbuntu as it is with ubuntu or kubuntu, but it is possible. In fact the two PCs I got running with it right now are hosting my group's shared folders trough samba. But with passwords.
If you need further help with this just let me know.

---

### Post by RedSquirrel on 2008-08-11
The Fluxbox wiki is a good source of information:

[http://fluxbox-wiki.org](http://fluxbox-wiki.org)

---

### Post by snowpine on 2008-08-11
> **Stunts said:**
> Snowpine's got it all covered.
=-)
BTW, a bit more costumizing:
You can edit menus using from a terminal:
```
leafpad ~/.fluxbox/menu 
```
Look at your menu and look at the file. It's quite simple to use once you figure it out. And it only takes like 5-10 minutes of paying attention to the syntax to understand how it works.


Here are two tips while you are learning to edit your menus. 

1. Make a backup of the original menu with the following command... just in case!

```
cp ~/.fluxbox/menu ~/.fluxbox/menu.backup
```


2. Add the following near the bottom of your ~/.fluxbox/menu file: 

```
[exec] (edit this menu) {leafpad ~/.fluxbox/menu}
```

:)

---

### Post by LitusMayol on 2008-08-12
Thanks **Red Squirrel**.

Another doubt I've not solved yet (in the *Fluxbox-wiki* either). How do I add more users? Right now I just've the user that you create during the installation process. 

I supose that you can create more than one users... If not, is there anyway to change the name and the password of the current one?




I thought it was gonna be hardest to start with ***Flux*buntu**, but surprisingly it's not.
Thanks everyone is doing it easiest!!

---

### Post by hyper_ch on 2008-08-12
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by LitusMayol on 2008-08-14
> **hyper_ch said:**
> It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Sorry man... Though it was easier to get the typical starting few problems in one thread than making  5 or 6 threads with just an question. and it's answer

---

### Post by Stunts on 2008-08-14
I'm not 100% sure how to do it, but you can do it in a terminal using the commands "adduser" (to add a new user) and "passwd" to change passwords.
to be sure how to tuse them make sure you look at the manual:
```

man adduser
man passwd

```

Good luck.

---

