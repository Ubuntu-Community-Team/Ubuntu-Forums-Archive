---
title: "Ubuntu 5.04 on a Alienware Area 51m-7700"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by Frank Zappa on 2005-08-19
Hi all...

I just installed ubuntu for the first time on my new alienware area 51m 7700.  At first, the wireless wasn't enabled, but I went and enabled it, and I think it works now.

However, I'm not sure about one thing.  The sound card is still giving me problems.  I don't really know where to begin with it.  When I try to play an MP3 in XMMS, I get the following error:

"Please check that:

Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard"

I don't hear any sound from the speakers at all when in ubuntu... I think this is because my sound card isn't detected.  I think this is like a "realtek" soundcard.

I'm a total n00b to ubuntu, so walk me through.  :-D

Thanks for your help, guys.  So far, I really like this distro.

---

### Post by TristanMike on 2005-08-20
Have you enabled your repositories [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) and proper codecs [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs). These are simple copy/paste commands run from the Terminal.

---

### Post by Lord Illidan on 2005-08-20
Try opening a terminal and write:

```
killall esd
```  before you play an mp3.

---

### Post by Frank Zappa on 2005-08-21
[QUOTE=TristanMike]Have you enabled your repositories [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) and proper codecs [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs). These are simple copy/paste commands run from the Terminal.[/QUOTE]


Yup, this was the first thing I tried.

[QUOTE=Lord Illidan]Try opening a terminal and write:

```
killall esd
```  before you play an mp3.[/QUOTE]

This results in:

```
esd: no process killed
```

---

### Post by sneax on 2005-08-21
When I'm in ubuntu with default setup I also have to do;

killall esd

before i cant make any sound with a program different then what ubuntu has installed (for example cedega), it's a pain in the ass, why can't it just be like windows that different programs can use the same card? or is esd responsable for taking in all the sounds and then mixing it so it seems like coming from one program (esd)? because then esd is doing a pretty bad job to me!

i followed a few 'ALSA' howto's but im very good at breaking things and since i already had to reinstall ubuntu im going to keep the small annoyances like they are and accept how great the rest of the system is :)

---

### Post by Frank Zappa on 2005-08-21
Again, I tried killall esd and got the output saying that no process had been killed... what's up with that?

---

