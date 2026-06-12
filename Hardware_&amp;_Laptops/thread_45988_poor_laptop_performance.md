---
title: "poor laptop performance"
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by aburda on 2005-07-02
Hello,

     I'm looking forward to the day when I'll be able to get off windows on my laptop (I've already transitioned to using almost entirely open source software on windows) but the performance of Ubuntu on my laptop is just too bad.  I have about a two year old Toshiba A10 (2.2 GHZ, 256 RAM) so performance should be fine (at least it is wonderful on windows using only open source software.
     For example, any time I am playing mp3's and do anything the MP3's start to skip.  When watching movies periodically the movie will by jumpy.  OpenOffice takes about a minute and a half to load.  If I dive into opening (or god forbid editing) pictures from my digital camera the system goes berserk.
     When I really get going with gedit open, several nautilus explorers and Firefox the system will really start swapping.
      I figured it must just be my laptop so I tried it on my girlfriends Acer (which is also a 2 year old laptop) and linux basically performs the same.
      I'm running Linux as a server on a desktop which I also use as a workstation and everything seems fine.  So I justed ended up sticking with windows and going open source until I get a new laptop.  I've been thinking of trying another distro (probably Suse) but I like Ubuntu too much and also like gnome.
     I've tried various things to increase performance, prelink, hdparm, stopping unnecessary services, installing the 686 kernel but all to no avail.  I know I only have 256 MB or memory but I don't believe that that is the problem (or at least it shouldn't be as open source software works great on windows at 256).
     I suspect it is a hard drive performance issue but that is just a guess.  When playing with hdparm I've got udma and all of the goodies going (I think) but I suspect its not actually working for some reason.

     Anyway, if anybody is having the same problem please ring in and let me know if I'm not alone on this, or if anybody has had the same problem and has a concrete solution also ring in.  Otherwise I'm afraid I'm going to have to wait for a new laptop before getting rid of windows  ](*,)

              Aaron

---

### Post by pjbright on 2005-07-03
Two answers - both addressing RAM issues.  256 MB is a little shy for full gnome functionality.  512 MB would solve the problem, or you could use a light window manager like XFCE to lower memory requirements.  Either one should reduce swap access and significantly improve performance.   Hope that helps.

---

### Post by aburda on 2005-07-03
I'm about to go by somemore RAM anyway, but I'm inclined to think that is not entirely the problem.  First off, the mp3's skip and the movies jump even when there isn't a terrible lot going on.  For example, ubuntu should be able to handle playing an mp3, multitasking/swapping and loading firefox seemlessly.  If it can't do this relatively minor task (even on 256 mb of memory) then it is a crap operating system....since I don't believe this conclusion, something else must be wrong.
      Secondly, (godforgive me, here comes the dreaded windows comparison), I know people say its not possible, but I can (or could until I moved over to gvim and gimp) run Photoshop, Word, Dreamweaver, Firefox and windows media player concurrently on my laptop under windows.  Yea, it would swap a good deal when I would context switch but it was usable.  I can hardly run gthumb, nautilus and gedit without my system going nuts and to be fair these applications should be much "lighter" than the above described windows apps I used to use.
      As I mentioned, I have a great ad hoc PC server/workstation running Linux where I don't have these problems so my inclination is to think at the hardware layer there is some problem between the memory managment or hard drive control and ubuntu/linux.  Either that or my laptop is somehow stuck in low power mode for the processor and hard disk.  I'm totally just guessing, but I can't come up with any other reasons why the performance would be so bad.

         Cheers

         Aaron

---

### Post by mr_mop on 2005-07-08
I was having bad performace on my laptop with ubuntu running Gnome, and XFCE really does help a lot.
I've got a lot more free memory, the boot time is reduced and the system is a whole lot more responsive.  Try it out :)

---

### Post by nocturn on 2005-07-08
Can you try running hdparm tests on your HD

```
sudo hdparm -tT /dev/hda
```

What is the output.

---

### Post by pear-i on 2005-07-08
for the open office issue check out ooqstart - open office quick start  - if you haven't already should be in repositories

of course... with the memory issue... and that applet needing around 20 mb ram might not the exact thing you want right now... 


for the  mp3 skipping i had that problem as well... after i added the multisound patch for ALSA/OSD i found that if i played music in the a player that used default OSD it would be sorta broken up and really garbage... but when i ran the same song / cd off xmms set to ALSA it worked seamlessly... so mp3 codecs / driver might be the source of that issue...

---

### Post by rusi_pathan on 2005-07-08
I run warty on a 1.2 GHz Pentium III with 512 Ram and everything runs like a charm. Once all the programs are loaded my hard disk activity is almost zero.

Try playing with swappiness (/proc/sys/vm/swappiness). Though with 256 MB Ram it may not make much of a difference.

---

### Post by aburda on 2005-07-08
Thanks for everybodies comments,  I went out and bought an additional 512 MB of memory (putting me at 768) the system runs great.  This is actually a bit of a disapointment for me.  I'm a big proponent of making Linux a suitable replacement for Windows.  Most windows users have 256MB of memory and their systems run 'ok.'  My experience with Ubuntu on 256 was really bad (albeit I never changed over to XFCE, but most normal people who install Ubuntu are going to expect it to work and the vast majority of them have no idea what a windows manager is).  Oh well.....my system performance is really good now, but it cost me $100.  

On the hdparm, I've got dma, unmaskirq, multcount = 16 and IO_support  or in a nutshell all of the performance boosters set for my hard disk.  My throughput is 23 MB per second (slower than optimal but it is a laptop).

             Aaron

---

### Post by varunus on 2005-07-08
That's something I've noticed about Linux in general; it runs really well on a slower processor as long as you have RAM.  This of course can be fixed by running XFCE, which zips along despite low RAM, but GNOME only runs full speed if you have 512 or up from my experience.

I suppose this would make it harder for Windows users to switch, but Windows likes having the extra RAM too.  I think with 256, Windows XP will suffer the same performance hit, but it shows itself in different ways.  Linux treats sound as a luxury and will cut into sound performance if it needs CPU power elsewhere, from what I've noticed, whereas in Windows, other things will freeze and the music will keep playing.  512 really needs to become the standard; RAM is really cheap nowadays.

---

### Post by mr_mop on 2005-07-25
[QUOTE=varunus]RAM is really cheap nowadays.[/QUOTE]

Ummm, yes and no.  My laptop can take a 64MB or a 128MB expansion.  The 64 is £17 and the 128 is £100.  Figure that out if you can :(
You can guess which I'm getting:)

---

### Post by WTF_Shelley on 2006-04-25
[QUOTE=mr_mop]Ummm, yes and no.  My laptop can take a 64MB or a 128MB expansion.  The 64 is £17 and the 128 is £100.  Figure that out if you can :(
You can guess which I'm getting:)[/QUOTE]


£100!!!! Sterling? if it for generic sodimm pc133 then kick him in the nuts. That guys ripping you off.

---

### Post by xyz on 2006-04-27
[QUOTE=nocturn]Can you try running hdparm tests on your HD

```
sudo hdparm -tT /dev/hda
```

What is the output.[/QUOTE] 

Sorry for barging in but this is of interest to me. I ran the command you indicated:

> th@meander:~$ sudo hdparm -tT /dev/hda
Password:

/dev/hda:
 Timing cached reads:   792 MB in  2.00 seconds = 395.66 MB/sec
 Timing buffered disk reads:   62 MB in  3.04 seconds =  20.37 MB/sec


Is it any good?
Toshiba Satellite A40
Intel(R) Celeron(R)
512MB 2.70 GHz

---

