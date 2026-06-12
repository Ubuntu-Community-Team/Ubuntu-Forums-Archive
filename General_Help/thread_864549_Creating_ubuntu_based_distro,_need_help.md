---
title: "Creating ubuntu based distro, need help"
date: 2008-07-19
forum: General Help
---

### Post by Separ on 2008-07-19
Hi all!

I am wanting to create my own distro based on ubuntu but with different packages installed by default. I have a small clue of how to do it (I downloaded remastersys) but as far as I can see, you need a fresh install with everything you want to create it.

Also I would like to use the existing ubuntu repositories because 1) They are awesome and 2) I have no space to host that many files. Would I be allowed to do this?

Is there anything that I can get without having to reinstall ubuntu on another partition?

I would also like to use an equivalent thing of the 8.04 Live CD that has the capability for a Wubi install in Windows.

Thanks!

Separ

PS: Forgive me if this is in the wrong forum :D

---

### Post by DagMan on 2008-07-19
I'm really haven't used wubi, put it on a CD that I've made, etc.  I usually remove it because it frees up a lot of room to fit more things on a CD.  At the same time, you can install on a DVD all the same and put heaps of stuff on it.  Either way, as far as my help goes, I have zero experience with wubi, and saying that it's best to get that answered as well is an understatement.

As for a custom install CD.  You can either start from scratch and build everything up or you can start with the contents of a CD or just the downloaded image file.  A breif overview is that you have a folder on your hard drive, in your home directory for example, that you copy the install CD into, or put the very basic tools in to start building up the install, and chroot into it, which means you're running kernel will drive the contents of that folder as if it was it's own install.  After that, you can either try to turn the CD into an install disk... I've had this work well in feisty but it failed for me in hardy though I didn't bother to troubleshoot... or you can look at the remastersys tool and see if it is capable of running at the command line, in which case running it inside of the chroot would work just fine.  Wubi seems like it would be an entirley differant thing to get running.

Here's the wiki page on customizing a live cd from an existing one or an existing cd image file [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
Don't be shy with it, you can test the result in virtualbox or qemu so it doesn't matter if you screw it up 40 times.  

This thread where it explains the manual method of making a live cd from the hard drive [http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872) also explains the process of using debbootstrap to go from a bare bones directory to all of your specific applications, though I find it's much easier to use a normal install cd or your hard drive files, update and upgrade once inside the chroot. and then remove unwanted things as is explained in the wiki page.

I think everything is best described in the wiki page, and it really sounds like greek at first but because much easier.  The key things to note is to follow it to the letter... but the important things will be copying things over before entering the chroot like copying your /etc/act directory over to replace the one in the chroot, copying over /etc/resolv.conf from your computer to the chroot.  Without that you won't have networking or the repos you want while you try to install files. I don't think the wiki mentions the /apt folder.  You also need to make sure you follow the part about mounting some things, /proc /dev and whatever else it tells you to.  Once you begin in the chroot, do an apt-get update, apt-get upgrade, and apt-get clean.  Do an apt-get clean when you are finished customizing, make sure you have the same kernel version in the chroot as the one you are running on your computer at the time, and be sure to follow the step where it says to update the initramfs or initd.gz file or whatnot... the implication in the wiki was that it might not always be necisarry but it usually will be when your doing a fair bit of customizing.  Your compressed image on a DVD can't go over 2 gigs, but that's obviously quite a lot compared to 700 megs on a CD.  My entire install of ubuntu-desktop plus all the ubuntu-studio packages plus everything else I'd installed was less than 2 gigs on a DVD.

Good luck and my best advice is just not to give up.  It seems very daunting at first but can actually become a bit easy given some time.

---

### Post by Separ on 2008-07-19
What can I say. WOW!

Thanks VERY much DagMan. I shall look into the links there.

Can you explain chroot tho or should i just do a "man chroot"?

---

### Post by DagMan on 2008-07-19
It means like "change root" or "change the loation of / "
so if you chroot into a folder, then in the terminal you do it from your root or / becomes the folder, and inside it you might have your normal linux fileystem, /boot /usr /etc . So if you have a linux filesystem in there you can chroot into it and run it as if it were its own intall.  You don't have access to your normal files outside of the chroot though, and to copy something in you would need to open a differant terminal and copy it into the folder.
Unless you can work out a way to attach to the display outside of the chroot though, you are pretty much there at the command line when you are there.  It is possible to run gui apps like that but it's a real pain to set up and I wouldn't be able to help with it personally.  To be clear, since this might be confusing right now, once you've created your install disk, your'e no longer in the chroot, so everything should run fine in the normal display.

---

### Post by Separ on 2008-07-19
Ah ok, thanks. :)

---

### Post by Separ on 2008-07-19
Ok, I've managed to get an iso built and it works. Now what I want is to have the default username and /home folder to be a different name than "ubuntu". I still have the folders + files (cd + work) from the debootstrap guide.

Also how do I give it a custom GTK theme and icon theme instead of the dreary default one?

EDIT: Ended up deleting the 2 folders since when I made a new ISO, it kicked me out to a busybox ash shell on boot inside my VM. Was there any way to use the 2 folders just to add stuff without me having to go and do it all over again?

---

### Post by DagMan on 2008-07-20
If you have the iso or the disk that you made, then you can use that, just have to mount the iso (unless you use the cd then this isn'nt needed)then mount the squashfs inside the iso, then copy the files into a new folder, and you'lle have the chroot directory that you built.

I really don't know about the customization.  I remember there being a brief mention of where things are in Live CD.  Icons and whatnot are usually stored in ~/.themes and ~/.icons and a lot of things are stored in ~/.gconf and maybe also ~/.gconfd but what else you'de want I'm not sure.  Perhaps copying your settings over to the appropriate location in the CD that creates the ubuntu account would work.  When I did something similar before I set things up the way I liked them in the live cd and copied them to a folder in in the home directory of the chroot then edited the chroot gdm script in /etc/init.d so that the first thing it does is move the folder I made to /home/ubuntu and the desktop appearance was how I wanted it.  Spin specifically, I had gdm remove the /home/ubuntu folder, move my folder in as /home/ubuntu, and then continue on doing what gdm does.  It's easier to do this from the Live CD because you know you've used the correct uid gid and file permissions for everything in order for it to work. 

As for the name of the account itself, I don't know how to do that.

Did the image not work in the VM btw?  I found that a problem last time when I tried it with hardy for the same reason you stated getting kicked out at a shell before boot was finished, but using remastersys did work which is why I suggested using it at the command line inside the chroot.  The man page suggests it can be run like that, however it's not clear about what the result is using the option that looks like it might be the one to use.
One problem I did have with remastersys though, is that it didn't let me use custom partitioning.  The installer would hang if I tried to.  It still served it's purpose at the time though and I did install with it.

---

### Post by Separ on 2008-07-20
The first ISO worked inside the VM, the rubbish one that I made and wasn't happy with. I tried to then chroot back into the directories in the guide and install more programs but when I repeated the steps for the guide and created the ISO, it wouldn't work.

UPDATE: It seems there is no /home/user folder on the CD ISO unless it is run in the VM so I don't know how to change the GTK theme :(
UPDATE on the UPDATE: GTK themes are stored in /usr/share/themes and the config file for them is /etc/gdm/gdm.conf but unfortunately they don't seem to have gone into my new ISO. New programs that I install in the chroot aren't going into a new ISO either.

Another Question: Do I need to redo the mksquashfs part if I install more stuff in the chroot or should new stuff be included in a new ISO?

---

### Post by DagMan on 2008-07-20
When you add new things in the chroot, you'lle need to redo the squashfs, deleted the old one and then make the new iso.  If you have added anything that might run during boot scripts then it may be necisarry to redo the initramfs, then make the squasfs, then do the iso in that order.

For the theming, I don't know what to do for things like the login window, but for the look of the desktop, icons, and panel layout, etc.  you can always try setting it up how you want, then copying the entire folder out of the VM to the chroot on the drive, and then making the squashfs and iso all over again.  I don't know if that would work, but you would want to have a shared folder that the VM can write to, or actually run the disk and mount your computer's hard drive, then to make sure you get all the hidden files as well, copy things out using the -a option
```
cp -a /home/ubuntu /some/place/on/your/drive
```
then try copying the ubuntu folder into the home folder of the chroot.  That might work, however even if it does work, someone using the install disk would still get the default ubuntu settings.

I'm wondering if /etc/gdm/gdm.conf isnt just the login manager settings.

---

### Post by Separ on 2008-07-20
I managed to change the username btw :D

EDIT: Did squashfs on it again after installing new stuff and it still didn't add it to the ISO.
EDIT2: Forgot to delete the old squashfs. Trying again. That worked! :D
All that's left to figure out now is changing the theme.

---

### Post by Separ on 2008-07-20
EDIT: Got the theme completely working now! :D

Just to figure out how to set it as default now.

---

### Post by Separ on 2008-07-20
Still needing a bit of help with setting my theme as the default along with the wallpaper and the icons. The themes are installed and they work if I choose them from the appearance menu, it's just a case of editing some conf file but I need to know what ones :(

---

### Post by Separ on 2008-07-21
bump :-s

---

### Post by DagMan on 2008-07-21
It's there in the wiki
[https://help.ubuntu.com/community/LiveCDCustomization#Custom%20Background%20for%20GNOME](https://help.ubuntu.com/community/LiveCDCustomization#Custom%20Background%20for%20GNOME)
[https://help.ubuntu.com/community/LiveCDCustomization#Change%20gconf%20values%20(fonts,%20panels%20etc](https://help.ubuntu.com/community/LiveCDCustomization#Change%20gconf%20values%20(fonts,%20panels%20etc).)
It's pretty general though.  Maybe you want to make a thread on help regarding specifically using gconftool-2 to edit the live cd, for example, as I don't know and there hasn't been anyone else besides us paying attention to this thread as the topic was originally more general.

---

### Post by Separ on 2008-07-21
I cannot thank you enough. This was the only thing stopping me finalizing an ISO :lolflag:
Finally I can proceed.

---

### Post by Separ on 2008-07-21
EDIT: Fixed.

---

