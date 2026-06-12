---
title: "Ubuntu Only!"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by e-zi on 2009-10-29
Hi all,
This is my first post here.

I have been trying Ubuntu (dual boot with windows 7) for almost 2 months now and I'm ready to get rid of Windows :)

I got 2 H.D. One with 640GB where windows is now found and a small one of 40GB that I added in order to try Ubuntu.
Now I'd like to use the 640GB for Ubuntu and disable the other one.

My question is:
Do you usually split large H.D in Ubuntu (like c:/d: in Windows)?
I used to do it with Windows to keep the c: cleaner for it to run better.
but I rather keep it all as one big H.D.

What do you think?

and one more thing... should I expect any speed deference when all of my file system use ext3 when copying instead of ext3+ntfs?

Thank you all in advance,
Hope to be able to help here as well in the future.

E-zi

---

### Post by dvlchd3 on 2009-10-29
The only usefulness in splitting your harddrive into different partitions is if you want to reinstall/upgrade Ubuntu and keep your personal files (home foler).  I use a completely different harddrive for my home folder.  This ensures if my OS harddrive ever craps out, I will still have all my files. (Not to mention I backup onto an external harddrive, and to a file server on the Internet.  Yep, as determined by another post on this fourm, I'm paranoid!)

I digress.  Most people do not split their harddrives into seperate partions.  There are no c:/d:/etc drives in Ubuntu.  Typically any special partitions are mounted to a specific location (typically /mnt/ or /media/).

Regarding ext3+ntfs/just ext3.  Since Ubuntu and Windows have been keep seperate from one another, you will not notice a difference.  When you were using Windows, you were only using ntfs, when you were using Ubuntu you were only using ext3 (unless you copied files to or from Windows).  Therefore, performance will remain static.

O, and by the way, congradulations on taking the leap to becoming a sole Linux user.  Once you get the hang of everything, you will NOT look back!

---

### Post by e-zi on 2009-10-30
Thank you dvlchd3 for answering.
I'll probably go on the simple way and won't split my hard drive. but just to understand how do you separate your home folder?

You do sound a little paranoid, but in a good way :) (I wish at my work place the took that much care of backup as you do)

Thanks again,
E-zi

---

### Post by nothingspecial on 2009-10-30
Have a look at [[COLOR="Magenta"]this[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by macogw on 2009-10-30
Separating your home directory to another partition does require partitioning/splitting.  

- Choose Manual partitioning mode. 
- Delete existing partitions.  
- Make a new partition about 10GB and set its "Mount Point" to a single  /  
- Then make a partition at the end of size 2*ram (so if you have 1 gig of ram, make it 2gigs) and tell it to use that as swap.  
- Then choose the big empty area left in the middle and, well I'd make that be "Use as: ext3" for the filesystem and set the mountpoint to /home

---

### Post by e-zi on 2009-10-30
Thank you all
that is very helpful.

Just last question:
Is there a way to save all off my setting and restore them after a new installation.
I mean drivers, configs, software, sources, etc.

Tx,
E-zi

---

### Post by nothingspecial on 2009-10-30
Most of your settings are in hidden files in your home directory so if you have a seperate home partition they will be saved.

Any drivers you manually install will have to be reinstalled (you`ll have to do that every time you have a kernel upgrade anyway)

For your software sources simply

```
sudo cp /etc/apt/sources.list ~/sources_backup
```

That will give you a copy of your sources list in your home folder, just back it up every time you change it. Do that for any config file you edit outside of your hame directory

---

### Post by macogw on 2009-10-31
To get lists of everything you've installed/removed:
```
dpkg --get-selections > ~/pkgs.lst
```
On the new system, first install dselect, then tell it to install the packages you had before
```
sudo apt-get install dselect
sudo dpkg --set-selections < ~/pkgs.lst
sudo apt-get dselect-upgrade
```

---

### Post by e-zi on 2009-11-01
Thanks for all the help, going to do the switch this week.

---

### Post by e-zi on 2009-11-03
That's it, a new sole Linux user!
Thank you all.

---

