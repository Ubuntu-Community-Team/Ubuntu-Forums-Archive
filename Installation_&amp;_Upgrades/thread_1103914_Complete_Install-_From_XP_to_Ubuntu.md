---
title: "Complete Install- From XP to Ubuntu"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by PK1990 on 2009-03-23
Hey guys, brand new here.

I have decided to get Ubuntu (Finally) and install onto 1 of my laptops. Windows XP is currently installed, but I want to install Ubuntu completely. By this, I mean wipe XP out of existence (No dual boot) and completely re-vitalise my laptop with Ubuntu.

Initially, I think I will backup anything I want to keep (Music files, work, etc) onto an external hard-drive I have my eyes on at the moment (FAT32 format). 

What I would like to know, is how this will work? I have read through the guides to downloading the ISO image and burning to a disk, and I have come up with some questions.

1. Can I burn the ISO image to a DVD-R, and will it work just the same as a CD-R? Will I be able to install Ubuntu from a DVD-R?

2. When using the live CD, if I choose to "Install" Ubuntu, it wipes the hard drive clean right? (This is what I want to do)

3. Like above, I want to start completely fresh with my laptop, get rid of all things windows and install Ubuntu completely.

4. When transferring my files back from the FAT32 external hard drive, will Ubuntu recognise the device instantly and use it as if it was a USB flash drive?

I know it's a lot of questions, but I am a noob at  Ubuntu, and I thought I would get some things cleared up before I did anything. 

Thanks guys.

P.S - I have another laptop with XP on too, so once Ubuntu is installed on one, I will still have access to windows.

---

### Post by Partyboi2 on 2009-03-23
Hi, welcome to the ubutu forums.
> 1. Can I burn the ISO image to a DVD-R, and will it work just the same as a CD-R? Will I be able to install Ubuntu from a DVD-R?Yes
> 2. When using the live CD, if I choose to "Install" Ubuntu, it wipes the hard drive clean right? (This is what I want to do) When you get to the partitioning stage it will give you the option to install Ubuntu to the entire disk.
> 4. When transferring my files back from the FAT32 external hard drive, will Ubuntu recognise the device instantly and use it as if it was a USB flash drive?
Yes Ubuntu can read/write fat as well as ntfs.

---

### Post by Moop on 2009-03-23
You can burn the image to a dvd and it will work fine. 

Choosing install from the live cd gives you the option to use the whole disk and will wipe XP if that's what you want. 

Ubuntu should recognize your external drive but you can always test that using the live cd. 

You don't need to copy stuff to a fat32 partition. Ubuntu can read from a ntfs (windows) partition.

---

### Post by PK1990 on 2009-03-23
Ok, thanks a lot guys. 

I haven't bought the external hard drive yet (Obviously, I just needed to get some things cleared up before hand), and yes, I want to completely clean windows off, so a complete install is just what I wanted!

By the sounds of it, it should be a pretty simple procedure(Considering I am doing a complete install). Being a Linux noob, I expected it to be a long winded process. 

Anyway, thanks for the quick replies.

---

### Post by PK1990 on 2009-03-23
Another quick question.

What is Ubuntu like when it comes to wireless, does it have problems with certain wireless adapters (Certain makes) or will it pick it up and connect to the internet as normal?

I ask, because I remember reading somewhere else about possible issues such as this. 

P.s- My laptops wireless adapter (I think) is an "**Atheros AR5005G**"

---

### Post by Liviu-Theodor on 2009-03-23
I don't have much experience with the wireless but from what I read in the forum, ubuntu can use wireless, sometimes out-of-the-box, sometimes using ndiwswrapper. But usually Ubuntu 8.10 works fine, also the Intel adapters.

---

### Post by PK1990 on 2009-03-23
Ok, well that's good news then. The only real way to find out though is to just try it I suppose. 

Hopefully then, by the end of the week I should have Ubuntu. 
(Will have to wait on external hard drive to be delivered)

Thanks everyone for the replies, they really helped. Will officially join you with Ubuntu soon. ;)

EDIT*
Well, as of now, I downloaded the Ubuntu ISO file, checked the MD5Sums and burned to a DVD. I'm all ready to go as soon as my external hard drive comes in a few days.

But I was reading up on Ubuntu, and came across the whole KDE/GNOME thing. Ubuntu starts in GNOME from the get go right? Are they really that different from one another?

---

### Post by oldrocker99 on 2009-03-23
Here is how to install Atheros drivers:

[http://ubuntuforums.org/showthread.php?t=1024443&highlight=toshiba+l305d-s5895](http://ubuntuforums.org/showthread.php?t=1024443&highlight=toshiba+l305d-s5895)

That should work. 

KDE and GNOME are pretty different from each other, especially KDE 4.1, which even Linus Torvalds has eschewed in favor of GNOME. I tried KDE 4.1 and just didn't like it. KDE 3 had a lot to like about it, but the new version...meh.

:guitar:

---

### Post by PK1990 on 2009-03-23
> **oldrocker99 said:**
> Here is how to install Atheros drivers:

[http://ubuntuforums.org/showthread.php?t=1024443&highlight=toshiba+l305d-s5895](http://ubuntuforums.org/showthread.php?t=1024443&highlight=toshiba+l305d-s5895)

That should work. 

KDE and GNOME are pretty different from each other, especially KDE 4.1, which even Linus Torvalds has eschewed in favor of GNOME. I tried KDE 4.1 and just didn't like it. KDE 3 had a lot to like about it, but the new version...meh.

:guitar:

Ok cool, at least I know where to go if I need it, because if Ubuntu is gonna take issue with something, it's most likely going to be my wireless! Cheers anyway.

Also, I know a a bit more about GNOME than KDE (And there are some seriously cool eyecandy from GNOME-Look.org)and from the comparisons I've read, GNOME looks more simplyfied and easier to use for a newbie like me.

---

### Post by PK1990 on 2009-03-24
Ok, well after using the Live CD of Intrepid Ibex (I was amazed I actually did it right)I realised that there were maybe some issues with my sound. 

I noticed this whilst playing with Rythmbox, I tried to play the sample music from the Live CD, but it just wouldn't play? Not only that, but I don't think there was sound at all during my use with the Live CD. Ok, that could have been down to me leaving my laptops volume all the way down in the first place, but the music wouldn't even play in rythmbox, the playback bar just didn't move? 

The strange thing is, I had this sort of problem with itunes on my windows laptop, if I unplugged my speakers while itunes was still running, it refused to play any music.

Even though this is strange, I'm glad the rest of the Live CD worked. However, once I fully install Ubuntu, I can see whether the problem still persists, as it may just be something to do with the Live CD. 

Anyone experience anything similar?

---

### Post by rambocommando on 2009-03-24
You might want to check the available sound devices under System->Preferences->Sound. You can also test the audio playback from there as well.

---

### Post by Az4x4Taco on 2009-03-24
My guess (and it's only a guess) is that the laptop you're going to install Ubuntu on is not one you're using as a main machine, but one you're trying to get additional value and use out of while moving away from the problems and issues that a reinstall of Windows would bring with it.  If that's the case then all I can tell you is that Ubuntu is an excellent choice as far as a Linux OS is concerned, and it may well be the best choice in many regards.  

The Gnome version of Ubuntu, as you are aware, is far and away the most popular Linux desktop OS in use world wide. Obviously there's good reason for its overwhelming popularity, and whatever you may encounter as far as hardware issues are concerned as you finalize your Ubuntu installation, there will be any number of Ubuntu users available to you on these forums to help solve such issues - including the lack of sound glitch you're experiencing.  All I would suggest is that you not let minor issues deter you, but that you carry through with your planned installation to the point of solving such issues, giving the full potential and power of Ubuntu the opportunity to forever change and enhance your desktop user experience!

---

### Post by PK1990 on 2009-03-24
> **Az4x4Taco said:**
> My guess (and it's only a guess) is that the laptop you're going to install Ubuntu on is not one you're using as a main machine, but one you're trying to get additional value and use out of while moving away from the problems and issues that a reinstall of Windows would bring with it.  If that's the case then all I can tell you is that Ubuntu is an excellent choice as far as a Linux OS is concerned, and it may well be the best choice in many regards.  

The Gnome version of Ubuntu, as you are aware, is far and away the most popular Linux desktop OS in use world wide. Obviously there's good reason for its overwhelming popularity, and whatever you may encounter as far as hardware issues are concerned as you finalize your Ubuntu installation, there will be any number of Ubuntu users available to you on these forums to help solve such issues - including the lack of sound glitch you're experiencing.  All I would suggest is that you not let minor issues deter you, but that you carry through with your planned installation to the point of solving such issues, giving the full potential and power of Ubuntu the opportunity to forever change and enhance your desktop user experience!

I really do intend to "power through" any issues dude, because this is a great learning experience for me. At the moment I am constantly learning more and more about computers, as I am doing a HND in software development.

But more importantly, I have always wanted to try Linux, but never had the chance. Now I can. 

By the way, I have yet to fully install, but using the Live CD completely wowed me. All I have known is Windows, and there is just something about Ubuntu that makes it seem oh so perfect!:D

I also really appreciate all the help the forum has given me so far.;)

EDIT*
Ok, I have just tried the tips about the sound, and I have chosen the Pulse audio one, and the test works out fine and also Rythmbox now plays the music. However, the sound is very choppy and disjointed, but I expect it's because it's running off the Live CD. Anyway, at least it actually works.

Although, when I selected the "Play sound effects when buttons are clicked" option, I don't think it's playing any of the sounds when I do anything. I have read this problem somewhere else in the forums. To be honest, there isn't a lot I can do now, because I obviously haven't properly installed it yet and am only running off the Live CD, but I'm just trying to anticipate any problems I may encounter later on!

---

