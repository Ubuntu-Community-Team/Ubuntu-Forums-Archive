---
title: "Can't see content of DVD (That worked in windows)"
date: 2008-09-22
forum: General Help
---

### Post by Nat90 on 2008-09-22
Hi everybody
I have a problem, maybe you can help me, when I put an specific DVD in the tray, it shows as mounted at the work desk but when I open it, y shows no content. When I put another DVD with files of the same extension it works perfectly. The first DVD work just fine in windows

The weird thing is that when I enter Nautilus from the terminal as root, I can see the content in the DVD, even play it, but it wont let me copy it to the hard drive, it says "you can't manage the file because you have no permission to read it" (it may be a little different because I'm translating it from Spanish Ubuntu)

Thanks beforehand for the help

---

### Post by mb_webguy on 2008-09-22
What is the output of "ls -lsh /media/cdrom0"?  And also "cat /etc/fstab".

---

### Post by Nat90 on 2008-09-23
natan@natan-desktop:~$ **ls -lsh /media/cdrom0**
ls: can not access /media/cdrom0/*(File Name)*: Permission denied

And so on like that with every file(they are all of the same extension)-it might be a little different, remember I'm translating it from Spanish-


and

natan@natan-desktop:~$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=51329bf2-ec2a-4c1f-90cf-1b69978d76fb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=b771ef28-3fd3-4d32-b629-170ea6fad920 /home           ext3    relatime        0       2
# /dev/sda1
UUID=f39acb7e-5157-4120-b5c4-93ebab4122f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by mb_webguy on 2008-09-23
Well, your fstab looks fine.  What about "ls -lsh /media"?

---

### Post by Nat90 on 2008-09-23
This is the *ls -lsh /medi*a with colours and everything

> natan@natan-desktop:~$ ls -lsh /media
total 8,0K
   0 lrwxrwxrwx 1 root           root              6 2008-09-21 01:37 [COLOR="Cyan"]cdrom[/COLOR] -> [COLOR="RoyalBlue"]cdrom0[/COLOR]
4,0K  dr--r--r--  2  4294967295  4294967295  4,0K 2007-04-18 04:08 [COLOR="RoyalBlue"]cdrom0[/COLOR]
   0 lrwxrwxrwx 1 root           root              7 2008-09-21 01:37 [COLOR="Cyan"]floppy[/COLOR] -> [COLOR="RoyalBlue"]floppy0[/COLOR]
4,0K drwxr-xr-x 2 root           root           4,0K 2008-09-21 01:37 [COLOR="RoyalBlue"]floppy0
[/COLOR]
Thanks for answering, any ideas?

---

### Post by mb_webguy on 2008-09-23
Oh, yeah... there's your problem.  I don't know what caused it, but take a look at the permissions on cdrom0.  It should be owned by root:root, and the permissions should be 555.  Type the following in the terminal, and see if it helps.```
sudo chown root:root /media/cdrom0
sudo chmod 555 /media/cdrom0
```
Like I said, I don't know what caused your permissions to get messed up like that, though, since your fstab entry for your optical drive looks correct...

---

### Post by Nat90 on 2008-09-23
I've tried it a couple of times and restarted but still nothing.
So I looked at the "ls -lsh /media" to see if it changed and it didn't (except por the time and date). Isn't there a text file I can change manually?

---

### Post by Atsuko on 2008-09-23
Just a question, did it play before this happen?

---

### Post by mc4man on 2008-09-23
I would think your setup is fine ( you did mention other dvds work fine)
If so then there is something about this particular dvd (am assuming it's a data dvd

The easiest may be to redo it in windows.

Otherwise while you said it wouldn't let you copy the files have you tried the whole disk?
See what happens with something like this 

```
dd if=/dev/[COLOR="Red"]scd0[/COLOR] of=dvd.iso
```  or
```
dd if=/dev/[COLOR="Red"]scd0 [/COLOR]of=dvd.iso conv=noerror
```

Adjust red to match your drive, if no go try adding sudo to beginning of command.

If you get an iso you could try chmodding if needed, extracting it with archive manager or mounting it.
```
chmod +rw dvd.iso
```

Another possibility is to install dvdisaster and see if it can read (extract the dvd) (in synaptic
Use the default settings to start - you'll just need to specify a destination - home/<username>/test.iso , see screen ( note this reflects a nonstandard use hence no attempt or ability to fix 'unreadable sectors', just using to 'dump' to an .iso

Or try 
```
dd_rescue -v -b [COLOR="Red"]2048[/COLOR]  /dev/[COLOR="Red"]scd0[/COLOR] /home/[COLOR="Red"]doug[/COLOR]/dvd.iso
```  with or without sudo

---

### Post by Nat90 on 2008-09-24
I didn't really get what to replace the red with, I'm kind of new, but I was able to sort it out.
I copied the DVD image to the computer, mounted it with Gmount-iso, and then copied it to the computer. It was kind of uncomfortable because the names of the files were changed, but in the end it was solved.
I just wish this doesn't happen with any other DVDs

Thanks everyone for the help, you make ubuntu posible for people like me

---

### Post by mc4man on 2008-09-24
> I didn't really get what to replace the red with
That's just to specify the dvd drive for a command so it can locate it.

the 'normal' is for your dvd drive, /dev/scd0
if you had 2 drives then the other one would be /dev/scd1

But normal isn't 'all the time'

If you wanted to see the 'device locations' of your drives run this in a terminal, it will show most of the 'names' that point to each drive. 


```
sudo lshw -C disk
```

---

### Post by Nat90 on 2008-10-13
I solved it!

all this time I was thinking the problem lay on the DVD permissions, But I realized that maybe it had something to do with the hard drive writing permissions, so I tried to change that, which it didn't work, so I said, what if a open two nautilus folders as root, one with the DVD and the other with the desktop, and it worked!! The answer was so simple!!

I just wish I could have root privileges in my day to day life:-)

---

