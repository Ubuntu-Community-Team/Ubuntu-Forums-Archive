---
title: "Suggestion - plug and play harddrives with proper permissions - heres my problem"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by Squish on 2007-10-22
I have not really found a precise answer for my problems, and I do restrain from posting new threads.So sit back and enjoi!
  
Well I just bought a new hitachi deckstar HD (750gb, sata2, 32mb cache), popped her into a new nexstar 3 HDD enclosure, and connected it to my computer. There was no default Filesystem on the drive, so it was all unallocated. I couldn't find the Harddrive on my desktop though... 

[B]Suggestion:1:
When an unallocated Harddrive mounts, display an option automatically to whether the user would like to partition the drive for external use. This I am sure would help allot of people who dont know anything about partitioning. It certainly would have brightened my experience. Also, I had no idea it had mounted, and I figured  that because it wasn't on the desktop, I could just turn it off (which can be bad for the drive). So also displaying the unallocated drive on the desktop would be very helpful.
[/B]
Well because I know a bit better, I downloaded gparted, and then went forth to research what type of filesystem I should use.
ext4 sounds nice, but its unavailable. This means Reiserfs is my choice of drive.
I partition it, and that goes fine.
[B]
Suggestion 2:
Offer a bit more help dialogue when it comes to setting the disklabel. I have no idea what it is, and even after wikipedia-ing it, I still couldnt find out. The fact that MSDOS was the default, was disconcerning, because for all I know, this means I cant use it on my computer because I use linux. My logic is that because I am running linux, I should use a linux disklabel.[/B]

So after partitioning it, it comes forth to the desktop, and all is fine. I open it up, and I try opening up a folder already in it called Lost+Found, and it says I dont have proper permissions to open it.
Arg:confused:. No problem, I will just rightclick to its properties, and change the permissions

[B]Suggestion 3:
Me and my friend agree that this is one of the biggest annoyances behind permissions in gnome. That is, for when it comes to changing permissions of folders owned by root, you cant do it through properties, or through a GUIin general. When you go to the permisssions dialogue, it just shows that unclickable grey text.. Even when I chmod it, its still wont comply. Thus this suggestion is for reg users to be able to change permissions of a root owned folder, with a simple password request, and of course a warning message. I hate the fact that even after diving into command line, I still am clueless to howto change the permission, much less make it permanent. Perhaps an external harddrive utility manager would be a good idea. But honestly, this is so incredibally frustrating, moreso because ubuntu does not let me log in as root. (unless I wanna rescue in command line of course). Can anyone relate to this?[/B]

So in the end, I have a external harddrive thats top of the line, but I cant write to it, to backup my computer, so I can do a fresh install of ubuntu.

so anyways...
How do I change the permissions? I did the chmod 777, but that didnt do nothing. yarg.

BTW, what do you think of my suggestions Ubuntu Community? I figure there must be a layer of ignorance on my part, that I have overlooked or something like that. I think that this would make new users experience allot less stressful, because I can recall about a dozen times to which I wish I could have just changed permissions easily like that.

:guitar:Cool!

---

### Post by fain on 2007-10-22
you can either do it that way 777 meaning user=rwx group=rwx and other=rwx or you can do it the way i like to and type 

```
$sudo chmod ugo=rwx /path/to/file
```
if you want to change the permissions on a directory and all its sub directories and files you would
```
$sudo chmod -R ugo=rwx /path/to/directory
```
i wouldnt ever let others with the w=write permission bad i dead less its a writable ftp or something.
dont forget to sudo. you have to be the owner of the file or folder you are trying to change the permissions on.
in case you dont know 

u=user
g=group
o=other

r=read
w=write
x=execute

and yes i like the idea of a better gui permission managment system.

---

### Post by Squish on 2007-10-23
yah I ended up figuring that I was chmodding all wrong.


However, it did spawn a thought - Perhaps a gui version of chmod would prove useful. I dont think it has been done, and you can imaging how useful a tool like that would be.


hmmm
Rock out man:guitar:

---

### Post by Linicks on 2007-10-23
All you need do is add an entry in /etc/fstab, something like this:

```

Device          Mount Point       FS       Mount Options           dump     fsck options
/dev/sdb       /home/user/mnt     ext3     rw,user,noauto.exec     0         2

```

etc.  This will then allow ordinary user to mount the disk to mount point /home/user/mnt as READ/WRITE, and can exec files.  noauto stops the drive being mounted at boot.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Nick

---

