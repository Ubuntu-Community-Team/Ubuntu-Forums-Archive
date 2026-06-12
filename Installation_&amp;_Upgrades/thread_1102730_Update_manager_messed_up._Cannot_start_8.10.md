---
title: "Update manager messed up. Cannot start 8.10"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by Mugzilla on 2009-03-21
Chances are, it was this user that messed up my using update manager.  Update manager told me there were new things to install (Little red arrow icon in taskbar...)

So, I clicked the little red arrow.  A message popped up that ubuntu was not able to download all of the packages.  No problem, I'll upgrade them later.

Then, I ran synaptic, and it uninstalled a bunch of things.  When I restart the computer, it will not go into gnome.  I have tried the recovery mode.  I have tried command line.

I am certain this is something that can be fixed by a guru.  However, my main concern is saving all the stuff out of my home folder. (Music and LOLCat pictures...)  
[B][SIZE="3"]
The Question:  Is there a live CD distribution that I can boot into, access my ubuntu partition on my SATA HD, and copy all the files to a USB external HD? [/SIZE][/B]

---

### Post by gali98 on 2009-03-22
Sure... Just use the ubuntu cd that you installed your present system with.
Use the Option Try Ubuntu.
(If you don't have it, you can just download an .iso at ubuntu.com and burn it to a cd.)
Just stick in your usb drive and start copying... Your hard drive should be in the my computer... just browse to your home folder and drag it over...
As far as your system goes, you can probably recover it...
First save all you files that you want.. 
then boot into recovery mode.. Can you at least get to the command line?
if so try running the command
sudo apt-get install ubuntu-desktop

that may fix it... but before you do this get all your files.
I can try and help you with fixing your system. just tell me how far you can get.

Kory

---

### Post by Mugzilla on 2009-03-22
Using my live cd, I was able to find my HD's home folder.  I was able to open my external USB hard Drive.

The problem is, I do not have the correct permissions to move any of my files!

---

### Post by Mugzilla on 2009-03-22
Yes, I am able to get to the command line.  I don't THINK sudo apt-get install ubuntu-desktop would do anything to my files.  However, I would rather back them up first before trying anything brash...

---

### Post by Mugzilla on 2009-03-22
> **Mugzilla said:**
> Using my live cd, I was able to find my HD's home folder.  I was able to open my external USB hard Drive.

The problem is, I do not have the correct permissions to move any of my files!

> **gali98 said:**
>  Can you at least get to the command line?
if so try running the command
sudo apt-get install ubuntu-desktop

that may fix it... but before you do this get all your files.
I can try and help you with fixing your system. just tell me how far you can get.

Kory

I was able to use the live CD to view both my USB drive and my home folder.  However, when I attempted to drag and drop the files, I did not have the necessary permissions. My solution was to run the following command from the command line that comes up after my failed load:

sudo apt-get install ubuntu-desktop

When I did this, the computer told me it was unable to run this.  It listed a bunch of packages.  Some were listed as RECCOMENDS, and some as DEPENDS.  I started installing each DEPENDS package as sudo apt-get install Esudo apt-get install ubuntu-desktop DEPENDS.  After installing about 12 of these DEPENDS packages, the distro let me run sudo apt-get install ubuntu-desktop.  I am now back into gnome, and am backing everything up.  I do not know what the problem was.  If I figure out what I messed up, I will add to this thread for the archive.

---

### Post by gali98 on 2009-03-22
Glad to here you got it working...
lesson learned is don't go into synaptic and start uninstalling packages... You are quite likely to get bitten unless you know exactly what you are doing...
Kory

---

