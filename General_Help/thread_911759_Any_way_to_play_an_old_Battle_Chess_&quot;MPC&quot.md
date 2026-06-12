---
title: "Any way to play an old Battle Chess &quot;MPC&quot; disk?"
date: 2008-09-06
forum: General Help
---

### Post by SoCalChris on 2008-09-06
I found an old copy of Battle Chess that I'm trying to get running for my son. When I insert the CD, it mounts two separate drives. The first is BATTLE7, and completely empty. The second drive is the CD audio. The first track of the CD audio disk is shown as data.

Is there any way to get this to work in Linux?

The disk copyrighted 1991 by Interplay, and contains the [Multimedia PC]("http://www.answers.com/topic/multimedia-pc") logo, if that helps.

I tried loading it on my Windows laptop, and it worked (Although the program itself complained about not having an extended memory manager installed).

It was originally a DOS program, so I would assume I could use dosbox, except that I can't access any of the data on the CD.

Thanks

---

### Post by Mister.Vash on 2008-09-06
It may work under wine, here is a report of someone that said most of it worked:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11830](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11830)

---

### Post by simguru on 2009-03-02
I got Battle Chess to work with DOSBOX, but after some tweaking.

First, you must create a BIN/CUE image of the disc. This is because, as you already noticed, extracting the tracks on the disc yields a data track and many audio tracks. This is what's known as a "mixed mode" disc. It is not possible to get an ISO image of such mixed discs since ISO images are limited to just one track. I wish I knew of a program in Linux that can create BIN/CUE files. I am aware of programs such as bchunk that can work with preexisting BIN/CUE files, but nothing that can **CREATE** a BIN/CUE file. So, somehow create a BIN/CUE image using a program such as ISOBuster or Alchohol 120%. (Aside: does anybody know of a Linux program to make BIN/CUE images? I'd love to know).

With the BIN/CUE image in hand, copy the BIN/CUE files to /home/user/cdimages and add the following lines to your ~/.dosboxrc:
```
[autoexec]
mount y /home/user/cdimages
imgmount d y:\chess.cue -t iso -fs iso
```

Now you can install Battle Chess and play it with all visual and sound effects. :D

One other note: Battle Chess is hard wired to use D as the CD ROM drive letter. If you already have a D drive mounted, you will need to shift it to another drive letter.

---

### Post by stevo1977 on 2009-08-23
Man, I have looked everywhere and I cannot find a single reference to CREATING bin/cue files under linux.  Everyone seems to use them, because there are literally hundreds of guides on how to mount and/or convert to .iso, but nobody mentions how to create the bin/cue files from a mixed-mode cd.

Is there program that can do it?  Should we just run Alcohol 120% under wine?

---

### Post by stevo1977 on 2009-08-23
It turns out that cdrdao can do it, but it looks like it only works on non-protected cds (it worked on Castles 2: Siege and Conquest, but not on TIE Fighter :sigh: ).

Here are some pretty simple instructions:
[http://miketeo.net/wp/index.php/2008/05/10/creating-bincue-files-on-linux.html](http://miketeo.net/wp/index.php/2008/05/10/creating-bincue-files-on-linux.html)

---

