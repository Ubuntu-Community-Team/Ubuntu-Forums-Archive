---
title: "Cannot edit audio files (please save the hair on my head)"
date: 2008-09-05
forum: General Help
---

### Post by Arrowx7 on 2008-09-05
Hello,
I have many wav files on my computer.  I can play them all file using mplayer.
However, when I try to open them in audacity (sound editing program) it says it can't recognize the type of the file.  It's a bloody WAV FILE!!!!

This makes no sense.  I tried it with Ardour, and it couldn't open it either.  However I can play them using any player.  Do I need some special package to do this?  However, the mp3 opens fine on audacity.


I tried a different wav file of a song, and it worked!! I know the first set of wav files aren't corrupt because I can play them fine.  What is going on?
Can anyone help me please?

Thanks!

---

### Post by Breakar on 2008-09-05
You may need to install 'ubuntu-restricted-extras' because .wav is a windows media format like .wmv

---

### Post by wolfen69 on 2008-09-05
```
sudo apt-get install w32codecs
``` you may need to add the medibuntu repos first.

---

### Post by Arrowx7 on 2008-09-05
thanks for your replies guys,
I have those packages.

Does anyone have any other ideas?

---

### Post by editrix on 2008-09-06
> **Arrowx7 said:**
> Does anyone have any other ideas?

I have some old .wav files on my HD left over from the Windoze days--some of which play, and some don't. I googled around and found a few similar questions, but so far no answer. Anyway, there are some types of .wav files that don't work on Linux, but I've yet to figure out why.

---

