---
title: "Installer defaults to a command prompt!"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by cs_at_colorado on 2009-03-30
Ok, I haven't found a specific case of this yet, here is the issue.

I boot a freshly minted installation CD I have tried the following: 8.10 32-bit, 64-bit, and the new 9.04 64-bit beta! All have the same or similar issues.

I get to the language selection screen (good), choose "F4 Graphics Safe mode", choose "F6 advanced options" than disable api-installation (not positive what exactly this is, but it is listed as "buggy"), I have tried running it both with and without the two previous options. In one case I am to see a few screens with progress bars and the ubuntu logo.

Next I default into this command prompt screen with a note about "man sudo" ect. and a command prompt: ubuntu@$ubuntu

If I CD around a bit I can I find what looks to be a basic file system for a ubuntu machine including the CD that is currently in my drive, but I can't launch the installer from there either, I would like to get to the GUI installed I have seen so I can work from there!

Don't know why it is doing this with multiple different versions? Anyways any help would be greatly appreciated.

System config:
Dell Optiplex 320
Intel Pentium Dual E2160
RAM 2GIG Kingston (working fine)
HD 160 gig partitioned up a bit so I can do a base OS (I wanted to reformat over Vista and install ubuntu!)

Thanks!

---

### Post by dandnsmith on 2009-03-30
I assume that you downloaded the desktop, rather than the server versions?

Have you then tried simply booting from the liveCD, picking the language, keyboard and waiting till the desktop comes up with the install icon as almost the only thing on it?

I don't do any other options unless the simplest attempt fails.

---

### Post by linux_tech on 2009-03-30
Sounds like the server version was insatlled
The desktop can be installed seperately using the command-
```
sudo apt-get install ubuntu-desktop
```

---

### Post by shijithsj on 2009-03-30
Network Error occured in Empathy during google talk configuration how can i solve this problem please help me pleaseeeeeeeeeeeeeeeee....

---

### Post by cs_at_colorado on 2009-03-30
> **linux_tech said:**
> Sounds like the server version was insatlled
The desktop can be installed seperately using the command-
```
sudo apt-get install ubuntu-desktop
```

Yes, it does strike me similar to the server version? 

I will try this command from the prompt I'm getting right now. But no I'm POSITIVE that I'm using the desktop install CD

Also? Thread hijack?

shijithsj	
Re: Installer defaults to a command prompt!
Network Error occured in Empathy during google talk configuration how can i solve this problem please help me pleaseeeeeeeeeeeeeeeee....

---

### Post by cs_at_colorado on 2009-03-30
> **linux_tech said:**
> Sounds like the server version was insatlled
The desktop can be installed seperately using the command-
```
sudo apt-get install ubuntu-desktop
```

Ok, just tried this from my CMD prompt. It starts the installer, than at "reading state..." I am told that ubuntu desktop is already is installed!? As far as I know I haven't previously installed the server or desktop at all...except on virtual machines that are stored on another partition!

Anyways, it says nothing to update and returns to the command prompt. It strikes me that it is defaulting to a command prompt version of the operating system?

---

### Post by coffeecat on 2009-03-30
> **cs_at_colorado said:**
> 
Also? Thread hijack?

shijithsj    
Re: Installer defaults to a command prompt!
Network Error occured in Empathy during google talk configuration how can i solve this problem please help me pleaseeeeeeeeeeeeeeeee....

I think more a new member who doesn't know how to use the forum. You can report such posts to a moderator to get them moved - there's a little clickable icon in the left pane of the post you want to report, like this: [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]

I've already reported this one for you.

---

### Post by Rocket2DMn on 2009-03-30
> **shijithsj said:**
> Network Error occured in Empathy during google talk configuration how can i solve this problem please help me pleaseeeeeeeeeeeeeeeee....

Please don't hijack other users' threads.  You should start a new thread by clicking the New Thread link near the top left of the forum - [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)
Thanks!

---

### Post by cs_at_colorado on 2009-03-30
bump after all this business--any ideas? I'm thinking I will format the partition I want to install too before hand so I don't encounter this "already" installed issue as I might have jogged some setting in the past and I'm not aware of it...? Perhaps the VMWare Workstation I have in Windows Vista currently set something that I don't know how to reverse.

---

### Post by dmaxel on 2009-03-30
Not sure if its 100% relevant, but it may help anyways.

I just tried installing Ubuntu 8.10 Desktop to a computer that had similar symptoms. It took forever to load when Install Ubuntu was chosen, and then right when it finished, it turned into a command prompt.
However, we tried again by booting from the CD and going to a Live Session user (Live CD, Try Ubuntu without changes to the computer). There it took forever to load, and entered command prompt, but suddenly continued to the Desktop. It notified us about Low Graphics mode being set or something, but we made it go through. Right now it's installing or is finished installing (need to check), as we could then click on the Install shortcut that was placed on the desktop space.
Basically, it went to the command prompt because our graphics weren't good enough to go to the GraphicalInstall ([https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)). Maybe this is your problem too.

---

### Post by cs_at_colorado on 2009-03-30
> **dmaxel said:**
> Not sure if its 100% relevant, but it may help anyways.

I just tried installing Ubuntu 8.10 Desktop to a computer that had similar symptoms. It took forever to load when Install Ubuntu was chosen, and then right when it finished, it turned into a command prompt.
However, we tried again by booting from the CD and going to a Live Session user (Live CD, Try Ubuntu without changes to the computer). There it took forever to load, and entered command prompt, but suddenly continued to the Desktop. It notified us about Low Graphics mode being set or something, but we made it go through. Right now it's installing or is finished installing (need to check), as we could then click on the Install shortcut that was placed on the desktop space.
Basically, it went to the command prompt because our graphics weren't good enough to go to the GraphicalInstall ([https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)). Maybe this is your problem too.

thanks, I will give this a shot this evening!

---

### Post by cs_at_colorado on 2009-03-30
> **dmaxel said:**
> Not sure if its 100% relevant, but it may help anyways.

I just tried installing Ubuntu 8.10 Desktop to a computer that had similar symptoms. It took forever to load when Install Ubuntu was chosen, and then right when it finished, it turned into a command prompt.
However, we tried again by booting from the CD and going to a Live Session user (Live CD, Try Ubuntu without changes to the computer). There it took forever to load, and entered command prompt, but suddenly continued to the Desktop. It notified us about Low Graphics mode being set or something, but we made it go through. Right now it's installing or is finished installing (need to check), as we could then click on the Install shortcut that was placed on the desktop space.
Basically, it went to the command prompt because our graphics weren't good enough to go to the GraphicalInstall ([https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)). Maybe this is your problem too.

When you say..."took forever" How long did you take? When I selected "Try Ubuntu..." it spins up the disk for a minute, reads than goes to a blinking cursor, I left it sitting for about 20 minutes...

---

