---
title: "Help me upgrade to 8.10"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by catwomisen on 2009-03-17
Hi
I'm sorry if there have been other posts made for this specific problem, but I've been looking around and I feel like such a n00b right now that I thought making a post was the best, and most secure option.

You see, a couple of months back I tried to update from 7.10 (I think) to 8.04, but the updater froze in the middle and eventually, after looking around the forums, I had to reboot. 
Now, whenever I try to log in Ubuntu completely freezes and after various attempts to fix this through the recovery mode I still haven't made any progress at all. After this I kind of just gave up, and went back to my Windows XP.

Though, since I know am about to move back to Sweden, from Japan and am unable to bring the computer with me I have to sell it. I have someone interested, but he doesn't want an unusable OS lying around the harddrive. It is also very important for him that I **keep Windows XP intact**.
So, I beg you all, can someone help me **get Ubuntu working** again?

My ubuntu is on it's own partion of the harddrive, if it helps at all.

*(Sorry for being so newbie... :()*

---

### Post by x33a on 2009-03-17
do you have a dual boot system?

and if you are selling the system, and the other person wants windows, then why do you want to retain ubuntu?

---

### Post by catwomisen on 2009-03-17
> **x33a said:**
> do you have a dual boot system?

and if you are selling the system, and the other person wants windows, then why do you want to retain ubuntu?

Yea, I have a dual boot system.
And the answer to the second question is quite simple really... I don't know how to uninstall ubuntu without damaging or deleting windows. And if I accedentally did so, I don't have a windows installation CD. All I have are some backup DVDs, but I don't know if these could completelly reinstall the system or not.

---

### Post by x33a on 2009-03-17
[http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)

or you can try supergrubdisk

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after fixing the mbr you can simply delete the ubuntu partition.

---

### Post by catwomisen on 2009-03-17
> **x33a said:**
> [http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)

or you can try supergrubdisk

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after fixing the mbr you can simply delete the ubuntu partition.

I'm going to guess mbr is a program of some sort.. do I burn it, or can I use it directly to windows, is it something needed to install? How do I download it? How do I use it? Also... supergrubdisk... what's that? "We want Linux newbies to restore their new toy"... to... windows?

I'm sorry for the stupid questions, but the websites aren't very straight forward, and I am a newbie. :(

---

### Post by can8dnSix on 2009-03-17
You should be able to repair the Windows MBR from the command line through Windows in recovery mode. I guess the second thing to ask is this, does your computer have an option to make "recovery disks" and if so, I would say just make new recovery disks and re-install the entire system so you can get rid of all your personal settings, files, etc on the computer hard drives. 

Typically the recovery disk creator program is located in All Programs --> Recovery Disk, or Recovery Tools, or even Tools depending on the company that made the original workstation. If the workstation is a Lenovo you can hit up their website for some direction, if it is an HP, same. 

But all in all, you have many options to do this. 

If you want to fix the Linux install, I would just re-install Linux and it will do the same thing it did before and detect Windows XP/Vista, etc and add it to the boot loader. 

L

---

### Post by x33a on 2009-03-17
hi, maybe this can help:

[http://www.raymond.cc/forum/linux/9367-how-to-remove-ubuntu-linux-from-dual-boot-tutorial.html](http://www.raymond.cc/forum/linux/9367-how-to-remove-ubuntu-linux-from-dual-boot-tutorial.html)

as for mbr

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by catwomisen on 2009-03-17
> **can8dnSix said:**
> You should be able to repair the Windows MBR from the command line through Windows in recovery mode. I guess the second thing to ask is this, does your computer have an option to make "recovery disks" and if so, I would say just make new recovery disks and re-install the entire system so you can get rid of all your personal settings, files, etc on the computer hard drives. 

Typically the recovery disk creator program is located in All Programs --> Recovery Disk, or Recovery Tools, or even Tools depending on the company that made the original workstation. If the workstation is a Lenovo you can hit up their website for some direction, if it is an HP, same. 

But all in all, you have many options to do this. 

If you want to fix the Linux install, I would just re-install Linux and it will do the same thing it did before and detect Windows XP/Vista, etc and add it to the boot loader. 

L

*Edited out the "what is MBR?" question, see I already got an answer*

I do have some kind of backup DVD, but I am unsure as for if I am able to reinstall the entire system with it. Also reading what the menues and options say doesn't help me much always, since my windows is in japanese, (X.x) I'm also unsure wiether the little sticker on the DVD's folder says "You will not be able to create a backup of your system now if you use this first", or if it says "You will only be able to use this once". Kanji... gah.

I talked to the guy interested in the computer today, and he seems quite curious as for what this "Linux Ubuntu" actually is, so if possible I think repairing would be the best option. And if I choose to do so, I just stick the disc into the drive, boot it up, install and it'll upgrade? It won't just install one more ubuntu or anything like that? I seem to remember that I'm not the only one with this "upgrade from 7.10 to 8.04 doesn't work"-bug, and someone must have been able to fix it... right?

(On a side note, the Ubuntu CD I currently got is a 8.10, should I make a 8.04 if I want to make it work?)

---

### Post by x33a on 2009-03-18
since your aim is to remove ubuntu, and retain windows, it is unnecessary to try fix ubuntu.

did you try the tutorial i referred to? it should do the job.

please update.

---

