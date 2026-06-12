---
title: "Preemptive Advice for 2 HD Dual Boot?"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by BJ_Covert_Action on 2008-12-09
Howdy folks,

First off I want to mention that this is my first post on the forums so if I manage to newb it up big time, please be gentle. I'm a fragile soul...

I am currently a windows XP user and I am eager to make a switch over to Ubuntu. Nonetheless, there are a few games/programs that I need in Windows that, so far as I can tell, neither Wine nor Cedega have ported to Ubuntu successfully, so I have decided to reconfigure my system to a dual boot configuration. 

Currently I have two hard drives installed (IDE) I have an 80G Maxtor as my primary hard drive and a 200G Maxtor as a slave hard drive that was, up until last night, used solely for data back up. I copied all my important files to a third external hard drive which I will play with later. For now, however, I need to start working on reconfiguring my two internal hard drives. Currently, my primary hard drive (80G) has Windows XP installed. I reformatted my slave HD last night and it is now sitting, blank, in my case with nothing on it. 

What I would like to do: 
My grand scheme involves a full system reboot. That is, I want to wipe my current XP version off my primary hard drive (I do not need or want any of my previous settings/files from that OS anywhere on my new system). I would like to end up with Windows XP on the 200G slave drive with Ubuntu as my primary OS on my 80G primary disk. I would also like to be given the choice to boot either windows or Ubuntu upon startup without having to muck about in my BIOS.

What I (might) know so far:
I've been scouring the forums and found many posts on dual boot configurations/help. So far it seems like the best way to do what I am trying to do is to:

1) Remove both harddrives and configure the 200G as master
2) Put the 200G (now master) HD back into the machine and install and configure windows XP on it.
3) Pull the 200G HD back out and reconfigure it to slave.
4) Put in the 80G HD configured as master, reformat and partition it.
5) Put the 200 G back in as slave and boot with the Ubuntu CD (version 7.10).
6) Install Ubuntu as the OS on the 80 G HD.

Ideally, as Ubuntu installs on the 80G HD it should detect the 200G HD (with Windows freshly installed) and configure Grub to work with both. However, it seems that there might be some problems with grounding windows in the corner on the slave drive. So I might have to edit something in grub to trick windows into thinking it is on the primary drive when it is not. 

So far that is what I think I have divined from the smattering of literature I have read on this subject. Does this sound right to you all? Is there an easier way to go about it (one that might not involve pulling and plugging in HD's like they were flash drives)? Am I completely missing anything major? Any general advice for newbie OS installers? (I have installed Windows 3 times previously, but never dual booted).

Any thoughts would be greatly appreciated. Thanks in advance for your advice guys.

Cheers,
Brady

---

### Post by caljohnsmith on 2008-12-09
I think your methodology to install Windows and Ubuntu would work just fine.  If you wanted to save yourself taking out the HDDs and reconfiguring them as master/slave, you could first create a temporary primary NTFS partition on your 80 GB master drive, and then when you install Windows to your slave drive, Windows will put its boot files in the primary partition of the master drive. Once the installation is done, then you can move the boot files back to the slave drive and boot Windows solely from the slave drive with the help of Grub. You would also have to do a small edit to Windows boot.ini file to in order for that to work. So the bottom line is that if you try to install Windows to a slave drive, Windows needs a primary NTFS/FAT partition on the master drive for its boot files; but it is possible to move the boot files back to the slave drive and boot Windows from Grub with a little bit of work. 

So if it is not too much trouble, I think your plan of just temporarily making the 200 GB drive master and install Windows to it is probably easier. When you go to install Ubuntu though, you don't have to remove the Windows drive; when you go through the Ubuntu installation process, just click the "advanced" button near the end, and then specify to have Grub installed to /dev/sda or whichever is the Ubuntu drive; then you should be fine (your Windows drive will be untouched). If for some reason the Ubuntu installer does not correctly configure Windows in your Grub menu, let me know and I can help you straighten it out if you want. Anyway, good luck and let me know how it goes or if you run into problems. :)

---

### Post by BJ_Covert_Action on 2008-12-10
Sweet, thanks caljohn. I figure I will probably start doing hardware reconfigs tomorrow afternoon. Hopefully by tomorrow evening I will have a fresh functioning Windows XP on my 200 G and be ready to zero out and reformat the 80 G.

Any more advice/thoughts would be appreciated. I'd offer to make cookies for those that respond...but I am not much of a baker.

Cheers Folks

---

### Post by BJ_Covert_Action on 2008-12-12
Well, a few days later and some careful planning paid off. I conducted things just like I listed up above and I have both Ubuntu 8.04 and Windows XP configured and operable as desired. Grub works with both just fine and now I am off to fine tune my new favorite OS :)

Cheers Folks,
Thanks especially John
-Brady

---

### Post by caljohnsmith on 2008-12-12
Congratulations on getting your dual boot working, Brady; that's great news. Cheers and have fun with your new Ubuntu install. :)

---

