---
title: "Eee PC - Several of questions"
date: 2008-12-10
forum: Hardware
---

### Post by Rubicon421 on 2008-12-10
I just got a used Eee PC 4G and have several questions. I really would just like some links to some threads and sites to help me get started, so you don't have to post detailed replies to each issue.

XP has been uninstalled. I have the disc, but no CD drive. How do I restore it to a fresh factory install? It has Ubuntu, which I will put back on, but first I want to wipe it clean and get it like it was new. Then delete all the unnecessary crap to save space before reinstalling Ubuntu.

Second, how do I install Ubuntu on an Eee PC and what version do I use?

Third, are the repos different, and are there certain ones I should add that are specific to Eee PCs?

Fourth, what, if any, major programs common to Ubuntu are not available and what suitable replacements are there for the Eee PCs?

Fifth, is there a good guide to tweaking out the settings to speed things up- both for XP and Ubuntu on Eee PCs?

Sixth, what am I forgetting? What do you love/hate about Eee PCs? Any other cool stuff I should know about them?

---

### Post by scottuss on 2008-12-10
A1) You don't need to reinstall xp to clear everythin off it, just boot from an Ubuntu CD (from an external USB cd drive, you can get one from your local computer guy or use an old cd drive with an Easy IDE connector)

A2) See above

A3) No, the repos are the same although I would visit array.org and maybe add that repo, it has a replacement kernel which is great (much faster than the standard one, plus all the wifi and other bits work "out of the box")

A4) All ubuntu programs will run

A5) Visit [http://wiki.eeeuser.com/#ubuntu_8.04_hardy_heron](http://wiki.eeeuser.com/#ubuntu_8.04_hardy_heron)

A6) My EEE PC is awesome, I have Ubuntu on it and it's fantastic! I also have an SD card (I also run Puppy Linux from the SD card) Generally speaking, I'm very happy with my EEE.


Any more questions, feel free to ask :-D

---

### Post by Rubicon421 on 2008-12-10
Just noticed that it's running 8.04. Is there a way to update to 8.10 just like I was updating a program, or will I have to download a live cd or wibi to an SD card and upgrade like I would on my desktop?

---

### Post by scottuss on 2008-12-10
Sure, just type sudo apt-get dist-upgrade into a terminal, that should upgrade you to 8.10. Make sure you backup first though, usually everything works smoothly but the last thing you want is for something to go bad with no backups!

---

### Post by Rubicon421 on 2008-12-10
Thanks. I don't have anything to back up though, I just got it. Is there any reason to do it anyway?

---

### Post by scottuss on 2008-12-10
If you don't have anything on it there's no point backing up, if anything goes wrong your'e OK to just re-install

---

### Post by scottuss on 2008-12-10
If you don't have anything on it there's no point backing up, if anything goes wrong you're OK to just re-install

---

### Post by Rubicon421 on 2008-12-10
I just did it. It said 1 update, 0 kb will be added. bunch of code ran after I entered my pw then when it was done I restarted and it's still 8.04????

---

### Post by scottuss on 2008-12-10
Ah my fault. I just remembered an easier way actually:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

check that out, follow the instructions there and you should be fine

Sorry about that! It's because the correct repos aren't enabled I suspect...

---

### Post by Rubicon421 on 2008-12-10
OK, I did that and after waiting a while on a greyed out upgrade screen a window opened with a text file with a bunch of info about 8.10 and links to more info, but it didn't upgrade. I got the screen that said there is a new update available (8.10) and clicked update, but that's all it did after that.

---

### Post by scottuss on 2008-12-10
That's strange. If you followed the instructions on that page correctly everything should work out...

What size SD card do you have? I'm just thinking, you could download the ubuntu alternative 8.10 cd, save the iso onto your card and then mount that iso as a "real cd" The alternative CD allows you to update from it.

That's the only thing I can think of right now, if i get any more ideas I'll post them.

Let me know what size SD card you have anyway and if you want to go ahead with that method I can talk you through it

---

### Post by Rubicon421 on 2008-12-10
another issue-

4GB SSHD and it says there is only 360MB free when XP has been removed. It's used so it's no telling where all the used space is but what should Ubuntu's footprint be and how can I tell if the deleted windows install is still taking up some space somehow?

---

### Post by Rubicon421 on 2008-12-10
Any fixes I do right now really are kind of pointless because I plan on starting with a fresh install of xp and then re-adding Ubuntu but I'd rather know what to do after that if I have any of the same issues. Most of them will probably be eliminated in the process but this is a good learning experience being that I'm new to linux.

---

### Post by scottuss on 2008-12-10
Yep, sudo apt-get install gparted will install the partition manager. Once that's done on the main menu go System > Administration > Partition Editor.

That app will list all partitions on the ssd.

I'm not entirely sure I understand your setup... was the eee running Windows then you over installed Ubuntu or what? I don't understand! lol.

---

### Post by Rubicon421 on 2008-12-10
not sure how he did it, like I said, it's used. As far as I know, it came with XP and without Ubuntu. Then he removed XP during or before the Ubuntu install.


here's some info on the partitions

dev/sda1  ext3 3.51GB, (3.04GB used)
sda2 extended 219MB
sda5 linux swap 219MB

usr folder is using 2.2 GB

and this is the weird part- every folder in usr is the same size, 304MB. Is all the space being taken up because ubuntu is reserving a set amount of space for each of these folders?

---

