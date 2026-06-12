---
title: "I want to REMOVE Ubuntu"
date: 2008-11-15
forum: General Help
---

### Post by Trevness on 2008-11-15
Hey, well...I really want to Remove Ubuntu because i really dont know how to install things and i read guides and i dont get it at ALL...

So i really need SPECIFIC INSTRUCTIONS on how to Remove Ubuntu

Needs to be SPECCFFIICC i dont know anything about this...

---

### Post by oilchangeguy on 2008-11-15
you can boot from the live cd, and use the partition manager to delete the ubuntu partitions. then expand your windows partition to use the space.

---

### Post by Trevness on 2008-11-15
What CD the CD i used to burn Ubuntu? I have that

and where is this Partition Manager?

---

### Post by Bigneil on 2008-11-15
I am a bit of a NOOOB at ubuntu too. It is really quite different from any windows system i ever used, but, it has some significant advantages. give it a bit of time and you'll soon be confident with it.  and there is a whole community of more experienced users waiting to help out us newbies. 

And don't forget you can always install xp and ubuntu and choose which one you want when you're booting up.

---

### Post by Trevness on 2008-11-15
I dont like Ubuntuuu...When i make topics on like..Oh how do i install this game?

I DONT GET SPECIFIC INSTRUCTIONS Like they tell me to instal it to..$HOME or somethin..where the hell is that? I just want to remove this..soo confusing

---

### Post by Mardoct909 on 2008-11-15
Unless you actually need to have a bunch of free space with no filesystem (If you're such a noob, you most likely don't.) just install another operating system and use its partitioning part of the install to remove the Ubuntu partitions and then use them for the other OS.

If you are dual booting and want to keep the other OS without having Ubuntu, refer to oilchangeguy's post. The partition manager comes up automatically during the installation.

By the way, $HOME is a variable that the computer sees as your home. Your home is comparable to "My Documents" in Windows. It's probably /home/[username]

---

### Post by oilchangeguy on 2008-11-15
> **Trevness said:**
> What CD the CD i used to burn Ubuntu? I have that

and where is this Partition Manager?

when you boot from the live cd (the cd you used to install ubuntu) after the desktop loads go to system, admin, partition manager.

---

### Post by Skripka on 2008-11-15
> **Trevness said:**
> Hey, well...I really want to Remove Ubuntu because i really dont know how to install things and i read guides and i dont get it at ALL...




Everyone starts as a (frustrated) newb in linux.

---

### Post by TeXtonyx on 2008-11-15
Besides deleting the Ubuntu partition which they told you how to do
you need to make Windows bootable. Right now you can boot Windows
because you are using grub which is the Ubuntu boot manager.

When the Ubuntu partition goes, so goes the grub support files. 
That means you need to make the Windows a standalone bootable
system again. You do that by setting your bios to boot from a
cd and put your Windows install cd into the cdrom before you boot.

What you will do is run "fixmbr" and "fixboot" which restores
Windows to the MBR. Those are two commands that you run from the
Recovery Console which is part of the XP or Vista install cd. 

Do a search on Google using the term, Recovery Console , and from
the many returns for the search, look them over and pick one that
has pictures of the steps. Print out one that makes sense to you
so that you can refer to it when you boot the Windows intall cd.

If you don't have the XP install cd, try to borrow one. If you
have Vista, they have a rescue iso that you can burn into a cd
which will let do the Recovery Console restore. You can find
it by doing a search on Google for: Neosmart  Vista  Recovery

---

### Post by CatKiller on 2008-11-15
> **Trevness said:**
> Hey, well...I really want to Remove Ubuntu because i really dont know how to install things and i read guides and i dont get it at ALL...

While I appreciate your frustration, how long have you been using Ubuntu? All new things take time to become familiar. Of all the things that are difficult in Ubuntu, software installation generally isn't. System -> Administration -> Synaptic Package Manager. Find the software you want to install, mark it for installation, hit Apply.

If you're trying to install some random thing off the Internet and the instructions there aren't clear, post the details to this forum and someone might be able to clarify them for you.

<EDIT>You appear to be trying to install Windows software in Linux. This won't work. Linux isn't Windows. It is possible to install Windows software in the pretend-Windows environment provided by Wine. Sometimes this works well (better than Windows) and sometimes it doesn't work at all. It would probably be easiest for you if you restricted yourself to installing Windows software in Windows and Linux software in Linux.</EDIT>

If you really cannot bring yourself to learn how to use Ubuntu, as has already been mentioned, it is straightforward to remove the Ubuntu partitions and give the free space to whichever other OS you have installed. You'll also need to replace the Ubuntu boot loader (GRUB) with whichever boot loader your other OS uses. If you are not confident about the process, and any data you which to keep is backed up, the most simple way to do so might be to just re-install your other OS.

---

