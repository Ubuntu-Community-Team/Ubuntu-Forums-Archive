---
title: "How do I copy my Windows files while in Ubuntu?"
date: 2012-02-17
forum: Hardware
---

### Post by computers101 on 2012-02-17
Hi. I am very new to Ubuntu and I have a question on copying windows files. First, though, I have to say that I really enjoy using Ubuntu (in trial mode at the moment) and the community here has been great. 

A Windows issue actually led me to discover Ubuntu and I'm hoping that with system's help I can recover my Windows files. 

Right now I can see my files in Ubuntu. It says 389 GB at the top of the left menu. My question today has to do with retrieving those files and getting them to work with Windows again after I restore my laptop. 

I have a new external hard drive that I'd like to copy these files to.

If would be great if someone could tell me what I need to do or direct me to a resource that outlines the steps. I searched through the forum a few times but couldn't quite find what I was looking for.

Any thoughts or ideas would be very helpful.

Thanks.

---

### Post by winh8r on 2012-02-17
You can just plug in an external disk drive (HDD) and drag them across from the internal hard drive to the external.

I am assuming that you are referring to your personal files like documents , pictures, music etc. ?

---

### Post by computers101 on 2012-02-17
Hi. You're right, its files like pictures, documents and movies. It would be great if my applications like skype, utility programs, etc were there but I'd settle for just the personal files.

I'll try and move the files. I was thinking I needed to do something to the drive first, and also that I would run into difficulty with the Ubuntu copied files when trying to have windows open them.

What do you think?

---

### Post by Apanta on 2012-02-17
Hi.
The way is the same used for win:

Open the folder where Win files are and select them.
Clic on right button of the mouse and select copy ---  then open the storage folder where you like to put these files and new clic on right button of the mouse --- paste.

If I understood well,  this is all.
Ciao  :D
Apanta

---

### Post by ahallubuntu on 2012-02-17
Yes, open a Nautilus (file browser) windows and navigate to your files on your Windows hard drive.  In XP they are mostly under /Documents and Settings/YOURNAME .  In Vista or Windows 7 they're under /Users/YOURNAME .

Then either open a new Nautilus window and navigate to your external hard drive and drag-and-drop the files from one window to another...or in the first Window, right-click over the folder(s) you wish to copy and choose "Copy" and then navigate to your External drive and do "Paste."

The copy may take a very long time if it's really 389 GB!!

---

### Post by computers101 on 2012-02-17
Thanks. I'll try these steps.

Yeah, the data is really that large. I think a ton of it has to do with the fact I made an extra copy of my data from another computer once and just left it there.

Thank God it's the weekend. Hopefully plenty of time to copy files :)

*now copying. Only 6 hours left :)

---

### Post by ahallubuntu on 2012-02-17
Ubuntu won't change the files when it copies them.  If you don't open them with any program (like LibreOffice) and edit them, then you won't have any trouble reading/using them again in Windows.

What exactly are you trying to do, though?  What problem are you trying to solve by doing this?  There may be a much more efficient way to preserve your programs and get Windows running again.   You can't merely copy your installed programs over FYI and expect to use them again automatically if you install Windows again.  You'll have to re-install the programs all over again.

If you have some major Windows software issue, you could try doing a "repair installation" of Windows which would preserve all of your installed programs but you'd have to re-install all the updates and service packs again.  Of course, doing the backup of all your documents/pictures/files to the external drive FIRST is a *WISE* idea!

I encourage you to use Ubuntu in the future, but if you will continue to use Windows in some capacity, look into something called "image backups" to allow for better Windows backups (when you have a clean installation working again) that can be restored pretty easily.

---

### Post by computers101 on 2012-02-17
Thanks. I think I plan download and reinstall most of my programs again, and its things like MS Word documents that I want to make sure I can read again.

"Image backups" are new to me. Thanks for mentioning this. I really think I'd like to use Ubuntu from now on, but we'll see. I just need to get past a few challenges. For example, my wireless mouse now doesn't work with my trial mode of Ubuntu...

I can see what you mean about easier ways to save data. It's just that I'd pretty much tried everything, including tech support with a Sony. My issue is that I have black screen with a blinking cursor. Just about all "F" functions/keys by default go the recovery center utility by Sony and when it tries to recover the data an error occurs in the process and shuts down. Western Digital says its a software issue.

But the process here sounds pretty straight forward. I'll be sure to come back and post how it goes.

---

### Post by ahallubuntu on 2012-02-17
For image backups, I recommend a free Windows program called True Image, made by a company called Acronis.  FYI, they offer a free version of True Image for Western Digital drive owners.  Go to Western Digital's website to find it and download.  I use it as a bootable CD so I can make images of Windows (and Linux) partitions for backup or copying.  It's very handy to make an exact snapshot of a partition - the ultimate "undo" for not just documents and pictures but programs and the operating system.

You can make image backups with Linux, too, but True Image is a very easy-to-use program I've been using for years.

In your situation, backing up is the first thing I'd try - but then I'd do these things to try to assess your situation:

1. Check the hard drive health.  I'd check the S.M.A.R.T. status of the drive and run tests.  The Utlimate Boot CD (google for it) contains some nifty utilities for testing hardware.  One of them is called Parted Magic, and you can boot into that (it's Linux-bassed) and run SmartControl to see if any S.M.A.R.T. attributes from the drive have flagged as errors (they would be highlighted in pink).  If the drive has some pending sectors or something, don't even bother trying to re-install Windows.

2. If hard drive health seems OK: find a Windows bootable disc  and run chkdsk on the Windows partition.  Also, if you have the same Windows version on disc (say a Windows XP CD for an XP install), you can do "fixmbr" to try to fix a boot sector corruption.

Either of those two things could fix your problem.  If not,

3. Try a "repair installation" with said Windows disc.  Just boot the disk and begin the process of installing Windows...but hope it offers to repair your existing installation.  If so, do that - and you can avoid having to re-install everything from scratch and maybe save yourself a lot of time.

---

### Post by computers101 on 2012-02-17
Hi. True image sounds great. I'll try to get that on my desktop pc today. I appreciate the heads up on Western Digital.

I was able to do a diagnostics test with Sony's Recovery Center, the utility that can perform system restore and backup. Everything checked out fine, though I don't know too much about what it does.

One thing with Sony is that at some point they stopped including disks with their systems. This may have changed but I have a 2009 Vista laptop.  

There is a program in place in my SONY system where you can make your own recovery CD's. My bad here because I never made one. However, the backup utility isn't working for me so it might not have helped.

Thanks for helping. I'll be heading to Western Digital's site now...

---

### Post by ahallubuntu on 2012-02-17
True Image is something you can use in the future when your Windows installation is fixed.  If you are able to create a rescue/bootable CD from the Western Digital version of True Image, then you could use that CD right now to create a backup copy of your whole C: (corrupted as it is, but including everything).  In your present situation, I'd still probably proceed with your first idea and just backup all your files to start with, if you HAVE no current backup...

If you can obtain a "generic" (or a Dell) Windows Vista Install CD, you can try to use it to repair your Sony system.  If you need to repair it, you can use the MS product key code on the bottom of your Sony.  However, you will need to have the same type of Vista CD - if it's Vista Home Basic, don't try to use a Vista Ultimate CD to do the "repair installation," though you can do chkdsk and "bootrec.exe /fixmbr" both from a command prompt from any Vista CD, to see if either would repair your computer.

---

### Post by computers101 on 2012-02-17
Thanks. That's actually what I had in mind - to use it in the future, once I restore all my files. I now have the True Image .exe file on my desktop via Western Digital. It says I need to have my external WD drive connected to install it so actually installing it might have to wait until tomorrow because Ubuntu is copying my windows files on there now.

In the Sony Recovery Center utility it does have the option to restore the system. I'm hoping this will work. The Rescue Data option didn't but that was to try to backup my data. Hopefully a system restore, or C Drive restore will get things running right again.

I didn't realize that windows disks, if done properly, can be used in certain ways with other systems. Thanks for mentioning this. I may have to look into using one or two of those tasks but I won't know until tomorrow. It's great to have this knowledge.

Thanks again. I appreciate your help. I think I'm on the right track...

---

