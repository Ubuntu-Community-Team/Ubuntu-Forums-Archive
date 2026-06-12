---
title: "tracking what you install/ sound problems"
date: 2008-08-02
forum: General Help
---

### Post by Tom_ZeCat on 2008-08-02
I'm annoyed.  On one of my Linux machines, I got the red arrow indicating there were security updates available.  There were also non-security recommended updates.  I unchecked all the recommended ones and allowed just the security ones to install.  Now all of a sudden the sound quality on that machine is trashed.  That's bad because the machines only purpose is to act as a juke box, holding all my music in Amarok and playing it through my entertainment center.  

Gggggrrrrrrrr!  I did not write down every update I let install.  Now I realize I should have so that I can go back and uninstall things one by one to see if they're what caused the problem.  

I therefore have two questions.  

1. Is there some way to keep an automatic record of what gets installed via Synaptec?  It would be great if every time the package manager installed something, it also wrote the name of the app installed into a text file.  

If this doesn't exist, I guess I'll type everything to be installed into a text file with a time and date.  And I'll post the automatic idea to a development forum.  

2. Is there a known sound problem caused by recent Ubuntu 8.04 updates and an easy way to fix it?  I googled for a solution and found sound problems from some time ago that probably weren't related to this recent update.  It was yesterday when this update was done.  

If there's not an easy fix, I'm probably going to just reinstall Ubuntu and Amarok and then carefully track what updates happen.  The music collection on that PC is already backed up, both on an external hard drive and on my other Linux machine (the one I'm typing this on).

---

### Post by ludovicc on 2008-08-02
Hello Tom,

To keep track of all changes in your configuration, including which packages where installed, you can install etckeeper. Follow the instructions here: 
[URL="http://www.google.com/url?sa=t&ct=res&cd=5&url=http%3A%2F%2Fdaniel.hahler.de%2Ftrack_changes_to_etc_configuration_files&ei=pfiUSPuTGoKUQd-J9KwK&usg=AFQjCNEVld9_o4Wwewi0mUPX0c3QaUrxKg&sig2=hzaSBYlrdERLyGPQ1ShN7g"]http://www.google.com/url?sa=t&ct=res&cd=5&url=http%3A%2F
track_changes_to_etc_configuration_files[/URL]

About fixing sound problems after an update, well the same story happened to me some 3 months ago, and I'm still on the forums trying to look for a solution. My sound 'works', but the level is quite low and I have to amplify the sound to the maximum to hear anything. Unfortunately, this distorts the sound and music sounds horrible. I have tried editing my alsa mixer settings, in particular the PCM volume, I have followed the 'Perfect Pulse audio setup' thread and a lot of other howtos, but nothing helps. Do you have a motherboard with an integrated NVidia chipset by any chance?

---

### Post by Tom_ZeCat on 2008-08-02
I do have an NVIDIA video card, but not in the machine whose sound went bad on me.  I have Ubuntu on an old Pentium III with 256 MB of RAM and on an Athlon 64 dual core machine with a gig of RAM.  The Pentium III is the one whose sound has gotten bad.  It might have an old NVIDIA sound card.  I'm not sure.  It was originally an HP Pavillion with Windows 98.  Ironically, it's the machine that Ubuntu installed flawlessly on the first time.  On the newer machine (also an ex HP Pavillion), I had to jump through a lot of hoops to get the video card working properly.  I don't even know what video card is on the Pentium III.  I just went to that machine to look for it in Admin, but couldn't find it.  

On both machines, the sound initially sounded bad until I installed Amarok.  I think Amarok must have brought in a sound driver or utility that automatically fixed the problem.  You might therefore try installing Amarok to see if it fixes your problem.  It did mine -- twice.

If you're still having NVIDIA problems, the following might work.  I did a ton of troubleshooting and tried a fix NVIDIA drivers wizard named Envy.  Oddly enough Envy didn't work the first time, but after I reinstalled Ubuntu and did all the steps shown in my quote below, it finally worked.  I saved my exact steps so that I can do this again if I need to.  I don't know why this sequence worked, but it did:

> System ==> Administration ==> Synaptic Package Manager



installed nvidia-glx-new-dev & nvidia-glx-new  (not sure if it really needed it)



System ==> Administration ==> Hardware Drivers



enabled NVIDIA accelerated graphics driver



------------

second time around this didn't work, but it did work to do that first, and then when the opening screen said it was a low res driver, i clicked on a button and chose Samsung SyncMaster 730a (it didn't have 731B).  It was still in low res, but I rebooted and then ran Envy on automatic and it finally worked.

Btw, I'm also going to start using Clonezilla so that I can roll a system back if an update #$%^s something up.

------------------
Edit: I've elected to reinstall Ubuntu and Amarok on the Pentium III machine.  I therefore don't need to figure out how to fix the sound, at least not yet.  If I have sound problems after the reinstall, I'll make another post.

---

