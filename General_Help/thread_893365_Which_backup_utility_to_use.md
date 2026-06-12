---
title: "Which backup utility to use????"
date: 2008-08-18
forum: General Help
---

### Post by fogelfink on 2008-08-18
I have difficulties finding a backup application that does what I want!!

What I would like to do is backup my music (which is in the home directory) to an external hard drive AND be able to access this backup on another machine (non-Linux Mac).
I have looked into "Home User Backup" and "Simple Backup Config", which both seem to store the backup in a zipped format - that means I can't use the backup of my music directory as an external music library for my Mac!

The other backup utility I tried is "File Backup Manager", which comes closer to what I am looking for, but on my external drive instead of replicating the source folder, all subfolders are renamed with crazy numerals, making it virtually impossible to browse through the backup! I have attached screenshots to illustrate this point.

Does anybody know of an application, which simply copies the source foder to my external drive, so it looks exactly like the source - and from then on just keeps track of the changes in the source, copying them to the backup whenever I run the application.

Your help is appreciated.

---

### Post by kpkeerthi on 2008-08-18
[rsync]("http://ubuntuforums.org/showthread.php?t=187894"), may be?

---

### Post by AndyCooll on 2008-08-18
If you're willing to use the command line then rsync will do this for you.

Another alternative is Unison.

:cool:

---

### Post by sameerds on 2008-08-18
> **kpkeerthi said:**
> [rsync]("http://ubuntuforums.org/showthread.php?t=187894"), may be?

Better than rsync, use rsnapshot. This uses rsync internally. It's very easy to configure. It's meant to be an automated backup job that you setup using cron, but it can also be used manually. Or you can even use some scripting to trigger it whenever the correct external drive is connected.

---

### Post by LinuxRocks713 on 2008-08-18
Or you can use GNU cp (part of coreutils?):

```

# if the dir is accessible as a regular user
cp -r /path/to/dir /path/to/destination
# if the dir needs root access
sudo cp -r /path/to/dir /path/to/destination

```

---

### Post by sameerds on 2008-08-18
> **LinuxRocks713 said:**
> Or you can use GNU cp (part of coreutils?):

Well, the only problem is that cp won't delete files. If it could, it would be named rsync! :)

Also, I was thinking a bit about rsnapshot, and I realise its mostly unnecessary. rsync is enough for this job. Assuming the music collection is under /home/music (the source), and the portable disc becomes visible as /media/MyDisc (the destination), this is all you have to run with rsync:

```

rsync -au --stats --delete /home/music/ /media/MyDisc/

```

[LIST=1]
[*]Don't worry about "--delete". It only means that if a file is deleted from the source, rsync should delete it from the destination also.
[*]--stats is optional. It just gives you some nice output about what happened.
[*]The forward-slash (/) at the end of the source name is important. Read more about it in the manpage.
[*] rsync has problems running on FAT32 filesystems
[/LIST]

You can put this command in a script so you don't have to remember that. You can then configure Gnome to run the script whenever the disc is connected!

---

### Post by fogelfink on 2008-08-18
> **AndyCooll said:**
> If you're willing to use the command line then rsync will do this for you.

Another alternative is Unison.

:cool:

I would love to avoid a command line tool - as I am fairly new to Linux and find it easier to have some sort of visual guidance.

So I tried Unison, but failed because of a permission error. This is what I get: >   /media/EXTERNAL/LinuxBackup/.#Important Documents.647aec350ea81d25a4672b4b2f5e6883.unison.tmp/OT11876770907.pdf to rwxrwxrwx: the permissions was set to rwx------ instead

I tried to change permissions as root user without success.  The external drive is formatted to fat32 - is that a problem?
:confused:

---

### Post by sameerds on 2008-08-18
> **fogelfink said:**
> 
So I tried Unison, but failed because of a permission error. This is what I get: 

I tried to change permissions as root user without success.  The external drive is formatted to fat32 - is that a problem?
:confused:

That probably is the problem. FAT32 does not have the concept of permissions. When Linux mounts a FAT32 partition, it emulates permissions by assigning some default setting that you can specify. When some tool tries to set its permissions, this results in an error. This is usually not a big deal, and you can ignore it. One way to make the error go away is to configure Unison so that it does not try to force any permissions ... dunno if Unison has such a setting, in rsync this is equivalent to the "--no-perms" command line switch.

---

### Post by stinger30au on 2008-08-18
easy peasy

install wine and run a windows app called syncback

runs perfectly in linux and will do what you want as i do it myself

[http://www.2brightsparks.com/downloads.html#freeware](http://www.2brightsparks.com/downloads.html#freeware)

---

### Post by Toufik on 2008-08-19
Unison is definitely the best tool for you. It can handle permission issues but not graphically (or I didn't see where :) ). You need to open the profile and modified it by hand:

In your home directory
```
cd .unison
ls
```
You'll get a list of file. Take a look only at .prf files which are the profiles. You probably have only default.prf : open it (or the one you want)
```
gedit default.prf
```
and add somewhere at the end this line
```
perms = 0
```
save and start using unison!

---

### Post by fcarramate on 2008-09-18
hello all

I'm running Ubuntu for 2months now and pretend to running Ubuntu on my computers!

definitely **perms = 0** works very fine!

thanks a lot! I was trying to getting around this some time ;)

---

### Post by thirdrev on 2009-03-12
Thanks, this worked great for fixing Unison.

---

### Post by TVC15 on 2009-03-21
Hi there,

Backup utilities seem to be a hot item on the forum.  A lot of people want something that looks and feels similar to the popular Windows tool Syncback.

For Linux, the best backup tool for me (and surely many others) is rsync.
Best of all: rsync now has a GUI called grsync that you can find in the Ubuntu repositories.
Looks and feels a lot like Syncback and also works on Samba shares or mounted network drives or over an ssh, ....

Very much worth giving a try!


Good luck!

---

### Post by DaOg75 on 2009-03-21
> **TVC15 said:**
> Hi there,

Backup utilities seem to be a hot item on the forum.  A lot of people want something that looks and feels similar to the popular Windows tool Syncback.

For Linux, the best backup tool for me (and surely many others) is rsync.
Best of all: rsync now has a GUI called grsync that you can find in the Ubuntu repositories.
Looks and feels a lot like Syncback and also works on Samba shares or mounted network drives or over an ssh, ....

Very much worth giving a try!


Good luck!
Thanks for this tip on grsync. I just installed it and it looks perfect for what I might need.

---

### Post by ogami1972 on 2011-01-16
much thanks to Toufik, Unison now works as it should. i know rsync is the "go to" but i am sticking with unison...will let you know if i have issues.

---

