---
title: "Just moved from Windows to Linux, need alot of help.."
date: 2008-09-21
forum: General Help
---

### Post by SuccessfulTroll on 2008-09-21
Ok, heres my dilema. I completely dont understand the file navigation system. When i click places>computer, my hard-drives are not shown, none of my things from windows are shown, ect. I have thousands of mp3s, videos, and other files I want to bring over to linux, although I understand a mass of conversions would need to take place to make them playable (alternatives, anyone?)
Also, Im completely addicted to Warcraft 3, is there any way I can bring my copy from Vista over to Linux directly, then reinstall it without a disk? Im guessing not, but just incase, I thought i would include it. All the files from Vista are still on the computer, along with the OS. 

...Halp?

---

### Post by bconover on 2008-09-21
> **SuccessfulTroll said:**
> ... I have thousands of mp3s, videos, and other files I want to bring over to linux, although I understand a mass of conversions would need to take place to make them playable (alternatives, anyone?)...

Ubuntu can play MP3 files just as well as Windows. Most video files, including WMV files, will play under Totem which comes with Ubuntu. I doubt if you will have to convert anything. If you have some really weird video file that the built-in player won't play, look up [VLC VideoLAN player](http://www.videolan.org/vlc/), a piece of software no computer is complete without.

You're main Hard Drive should be called "Filesystem". If thats not listed, then something is seriously wrong, as that's where Ubuntu is stored in the first place :) .

I don't know how Warcraft will run under something like WINE. Here's something you need to know: Linux is not Windows. You can't just run a Windows program under Linux. Some programs will work under WINE, but don't expect high graphical programs like games to run well.

I'm a little confused by your post; did you already install Ubuntu? Or are you running from a Live CD? You say Vista is still on your computer, did you set up a dual boot with Ubuntu and Vista?

---

### Post by bconover on 2008-09-21
[https://help.ubuntu.com/](https://help.ubuntu.com/)

A site with extensive documentation on using Ubuntu.

Definitely read the first one, it discusses the basics to learn when switching from Windows to Ubuntu.

---

### Post by SuccessfulTroll on 2008-09-21
Well, I havn't set up a live boot, I downloaded it ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)), and then selected ubuntu when my comp was starting.
And in Filesystem, I dont see any of my files from over on vista, Its a bit odd.

---

### Post by bconover on 2008-09-21
> **SuccessfulTroll said:**
> Well, I havn't set up a live boot, I downloaded it ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)), and then selected ubuntu when my comp was starting.
And in Filesystem, I dont see any of my files from over on vista, Its a bit odd.

Did you actually install Ubuntu? Or did you just insert the CD/DVD and boot from that? If you're running it from the CD, the file system won't be set up yet, so I don't know what will work (never used the Live CD).

---

### Post by SuccessfulTroll on 2008-09-21
Actually installed it

---

### Post by bconover on 2008-09-21
> **SuccessfulTroll said:**
> Actually installed it

Did you make sure to partition the drive? Otherwise, you're files are gone :shock:

---

### Post by SuccessfulTroll on 2008-09-21
I didnt, but if im at the menu pre-startup, I can select windows, and they are all there

---

### Post by SuccessfulTroll on 2008-09-21
Maybe it has something to do with Ubuntu being installed on my secondary hard drive?

---

### Post by bconover on 2008-09-21
> **SuccessfulTroll said:**
> I didnt, but if im at the menu pre-startup, I can select windows, and they are all there

Sounds like you did partition it... thus a dual boot is set up, which means both Ubuntu and Windows are on your computer. Unfortunately, I have zero experience in dual-booting Ubuntu, so I probably won't be too much help in this matter. From what I do know, I believe that when your hard drive is partitioned for a dual boot, it is split into two separate "drives". One is formatted for Linux, the other for Windows. How to access the Windows drive from within Linux, I don't know. Sorry :-( Good Luck solving this.

---

### Post by bconover on 2008-09-21
> **SuccessfulTroll said:**
> Maybe it has something to do with Ubuntu being installed on my secondary hard drive?

Are there any other things listed under Places -> Computer besides Filesystem?

---

### Post by SuccessfulTroll on 2008-09-21
cd-rw drive, hp, recovery, usp drive x4

---

### Post by pommattski on 2008-09-21
What happens when you open the 'place' called 'hp'?
Is that not your Windows partition?

---

### Post by TeXtonyx on 2008-09-21
If you go for the automatic configuration, install ntfs-config. It will automaticly install ntfs-3g :
Code:

sudo apt-get install ntfs-config

Now, it's rather easy. Just launch ntfs-config via the menu (in system tools) or via the terminal :
Code:

gksu ntfs-config

This will mount your windows partition (NTFS file system) so that you
can read and write files to it. It will put an icon on your desktop.

---

### Post by Gdschaf on 2008-09-21
i dual boot vista and ubuntu with a program caleld wubi, love it!
a way to access ur files from vista if they are both on the same hard drive is computer > filesystem > host
if its on a different hard drive it should show up under computer 
i my self used to dual boot off one hard drive but ended up buying an external hard drive i can carry around to all my computers i have wubi installed on and get all my stuff (including school :-)) 
as for warcraft 3, im pretty sure u'll need to reinstall that with the disk which im not positive how to do with wine, i've tried to install spore but no luck, i think u can run it from ur host hard drive by typing in 
```
wine host/program files/warcraft 3/warcraft3.exe
```
im not positive on that though cuz i don't know where warcraft installs
if u havn't noticed :-/
and ur gonna have to download and install wine before u type that in if u havn't already

---

### Post by SuccessfulTroll on 2008-09-22
It didnt put an icon on my desktop. Still having the same problems :(

---

### Post by enchesss on 2008-09-22
your windows partition looks like it has been named hp - probably for hewlett packard?
Open it by double clicking
depending on how it has been installed (by you or the factory) the files should look like a normal windows directory. eg documents and setting/user/my documents etc...

---

