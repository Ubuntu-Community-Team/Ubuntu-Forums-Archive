---
title: "Coby MP3 Player Clip"
date: 2008-05-24
forum: Hardware
---

### Post by MaindotC on 2008-05-24
Hi, all.  I needed a simple, cheap mp3 player to play clips of TWiT and today I got my Coby MP3 Player Clip in the mail and thought I'd fill you in.  Here are some outputs if you ever need to identify it:
```

f311-laptop:/media/disk$ lsusb 
Bus 005 Device 010: ID 0402:5667 ALi Corp.

```

```

311-laptop:/media/disk$ mount
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

```

I can't get it detected by Gnomad2 or Rythmbox, but it is viewable as a file system.  I couldn't move music onto it with nautilus but I could via the command prompt.  One issue you may run into is that it will be listed as a read-only file system.  I've not found a way to change that, but I was able to move files just as the user (myself) and not with sudo or root permissions.

```

311-laptop:/media/disk$ ls
Twin Peaks Intro.mp3  TWiT0143H.mp3

311-laptop:/media/disk$ sudo mv /home/311/Desktop/Kanye\ West\ -\ Flashing\ Lights.mp3 /media/disk
[sudo] password for 311:
mv: failed to preserve ownership for `/media/disk/Kanye West - Flashing Lights.mp3': Operation not permitted

311-laptop:/media/disk$ mv /home/311/Desktop/Marlena\ Shaw\ -\ California\ Soul.mp3 /media/disk
311-laptop:/media/disk$ ls
Marlena Shaw - California Soul.mp3  Twin Peaks Intro.mp3  TWiT0143H.mp3

```

It works fine after files are transferred.  Perfect for my morning :)

---

### Post by mrmoney on 2008-09-10
Hi,

I was wondering if you could help me out a bit. I just purchased the same one, and have the same problems. I cant drag-drop files nor can I copy/move files via the command line. It is saying permission denied due to it being a read-only file system. I cant copy files as my own user or as root.

Did yours just work out of the box or what did you do to be able to copy files to it?

Thanks

---

### Post by hwttdz on 2010-01-27
To make it pop up when you plug it in I think you might need a .is_audio_player file in the / of the mp3 player filesystem.  See here [http://live.gnome.org/Rhythmbox/FAQ](http://live.gnome.org/Rhythmbox/FAQ)

Sorry, was looking up an answer for a current thread and accidentally responded in the wrong one.

---

### Post by jm0n on 2011-06-10
Mine used to work when plugged in, but now is also giving me the "locked file system" error. Does anyone know how to restore it?

---

### Post by mrmoney on 2011-06-10
If I remember correctly, that happened if the switch on the device was set to locked when it was mounted (ie the switch that locks the button presses).

If you unmount it, flick the switch to unlocked, then remount it, it should work

---

