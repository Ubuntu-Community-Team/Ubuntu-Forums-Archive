---
title: "Photo import does ... nothing!"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by asbesto on 2007-05-08
Hi all,

I connect my NIKON Coolpix 4800 via USB; it will be mounted perfectly - i see it on /media/disk or something like that, i can copy files via shell with cp/move and so on.

But a requester pop on my desktop saying:

[I]
Photo Import

A Photo Card has been detected, BLA BLA BLA.

X Always perform this action

Ignore    Import photos
[/I]

and, every thing I choose, it does **NOTHING**.

this is very annoying, I can't find how to configure or set up this photo import stupid daemon , so I manually have to move my images from the camera to my photo directory.

Can someone help me ? 
:confused:

---

### Post by jjordan on 2007-05-08
What program are you using to organize your pictures?  Try setting up the camera in configuration dialog of that program.  I use Digikam so I select "Settings" > "configure Digikam" and them "Cameras" in the dialog box.  

Digikam is good because it allows you to keep your pictures organized in whatever directory structure you want.

-j

---

### Post by asbesto on 2007-05-11
> **jjordan said:**
> What program are you using to organize your pictures?  Try setting up the camera in configuration dialog of that program.  I use Digikam so I select "Settings" > "configure Digikam" and them "Cameras" in the dialog box.  

Digikam is good because it allows you to keep your pictures organized in whatever directory structure you want.

-j

AH!

I don't use any program to organize my photos :)

I just move my pictures in directories, by hand, using shell commands, and I put online via scp and make albums with the "album" perl script and stuff like that... 

maybe this is the problem - this dialog work only by using a particular program to organize pictures, like digikam ?

If so - well, I really don't need it: how can I remove this annoying dialog message that come up every time I connect my camera ? :)

tnx!!!

:popcorn:

---

### Post by jjordan on 2007-05-11
Honest recommendation is to take a look at Digikam.  The reason I use it it because it allows me to organize my pictures the way I want to in directories that I choose or create on the fly.  You don't actually have to use DigiKam, just set up your camera using its dialog boxes.  

To disable the dialog that pops up I would need to know what desktop you are running.  Under KDE select "do nothing" and then check the box "always do this for this type of media."    Of course you could select "Open in a new window" and "always do this for this type of media" then it would open Konqueror to allow you to copy your photos manually to the directories you choose.

I don't have Gnome loaded so someone else will have to give you the verbage under Gnome.

-j

---

### Post by Daveth on 2007-08-25
if you able to change the way usb is dealt with in your camera then try altering that. My panasonic FZ30 was similarly recognised but never dealt with. I then changed the cmaera usb handling setting and the system now imports pictures from it and deletes from the sd card.

Bit old, but worth a comment!

---

### Post by markoloka on 2007-08-27
I use Digikam... it used to work but yesterday it wouldn't import pics to pc. It recognises my cam correctly but getting pics to pc is now the problem. On xp it works fine.

---

### Post by can_erogul on 2007-11-04
Ubuntu uses gthumb program, when you want to import your photos. I guess your gthumb program is missing. If somehow that program is uninstalled, the import photo behaves that way.

---

