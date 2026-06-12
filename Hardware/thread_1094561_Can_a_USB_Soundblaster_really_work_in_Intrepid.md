---
title: "Can a USB Soundblaster really work in Intrepid?"
date: 2009-03-12
forum: Hardware
---

### Post by JerryI on 2009-03-12
I am a new linux user and have been trying unsuccessfully for about 20 hours to get my soundblaster USB card to work.  One article suggested that I put a file named .asoundrc.asoundconf in my home directory (among other things, including setting everything to alsa). The period at the front of the filename puzzles me, but I presume it is correct.


The file has the following text:

pcm.!default {
type hw
card 1
}

ctl.!default {
type hw
card 1
} 

I am new to linux and gedit and do not know how to put something in my home directory.  It seems to demand that I save it into one of the child directories of the home directory such as Documents.

How do I save or move something into my home directory?

---

