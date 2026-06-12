---
title: "Utorrent in wine does not work"
date: 2008-08-11
forum: General Help
---

### Post by davidw89 on 2008-08-11
[[IMG]http://img397.imageshack.us/img397/5219/screenshotlk5.png[/IMG]](http://imageshack.us)
[[IMG]http://img397.imageshack.us/img397/5219/screenshotlk5.86f8dba563.jpg[/IMG]](http://g.imageshack.us/g.php?h=397&i=screenshotlk5.png)

---

### Post by eternalnewbee on 2008-08-11
Go to Applications-add/remove... and in the search bar type: azureus.
Works just as fine as Utorrent

---

### Post by Ryadt on 2008-08-11
Is there any reason why you want to use utorrent? Try the alternatives, they work as well if not better. I use deluge, it's in the repos, and I will never change it for utorrent.

---

### Post by hyper_ch on 2008-08-11
just go for the power-combo: rtorrent & screen ;)

---

### Post by Alexander Lindskog on 2008-09-04
The problem here is the path uTorrent got from when you (I assume) drag&dropped the file.

You see, / (root) is usually called Z:\ in wine.

I use a tiny script for launching torrents with uTorrent:

Make a small file named "uTorrent.sh" and copy&paste this into it (assuming you've used the standard installation path)
```

#!/bin/sh
wine ~/.wine/drive_c/Program\ Files/uTorrent/utorrent.exe "Z:$*"
```

Now when you're asked to open a .torrent in Firefox you pick "open with" and browse for this script file and it should work. The same goes for your file-manager (Nautilus).

Oh, and don't forget to make your uTorrent.sh executable (under File Properties)

---

### Post by stinger30au on 2008-09-04
ditch utorrent and use a native linux one.save yourself all the headaches

qbittorrent 
[http://qbittorrent.sourceforge.net/](http://qbittorrent.sourceforge.net/)

good little app but not in the repos

ktorrent
[http://ktorrent.org/](http://ktorrent.org/)
magic little app and in repos

---

### Post by mb_webguy on 2008-09-04
> **Ryadt said:**
> Is there any reason why you want to use utorrent? Try the alternatives, they work as well if not better. I use deluge, it's in the repos, and I will never change it for utorrent.

+1

Deluge works great, is in the repositories (though a newer version is available through the Deluge website), and it has a very similar interface to uTorrent.

I used uTorrent exclusively in Windows and loved it, but I haven't missed it much since switching to Deluge under Ubuntu.

---

### Post by Nafetitive on 2009-06-17
I'm so tired of people trying to avoid the problem by saying "why use uTorrent? Try using Blah Blah Blah instead!" 
I'm using uTorrent because I like it and I'm comfortable using it. I shouldn't have to get this run around just to figure out how to properly setup uTorrent! 
If you don't like the fact that people are still using uTorrent, get over it.  Don't make us feel like complete losers for choosing to stay with it. Users of uTorrent most likely already know of alternatives.

---

### Post by Chronon on 2009-06-17
I think you're getting needlessly defensive.  These are Ubuntu forums and people are merely suggesting native applications because that's generally desirable.  I didn't see anyone being overly critical.  They just pointed out options that don't require WINE or fiddling with different path delimiters.  You are, of course, free to follow their advice or not.

---

### Post by ~sHyLoCk~ on 2009-06-17
> **Nafetitive said:**
> I'm so tired of people trying to avoid the problem by saying "why use uTorrent? Try using Blah Blah Blah instead!" 
I'm using uTorrent because I like it and I'm comfortable using it. I shouldn't have to get this run around just to figure out how to properly setup uTorrent! 
If you don't like the fact that people are still using uTorrent, get over it.  Don't make us feel like complete losers for choosing to stay with it. Users of uTorrent most likely already know of alternatives.

People are only trying to help you, no need to ridicule their suggestions. 
I think from the screenshot itself it's quite simple that "Path not found" suggests uTorrent is impotent when it comes to understanding the Linux way of naming files/drives. So instead of drag and drop , just use the browse for torrents button and it should work. 
Good luck

---

### Post by Nafetitive on 2009-06-17
Yes I am overly defensive, only because I'm frustrated. I'd really like to get my issue with uTorrent settled before I try any other program. I just got tired of people talking about alternatives rather than solutions. Sorry for the hostility. Being technologically inept is such a hurdle when having to get to know my computer all over again, having just installed Ubuntu not too long ago. So far I love it, but it has its frustrations.

---

### Post by ngsupb on 2009-06-17
You should be opened for changes. Otherwise if you don't like to change anything in life you will end by erasing Ubuntu and installing Windows, because Ubuntu doesn't have MSOffice, no Photoshop etc.

Try to run applications that are designed for Linux instead of porting win application into Ubuntu.

---

### Post by TheNosh on 2009-06-17
first of all wine isn't perfect, and it never claimed to be. if you absolutely insist on using windows applications use windows.

however in this instance i can't think of what may have caused your problem, Utorrent used to work perfectly for me in wine. (since then i switched to deluge though) have you at least tried reinstalling it?

---

### Post by Nafetitive on 2009-06-17
Okay, scratch all the unnecessary junk with uTorrent. I just downloaded Deluge, after reading many opinions about it. So far so good. It has all the options that uTorrent has, and a few extras that I am not quite familiar with.
Thanks to everyone for their patience in putting up with yet another frustrated (former) uTorrent user!:D

---

### Post by Entropy_Sam on 2009-06-17
> **Ryadt said:**
> Is there any reason why you want to use utorrent? Try the alternatives, they work as well if not better. I use deluge, it's in the repos, and I will never change it for utorrent.
 
All sorts fo reasons why you might want to use uTorrent.
 
In my case, I've become pretty attached to VS2008 Express for my C# coding - especially as I've had issues getting MonoDevelop 2's debugger up and running properly. As I'm using OpenGL, a VM XP install just won't cut it, so I have to dual boot Ubuntu/XP until MonoDevelop catches up a little more with Visual Studio Express (or until 3d support in VirualBox improves sufficiently enough to run my projects properly).
 
I'd like to continue the downloads across both operating systems, and with uTorrent in WINE, if I set up the downloads on a shared partition, I can.
 
And IMO Azureus is overly bloated. I want something lightweight to handle my torrents, and I don't want it to do *anything* else (Azureus on XP kept waving suggested movie clips in my face - if I want that, I'll visit YouTube).

---

