---
title: "[SOLVED] BASH: Multiple input files for ffmpeg"
date: 2008-10-01
forum: General Help
---

### Post by Hiperi0n on 2008-10-01
Hi everyone.

I am trying to write a simple script to recode all the .mp3 files in a folder to 160k using ffmpeg. I have one little problem, I would like the output file to be the same as the input file (rewrite) so ffmpeg warns you about this and asks you for confirmation (y/N). Is there a way to automatically "echo a y and an enter" (sorry for the poor explanation) for every question it asks? I have tryied the yes command but it infinitely prints y and the loop won't finish. This is the code I have written so far:

```

for f in *.mp3; do
   ffmpeg -i $f -ab 160k $f
done

```

Is it possible to do something like this: 

```
ffmpeg -i $f -ab 160k $f & echo -e "y \r"
```

I guess the trick is in the piping/redirection... is the & correct? I know I can avoid this problem simpli not rewriting the original file, but I am curious and would like to enlighten my mind a bit. Thanks. Smile

---

### Post by ibuclaw on 2008-10-01
Do you mean something like this?
```

for mp3 in *.mp3; do
    read -p "overwrite $mp3? " confirm
    [ "$confirm" == "y" ] && echo "YES, Overwrite" || echo "NO, Skipping"
done

```

This won't do anything ffmpeg-wise. But you should have no difficulty in changing it to do so.
The commands after the **&&** is execute if true (you inputted "y" - case sensitive), and the command after the **||** is executed if false (anything else).

Regards
Iain

---

### Post by MusicMastaMike on 2008-10-01
Use the -y option for ffmpeg to force overwrite.

---

### Post by Hiperi0n on 2008-10-01
> Use the -y option for ffmpeg to force overwrite. 

Thanks, I knew there was that option, but I was just curious about the BASH trick of answering yes to all questions.

> Do you mean something like this?
Code:

for mp3 in *.mp3; do
    read -p "overwrite $mp3? " confirm
    [ "$confirm" == "y" ] && echo "YES, Overwrite" || echo "NO, Skipping"
done

This won't do anything ffmpeg-wise. But you should have no difficulty in changing it to do so.
The commands after the && is execute if true (you inputted "y" - case sensitive), and the command after the || is executed if false (anything else).

Thanks tinivole, I have learned a bit more of bash with that, but my question wasn't exactly that. ffmpeg already asks me for confirmation, so I would like to automatically place a "y" and then an enter, or \r (I think), so that would let me skip the question for every rewriting of every mp3 file in the folder and do it automagically (think if there are 100 files...).

I think it is applicable to any program that asks for confirmation, and may not have the typical "dont ask/force" option, and it is just curiosity :D

---

### Post by Hiperi0n on 2008-10-02
Well, I got it solved. redirecting an echo y to the ffmpeg function (echo y | ffmpeg....) works. However as I am overwriting the original file it will not convert it, just the first kBs...

I must change the name of the new files and then replace them with the original audio file names. I guess that will be a piece of cake.

Thanks.

---

### Post by Nyken on 2009-10-31
Just want to say thanks guys for even having this conversation. Linux taught me to love the command line, so was looking for a simple way to convert folder of files from one type to another and this gave me what I needed to start. Just had to customise things a bit.

:D

---

