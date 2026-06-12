---
title: "Installing Simon Tatham's Portable Puzzle Collection"
date: 2008-08-29
forum: General Help
---

### Post by fparedesg on 2008-08-29
I really like that set of puzzle games (title). I first played on an iPod (touch) and I really liked it. I later installed in Windows, and now I want to install them in Ubuntu. I already downloaded "sgt-puzzles" off of the Synaptic Package Manager, but I don't know how to open it. Sorry, I'm a noob. This page shows you how to run a script on how to create an icon for it, but I don't know how to do that... -_-

[http://www.kryogenix.org/days/2006/08/14/simon-tathams-portable-puzzle-collection-launcher](http://www.kryogenix.org/days/2006/08/14/simon-tathams-portable-puzzle-collection-launcher)

Well, thanks for anyone that helps me!!

[EDIT] Oh yeah..I didn't say what I wanted. I want to be able to have an icon to open them, to learn how to execute that script.

---

### Post by lyni on 2008-08-29
if you installed from the Synaptic Package Manger I thought it was already installed. so if you go to Applications>Games it should be there ready to play.

---

### Post by mixmaster on 2008-08-29
> **lyni said:**
> if you installed from the Synaptic Package Manger I thought it was already installed. so if you go to Applications>Games it should be there ready to play.
No, the whole point is that the package does not install itself on the menu.  The link is to a python script to create a menu system for the applets (or some such, I haven't installed/run it).

To get the python script to run you need to open the file /usr/local/bin/sgt-index in your editor of choice and type in the script given (or cut&paste it).  You can then run this script from a terminal by simply typing sgt-index or you can create a menu item for it or add a launcher.  How you do that depends on which window manager you use.  I use Xubuntu so it is unlikely that my method would work for you and I'm not sufficently fluent with Kubuntu or gnome to give you instructions blind, sorry.

Oops - forgot to say that you will need root access to write to /usr/local/bin and you will need to make the file executable afterwards.  If you are not planning to make these things available to other users on your system then I suggest you write the script to ~/sgt-index instead (this will put it in your home directory) and then execute
chmod 755 ~/sgt-index to make to executable.

---

### Post by fparedesg on 2008-08-29
Thanks for helping! I didn't know how to make it an executable file. I imagined I had to copy it into a text document, but I didn't know how chmod it.

Just one last question. Is there a way to put it into the "Games" Folder (Applications -> Games) Thanks!

---

### Post by Bearly Able on 2009-07-15
Hi,

I'm having two problems with this puzzle collection, and would be grateful for help.

I installed the package a couple of days ago on my desktop, running Intrepid, and my laptop, running Hardy.  On the desktop, the puzzles all appear under the games menu; on the laptop, they don't.  My first question was how to add them to the laptop menu, but having just found this thread, I'll give it a go.

My second problem is with the "Help" files.  On the laptop, I can open the "Help" file for any puzzle without a problem; on the desktop, I get ```
The file ‘/usr/share/sgt-puzzles/help/map.html’ could not be read.  This file might be missing, or you might not have permissions to read it.
```The file exists, because I can navigate to it and open it, which suggests to me that file permissions are not the issue, either, but I'm still pretty much a newbie, so feel free to tell me I'm wrong there!

I know it's a puzzle series, but trying to puzzle out why the Menu works on one install and the Help on the other wasn't quite what I had in mind!  Any assistance would be much appreciated.

---

### Post by Flymo on 2010-05-15
Thanks very much!  

But..... Stuart Langridge seems to have moved his all-important script to [**_this page_**]("http://www.kryogenix.org/days/2006/08/13/simon-tathams-portable-puzzle-collection-launcher")

It's only one day away - maybe we should inform [**_The Doctor_**]("http://www.bbc.co.uk/doctorwho/dw") of this? :)

hth,  Ben

---

