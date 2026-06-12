---
title: "Mounting and external HD on a network"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by HieroPosche on 2007-11-05
I've got a WD external HD attached to my windows desktop (Vista) and I'm not sure how to mount it from my laptop (Gutsy).

I've got samba configured so that I can access the files, but nothing from the HD will play in XMMS I"m assuming because it's not mounted.

Any help I could get would be much appreciated.

---

### Post by jonathanmotes on 2007-11-05
It might be a codex problem (meaning you don't have the plugins you need to play the file). What type of files are you trying to play (wma, mp3, ogg, etc.)? 

To "mount" a drive, you can usually go to File->Connect to Server once you've browsed to the location, but I don't think you have to mount the drive to play music from it. 

You might try copying a file to your desktop, then trying to play it to help you figure out if its a codex problem.

---

### Post by HieroPosche on 2007-11-05
Copied a file to my laptop and it played fine. I then tried to play it from my external and got the same thing.

Also, XMMS has a popup that lets you know when it's a codec or I/O setting issue, I don't get this when I try to play from the external. If I drag an album from my external to the playlist in XMMS ad then try to play it, it quickly highlights each song in the playlist but doesn't play anything.  It's like each song is only a half second long... and... Umm.. Silence?

Oh, and I can play the music on the drive through Rythmbox or the gnome default movie player just fine, Only XMMS has this issue.

---

### Post by jonathanmotes on 2007-11-05
OK, its certainly not a codex problem then. Did you figure out how to map the drive?

---

### Post by jonathanmotes on 2007-11-05
Um, I installed XMMS to test this out. I am having the same issue. I copied a file to a mapped network HD and could not play it with XMMS, but it plays fine with other players. Sorry, I guess it's a bug. Maybe you should see if similar players (Beep, Audacious, etc.) have the same issue.

---

### Post by daengbo on 2007-11-05
I don't think XMMS is aware of Gnome-VFS, which is what the Gnome apps like Rhythmbox use, and it may not even be aware of the smb:// protocol. Is your shared folder password protected?

Anyway, you might need to mount the share locally. Look here on how to do it:
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

Cheers

---

### Post by HieroPosche on 2007-11-05
The shared drive is not password protected so that's not the issue.

I'm trying to mount it using the howto that you posted but doesn't seem to want to work, I'm still pretty new to command line but here's what I'm getting.
```

name@comp:~$ sudo mount -t smbfs //Posche/Server /home
mount: wrong fs type, bad option, bad superblock on //Posche/Server,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

That seems to be the closest I got to accomplishing anything :P

---

