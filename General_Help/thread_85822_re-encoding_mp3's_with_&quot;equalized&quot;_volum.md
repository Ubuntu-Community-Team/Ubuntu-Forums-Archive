---
title: "re-encoding mp3's with &quot;equalized&quot; volume"
date: 2005-11-03
forum: General Help
---

### Post by muszek on 2005-11-03
The problem: my father owns several jukeboxes (running linux :) ) - computer connected to hi-fi hardware, insert-a-coin-and-choose-a-song thing.  The owner of one place that we have a jukebox in keeps complaing about some songs being louder or quieter, which makes him use the remote all the time (while having better things to do).  The problem is that it's impossible to rip all CDs again (1.  I'm not a person who does that, it's outsourced.  2.  It's several hundreds of albums).

So I have to figure out a way to somehow equalize the volume of all mp3's in one directory and all subdirectories.  Do you know of any piece of software that could do that on the fly?  Something that would analyze mp3's and encode them again.

May be a windows soft (I'm willing to make my hands dirty on special occasions ;) ).

---

### Post by bmgz on 2005-11-03
check out a package called _normalize-audio_, apt description says it is for WAV files, but I am pretty sure MP3's works...

---

### Post by sethmahoney on 2005-11-03
There should be a couple programs in Synaptic that will do this.  Have a search for "normalize" and see what comes up.

---

### Post by peterbrowne on 2005-11-03
1. Filename Cleanup

   1.

      Collect all MP3 files in one directory.
   2.

      If any filenames contain spaces, first convert them to underscores:

     for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done 

      This first step is important because, even if unix itself allows spaces in filenames, most programs get confused by them.
   3.

      If your MP3 files came from DOS/Windows, they may have uppercase extensions. You can convert whole names to lowercase or just extensions. For everything lowercase do:

	for i in *.[Mm][Pp]3; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done 

      to convert just extensions:

     for i in *.MP3; do mv "$i" "`basename "$i" .MP3`.mp3"; done

2. Conversion
Convert the files to WAV's
     for i in *.mp3; do madplay -o `basename $i .mp3`.wav $i; done 
run "file *.wav" and check the output for any files that differ from 16 bit, stereo 44100 Hz.

If there are files with different characteristics, convert them to the above specs. For example, to convert file track01.wav to obtain sample rate 44.1 kHz, you could use:

     sox track01.wav -r 44100 track01-new.wav resample
     

or, if the above introduces static when converting mono files:

     sox track01.wav -r 44100 -c 2 track01-new.wav

3. Normalize
     normalize-audio -m *.wav

That should work

---

### Post by peterbrowne on 2005-11-03
or just use mp3gain

---

