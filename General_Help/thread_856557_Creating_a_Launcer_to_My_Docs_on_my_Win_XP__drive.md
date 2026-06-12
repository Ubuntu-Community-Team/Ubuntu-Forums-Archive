---
title: "Creating a Launcer to My Docs on my Win XP  drive"
date: 2008-07-11
forum: General Help
---

### Post by sirbingo on 2008-07-11
Whats up Y'all

Here' s my question...

First off,  Im a UBUNTU Noob and I've got a dual boot machine.  One drive is UBUNTU and the c: drive is Windows.

I'm trying to create alauncher on the UBUNTU desktop that points to location on my C"drive.  Without there being lettered drives like in UBUNTU,  how do I point a launcher (aka shortcut) to other drives on the system  that are not the dive UBUNTU is installed on?

Hope I made sense here.   8-[

---

### Post by rbprogrammer on 2008-07-11
Ok from what I understand is that you want to click on a folder on your Ubuntu desktop and it will open up a location on your windows partition.

If that is what you want you will need to create a link in your desktop directory.  Executing a command like this would do the trick:
```

ln -s ~/Desktop/<your-folder-name> /media/<mount-point>/<path-to-win-folder>

```
<your-folder-name> is the name you want on the folder that will appear on your desktop

<mount-point> is the place where your windows partition is mounted at

<path-to-win-folder> is the obvious path to the folder you want to link to

This all assumes you have the appropriate permissions.  If you need any more help setting up the command or this is not what you wanted, I'll be checking up on the thread.

---

### Post by PGScooter on 2008-07-11
were you able to mount windows ok in ubuntu?

---

### Post by sirbingo on 2008-07-11
> **PGScooter said:**
> were you able to mount windows ok in ubuntu?

Thanks for the the replys! 

I guess I was able to mount the Windows drive?!?  
It shows up under places and if I click on it an icon apears on the desktop and I can navigate and access files on it without a problem.  That means its mounted..right?

---

### Post by rbprogrammer on 2008-07-11
> **sirbingo said:**
> Thanks for the the replys! 

I guess I was able to mount the Windows drive?!?  
It shows up under places and if I click on it an icon apears on the desktop and I can navigate and access files on it without a problem.  That means its mounted..right?

Yes that means its mounted and you have at least read permissions.  Now is the option I first presented you what you wanted?  If so, when you click on the icon in the places menu, what is the "address" that shows up?  This will help with creating the link for your desktop.

---

### Post by sirbingo on 2008-07-11
> **rbprogrammer said:**
> when you click on the icon in the places menu, what is the "address" that shows up? 

The address that shows up is:  /media/disk

The address for yhe my documents folder is:  
/media/disk/Documents and Settings/Mel

Does this help?  8-[

---

### Post by rbprogrammer on 2008-07-13
> **sirbingo said:**
> 
The address that shows up is:  /media/disk

The address for yhe my documents folder is:  
/media/disk/Documents and Settings/Mel

Does this help?  8-[

Well, then try and execute these two commands:
```

mkdir ~/Desktop/documents
ln -s ~/Desktop/documents "/media/disk/Documents and Settings/Mel"

```

Oh and I see you are quite new, you might need to know how to execute a command.  If you use GNOME, then in the applications menu, go to:
```

Applications -> Accessories -> Terminal

```
If you use KDE, then somewhere in you K-Menu, you want to look for "Konsole"

Hope that helps you.

---

