---
title: "Camera not auto-importing in edgy"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by nalthien on 2006-10-09
Hello all,

I'm running Edgy--so I guess I'll post here since the admins for some reason thought it was a good idea to get rid of the section specifically for edgy.

Since upgrading my Dapper to Edgy, My digital camera (Canon EOS 350D / Digital Rebel XT) appears to no longer be autodetected by the system when I attach the USB cable. In Dapper, a window would pop up asking me what I wanted to do--no such window appears in Edgy.

I checked the settings in my "Removable drives and media" preferences, and found that the settings for mounting media when inserted options were checked. Also, under the Cameras tab, the box was checked for "import digital photographs when connected" The command listed is:

> gnome-volume-manager-gthumb %h

I copied that command into a terminal window and ran it and it opened the gthumb image import window with my camera detected and imported the photos just as I would expect it to do.

Once I connect the camera, I am able to manually import photos using either the gthumb importer or using F-Spot's import functionality. However, I cannot seem to have this happen automatically as it used to when I connect my camera.

---

### Post by pagaboy on 2006-11-02
I'm having the same thing.  No autodetect on my account, but my wife's account detects it fine.  Very irritating.  If anyone has a solution (and yes, the right boxes are ticked in Preferences->Removable stuff), that'd be grand.

---

### Post by chenel on 2006-11-08
ditto for me to all of that

---

### Post by andymaclean on 2006-12-01
I had the same problem.  Accounts which had been used in an older Ubuntu install (5.10) to import photos don't auto-import in 6.10.  The broken accounts are the ones where I ticked the 'always perform this action' box in Ubuntu 5.10 before clicking on 'import photos'.  Other accounts seem to work OK.  

This probably isn't the proper way to do and I guess it might break other peoples' systems but I fixed my account by doing this and then logging out/in:

rm -rf ~/.gconf/desktop/gnome/volume_manager

That particular group of gconf settings doesn't appear to exist for the accounts which import correctly.  All it had in there was a bunch of true/false settings for automatically acting after detection of various types of device.

---

### Post by chenel on 2006-12-02
Hey, that fixed it for me too!  (And nothing else seems to have broken!)

Thanks!

-chenel

---

### Post by Mrs Harris on 2007-01-19
Nice one Andy, was having the same since my upgrade to edgy... I'll spread the word

---

### Post by HarmonicaGoldfish on 2007-04-22
I am going to try this. Have the same problem and it has immigrated to feisty :)

---

