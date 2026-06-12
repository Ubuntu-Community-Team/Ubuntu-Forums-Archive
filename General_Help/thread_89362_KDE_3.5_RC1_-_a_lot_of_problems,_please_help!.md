---
title: "KDE 3.5 RC1 - a lot of problems, please help!"
date: 2005-11-12
forum: General Help
---

### Post by dolny on 2005-11-12
**SOLVED: READ MY LAST POST - This has nothing to do with KDE probably.**

I installed KDE 3.5 RC1 on KDE 3.5 Beta 1. I had to force kde-libs. Then Kontact, Kcontrol, The "K Menu" and other stuff (like all things on desktop dissapeared) stopped working. I tried sudo apt-get install kubuntu-desktop but that didn't help. When I try to run Kontact or Kcontrol a message pops up 'Can't find MIME type application/octet-stream' or and a moment later 'No MIME types installed'.

Console output:

```
mrplant@milkshake:~$ kontact
kio (KSycoca): WARNING: Found version 92, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): WARNING: Found version 92, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): WARNING: Found version 92, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KMimeType): WARNING: KServiceType::offers : servicetype Kontact/Plugin not found
mrplant@milkshake:~$ kontact: ERROR: : couldn't create slave : Nie mo&#380;na utworzy&#263; io-slave:
Program klauncher zwr&#243;ci&#322; komunikat: Nieznany protok&#243;&#322; 'file'.
kontact:
kontact: ERROR: : couldn't create slave : Nie mo&#380;na utworzy&#263; io-slave:
Program klauncher zwr&#243;ci&#322; komunikat: Nieznany protok&#243;&#322; 'file'.
kontact:
kontact: ERROR: : couldn't create slave : Nie mo&#380;na utworzy&#263; io-slave:
Program klauncher zwr&#243;ci&#322; komunikat: Nieznany protok&#243;&#322; 'file'.
kontact:
kontact: ERROR: : couldn't create slave : Nie mo&#380;na utworzy&#263; io-slave:
Program klauncher zwr&#243;ci&#322; komunikat: Nieznany protok&#243;&#322; 'file'.
kontact:
kontact: ERROR: : couldn't create slave : Nie mo&#380;na utworzy&#263; io-slave:
Program klauncher zwr&#243;ci&#322; komunikat: Nieznany protok&#243;&#322; 'file'.
kontact:
kio (KSycoca): WARNING: Found version 92, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found

mrplant@milkshake:~$ kcontrol
kio (KSycoca): WARNING: Found version 92, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): ERROR: No database available!
kcontrol: WARNING: No K menu group with X-KDE-BaseGroup=settings found ! Defaulting to Settings/
kio (KSycoca): WARNING: Found version 92, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): WARNING: Found version 92, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
mrplant@milkshake:~$ kio (KSycoca): WARNING: Found version 92, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kcontrol: ERROR: : couldn't create slave : Nie mo&#380;na utworzy&#263; io-slave:
Program klauncher zwr&#243;ci&#322; komunikat: Nieznany protok&#243;&#322; 'file'.
kcontrol:
kcontrol: ERROR: : couldn't create slave : Nie mo&#380;na utworzy&#263; io-slave:
Program klauncher zwr&#243;ci&#322; komunikat: Nieznany protok&#243;&#322; 'file'.
kcontrol:
                                                      
```

Help, please. Should I remove kubuntu-desktop and kde and reinstall it? Will the settings stay on their place? Any suggestions :( ?

---

### Post by mlomker on 2005-11-12
> Help, please. Should I remove kubuntu-desktop and kde and reinstall it? Will the settings stay on their place? Any suggestions :( ?

It isn't that simple because kubuntu-desktop is just a list of packages.  You'd have to drop to a command line and remove all of them one at a time...

At this point I'd probably just[ backup my /home and /etc folders ]("http://www.ubuntuforums.org/showpost.php?p=361622&postcount=4")are reinstall Kubuntu.

I hope that other people read this and understand that KDE 3.5 is a beta and not something that you should install on your main computer.  I recommend that everyone wait until Drake for 3.5.

---

### Post by dolny on 2005-11-12
Interesting: When I create a new user, and log in as him - everything works ok o_O

---

### Post by DoeRayMe on 2005-11-12
i had the same problem till i rebooted and it fixed its self

---

### Post by dolny on 2005-11-12
Reboot doesn't help :(

---

### Post by mlomker on 2005-11-12
[QUOTE=dolny]Interesting: When I create a new user, and log in as him - everything works ok o_O[/QUOTE]

If you don't mind losing some of your personalized settings then you can delete your ~/.kde directory to reset everything.

---

### Post by dolny on 2005-11-12
Tried that and... that didn't work :shock:

---

### Post by DoeRayMe on 2005-11-12
Okay go into your package manager and check if there are any broken packages, maybe thats causing the problem

---

### Post by dolny on 2005-11-12
Nah :( No broken packages.

I can't reinstall everyting... I installed too much stuff.
I can't believe I'm the only one having this error :|

---

### Post by skyboy on 2005-11-12
or try apt-get -f install
then apt-get update & upgrade

when you do an upgrade, never force !! always try to fix while meeting the dependencies with apt-get -f install

---

### Post by dolny on 2005-11-12
sudo apt-get install -f does nothing

I tried install -f but it didn't work, nobody had a better solution so I forced kdelibs...

I thought that upgrading from Beta 1 to RC1 would be safe enough :/

---

### Post by dolny on 2005-11-12
OK, look at the screenshots:

[http://www.echostar.pl/~dolny/ubu/blad1.jpg](http://www.echostar.pl/~dolny/ubu/blad1.jpg)

1."Can't find mimetype..."
2."Cannot init process" "Cannot create io-slave"

Second window:
1. "Klauncher returned message: unknown protocol 'file' "

---

[http://www.echostar.pl/~dolny/ubu/blad2.jpg](http://www.echostar.pl/~dolny/ubu/blad2.jpg)

1. "No MIME types installed"

---

[http://www.echostar.pl/~dolny/ubu/blad2.jpg](http://www.echostar.pl/~dolny/ubu/blad2.jpg)

1. "Cannot init process" "Cannot create io-slave"
2. 1. "Klauncher returned message: unknown protocol 'thrash' "

----

Konqueror, Kcontrol and Kontact:

[http://www.echostar.pl/~dolny/ubu/appsbledy.jpg](http://www.echostar.pl/~dolny/ubu/appsbledy.jpg)

:-s :cry: :cry: :cry:

---

### Post by dolny on 2005-11-12
After sitting on it for a long time I checked:

.xsession-errors in my dir and found some error saying that it cannot create something in: /var/tmp/kdecache-mrplant probably because disk is full... so I checked whether the new user has /var/tmp/kdecache-usersname dir - he didn't. So I deleted /kdecache-mrplant and the new KDE started. 

I have /var/ on my / partition (no separate /var/ partition) and .... there's no free space, even though there was a huge amount of it when I last checked :shock:

So the error is probably on my side. Sorry everybody!!!!!!!

---

### Post by Wizzard on 2005-11-14
I have KDE 3.5 RC1 too and the main problem I have is with Noatun, it always crashes so I have to use XMMS. Terminal sessions menu does not work either, like in beta 1 and 2. Seems that we have to want a week till official release.

---

