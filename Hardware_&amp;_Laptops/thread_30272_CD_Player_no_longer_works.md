---
title: "CD Player no longer works"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by David Haas on 2005-04-27
My CD player worked perfectly under Warty, but now, after a partial upgrade to Hoary, when I open "CD Player" it gives the message "Drive Error" and won't play my audio CD. My version of Gnome is 2.10.0. The build date was 3/7/2005. When I right click on the main status window of the CD player GUI, it doesn't show a help menu, but presents a dialog saying that "The application "gnome-cd has quit unexpectedly." Any ideas about fixing this?

---

### Post by wulf on 2005-04-28
You too? I'm sure I played an audio CD just after upgrading to Hoary (Monday) but I'm not 100% sure and it definitely wasn't working from Tuesday, onwards.

Doing some searching, I've found an [earlier thread](http://ubuntuforums.org/showthread.php?t=19523&highlight=cd+audio) (now locked because it was in the Hoary Dev forum) that gave me a few clues. Having looked at the "CD Audio Player" input plugin (options | Preferences | Audio I/O Plugins) I've solved my problem by creating a cdrom entry in /dev:

```
sudo ln -s /dev/hdc /dev/cdrom
```

I'm now happily spinning a *Greatest Hits* compilation from The Police, and everything's fine. Is this missing symlink a bug with Hoary?

Wulf

---

### Post by David Haas on 2005-04-28
Wulf-Thanks loads for your reply which solved the problem. I had to make a similar symbolic link to get Real Player working. I see that Ubuntu had the cdrom link to /dev/hdc in /.dev. 
Happy playing,
David

---

### Post by Claus Cyrny on 2005-05-03
I'm having a similar problem: Gnome-CD recognizes the tracks of the CD, but doesn't play them. Prior to the update I had no problems playing CDs. Now, after the update, I can read a CD via CD Ripper and save it (and replay it via XMMS or noatun), but not with gnome-cd. What can I do? RealPlayer works, too.

Thanks,

Claus

---

### Post by wulf on 2005-05-04
Have you got a symlink called */dev/cdrom*, as described above?

Wulf

---

### Post by Claus Cyrny on 2005-05-04
[QUOTE=wulf]Have you got a symlink called */dev/cdrom*, as described above?

Wulf[/QUOTE]

Yes, it is there. In "Properties" it says: File owner is "root". I already tried the tip you gave above, but apparently to no avail! Thanks anyhow!

Claus

---

### Post by wulf on 2005-05-05
My symlink looks like this (from a terminal, with *ls -lh /dev/cdrom*):

```
lrwxrwxrwx 1 root root 3 2005-04-28 10:10 /dev/cdrom -> hdc
```

In other words, it's owned by root but all permission levels (owner, group and world) are set to read, write and execute.

What happens if you try to play a CD in XMMS without ripping it first? I don't use Gnome-CD, so I can comment on that so much.

Wulf

---

### Post by Claus Cyrny on 2005-05-05
[QUOTE=wulf]My symlink looks like this (from a terminal, with *ls -lh /dev/cdrom*):

```
lrwxrwxrwx 1 root root 3 2005-04-28 10:10 /dev/cdrom -> hdc
```

What happens if you try to play a CD in XMMS without ripping it first? I don't use Gnome-CD, so I can comment on that so much.

Wulf[/QUOTE]
XMMS doesn't show any content of the CD (I access the CD via /media/cdrom0). Since I couldn't find Gnome-CD in Synaptic, I found & installed the command line player "cdcd" today & and was able to play a CD, but "Eject" doesn't work! :-( When I open the file browser in the panel ("Places > Audio Disc") the location of the CD is being displayed as "cdda:///dev/hdc". Could it be that there's still no symbolic link present? Shouldn't the location read "cdda:///dev/cdrom" instead? And: In / I found /cdrom as well. Is this correct? (I'm  actually *relatively* new to Linux, so please forgive me this "beginner's" question!)

Thanks,

Claus

P.S.: XMMS plays the CDs now alright! I don't know what's the matter with Gnome-CD!

---

### Post by wulf on 2005-05-06
In order to browse the files on a CD, you need to mount it. However, an audio CD doesn't need to be mounted in order to play. To be honest, I don't understand the reason for that distinction (although I'd be interested if anyone else knows)!

/cdrom is probably a link to /media/cdrom, which is probably a link to /media/cdrom0 - you can have a whole chain of these links going on, one file but several ways to get to it! If you put in a data CD, it probably automatically gets mounted from /dev/hdc to /media/cdrom0 (and thus the other links will also point to the CD player). Why so many links around? It's probably because there's more than one way to do things and it's not quite standardised!

Wulf

---

