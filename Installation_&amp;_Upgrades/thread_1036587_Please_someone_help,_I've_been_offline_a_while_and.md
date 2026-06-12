---
title: "Please someone help, I've been offline a while and can't upgrade"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by sargosis on 2009-01-11
It's been over a year since I've been online and I'm having real trouble trying to upgrade from 6.10 to 8.04. I don't have a lot of knowledge about ubuntu and I've been trying to get the update manager to work. I've added the repositories that were suggested on other threads, but i'm still getting errors about missing repositories. I could really use some help because all i want to do is get my OS upgraded so i can use my new keyboard (this **** took less than a minute on windows).

if anyone's actually willing to help i'd appreciate it.

---

### Post by Briped on 2009-01-11
I would have thought that a leap from 6.* to 8.* is rather a big mouthfull. I know this doesn't answer your question, but I would suggest you make a clean install instead of upgrading, and while you're at it, why don't you try 8.10 instead of 8.04? 

Kind regards,
Britta

---

### Post by Elfy on 2009-01-11
6.10 has been out of support since April of last year, Feisty the next version has been out of support since October.

It's likely that you'd be better of doing a clean install to 8.04.1 if you want to keep version for a long time, it being LTS and you'll have a direct upgrade route to the next LTS.

If you have a seperate /home it would maybe make life easier to do a clean install, otherwise make sure to backup anything you need from /home.

You can post your sources list and maybe point to where you got the information from, > I've added the repositories that were suggested on other threads

---

### Post by Partyboi2 on 2009-01-11
As what has been mentioned a clean install would be the way to go. A clean install will be a lot quicker then upgrading 3 releases. As mentioned by forestpixie if you have your  /home on its own partition doing a clean install is pretty hassle free. [[COLOR=Blue]Here[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome") is a link to moving your /home folder to its own partition if you decide to go this way.

---

### Post by Partyboi2 on 2009-01-11
double posted

---

### Post by sargosis on 2009-01-11
well thanks guys...

---

### Post by albinootje on 2009-01-11
> **sargosis said:**
> It's been over a year since I've been online and I'm having real trouble trying to upgrade from 6.10 to 8.04.

Did you test the "live session" from the Ubuntu 8.04.1 installation cdrom to see how well your system works with it ? Please do so first.

And, depending on your machine, and depending on how many applications you have installed, a single dist-upgrade can take 1 till 2 hours.
Making a *proper* backup of /home, and then do a fresh install of 8.x is likely to be so much faster.
With proper backup I mean here :
1) Make sure the hidden dot files and directories are copied too.
2) Make sure the permissions and timestamps of the files+directories are reserved. 
A simple 1:1 copy to a FAT32 partition is for example a bad way of backing up your Linux /home directory.
Using tar or zip to create archives, and *then copy to a FAT partition should be OK however.

Best is to use external media like usb disk, or DVD.

---

