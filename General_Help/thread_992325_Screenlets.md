---
title: "Screenlets"
date: 2008-11-24
forum: General Help
---

### Post by Noctrum93 on 2008-11-24
Hello!

Recently I have installed Ubuntu 8.10. I wanted to install some screenlets but I am not able, when I go to System and Preferences theres no screenlets manager, I have to go to Applications and Accesories but it doesnt matter, when I have downloaded some screenlets I wanted to install them I opened screenlets manager by typing sudo screenlets-manager (only that way I could open) and then I clicked on install and I chosen all it said that it has been installed correctly but I cant use it :/ dont know why 

[http://img128.imageshack.us/my.php?image=63088503wm9.png](http://img128.imageshack.us/my.php?image=63088503wm9.png)

---

### Post by theApokalypsis on 2008-11-24
(oops)

---

### Post by Ivo Moelans on 2008-11-24
The Screenlets Manager should be in the main menu under *Applications&#8594;Accessories*. If not, open *System&#8594;Preferences&#8594;Main Menu*. There go to *Accessories* and select *Screenlets*. Now it should be in your menu.
Open the Screenlets Manager select the screenlet you want to activate (click on it) and on the left select *Start/Stop*.
If you are using Compiz the screenlets become visible by pressing function key *F12* (if you haven't made changes to the hotkeys).

Does this help?

---

### Post by Noctrum93 on 2008-11-25
I know, I have it in accessories but when I want to start up it but it doesnt come up I need run it from console by typing "sudo screenlets-manager" and when I want to choose 1 I cant because it is not available like on screenshot I gave.

---

### Post by Ivo Moelans on 2008-11-25
Very strange. The Screenlet Manager should work without superuser privileges.
Have you tried reinstalling the package *screenlets* with Synaptic Package Manager?

---

### Post by Noctrum93 on 2008-11-27
when I typed in console "screenlets" it comes up but when I want to start it up from Applications > Accessories then it is not working and screenshot from first post shows how it looks when I type "SUDO screenlets"
```
File /home/-----/.screenlets/config.ini not found
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 1308, in <module>
    app = ScreenletsManager()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 95, in __init__
    self.create_ui()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 487, in create_ui
    self.recreate_infobox(None)
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 522, in recreate_infobox
    f = open(DIR_USER + '/config.ini', 'w')
IOError: [Errno 13] Permission denied: '/home/-----/.screenlets/config.ini'

```

---

### Post by Ivo Moelans on 2008-11-27
You could try the following. In the console type:

```
sudo apt-get remove --purge screenlets
```

This removes the program and its settings completely.

Then reinstall:

```
sudo apt-get install screenlets
```

---

### Post by Ostomizer on 2009-05-22
I've been having this exact same problem since I Installed screenlets.  I even tried one of the previous poster's suggestions of purging and reinstalling the package, but it didn't help. My errors looked like this:

> 
<username>@<username>-desktop:~$ screenlets-manager
True
Create autostarter for: Screenlets Daemon
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 1308, in <module>
    app = ScreenletsManager()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 104, in __init__
    utils.lookup_daemon_autostart()
  File "/usr/lib/python2.6/dist-packages/screenlets/utils.py", line 519, in lookup_daemon_autostart
    f = open(starter, 'w')
IOError: [Errno 13] Permission denied: '/home/<username>/.config/autostart/Screenlets Daemon.desktop'
It turned out that a file named "Screenlets Daemon.desktop" didn't exist, and the directory permissions were 755, so presumably the screenlets-manager process was unable to create the file (?).

Anyway, what DID help was a stupid workaround I came up with, that should be unnecessary, but it works, so I'm posting it here to help others avoid searching for hours to find a way to make this work.

```

cd /home/<username>/.config/autostart
sudo touch Screenlets\ Daemon.desktop

```After creating the empty file via the 'touch' command, screenlets-manager will now work without having to preface it with a 'sudo'.  I suspect that this file is supposed to contain some configuration data, similar to the 'adesklets.desktop' file I have in the same directory, and so I might run into some configuration problems further down the line.  However, for now, it gets the manager working.  Enjoy.

---

