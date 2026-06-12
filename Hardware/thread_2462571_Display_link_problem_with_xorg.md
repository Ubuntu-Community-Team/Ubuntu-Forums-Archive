---
title: "Display link problem with xorg"
date: 2021-05-23
forum: Hardware
---

### Post by triplemaya on 2021-05-23
New install of ubuntu mate 20.04
installed displaylink with
displaylink-driver-5.4.0-55.153.run
install goes fine
Monitor is connected to docking station with displayport cable.

PROBLEM
key presses and mouse clicks take about one second to register. So the system is unusable.
Mouse movement is fine

PROBLEM FIX
Displaylink have - finally - acknowledged this problem and produced a workaround with a patch for the xorg server which is causing the problem. Details here:
[https://www.displaylink.org/forum/showthread.php?t=67148]("https://www.displaylink.org/forum/showthread.php?t=67148")
download here:
[https://www.displaylink.com/downloads/file?d=310]("https://www.displaylink.com/downloads/file?d=310")

NEW PROBLEM
The trouble is that the patch is written over on startup. This happens often with updates, but also happens when just starting up quite often. So I have to reinstall the patch and reboot. Again and again!
(I have posted on the displaylink forum and been totally ignored.)

ATTEMPTED SOLUTION
I installed synaptic and used it to lock the version on:
xorg
xserver-xorg
xserver-xorg-core

Still have the same problem

---

### Post by TheFu on 2021-05-24
Have you attempted to set the driver file to "immutable"?  
[https://www.tecmint.com/make-file-directory-undeletable-immutable-in-linux/](https://www.tecmint.com/make-file-directory-undeletable-immutable-in-linux/)

Just be certain to manually keep track of driver updates.

---

### Post by triplemaya on 2021-05-24
Thanks. Yes, that is what I meant by lock.
Still does it.

---

### Post by triplemaya on 2021-05-24
I went back and found one I had not made immutable. I think this fixed it. The complete list is:
xorg
xserver-xorg
xserver-xorg-core
xserver-xorg-input-all
xserver-xorg-video-all

I just noticed that these four
xorg
xserver-xorg
xserver-xorg-input-all
xserver-xorg-video-all

are installed version 1:7.7+19ubuntu14, which is the version the patch installs, so presumably these are the key packages for anyone with this problem.

Marking as solved, again!

---

### Post by TheFu on 2021-05-24
> **triplemaya said:**
> Thanks. Yes, that is what I meant by lock.
Still does it.

"lock" in the package world usually means you did something with **apt-mark hold** to prevent package updates. At least that was my assumption.  Very few people would equate "lock" with a chattr command.  Heck, perhaps 10% of Unix/Linux users have ever heard of the chattr command at all.

Use **apt-mark showhold** to see which packages are held.

Regardless, happy you found some solution, but for most packages that you want to hold back, the **apt-mark hold {name of package}** would be a better answer.

---

### Post by triplemaya on 2021-05-25
Hi. Thanks. 
This is all new to me!
I thought perhaps apt-mark hold does the same as make immutable in synaptic. But I ran apt-mark showhold and nothing shows. No packages found. So these are different kinds of things?
I am also curious as to what chattr has to do with this?

---

### Post by TheFu on 2021-05-25
I haven't used synaptic (or any GUI package manager) in about a decade.  Can't help.  What does the manpage for each command say?
I don't see any "immutable" in synaptic.  There is a "lock".  Look for the exact words to be used.  "immutable" means something very specific in Unix (English), so if translation is happening, it might not be the best word choice.

> I am also curious as to what chattr has to do with this? 
**chattr** is the only Unix/Linux command that I know which uses the exact term "immutable".   **chattr +i {file}**

---

### Post by triplemaya on 2021-05-25
Lock version is the language used in synaptic. Not sure where I got immutable from. 

apt-mark hold
           hold is used to mark a package as held back, which will prevent the package from being
           automatically installed, upgraded or removed.
 showhold
           showhold is used to print a list of packages on hold in the same way as for the other
           show commands.

But showhold does not return any results. So synaptic lock version is something different. 

In synaptic
To Lock a Package to the Current Version (Debian only)
To lock a package to the current version follow these steps:
Select the package that you want to lock in the package list.
Choose Package &#9656; Lock Version.
The Synaptic Package Manager will reload the package information. You should now see, that the menu item Package &#9656; Lock Version is checked. Furthermore all actions in the menu Package are disabled now.
To unlock the package uncheck Package &#9656; Lock Version.

---

### Post by triplemaya on 2021-05-25
Just had it fail again so this is NOT solved!

---

### Post by triplemaya on 2021-05-25
Trying apt-mark hold

---

### Post by TheFu on 2021-05-25
> **triplemaya said:**
> Lock version is the language used in synaptic. Not sure where I got immutable from. 
 

Think I'm to blame for that.  Post #2 above used the "immutable" term. Intended to be clear that it was for driver file only AND provided a link for how to do it.  At least that was my intent. Sorry if that wasn't obvious.

I use **apt-mark** to hold packages.  My goal is to NOT have any held packages, since that's a good way to get the APT DB into an inconsistent state.  That usually takes a few months for APT to break.  Don't hold too many packages too long. Guess that's the moral to this story.

---

### Post by triplemaya on 2021-05-25
Thanks
I can see holding packages is not a good idea in principle. Given the displaylink issue remaining unresolved and apparently unmanaged it seems I do not have a lot of choice.
Hoping the hold does the job, and very grateful for your help.

---

### Post by lastdanz on 2021-05-26
> **triplemaya said:**
> Just had it fail again so this is NOT solved!

Yep, it doesn't even work for me. Lots of thanks anyway!

---

### Post by triplemaya on 2021-05-26
The solution is:

apt-mark hold xserver-xorg-core

A bit obvious in retrospect. The display patch script output is:

dpkg: warning: downgrading xserver-xorg-core from 2:1.20.9-2ubuntu1.2~20.04.2 to 2:1.20.8-2ubuntu2
(Reading database ... 291001 files and directories currently installed.)
Preparing to unpack xserver-xorg-core_1.20.8-2ubuntu2_amd64.deb ...
Unpacking xserver-xorg-core (2:1.20.8-2ubuntu2) over (2:1.20.9-2ubuntu1.2~20.04.2) ...
Setting up xserver-xorg-core (2:1.20.8-2ubuntu2) ...
Processing triggers for man-db (2.9.1-1) ...

and  xserver-xorg-core is the only package with 2:1.20.8-2ubuntu2 in synaptic.

Thanks again The Fu

---

### Post by lastdanz on 2021-05-27
Doing apt-mark hold is a little bit risky, isn't it?

---

### Post by triplemaya on 2021-05-27
The whole thing seems worrying, having a compromise in the fundamental graphics server. 

I wonder if the best policy is to go back to Ubuntu 18.04 and stay there until this is fixed. If and when!

---

### Post by lastdanz on 2021-05-30
Well, holding xserver-xorg-core doesn't seem to work for me :_(

---

### Post by triplemaya on 2021-05-31
I did also use synaptic to lock the version of packages as above in this thread. Might we worth a try.

---

### Post by lastdanz on 2021-05-31
I did it both using synaptic and typin the instruction in terminal, no success.

---

