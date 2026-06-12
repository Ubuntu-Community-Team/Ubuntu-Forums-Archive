---
title: "Installation issue"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by Kochon on 2009-05-19
Hey guys, I have a few issues with Ubuntu, but first let me give the context:

I had a Dual-boot setup with XP SP3 x86 and Vista x64 and everything was fine, I modified the vista bootloader with EasyBCD.

Then I had this great idea to try back Ubuntu which I had already tried and liked in the past, on a VM.

Triple boot, no problem, right? Well, not exactly. As I was installating Ubuntu, it detected my Vista installation and asked me if I wanted to install it with it, using the GRUB bootloader. I clicked Yes.

So Here are My Problems:

[LIST]
[*]First, I totally hate the GRUB bootloader and would like to switch back to vista's and create an entry for Ubuntu. Problem is, I have no clue how, and It seems ubuntu installed itself on the same partition as Vista, 'cause there is no new partition.
[*]Second, I can't install or download anything using Ubuntu, it says that there's no space available. Problem is kind of the same as above, as I can't see the partition at all, so how should I extend it?
[/LIST]
And hmm, as a last kind of question, I noticed Ubuntu is kind of all about free and open source stuff, but hey, I like my mp3's. I heard of Automatix, which seemed to install a lot of codecs and stuff, but the website is dead, so any suggestion?

---

### Post by zvacet on 2009-05-20
If you don't see new partition then maybe you installed Ubuntu inside windows(Wubi install).If that is what you did delete Ubuntu like every other app form Windows and shrink one of windowspartition and on unallocated space install Ubuntu.For condecs type in terminal

```
sudo apt-get install ubuntu-restricted-extras
```

and add [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") to your source list.

---

### Post by Kochon on 2009-05-20
Thanks for the reply, but I cannot see Ubuntu in the Programs and Features menu from Vista. And thanks a lot for the source and command!

---

### Post by Kochon on 2009-05-20
Sorry for the double posting but... up.

---

### Post by lisati on 2009-05-20
> **Kochon said:**
> Thanks for the reply, but I cannot see Ubuntu in the Programs and Features menu from Vista. And thanks a lot for the source and command!

If you used the option to install "within Windows" (many of us refer to it as "Wubi" after one of the programs used to do so) there should be a folder on the Windows partition. It's usually called something like c:\ubuntu  If there is such a folder my knowledge of how to modify the Windows boot process isn't up to the task of advising you how to proceed. Someone else might be provide pointers.

A "regular" install sets up Ubuntu in it's own partition which won't normally be accessible within Windows. If you have a "Live CD" to boot from, there are options for finding where Ubuntu lives on your system.

EDIT: if you did a "regular" install of Ubuntu there probably won't be a folder for it within Windows

---

### Post by Kochon on 2009-05-20
I just discovered something. Indeed, the Ubuntu partition won't be seen by Windows. But by booting from the latest GParted Live CD, I found out that I have indeed a new partition for Ubuntu, with the Linux swap and stuff. I will try to resize my Vista partition and take the new space for Ubuntu and give you news on that.

---

### Post by zvacet on 2009-05-21
If you want your Windows partition to seee Ubuntu install [fs driver.]("http://www.fs-driver.org/")

---

### Post by albinootje on 2009-05-21
> **Kochon said:**
> 
I totally hate the GRUB bootloader 

Why ? Did you try Startup Manager to handle the Grub configuration ?
> 
and would like to switch back to vista's and create an entry for Ubuntu.

I think you might expect too much from Microsoft. 
I would be very surprised to see the first Microsoft bootloader in more than 20 years time which can actually boot anything else than Microsoft products.
> 
And hmm, as a last kind of question, I noticed Ubuntu is kind of all about free and open source stuff, but hey, I like my mp3's. I heard of Automatix, which seemed to install a lot of codecs and stuff, but the website is dead, so any suggestion?

Read this :
[http://www.medibuntu.org/](http://www.medibuntu.org/)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Kochon on 2009-05-21
Yeah, thanks guys. When I tried to resize the partitions, **** happened, so I had to completely make a fresh install on Ubuntu after having backed up my stuff. Now I'd like to install Vista, too. Do I just resize and install Vista? Won't it overwrite the bootloader?

And btw, it is indeed possible to boot Linux and OsX operating systems from Vista by using EasyBCD, a bootloader manager, free of charge.

---

### Post by Kochon on 2009-05-21
Up, up goes the thread. Anyone?
> Yeah, thanks guys. When I tried to resize the partitions, **** happened, so I had to completely make a fresh install on Ubuntu after having backed up my stuff. Now I'd like to install Vista, too. Do I just resize and install Vista? Won't it overwrite the bootloader?

And btw, it is indeed possible to boot Linux and OsX operating systems from Vista by using EasyBCD, a bootloader manager, free of charge.

---

### Post by zvacet on 2009-05-23
> And btw, it is indeed possible to boot Linux and OsX operating systems from Vista by using EasyBCD, a bootloader manager, free of charge.

I believe that you think of some Hackintosh version.Piracy is not supported here.

---

### Post by Kochon on 2009-05-23
I never talked about piracy, but meh, I found out how on my own, thanks anyways.

---

