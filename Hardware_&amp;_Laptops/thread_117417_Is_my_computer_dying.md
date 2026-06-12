---
title: "Is my computer dying?"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by dcast on 2006-01-14
My computer is making funny sounds and keeps crashing.  Sometimes when im not doing anything at all that is intense like word processing with ooffice or sometimes whenim doing something intense like compiling it starts making noises and the processor spikes up to 100% and sits there. Everything locks up mouse, keyboard, numlock... everything. The sounds are like a car with a dying battery (losing power) like the engine is revving and everything sounds good and then it starts to go to a low hum and then back up (its very gradual but happens like every 5 seconds. I thought maybe my cpu was heating up but it doesn't have a fan and never did so why should this happen now. Is it my harddrive(s) or maybe my power supply? Any help is appreciated

Edit: oh ya and this doesnt always happen just sometimes. Also it won't let me use repositories in synaptic (I just connected ubuntu to internet for the first time) although I dont think that has anything to do with it but whenever I run synaptic and try to update the repositories my computer does the above.

David

---

### Post by Zelut on 2006-01-14
My first guess would be the hard drive.  Its the only thing (besides a CD/DVDROM/fans) that even has moving parts.  If you hear grinding and things thats most likely the case.  As far as the CPU & the heat.. if you've never had a fan/heatsink you probably don't need one now.  That wouldn't cause a grinding though.

It could be a case fan if you have any of those.  Take off the side of the case and look at some of the fans.. see if some of them are struggling.  If that isn't the case I'd guess HDD.  Backup what you need & try another drive, see if that solves the problem.

---

### Post by nalmeth on 2006-01-14
that sucks

sorry, when did this start happening? Just recently?
Anyway, open up a terminal, and type:
sudo apt-get update
sudo apt-get dist-upgrade
since terminal wastes no processor memory, you should be able to access the repositories without clogging up the CPU.
I don't know much about hardware, but I do know that whenever I have had weird hardware problems (even with my xbox), cleaning out all the dust and crap inside the box suprisingly helped more than not.
You can buy cans of compressed air designed for cleaning out delicate things like computers. They are really good for getting crap out of your computer.

---

### Post by dcast on 2006-01-14
that was my initial thought as well. Thank you for the advice. One thing though. I have two hard drives the installation is on a 20gb which is ide-1 or the primary slave and the other disc is on ide-0 or the primary master. If the second disc gave out would that cause the problems? because I dont really want to replace my normal disc to find thats not the problem. Thanks for your help.

David

---

### Post by Azion on 2006-01-14
Not really, if u have Linux on the other drive it'll be fine

As long as Grub/Lilo is there it'll be fine

---

### Post by dcast on 2006-01-14
kuyaedz- thanks thats working for the upgrades. To azion the other disc doesnt have an install I just use it for extra space but I guess doing an install isn't that big a deal. Its weird because I'm posting from the computer inquestion and there is no problem. The problem is so inconsistent. I will try an install on the other disc and let you guys know how that goes. Unfortunately it will have to wait since I have a lot of school work to do with exams coming up. Thanks for all your help guys.

David

---

### Post by Azion on 2006-01-14
Install where ur Windows disc is, that won't affect anything.
Your second hard disk will still be fine.

---

### Post by drfalkor on 2006-01-14
I guess it is your hdd

---

### Post by southernman on 2006-01-14
You best make a backup ASAP (to a seperate drive)... school work and exams, or not! 99.995% of the time you hear metallic sounds coming from your computer... take it to the bank, your hdd is going out. Who knows how long the bad drive will last, maybe a day - maybe longer. I've got an older seagate 4.3GB SCSI (on a test box) drive that makes a god awful noise but, it's done this for over a year now.

Unless of course, you have little gremlins inside your computer. ;)

---

### Post by handy on 2006-01-15
You can carefully vacuum out the dust.  

If there is no CPU fan, you will probably find that there is a case fan, (although you did not give any spec's for the machine, so we really don't know much about what we're trying to diagnose, like what kind of CPU & speed?)

If you do have a CPU that needs cooling, ie. a case fan, & that fan is playing up - they can be quiet & then noisy & vary their speed...  Unlikely but possibly your problem.

The last part of your post is intriguing...

Does it crash every time you try to download with Synaptic?  If so can you be more descriptive?  Does it happen when Synaptic is attempting to write to your drive?

---

### Post by dcast on 2006-01-15
I put in a different drive with similar specs and im currently doing an install and I havent had any problems. Thanks for everyone's help.

---

### Post by dcast on 2006-01-15
Ok... I did the reinstall on a different harddisk. Same thing. Same issues. I thought I had corrected it but no. So what is the problem. Also it won't mount the second disk. I dont understand what the problem is. Also now after the reinstall its taking a long time to boot up. It just comes to the emachines splash screen and sits there at least 3 times longer than it used to. WHy is this happening.

---

### Post by handy on 2006-01-16
Just a shot in the dark...  It sound like your mainboard could be stoinked!

I could certainly be wrong though, so the best you can do is remove all cards except the video card, make sure the ram & vid card are seated properly, disconect all but your boot drive, & see how it goes, if is ok, then add one thing, & test for a while, then add another & so on, untill you find a culprit.  You might be lucky  & find bad component is causing the strange behavior.    It certainly can & does happen.

Don't overlook the power supply unit (PSU) it is a possible culprit, but save it to last, the other thing is the graphics card too, even if it is working properly, unfortunately you can't trust anything in a situation like this.

All the best.

---

### Post by micjustmic on 2006-01-16
If your other hard drive has <> the bed, your BIOS will attempt many times to get the info it needs from the drives controller, this could be causing the long startup times during POST.

The fact you can't mount the other drive is a good indication that the other drive is now an expensive door-stop.

Take the other drive out and see if your boot problems go away, if they don't, it could be the hard drive logic in the chipset has gone bad, rare but it can happen.

Mic

---

### Post by dcast on 2006-01-16
I took the other drive out it seems to be running fine. so far so good. Ive been working on it for about 1.5 hours

---

