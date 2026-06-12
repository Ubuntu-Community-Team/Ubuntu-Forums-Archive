---
title: "[SOLVED] How can I set myself as owner for EVERYTHING on the HDD?"
date: 2008-09-29
forum: General Help
---

### Post by riahc3 on 2008-09-29
There are some folders/files I want to copy/move/etc but I cant because they belong to root. How can I change so that EVERYTHING belongs to (example) user1. This means I can modify it any way I would like.

---

### Post by C.S.Cameron on 2008-09-29
gksu nautilus, chown ....
But if this your boot disk I don't think you want to.
Root should own a bunch of stuff if you don't want problems.

---

### Post by ju2wheels on 2008-09-29
Thats not a good idea. That would undermine the very security that Ubuntu is built on make you potentially vulnerable to attacks. Theres a reason why you need to "sudo" to modify system files, it keeps you protected from rootkits and unauthorized modifications to your system.

---

### Post by phidia on 2008-09-29
What C.S.Cameron said. This is a really bad idea which will compromise your system.
 What is it you want to accomplish? If you are looking to back up your entire system or a part of it there are command line tools which will allow you to do that. 

Have a look at man rsync & man dd.

---

### Post by soxs on 2008-09-29
> **riahc3 said:**
> There are some folders/files I want to copy/move/etc but I cant because they belong to root. How can I change so that EVERYTHING belongs to (example) user1. This means I can modify it any way I would like.

I case they are system folders, you should copy them with ```
sudo cp -vf /source/location /target/location
``` (alternatively do: sudo nautilus and copy them via DND) and _afterwards_ change their ownership to your user via ```
sudo chown ${USER}:${USER-GROUP} -Rvf /target/location
```
Making them accessable, but _NOT_executabel: ```
chmod 644 -Rvf /target/loaction
```(no sudo required, as they belong allready to you).

In case they asre userrelated folders do: ```
sudo chmod 644 /target/location
``` and tehn simply copy via nautilus (standard gnome file maneger)

GL :-D

---

### Post by jerome1232 on 2008-09-29
I wouldn't chown anything as your user outside of your ~/, You can just operate as root to do these operations. either prepend your operations with sudo, or run nautilus as root, note running nautilus as root lets you modify ANY system file and you should tread lightly.

```
gksudo nautilus
```

I can't think of anything you can't read without root privileges that you would want to copy, much less actually move.

---

### Post by riahc3 on 2008-09-29
I use the GUI for everything so I need root access to everything.

I could careless about security.


Again please just answer the question: How do I become the owner of all the files in Ubunutu?

---

### Post by Whiffle on 2008-09-29
Its not a security issue.  Its a linux-won't-work-right-at-all issue.

---

### Post by jerome1232 on 2008-09-29
Read my post again I answered your question, owning everything as your user will probably break things. It's not just about security, it's about having a working system at the end of the day. 


To make a graphical launcher for root nautilus:
Right click your panel, now click add to panel, select custom application launcher, select add

name: Root Nautilus
command: gksudo nautilus
comment: Run Nautilus as Super User

now select ok.

If you click your launcher you just made it will open a root nautilus that can manipulate all files on your system.

---

### Post by C.S.Cameron on 2008-09-29
I hope nobody thought I was actually suggesting chrooting the boot disk.
I tried this once and it was really hard to fix.
The boot process is run by root and I think the stuff in /boot and /etc, etc. need to be owned by it. 
I did not think to try if just giving root r/w permissions was enough

Jerome has a handy launcher for root Nautilus or Thunar or whatever.
Very powerful if you want to do everything in GUI. You can edit and save some really dangerous files, forget about the trash folder as backup.

---

### Post by aysiu on 2008-09-29
Please do not *chown* or *chmod* system files. That's a quick way to break your system.

A ```
gksudo nautilus
``` launcher or keyboard shortcut is the best way to go.

---

### Post by jerome1232 on 2008-09-29
> **C.S.Cameron said:**
> I hope nobody thought I was actually suggesting chrooting the boot disk.
I tried this once and it was really hard to fix.
The boot process is run by root and I think the stuff in /boot and /etc, etc. need to be owned by it. 
I did not think to try if just giving root r/w permissions was enough

Jerome has a handy launcher for root Nautilus or Thunar or whatever.
Very powerful if you want to do everything in GUI. You can edit and save some really dangerous files, forget about the trash folder as backup.

Actually root has it's own trash, when you delete files in Nautilus while running as root they will be moved to /home/.trash-01 I believe those numbers can vary but I've only used nautilus as root once for the very purpose of figuring out if it did utilize a trash mechanism or not.

---

### Post by C.S.Cameron on 2008-09-29
ahh, yes I see it there now, right under root in file manager.
Starting to wonder where all my free space was going.

Any way to stick a password in this root Nautilus launcher so you do not need to type it?

---

### Post by riahc3 on 2008-09-30
Well at least can I have the command so I can read, write, modify, and execute, ect all the files, even though Im not the owner

---

### Post by C.S.Cameron on 2008-09-30
gksu nautilus, (ubuntu) or gksu thunar, (xubuntu)
You can type this in terminal or after ALT F2.
This gives you a superuser terminal.
You can double click a file to edit it or start it with full permission.
(You can right click a file to change permissions)

---

### Post by jerome1232 on 2008-09-30
> **riahc3 said:**
> Well at least can I have the command so I can read, write, modify, and execute, ect all the files, even though Im not the owner

We've given that to you about 3 times, 2 of my previous posts, a post by aysiu, and lastly by C.S.Cameron.

---

### Post by EvilRobotDrew on 2008-09-30
mabie we should delete this thread, i can just imagine another post in about a week "help i deleted /etc how do i restore it, and why doesn't my computer boot anymore? screw it i am going back to XP"

why exactly does this guy need full access to everything? I have never encountered a problem that either sudo or recovery console couldn't fix (except the occasional privilages issue with files from a thumb drive, and that is why god made chown). while running Nautilus as root is easier then command line, i find that actually having to type everything in forces me to at least kind-of understand what the hell i am doing to my computer.

---

### Post by jerome1232 on 2008-09-30
I fully agree but I warned him it is dangerous.

---

### Post by C.S.Cameron on 2008-09-30
Come on guys, where would Linux be now if nobody tried things that seemed a little crazy to others.
Experience is the best teacher, 
I'm getting really good at re-formatting hard drives.

---

### Post by gombadi on 2008-09-30
Sometimes people don't listen so here is a practical example of what happened when I changed the owner of all files on my system to be my user.

First take a snapshot in Virtualbox - I am not silly enough to try this on a real system :-)

Start the machine, log in, become root, change to the / directory and change every file on the system to be owned by me.

Reboot the system.

I was actually surprised that it did come up and I was able to log in but then the problems started.

It had no ip address because dhcp could not run a script as the dhcp user that was permission 0754.

I tried to set an ip address manually - no go as I was not root so I did not have permission.

Surprise surprise - The kernel still runs as root and will not let ordinary users change things.

So why don't I become root. 

Try to sudo and get an error as the binary does not have the correct permissions to run.

Try and chmod the sudo binary but you guessed it - I don't have permission to do that.

The end result is I now have a system that will not work and needs to be re-installed or in this case rolled back to the snapshot so it will work again.

So the story is - If you change all the files on your system so you are the owner you will destroy your system and have to re-install it.

---

### Post by dcstar on 2008-09-30
> **C.S.Cameron said:**
> Come on guys, where would Linux be now if nobody tried things that seemed a little crazy to others.
......

"Wahhhh, Linux is useless!!! All I did was change some things (despite being told not to many times) and I have lost all my data!!!!"

"Even if I wasn't supposed to do this, Linux should have (somehow) stopped me...... I'm going back to Windows now and I'm going to tell all everyone who will listen how bad my experience with Linux was......."


If that sort of thing hadn't happened so often, it might be funny....  :(

---

### Post by davidryder on 2008-09-30
> **riahc3 said:**
> Well at least can I have the command so I can read, write, modify, and execute, ect all the files, even though Im not the owner

> **aysiu said:**
> Please do not *chown* or *chmod* system files. That's a quick way to break your system.

A ```
gksudo nautilus
``` launcher or keyboard shortcut is the best way to go.

> **jerome1232 said:**
> I wouldn't chown anything as your user outside of your ~/, You can just operate as root to do these operations. either prepend your operations with sudo, or run nautilus as root, note running nautilus as root lets you modify ANY system file and you should tread lightly.

```
gksudo nautilus
```

I can't think of anything you can't read without root privileges that you would want to copy, much less actually move.


.........

---

### Post by TreeFinger on 2008-09-30
log-in as root?

---

### Post by mikewhatever on 2008-09-30
Here's a good example of chmoding wrong files->[http://ubuntuforums.org/showthread.php?t=932890](http://ubuntuforums.org/showthread.php?t=932890).

---

### Post by riahc3 on 2008-10-01
I dont wish to become owner of the files anymore; Which is what your quotes do.

I want all the system files to still belong to root BUT also give my user premission to do whatever I want to them.

---

### Post by MunkyJunky on 2008-10-01
As has been said many times over, just press alt+f2, and type **gksudo nautilus**. You'll be given a superuser window, and you can freely peruse your entire system, with complete access to everything.

---

### Post by snowpine on 2008-10-01
> **riahc3 said:**
> I dont wish to become owner of the files anymore; Which is what your quotes do.

I want all the system files to still belong to root BUT also give my user premission to do whatever I want to them.

Ubuntu has a system in place for doing exactly that. You temporarily elevate your status to root using 'sudo' or 'gksu'. That allows you to do anything that root can do.

---

### Post by aysiu on 2008-10-01
*gksudo nautilus* basically translates to "Launch a point-and-click file browser with root permissions"

*chown* changes ownership of files

*chmod* changes permissions of files

If you use **gksudo nautilus**, as many people recommend you do, you will be able to modify root-owned files.

Changing ownership or permissions of system files will likely leave you with a broken system, so you want *gksudo nautilus*

---

### Post by davidryder on 2008-10-01
Classic example of reading comprehension problems.....

---

### Post by riahc3 on 2008-10-01
> **davidryder said:**
> Classic example of reading comprehension problems.....

Classic example of not writing correctly and exactly what I asked for problems.....

---

### Post by porchrat on 2008-10-01
What they are all trying to tell you is that nautilus is the name of the file explorer thing in your Ubuntu operating system that you use to look at all of your files.  You can run this nautilus explorer as root...allowing you to do whatever you want to the files on your system.

To do this open a terminal window (found by going to "applications"  ---> "accessories"  ---> "terminal" (or something like that...not in front of the machine right now) from the menu in the top left corner.

Then you need to type this in:

```
gksudo nautilus
```

It will then prompt you for your password.  After typing that in it will open a nautilus window for you so that you can browse all your files as root.  You need to do it this way or else you won't have root permissions.

Hope that clears up the confusion

Also what exactly are you trying to modify, move and/or copy?  I would recommend you seek help before just messing with things, people on this forum can be very helpful.

---

### Post by jerome1232 on 2008-10-01
> **riahc3 said:**
> Classic example of not writing correctly and exactly what I asked for problems.....

Well exactly what you asked for would break your system, so instead we informed you of such and told you how to open your file browser as root which give the same result. Easy access to all files on the system. I even gave you a detailed explanation how to create a launcher that you can click on to do so.

If we just gave you what you asked for and didn't offer ***helpful*** advise you would have a broken system.

---

### Post by riahc3 on 2008-10-01
> **porchrat said:**
> What they are all trying to tell you is that nautilus is the name of the file explorer thing in your Ubuntu operating system that you use to look at all of your files.  You can run this nautilus explorer as root...allowing you to do whatever you want to the files on your system.

To do this open a terminal window (found by going to "applications"  ---> "accessories"  ---> "terminal" (or something like that...not in front of the machine right now) from the menu in the top left corner.

Then you need to type this in:

```
gksudo nautilus
```

It will then prompt you for your password.  After typing that in it will open a nautilus window for you so that you can browse all your files as root.  You need to do it this way or else you won't have root permissions.

Hope that clears up the confusion

Also what exactly are you trying to modify, move and/or copy?  I would recommend you seek help before just messing with things, people on this forum can be very helpful.

Best post in this thread; Added that shortcut to my panel. Thanks.

---

### Post by davidryder on 2008-10-04
I don't mean to offend, it's just that your solution was posted many times, you just either didn't read it or didn't understand it... 

I'm glad a solution was found though!

---

### Post by porchrat on 2008-10-04
He didn't understand it.  Probably should've posted in Absolute Beginners instead, but I suppose people with fragile egos find "Absolute Beginners" insulting?

---

### Post by riahc3 on 2008-10-05
> **davidryder said:**
> I don't mean to offend, it's just that your solution was posted many times, you just either didn't read it or didn't understand it... 

I'm glad a solution was found though!
> **porchrat said:**
> He didn't understand it.  Probably should've posted in Absolute Beginners instead, but I suppose people with fragile egos find "Absolute Beginners" insulting?

Both wrong.

It wasnt explained that the command was for that.

And Im not a "Absolute Beginner"; Im starting out in Linux but I know most of the popular/important commands.

---

### Post by Sylvertwyst on 2008-10-06
if you had just tried the command you'd have seen for yourself what it does, you wouldnt need the explanation.

---

### Post by davidryder on 2008-10-06
> **Sylvertwyst said:**
> if you had just tried the command you'd have seen for yourself what it does, you wouldnt need the explanation.

Or a quick Google search...

---

### Post by riahc3 on 2008-10-06
> **Sylvertwyst said:**
> if you had just tried the command you'd have seen for yourself what it does, you wouldnt need the explanation.
So if someone would have told me (example)

format c: *.*

I should just try it out and see what it does right? Great advice...

> **davidryder said:**
> Or a quick Google search...

You really think I didnt do a google search before coming here? You must be joking.

---

### Post by davidryder on 2008-10-06
> **riahc3 said:**
> 
You really think I didnt do a google search before coming here? You must be joking.

I don't really know what you did before coming here. I never implied that you didn't do a google search. If the explanation was lacking a quick google search or a request to clarify would have sufficed. Instead you kept asking the same question as if it was never answered. 

Do you get it? Or are you never wrong?

---

### Post by Joeb454 on 2008-10-06
Thread closed. It's been marked as solved, and is decending into an insult-fest.

---

