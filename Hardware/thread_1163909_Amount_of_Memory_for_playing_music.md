---
title: "Amount of Memory for playing music"
date: 2009-05-19
forum: Hardware
---

### Post by thelugnut on 2009-05-19
This is a very general question.

What function does the amount of memory play when playing music?
That is, from the hard disk, from the cd-rom, streaming from the Internet, etc.
My neighbor has a new notebook (ASUS EEEc or something)with 1 GB of memory. She says it isn't enough, because the music breaks up continuously. 
I would have thought that 1 GB would be sufficient, but now I don't know.
Maybe someone could list the requirements for playing music, or provide a link that would explain it.
I would appreciate it very much.

---

### Post by YldGuy on 2009-05-19
> **thelugnut said:**
> This is a very general question.

What function does the amount of memory play when playing music?
That is, from the hard disk, from the cd-rom, streaming from the Internet, etc.
My neighbor has a new notebook (ASUS EEEc or something)with 1 GB of memory. She says it isn't enough, because the music breaks up continuously. 
I would have thought that 1 GB would be sufficient, but now I don't know.
Maybe someone could list the requirements for playing music, or provide a link that would explain it.
I would appreciate it very much.

1 GB is more than enough to play music from her hard disk on her machine. The break in music can be if her cd-rom is scratchy, the cd-rom drive is faulty or the internet is slow.

---

### Post by glotz on 2009-05-19
This is the player I use. [http://mpd.wikia.com/wiki/MusicPlayerDaemonHardwareRequirements](http://mpd.wikia.com/wiki/MusicPlayerDaemonHardwareRequirements)

---

### Post by stderr on 2009-05-19
1GB = Easily sufficient. The audio breaking will almost certainly be down to something else. 

Perhaps advise her to right-click the top panel, click add to panel, and add a System Monitor. Right click the new system monitor, click preferences, and additionally select the Memory option. Then she'll have a visual view of memory usage at all times. If she is not very computer-savvy, you may like to edit the settings in the Memory tab, making all of the assignations the same colour, aside from Free. Then she'll have a quick view of *required* versus *available* memory.

You can even get loads of command line music players. Think about it - how much memory for a standard command line app? Almost none. Then what's it got to do? It needs to keep a small music buffer in RAM, and that's about it. The buffer could be a few MBs... or, more likely, maybe a hundred KB or so. Or less. That's about all the memory requirements of basic music playback.

So, using something like Rhythmbox will increase those requirements somewhat (for graphics, images, interface details, somg database etc), but none of that is huge. We're still talking about a tiny RAM footprint.

Does she have this problem with other audio or audio/visual applications? Of course I'm assuming the music is on HDD; if it's on disc or streaming over the 'net/LAN/whatever, as YldGuy says, the breaking is likely caused by something entirely different!

---

### Post by thelugnut on 2009-05-19
Excellent! I'll relay the info.
Much obliged, as usual.):P

---

