---
title: "7zip: specify archive size"
date: 2008-09-26
forum: General Help
---

### Post by muzikoverdose on 2008-09-26
I've just started to back up my substantial image archive to Mediafire. However, Mediafire only accepts files below 100mb. It would take forever to go into each folder and make 99mb 7zip archives on Ubuntu.

The windows release of 7zip can take a folder and divvy up the contents into sizes of your choice.  A very handy thing.  I played with a Linux GUI for 7zip but it will only break a folder up into predetermined sizes (floppy, CD, DVD)

Does anyone know of a other archiving program that you can specify archive file size?

---

### Post by Pelham123 on 2008-09-26
First one that comes to mind is 'rar' - you can specify volume size in command line with:

```
 v<size>[k,b]  Create volumes with size=<size>*1000 [*1024, *1]
```

---

### Post by muzikoverdose on 2008-09-26
apologies, i should've been clearer:  i know less than nothing about the command line.  could you give me an example?  my images live in /home/pictures/[folder name]

---

### Post by Pelham123 on 2008-09-26
In that case take a look at this post:

[http://ubuntuforums.org/showthread.php?t=556756](http://ubuntuforums.org/showthread.php?t=556756)

It is a GUI for rar compression. Follow the instructions in the [COLOR="Red"]Current Version Info:[/COLOR] You will need to download 

[http://ubuntuforums.org/attachment.php?attachmentid=46650&d=1192672069](http://ubuntuforums.org/attachment.php?attachmentid=46650&d=1192672069)

Download to desktop etc, double left click on file, choose extract and choose location. Double left click on mkrar.sh file and follow instructions.

Any questions...feel free to post

Good luck ;)

---

### Post by muzikoverdose on 2008-09-26
Excellent.  Thanks heaps.  I love these forums as everyone is so helpful.  I just don't have the time to really get into the nitty gritty of Linux but refuse to go back to Windows.  Using legit software for once feels great :) no more astalavista.box.sk.  

Many thanks mate :)

---

### Post by Pelham123 on 2008-09-27
Hey I learnt something too.

7zip apparently doesnt honour file permissions...so is unsuitable for system backup unless you 'tar' it first:

> Also the 7z archive format does not store unix file permissions and ownership, which makes it unsuitable for backing up a system. To work around this, you can use tar to archive, and 7z to compress the tar

Great thing about these forums...I help so that I can learn.

So you are very welcome :)

---

### Post by muzikoverdose on 2008-09-27
So does that mean if I password it or something it's not going to work?  Not sure what permissiojns means :) I'm about to look at that RAR thing you pointed me to.  Does it allow for the reassembly of the split archive?

---

### Post by Pelham123 on 2008-09-28
By 'permissions' I mean who has rights to read/write individual files, ie- root for system files, etc. Not to be confused with permission to open archive - sorry.

To extract archives, should be able to just double Left click on 'part1.rar' and extract to directory of your choice. As long as the other .rar archives parts are in the same directory it should merge them for you.

Tried it and it worked for me :)

---

### Post by muzikoverdose on 2008-09-28
Oh very cool. Gave it a crack & it worked well. The only problem i've found so far is that it can't do a directory with multiple directories in it. Seems I have to go into each directory and zip things up. No biggie.  Now, challenge time:  is it at al possible to assign this script to a right click function and make it run with default values from that right click?  Once again, thanks for all your help and patience with a linux n00b :)

---

### Post by Pelham123 on 2008-09-28
> **muzikoverdose said:**
> The only problem i've found so far is that it can't do a directory with multiple directories in it.

First solution that comes to mind: If you Right click on the main folder there will be a choice to 'Create archive....' from this menu you can select .tar. The .tar archive doesnt compress, it gathers all files and sub-folders into one neat tar package. This file can then be rar'd and split.

-----------------------

> **muzikoverdose said:**
> Now, challenge time:  is it at al possible to assign this script to a right click function and make it run with default values from that right click?

Had a little mess around. You can assign the 'mkrar' command to the Right-Click menu. However, the mkrar program does not allow arguments to be put to it. Eg, you cannot specify a file or conditions for mkrar to use, you have to wait for mkrar to *ask* what file you want rar'd and compression conditions.

Of course, you could open up the script and have a tinker...but maybe a bit beyond me ;)

IMO its easier to Alt-F2 and type in 'mkrar'

Anything else? :p

---

### Post by muzikoverdose on 2008-09-29
nah thats all great :) i'll muddle my way through from here.  cheers!!

---

### Post by Hurter on 2008-11-11
Hi 

You can set the -v suffix at any level from the command line or in a script

I use the following command in a script to make volumes in DVD size. (I did mod it a bit with less option) ;) 

7zr a -t7z -v4450m /mnt/data/Backup/All_zip/Tony.7z /mnt/data/Backup/Users/Tony/ >>/mnt/data/Backup/All_tower35_zip/Tony.txt

So all the files in /mnt/data/Backup/Users/Tony/ dir will be compressed in /mnt/data/Backup/All_zip/Tony.7z with volume no greater than 4450Meg.
Because I use cron to do this for me I store the results into a file. /mnt/data/Backup/All_tower35_zip/Tony.txt

Hope this help
H

---

