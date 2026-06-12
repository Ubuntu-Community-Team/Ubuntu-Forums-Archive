---
title: "Alternate install CD?"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by manoka on 2008-12-08
Hello,
What is an alternate install CD, where can I get one and can't I do an upgrade with a regular Install CD Desktop Edition without losing my applications and files?
Kind regards
manoka

---

### Post by Kobalt on 2008-12-08
The Alternate install CD lets you install Ubuntu in a graphical mode but not a Live session. It offers multiple install options (server, OEM, etc.) and it can be used as an upgrade support for an existing Ubuntu install (whereas the Ubuntu desktop CD, aka Live CD, doesn't offer this option).

---

### Post by Drostie on 2008-12-08
You can upgrade a version of Ubuntu without losing apps and files without using a CD.

Details here:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by manoka on 2008-12-08
Thanks Kobalt and Drostie,
As I did an upgrade from 7.04 to 7.10 via an online download which left me with an OS that doesn't work very well, I would like to upgrade but this time with a clean install using an Install CD Desktop Edition or whatever will be suitable to do so.
I wonder whether I can save the downloaded applications software and use it with the newly installed OS, and if yes, how.
I.e. I'm looking for informations about how to save my files and applications, and how to make them available again, respectively how to connect them with the new OS after the installation.
I have two hard drives, so I would prefer to use one just for the OS and the applications, and the other for the files.
Any detailed step by step help would be very much appreciated by a newbie.
Actually I thought there were only two types of Ubuntu CD's: A Live CD and an Install CD, respectively when I ordered an Install CD, there was only a Server CD as another option.

---

### Post by snkiz on 2008-12-08
what is the state of your current setup? You said you have 2 harddrives, how are they partitioned?

---

### Post by manoka on 2008-12-08
Thanks snkiz,
I have everything on a 20 GB harddrive. On the other, a 320 GB harddrive I have only some data or software which remained from the previously, but no longer used Windows XP - which BTW I don't seem to be able to delete (when I try to do so, I'm getting a message which says that I have no rights for this action).

---

### Post by Drostie on 2008-12-08
If Ubuntu ever tells you that you don't have the right rights, you can usually *sudo* around it on the command line.

The easiest scenario right now is if all of your /home folder is on a separate partition from the rest of your files. (If you don't yet know what a 'partition' is, then you're in a bit of trouble right now anyway, since hard drive partitioning is fundamental to what you want to do.) 

Good applications should store most of your personalized settings in your /home folder, but there may also be a bunch of config files in the /etc folder, which is kind of like "C:\Program Files" was to Windows XP, but without the executable files or software libraries. So, for example, if you're running Apache Server on an Ubuntu Desktop version (which I believe is against recommendations, but whatever) then its settings are stored in /etc/apache, and you might want to back those up.

Okay, so I've outlined the task for you: get your /home and /etc directories and separate them from the rest of the disk. There are many ways to do this: USB drives, optical media, sending them over a local ethernet connection to another computer you own, et cetera. If you don't have those, but you're reasonably technically minded, you can install GParted from the repositories and try to create a new partition that you can use. (I don't remember whether GParted lets you resize partitions that have a lot of free space, but if it does, then that would be my first inclination.)

*Important: If you use GParted, or any partition editor, under *no* circumstances should you delete a partition that has something useful on it. It is a Bad Idea, and you might not be able to recover from it.*

Let's assume, then, that you get your config files copied nicely to another drive. On this other drive, you should also put [a list of installed packages]("http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/"). Follow that link, read the commands, and use them.

Then, you've got all of the building blocks. Install fresh, then reinstall your packages (see the above link), then put your /home and /etc configuration files back into place, overwriting as you need to.

Subtleties: You should probably do your copying from the command line, with sudo commands, and you should make sure that you also copy the hidden files that start with periods.

If your /home and /etc files are already on separate partitions, then all of the hard work should already be done for you. Format the system partition and install Ubuntu to it, while keeping your other partitions unmodified. Hopefully the dpkg tool is smart enough to not overwrite your preexisting config files with the defaults, though I would want to check its man page just to be sure.

---

### Post by Drostie on 2008-12-08
Oh, also: 

(1) Use the normal CD, not the alternate install CD. The alternate installer is text based, which isn't very easy on the eyes. Also, (and this is much more important) the normal CD lets you boot into Ubuntu without making any changes to your system. That doesn't sound very important, but it means that you can run Ubuntu even if something goes very wrong -- which means that, if you run into a problem, you can use the CD to come back here and ask for more help. This might make a huge difference; you never know.

(2) When you move to install, if you're using a partition to hold your files, do not use "automatic" or "guided" partitioning. Do it manually, so that you're sure that your important files don't get overwritten.

(3) In your particular case, you might want to just install Ubuntu to your 320 GB drive (thereby wiping everything else on it) and leave your 20GB drives alone, then worry about migrating everything else once you're done. In this case, you can possibly use guided partitioning if you use GParted to delete the Windows partition on the 320 GB disk, and you just leave it as free space. The install CD should install to the place with the most free space. Just to be safe, you  might want to be a little paranoid: for example, you might want to unplug the 20 GB drive from your computer before you even run the Ubuntu installer. You will have to edit your BIOS settings later, to make sure that it boots from the 320 GB hard drive and not the 20 GB hard drive.

---

### Post by manoka on 2008-12-09
Many thanks Drostie for your extensive response.
Unfortunately I'm too much of a newbie to understand all of your instructions, as well as the instructions of the link which you indicated.
I guess I'll have to try to upgrade via the Update Manager instead. Hopefully this time it will work better than last time, when, I believe, I did the upgrade another way.

---

### Post by snkiz on 2008-12-10
Drostie stole my thunder lol. Thats pretty much what I was going to say to do. But a note, be sure when you add your users back in your new system that they have the same user names AND UID's os the old ones, that's a horrible mess to figure out.

---

