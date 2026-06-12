---
title: "Need Linux Help!"
date: 2005-11-08
forum: General Help
---

### Post by Brandon14u2 on 2005-11-08
I need to be able to rip multiple tracks into one file at a low bitrate that I can publish to the web.  I have hundreds of cd's of a people speaking that are broken into tracks.  From what I've read about the command line I feel like there should be a way to do so with that.  Or maybe a program.  If not rip it directly then at least combine multiple files into a single continuous one after they've been ripped.  Any help would be GREATLY appreciated.

Brandon

---

### Post by irv on 2005-11-08
The first question I have: are you ripping to MP3 format?
I have been ripping MP3 format files from messages given by Christian speaker for some time now, but have been doing so on a WinXP machine. I am looking for a way to do it on my Linux Breezy 5.10 machine, but have not started my search as of yet. If I find something I will pass it on.

---

### Post by Bachstelze on 2005-11-08
If you can get hold on a Win XP machine (friends, family, work...), iTunes does it very well

---

### Post by zombie.daemon on 2005-11-08
you might want to check out 
[http://bladeenc.mp3.no/skeleton/bladeenc.html]("http://bladeenc.mp3.no/skeleton/bladeenc.html")

it will convert wav to mp3 and let you concat the mp3 files together into one mp3 file

---

### Post by afonic on 2005-11-08
Try Goobox. It should encode to mp3 and ogg. You can find it in Synaptic.

---

### Post by Joe_lurker on 2005-11-08
You can use cdparanoia to rip the tracks, cancatenating them as you rip.  Then use lame to encode them to mp3.  This can be done as one command:
```
cdparanoia -w 1-2 - | lame -b 8 - test.mp3
```
In this example I used cdparanoia to rip a wav file ( -w ) from tracks ( 1-2 )  to stdout ( - ). Then I piped ( | ) the output to lame at a bitrate of 8 ( -b 8 ) from stdin ( - ) out to file test.mp3.

I don't know of a program that has a UI to do this but using the command line is much more fun and powerful.  Look at the man pages for the full power of these commands: 'man cdparanoia' & 'man lame'

-Joe

---

### Post by ssam on 2005-11-08
grip is a very comprehensive graphic cd ripper.

you may need to install lame, which is a mp3 encoder for it to use a back end.

sam

---

### Post by Brandon14u2 on 2005-11-08
Thanks everyone for the help.  I also agree that the command line is more fun, but for someone like me who's just getting into linux, it can be a little daunting.  Of course, it does take me back to my DOS days:)   Thanks again for the help

---

### Post by Brandon14u2 on 2005-11-08
I used the cd paranioa, but when I try to run the resulting file in Muine, then it tells me I'm missing a decoder for the file and I may need to install plugins for it.  Any idea what it's meaning?

Edit - Ok, I got it working.  Was just missing a codec.  In regards to the command line tip.....   THANKS!!!!  That worked perfectly and faster than I could have hoped for.  I can't wait til I have the time to really learn it.

---

