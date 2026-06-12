---
title: "mtpfs - directory problem and automating mount operations"
date: 2009-05-05
forum: Hardware
---

### Post by Nareto on 2009-05-05
Hello. Just bought a Creative Zen Mozaic 2gb, and i've been struggling all day to find an easy way to transfer files to and from the player. I haven't found a good and comprehensive source of information on mtp support.

i'm using 
```
sudo mtpfs -o allow_other /media/MyZen
```
to mount the device and 
```
sudo umount /media/MyZen
```
to unmount it. Problems are:
1) could this mount/unmount process be automatized or simplified somehow?
2) i'm having problem with directories. No matter if i create the directory inside the player and then copy single files into it, or directly copy the directory from my computer to the player, the files are being placed in Music (directory present by default inside the player). The directories too are being placed there, but if i try to move the files in it, i get "No such file or directory" error.
This is pretty annoying because i'd like to maintain the same directory hierarchy on the player as on my computer, rather than having all songs smashed together in one directory.

Any help appreciated

---

### Post by Nareto on 2009-05-12
kind of resolved...
1) i just created two scripts with the above commands, although the sudo makes it ask for password; moreover it would be nice to have something detect when the player is plugged in and automatically run the script

2)i found out that the occasional .jpgs of album covers would remain in the directory when copied, so i immagine it's just the player that will move all the mp3s up to the Music/ directory. I can cope with this; it is a big mess browsing, but the player supports deleting albums directly from within it so i'm deleting from there and then copying new stuff in the big mess

---

### Post by Fractalinear on 2009-08-04
I'm bumping this because I can't cope with this file moving nonsense. I would like to connect my Zen to my roommate's Xbox 360 to listen to music, but when I try to browse it the 360 has to lock up for five minutes to scan through one folder holding 4,000 songs. If they were properly sorted into a directory hierarchy this problem would not be happening.

I have doubts about this being the Zen's doing. I've used my Zen on Windows and the included software preserves directory structure just fine. Gnomad2 has the same behavior (of not preserving structure). Your thoughts, please?

---

### Post by fozzytbear on 2009-10-03
Bump.

I'm having the same problems.  They're more annoyances than anything else, but I feel like these should be fixable.

---

### Post by danielferber on 2009-10-15
I also experience the same problem. All songs are copied to the /Music directory, regardless to which directory I copy to.

This did not happen while I used Fedora (two years ago, mtpfs compiled by myself). However, I tried to compile latest version of mtp/mtpfs for ubuntu and the same problem still happens.

---

