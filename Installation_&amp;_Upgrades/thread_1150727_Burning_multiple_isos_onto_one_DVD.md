---
title: "Burning multiple isos onto one DVD"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by octotom on 2009-05-06
I was wondering if it is possible to burn multiple iso files onto one DVD and then use those isos later to burn onto two separate DVDs.

I ask this because at the moment, I'm on a Windows computer that's not my own and I don't want to download programs onto it.  I want to give the newest Ubuntu and Kubuntu distrobutions a try and I thought that maybe I could download the files, burn them each onto a DVD and then when I'm back at my computer, I could burn them onto DVDs and run them live.

Thanks in advance!

---

### Post by dabl on 2009-05-06
Almost ...

YES, you can burn the Ubuntu and Kubuntu Live CD ISO files to a DVD -- no problem there.

But, when you've got your DVD at home, what you need to do is burn each ISO to its own _CD_ (not RW, not a DVD).  Make sure the md5sum on the ISO file remains unchanged, as per the download site, and burn it slow, at 4X, using DAO mode if your burning software has that.

There are reports of success burning the CD ISO image to a DVD, but that's not what they are designed to be, and it may not work for you doing it that way.

---

### Post by Topsiho on 2009-05-06
As far as I'm aware the .iso files are just ordinary files, which you can copy from one place to another, which I do quite often.

So you could download the separate .iso files and copy them onto a DVD, and later use that DVD to burn each .iso file AS AN IMAGE onto a CD, which CD's you can use to do the installs proper.

You can also, and far better, use one CD for the install, and after that install the other desktop with apt-get:

If you first install Ubuntu you can. in Ubuntu, also install Kubuntu by typing in a terminal:

sudo apt-get install kubuntu-desktop
and then enter your password when it is asked for.

After that you can choose whether you want to use the Gnome (Ubuntu) or the KDE (Kubuntu) desktop! You then have both Ubuntu AND Kubuntu.

Success.

Topsiho

---

### Post by Topsiho on 2009-05-06
Ah, Dabl was first :)

He says that you should not use a RW CD-Rom, but that is not quite true. I always use a RW (Read and Write), and almost never do not succeed in getting a good Live CD. I even do that at higher speeds such as 10 or 16 times.

That is much cheaper if you burn Live CD's every 6 months :), and here in Holland we have to pay unjust taxes buying CD-Roms ... as they can be used to put illegal stuff on.

His other advices are quite OK, though, and it's true that with an Write once CD the chance of success is greater.

Always check your CD's on errors ***in the computer on which you are going to install***, the Live CD's have an option to do that.

Topsiho

---

