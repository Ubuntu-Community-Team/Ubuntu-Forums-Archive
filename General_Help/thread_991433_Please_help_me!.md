---
title: "Please help me!"
date: 2008-11-23
forum: General Help
---

### Post by Mikey Teh Zombeh on 2008-11-23
Okay im thinking of installing ubuntu i really like the setup but im very confused :(. I couldnt play mp3's , run programs , or even play videos. I am trying to run it on my computer that doesnt have internet but i want ubuntu to be my OS  but i find it so hard to use and so different from MS XP.
Please anwser these questions.
KEEP IN MIND I DO NOT HAVE INTERNET. Buti can download things on my thumbdrive and trasnsport them to the computer,
1.Where can i download the codecs
2.Wheres the MS word equivelent
3. Wheres the Windows movie maker equivelent
4. How do i run exe programs like GOM video player,antivirus, damoen tools, limewire , magic video converter.
 etc
5. explain the basics please

---

### Post by doas777 on 2008-11-23
> **Mikey Teh Zombeh said:**
> Okay im thinking of installing ubuntu i really like the setup but im very confused :(. I couldnt play mp3's , run programs , or even play videos. I am trying to run it on my computer that doesnt have internet but i want these questions anwsers
Please anwser these questions.
KEEP IN MIND I DO NOT HAVE INTERNET. Buti can download things on my thumbdrive and trasnsport them to the computer,
1.Where can i download the codecs
2.Wheres the MS word equivelent
3. Wheres the Windows movie maker equivelent
4. How do i run exe programs like GOM video player,antivirus, damoen tools, limewire , magic video converter.
 etc
5. explain the basics please

you can get most of your codecs from 2 places. first open a terminal and run:
```
sudo apt-get install ubuntu-restricted-extras
```
then go to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and follow the repository how-to, installing both the dvd decoder and teh win32/64 codecs.

as for ms word, it is the openoffice word processor, and it's in ther by default

don't know about video editing, but i've seen some threads on teh forums about them. search, and ye shall find.

some of your apps may work with wine. check out wine. as for daemon tools, theres no such thing, but you mount the iso as a folder rather than a drive. you don;t need antivirus. I've never heard of that movie player, but totem is pretty good, and if it won;t play somthing, 9/10 vlc will.

good luck,
franklin

---

### Post by Mikey Teh Zombeh on 2008-11-23
i still need more anwsers

---

### Post by lukjad on 2008-11-23
Well, if you order the disks from ubuntu.com, they will be shipped to you at no cost. The Open Office Suite will be preinstalled, that is the "MS word equivalent" you were asking about. I know that you can buy for about $45 a set of CD/DVDs with a few of the repositories. If you can't do that, or don't want to, you can download .deb packages from the websites themselves. There is something called Kino that is supposed to be a movie maker. I haven't used it so cannot comment on its quality.

For some programs, there is a program called WINE that can sometimes run them in Linux, but that depends on the program, your computer, and the alinement of the planets. ;)

What I would suggest you do is dual boot. Install Ubuntu alongside  Windows and when you hit a snag where you can't find out how to do something quickly, boot into Windows and finish the task. That is how I started my Ubuntu experience, and I finally adjusted to the point where I didn't want/need Windows anymore.

---

### Post by Mikey Teh Zombeh on 2008-11-23
What is dual boot?

---

### Post by mkvnmtr on 2008-11-23
You need to find the distribution you need for your machine Probably best to go with 8.04. On a machine connected to the internet download and burn to a disk or send of for a free disk. Then boot up to the disk and use Ubuntu for quit some time to see if you like it and how it works on your machine. Then you will be in a better position to ask for help.

---

### Post by lukjad on 2008-11-23
Dual Booting is when you install Ubuntu alongside Windows and you can choose which OS you wish to use every time you reboot.

---

### Post by Yellow Pasque on 2008-11-23
gtk-gnutella is the GNOME equivalent of limewire.

---

### Post by HousieMousie2 on 2008-11-23
> **Mikey Teh Zombeh said:**
> What is dual boot?

A dual-boot is, typically, where your hard drive has been partitioned to hold more than one operating system... or using more than one hard drive, each with it's own operating system installed upon it.

Upon start up, you will see an additional screen, this will likely be either LILO or GRUB, from which you can chose which operating system you wish to load (Windows or Linux.)

I would recommend an LTS version (Long Term Support.)  For Ubuntu, that is Hardy Heron 8.04, as someone else mentioned.  It uses Gnome, but some people prefer KDE (Kubuntu) since it acts a little more like Windows.

Make a choice, download the Live CD ISO disk image, get the correct md5sum to verify the ISO is good.  Burn it to a CD and use the 'try it out' option, see if you like it.

Keep doing this until you find the one that feels the best to you.  Keeping in mind what you have already learned, that where proprietary software is concerned, getting some media types to play will require you to install and make changes, since they would be violating the law if they were to include the means to read certain software types on a installation CD.

---

### Post by HousieMousie2 on 2008-11-23
Oh yeah, another thing.  Relax.  There is a learning curve to Linux, so you can't expect to get everything worked out right away, that will take some time.

There are MANY free tutorials on-line, (remember Google is your friend  :-) check a few out.  They might not be the most juicy or entertaining reading you have ever done, but they are well worth your time.

I suggest you also take notes, makes life easier than flipping through a tutorial looking for some command you know exists, but can't recall.

Another side note... the title of your posts in a forums:

Try to include information about your problem, as there are so many cries for "help" that give no clue as to what kind of help you are after... many times these types of posts can get passed over.

Welcome to the wonderful world of Linux!  Best of luck to you!

---

### Post by Yellow Pasque on 2008-11-23
> Another side note... the title of your posts in a forums: Try to include information about your problem, as there are so many cries for "help" that give no clue as to what kind of help you are after.
Also, if there's good info in your thread, it makes it harder for others to find when searching.

---

