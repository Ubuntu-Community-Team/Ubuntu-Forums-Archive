---
title: "[SOLVED] Newbie Mistake &amp;gt;.&amp;lt;"
date: 2008-08-06
forum: General Help
---

### Post by ScrollMaker on 2008-08-06
So somewhere along the lines I messed up and the add/remove programs and adept won't launch. I believe this is due to an error in my sources.list found in /etc/apt/ . However when I try to correct the bugged line with Kate it keeps telling me I don't have permission to do this.

"For file /etc/apt/sources.list no backup copy could be created before saving. If an error occurs while saving, you might lose the data of this file. A reason could be that the media you write to is full or the directory of the file is read-only for you."

I choose Save Nevertheless.

"The document could not be saved, as it was not possible to write to /etc/apt/sources.list.

Check that you have write access to this file or that enough disk space is available."

My hard drive is definitely not full and I think I have write access to both the folder and the document.

Edit: I forgot to mention that this is KDE if it matters.

---

### Post by Locutus_of_Borg on 2008-08-06
edit as root
```
 sudo kate /etc/apt/sources.lst
```

---

### Post by macaholic on 2008-08-06
The reason is, you do not have "root" privledges of the system, the reason beign to keep people from destroying their system accidently. However (k/x)ubuntu lets you temporarily have root privledges for individual commands. To do so, launch a terminal (either konsone or terminal) and tpye sudo for command line applications, and for graphical applications either gksu, for gnome, or kdesu, for  kde. Adding that before the command of a text editor should do the trick for you, probably "kate" since you appear to be using kde.

---

### Post by ScrollMaker on 2008-08-06
That gives me:

"sudo: kate: command not found"

---

### Post by mb_webguy on 2008-08-06
Did you run Kate from the terminal using kdesu?  The sources.lst file requires root privileges to edit.  So in the terminal type "kdesu kate /etc/apt/sources.lst".

---

### Post by macaholic on 2008-08-06
> **ScrollMaker said:**
> That gives me:

"sudo: kate: command not found"
You have to run it from a terminal (konsole).

---

### Post by ScrollMaker on 2008-08-06
Gives me

"kbuildsycoca running...
sudo: kate: command not found"

aswell as a KdeSudo, command not found popup error

edit: yes, running from konsole

---

### Post by Locutus_of_Borg on 2008-08-06
> **ScrollMaker said:**
> That gives me:

"sudo: kate: command not found"

```
sudo -i
kate
```

maybe

---

### Post by ScrollMaker on 2008-08-06
Weird, that tells me that Kate is not installed even though I clearly have been using it to open sources.list !

---

### Post by lisati on 2008-08-06
What (or who) is "kate"? is it actually installed? The "command not found" can happen if kate's either not installed or not in the usual program search path; maybe this is worth investigating.

---

### Post by ScrollMaker on 2008-08-06
So it tells me that Kate is not installed for some reason and that I should do apt-get install kate. However this brings me full circle back to the problem that I can't run the add/remove programs!

---

### Post by dhughes on 2008-08-06
> **lisati said:**
> What (or who) is "kate"? 


"*Kate is a multi document editor, based on a rewritten version of the kwrite editing widget of KDE, offering all the features of that plus a bunch of its own. Kate has been been moved to the kdebase package, and is a built-in part of your favorite desktop since release 2.2.* " [http://kate-editor.org/kate](http://kate-editor.org/kate)

 A KDE editor it seems, maybe that's the problem? Not that it should be a problem using KDE stuff in Gnome.

 Maybe in Terminal

 ```
sudo aptitude-install kate
```

---

### Post by ScrollMaker on 2008-08-06
This is on Kubuntu! This situation has put me in a complete pickle because I need to use Kate (or some other text editor) to fix my "sources.list". My sources.list is bugged so I cant use add/remove, apt-get, all those package and programs managers without them erroring out. However for some other weird reason after running "sudo -i", then "kate" it tells me kate is not installed. I can still run Kate from the program launcher bar but I need to run as root so I can edit the system files, yet I can't run as root because it says Kate isn't installed. And I can't install Kate because my sources.list is bugged! A three hundred sixty degree pickle. I'm going to reinstall Kubuntu if I can't figure this. :(

---

### Post by kidux on 2008-08-06
Try using vi or vim to edit the file. ```
sudo vi sources.list
``` You also may need to include the full path to the file as well.

---

### Post by ScrollMaker on 2008-08-06
Thank you all for the help!

---

### Post by kidux on 2008-08-06
So were you able to fix it with vi, or some other method?

---

